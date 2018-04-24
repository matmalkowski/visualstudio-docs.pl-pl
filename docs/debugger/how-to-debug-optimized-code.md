---
title: 'Porady: debugowanie zoptymalizowanego kodu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, in optimized code
- debugging [C++], optimized code
- optimization, debug builds
- debug builds, optimizing
- optimized code, debugging
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9610f71a197c47521e2139d40aff1afde6a8a894
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-debug-optimized-code"></a>Porady: debugowanie zoptymalizowanego kodu
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz polecenie Import i eksport ustawień w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
> [!NOTE]
>  [/Zo (zwiększenia zoptymalizowanych pod kątem debugowania)](/cpp/build/reference/zo-enhance-optimized-debugging)— opcja kompilatora (wprowadzona w programie Visual Studio Update 3) generuje bardziej rozbudowane informacje debugowania zoptymalizowanego kodu (projektów, które nie zostały skompilowane z **/Od** — Opcja kompilatora. Zobacz [/O opcje (Optymalizuj kod)](/cpp/build/reference/o-options-optimize-code)). W tym ulepszoną obsługę debugowania zmiennych lokalnych i funkcji śródwierszowych.  
>   
>  [Edytuj i Kontynuuj](../debugger/edit-and-continue-visual-csharp.md) jest wyłączona, gdy **/Zo** jest używana opcja ocompiler.  
  
 Gdy kompilator optymalizuje kod, zmiana i Reorganizuje instrukcje. Powoduje to efektywniejsze skompilowanego kodu. Ze względu na to rozmieszczania debuger nie może zidentyfikować zawsze kodu źródłowego, umożliwiająca zestaw instrukcji.  
  
 Optymalizacja może mieć wpływ na:  
  
-   Zmienne lokalne, które mogą zostać usunięte przez optymalizator lub przenieść do lokalizacji, których nie rozpoznaje debugera.  
  
-   Położenie wewnątrz funkcji, które są zmieniane po Optymalizator scala bloków kodu.  
  
-   Nazwy funkcji ramek na stosie wywołań, która może być nieprawidłowy, jeśli Optymalizator scala dwie funkcje.  
  
 Ramek, które są wyświetlane w stosie wywołań są prawie zawsze poprawne, jednak przy założeniu, że masz symboli dla wszystkie ramki. Ramek na stosie wywołań będą nieprawidłowe, jeśli masz uszkodzenie stosu, jeśli masz napisane w języku zestawu funkcji lub jeśli istnieją ramki systemu operacyjnego bez pasującego symboli w stosie wywołań.  
  
 Zmienne globalne i statyczne są zawsze wyświetlane prawidłowo. Dlatego jest układ struktury. Jeśli masz wskaźnika do struktury i wartość wskaźnika jest poprawna, co zmiennej członkowskiej struktury wyświetli poprawną wartość.  
  
 Ze względu na ograniczenia te powinny debugowania, jeśli to możliwe przy użyciu zoptymalizowanego wersji programu. Domyślnie Optymalizacja jest wyłączone w konfiguracji debugowania programu Visual C++ i włączone w konfiguracji wydanie.  
  
 Jednak błąd może występować tylko w zoptymalizowanej wersji programu. W takim przypadku należy debugowania zoptymalizowanego kodu.  
  
### <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>Aby włączyć funkcję Konfiguracja kompilacji optymalizacji podczas debugowania  
  
1.  Podczas tworzenia nowego projektu, zaznacz `Win32 Debug` docelowej. Użyj `Win32``Debug` docelowe, dopóki program pełni debugowania i wszystko jest gotowe do tworzenia `Win32 Release` docelowej. Kompilator nie optymalizuje `Win32 Debug` docelowej.  
  
2.  Wybierz projekt w Eksploratorze rozwiązań.  
  
3.  Na **widoku** menu, kliknij przycisk **strony właściwości**.  
  
4.  W **strony właściwości** okna dialogowego upewnij się, `Debug` wybrano **konfiguracji** listy rozwijanej.  
  
5.  W widoku folderów po lewej stronie wybierz **C/C++** folderu.  
  
6.  W obszarze **C++** folderu, wybierz opcję `Optimization`.  
  
7.  Na liście po prawej stronie właściwości znaleźć `Optimization`. Ustawienie obok niej prawdopodobnie mówi `Disabled (` [/Od](/cpp/build/reference/od-disable-debug)`)`. Wybierz jedną z opcji (`Minimum Size``(`[/O1](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Maximum Speed``(` [/O2](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Full Optimization``(` [ox](/cpp/build/reference/ox-full-optimization) `)`, lub `Custom`).  
  
8.  Jeśli została wybrana opcja `Custom` opcja dla `Optimization`, można teraz ustawić opcje dla innych właściwości wyświetlane na liście właściwości.  
  
9. Wybierz pozycję Właściwości konfiguracji, C/C++, węzeł wiersza polecenia strony właściwości projektu i dodać `(` [/Zo](/cpp/build/reference/zo-enhance-optimized-debugging) `)` do **dodatkowe opcje** pola tekstowego.  
  
    > [!WARNING]
    >  `/Zo` wymaga programu Visual Studio 2013 Update 3 lub nowszym.  
    >   
    >  Dodawanie `/Zo` spowoduje wyłączenie [Edytuj i Kontynuuj](../debugger/edit-and-continue-visual-csharp.md).  
  
 Podczas debugowania zoptymalizowanego kodu, użyj **dezasemblacji** okna, aby zobaczyć, jakie instrukcje faktycznie są tworzone i wykonywane. W przypadku ustawienia punktów przerwania, musisz wiedzieć, że punkt przerwania może przenosić wraz z instrukcji. Rozważmy na przykład następujący kod:  
  
```  
for (x=0; x<10; x++)  
```  
  
 Załóżmy, że Ustaw punkt przerwania w tym wierszu. Może spodziewać się punkt przerwania są osiągane 10 razy, ale jeśli kod jest zoptymalizowany, punkt przerwania zostaje trafiony tylko jeden raz. Wynika to z pierwszej instrukcji, która ustawia wartości `x` na 0. Kompilator rozpoznaje, że to tylko musi odbywać się jeden raz i przenosi ją poza pętli. Punkt przerwania przenoszona razem z nim. Instrukcje porównywania i zwiększyć `x` pozostają w pętli. Po wyświetleniu **dezasemblacji** okna, [jednostka kroku](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9) jest automatycznie ustawiana instrukcji większej kontroli, co jest przydatne, gdy krokowo zoptymalizowanego kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)