---
title: Zdarzenia sterty niestandardowych ETW natywnego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/24/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- C++
ms.workload:
- cplusplus
ms.openlocfilehash: 5b927260f505640eb6dc3c74d00dc3ee382d9f76
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="custom-native-etw-heap-events"></a>Zdarzenia sterty niestandardowych natywnego ETW

Visual Studio zawiera szereg [profilowania i narzędzia diagnostyczne](../profiling/profiling-tools.md), tym profilera natywnej pamięci.  Ten program profilujący przechwytuje [zdarzenia ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) od dostawcy sterty i umożliwia analizę sposobu pamięci są przydzielone i używane.  Domyślnie to narzędzie można analizować tylko przydziałów wykonanych ze standardowego stosu systemu Windows, a poza tym natywnej sterty alokacje nie będzie wyświetlana.

Istnieje wiele przypadków, w których warto użyć własnych niestandardowych sterty i uniknąć zadań alokacji ze standardowego stosu.  Na przykład można użyć [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) można przydzielić dużej ilości pamięci podczas uruchamiania aplikacji i gier, a następnie Zarządzaj własne bloki w obrębie tej listy.  W tym scenariuszu narzędzie pamięci profilera byłaby widoczna tylko tej początkowej alokacji i nie niestandardowych zarządzania infrastrukturą wykonać wewnątrz fragmentu pamięci.  Jednak przy użyciu niestandardowego natywnej sterty ETW dostawcę, możesz pozwolić, aby wiedzieć o alokacje tworzonego poza standardowe sterty narzędzie.

Na przykład w projekcie podobnie do następującej gdzie `MemoryPool` jest niestandardowe sterty, byłaby widoczna tylko jednego alokacji w stercie systemu Windows:

```cpp
class Foo
{
public:
    int x, y;
};

...

// MemoryPool is a custom managed heap, which allocates 8192 bytes 
// on the standard Windows Heap named "Windows NT"
MemoryPool<Foo, 8192> mPool;

// the "allocate" method requests memory from the pool created above
// and is cast to an object of type Foo, shown above
Foo* pFoo1 = (Foo*)mPool.allocate();
Foo* pFoo2 = (Foo*)mPool.allocate();
Foo* pFoo3 = (Foo*)mPool.allocate();
```

Migawka [użycie pamięci](../profiling/memory-usage.md) narzędzia bez sterty niestandardowych śledzenia pokazuje, tylko alokacji jednobajtowych 8192 i żadne niestandardowe alokacje wysyłanych przez pulę:

![Alokacja sterty systemu Windows](media/heap-example-windows-heap.png)

Wykonując poniższe kroki, możemy użyć tego samego narzędzia do śledzenia usgae pamięci w naszym sterty niestandardowych.

## <a name="how-to-use"></a>Sposób użycia

Ta biblioteka można łatwo C i C++.

1. Dołącz nagłówek dla dostawcy ETW stosu niestandardowych:

   ```cpp
   #include <VSCustomNativeHeapEtwProvider.h>
   ```

1. Dodaj `__declspec(allocator)` dekoratora żadnych funkcji zwracającej wskaźnik do pamięci sterty nowoprzydzielonych menedżera sterty niestandardowych.  Ta dekoratora umożliwia narzędzie poprawnie zidentyfikować typ pamięci zostały zwrócone.  Na przykład:

   ```cpp
   __declspec(allocator) void *MyMalloc(size_t size);
   ```
   
   > [!NOTE]
   > Ten dekoratora informuje kompilator, czy ta funkcja jest wywołaniem do przydzielania.  Każde wywołanie funkcji dane wyjściowe obejmują adres callsite, rozmiar instrukcji wywołania i identyfikator nowego obiektu do nowego `S_HEAPALLOCSITE` symbolu.  Przy nadawaniu stos wywołań systemu Windows będzie Emituj zdarzenia ETW z tymi informacjami.  Narzędzie pamięci profilera przeprowadzi stos wywołań, wyszukiwanie pasujący adres zwrotny `S_HEAPALLOCSITE` symboli i informacji typeId symbol jest używany do wyświetlania typu środowiska uruchomieniowego alokacji.
   >
   > Krótko mówiąc, oznacza to, że wywołanie, która wygląda jak `(B*)(A*)MyMalloc(sizeof(B))` będą widoczne w narzędziu jako typu `B`, a nie `void` lub `A`.

1. Dla języka C++, Utwórz `VSHeapTracker::CHeapTracker` obiektu, podając nazwę sterty, które będzie widoczne w narzędziu profilowania:

   ```cpp
   auto pHeapTracker = std::make_unique<VSHeapTracker::CHeapTracker>("MyCustomHeap");
   ```

   Jeśli używasz C, użyj `OpenHeapTracker` zamiast tego działania.  Ta funkcja zwróci uchwytu, która będzie używana przy wywoływaniu innych funkcji śledzenia:
  
   ```C
   VSHeapTrackerHandle hHeapTracker = OpenHeapTracker("MyHeap");
   ```

1. Podczas przydzielania pamięci funkcja niestandardowe, należy wywołać `AllocateEvent` (C++) lub `VSHeapTrackerAllocateEvent` — metoda (C), przekazując wskaźnik do pamięci i rozmiar alokacji śledzenia:

   ```cpp
   pHeapTracker->AllocateEvent(memPtr, size);
   ```

   lub

   ```C
   VSHeapTrackerAllocateEvent(hHeapTracker, memPtr, size);
   ```

   > [!IMPORTANT]
   > Nie zapomnij tagu funkcji niestandardowych alokatora z `__declspec(allocator)` dekoratora opisany wcześniej.

1. Gdy dealokowanie pamięci funkcja niestandardowe, należy wywołać `DeallocateEvent` (C++) lub `VSHeapTracerDeallocateEvent` — funkcja (C), przekazując wskaźnik do pamięci, aby śledzić dezalokacji:

   ```cpp
   pHeapTracker->DeallocateEvent(memPtr);
   ```

   lub:

   ```C
   VSHeapTrackerDeallocateEvent(hHeapTracker, memPtr);
   ```

1. Podczas ponownego przydzielania pamięci funkcja niestandardowe, należy wywołać `ReallocateEvent` (C++) lub `VSHeapReallocateEvent` — metoda (C), przekazując wskaźnik do nowej pamięci, rozmiar alokacji i wskaźnika do starego pamięci:

   ```cpp
   pHeapTracker->ReallocateEvent(memPtrNew, size, memPtrOld);
   ```

   lub:

   ```C
   VSHeapTrackerReallocateEvent(hHeapTracker, memPtrNew, size, memPtrOld);
   ```

1. Na koniec, aby zamknąć i wyczyścić śledzenia sterty niestandardowe w języku C++, użyj `CHeapTracker` destruktor, ręcznie lub za pośrednictwem standardowych reguł zakresu, lub `CloseHeapTracker` funkcji w C:

   ```cpp
   delete pHeapTracker;
   ```

   lub:

   ```C
   CloseHeapTracker(hHeapTracker);
   ```

## <a name="tracking-memory-usage"></a>Śledzenie użycia pamięci
Z tych wywołań w miejscu użycie niestandardowego sterty teraz można śledzić za pomocą standardowego **użycie pamięci** narzędzia w programie Visual Studio.  Aby uzyskać więcej informacji na temat korzystania z tego narzędzia, zobacz [użycie pamięci](../profiling/memory-usage.md) dokumentacji. Upewnij się, że włączono profilowanie sterty z migawkami, w przeciwnym razie nie będzie mógł przeglądać użycie niestandardowego sterty wyświetlane. 

![Włącz profilowanie sterty](media/heap-enable-heap.png)

Aby wyświetlić Twoje niestandardowe stosu śledzenia, użyj **sterty** listy rozwijanej znajdujący się w prawym górnym rogu **migawki** okno, aby zmienić widok z *sterty NT* do własnych stosu jako o nazwie wcześniej.

![Wybór sterty](media/heap-example-custom-heap.png)

Za pomocą powyższego przykładu kodu z `MemoryPool` tworzenie `VSHeapTracker::CHeapTracker` obiektu i własnej `allocate` obecnie podczas wywoływania metody `AllocateEvent` metody, możesz teraz przeglądać wynik tej niestandardowej alokacji pokazujący 3 wystąpień sumowanie 24 bajty typu `Foo`.

Wartość domyślna *sterty NT* sterty wygląda tak samo jak wcześniej, dodając nasze `CHeapTracker` obiektu.

![Stos śledzenia, NT](media/heap-example-windows-heap.png)

Tak jak z standardowe sterty systemu Windows, można użyć tego narzędzia do porównywania migawki i wyszukaj przecieki lub uszkodzenie w niestandardowych sterty, który jest opisany w głównym [użycie pamięci](../profiling/memory-usage.md) dokumentacji.

> [!TIP]
> Visual Studio zawiera także **użycie pamięci** narzędzie w **profilowanie wydajności** zestawu narzędzi, które można włączyć **debugowania > wydajności programu profilującego** opcji menu lub **Alt + F2** klawiatury kombinacji.  Ta funkcja nie obejmuje śledzenia stosu i nie będzie wyświetlany na Twojej niestandardowych sterty, zgodnie z opisem w tym miejscu.  Tylko **narzędzia diagnostyczne** okna, które można włączyć za **debugowania > Windows > Pokaż narzędzia diagnostyczne** menu lub **Ctrl + Alt + F2** klawiatury kombinacja, zawiera tę funkcję.

## <a name="see-also"></a>Zobacz też
[Narzędzia profilowania](../profiling/profiling-tools.md)  
[Użycie pamięci](../profiling/memory-usage.md)
