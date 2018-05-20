---
title: Zobacz zależności między pliki źródłowe C++ i pliki nagłówkowe
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: d274241700dfdac393544f554f7025ea4d0bcb46
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="code-maps-for-c-projects"></a>Mapy kodu dla projektów C++

Jeśli chcesz utworzyć bardziej szczegółowy mapy dla projektów C++, ustaw opcję kompilatora informacji o przeglądaniu (**/FR**) na tych projektów. W przeciwnym razie pojawi się komunikat i monit o ustawienie tej opcji. W przypadku wybrania **OK**, to ustawienie opcji dla bieżącej mapy. Można ukryć w komunikacie wszystkie nowsze mapy.

Po otwarciu rozwiązania, które zawiera projekty Visual C++, aktualizacja bazy danych w technologii IntelliSense może zająć trochę czasu. W tym czasie nie można utworzyć mapy kodu dla nagłówka (*.h* lub `#include`) pliki zakończenie bazy danych IntelliSense aktualizacji. Można monitorować postęp uaktualnienia na pasku stanu programu Visual Studio.

- Aby wyświetlić zależności między wszystkie pliki źródłowe i pliki nagłówkowe w rozwiązaniu, wybierz **architektura** > **Generuj wykres z pliki dołączane**.

   ![Wykres zależności dla kodu natywnego](../modeling/media/dependencygraphgeneral_nativecode.png)

- Aby wyświetlić zależności między aktualnie otwarty plik i pliki źródłowe pokrewne i pliki nagłówkowe, otwórz plik źródłowy lub plik nagłówka. Otwórz menu skrótów pliku dowolne miejsce w pliku. Wybierz **Generowanie grafu plików dołączanych**.

   ![Wykres zależności pierwszego stopnia dla pliku .h](../modeling/media/dependencygraph_native_firstlevel.png)

## <a name="troubleshoot-code-maps-for-c-and-c-code"></a>Rozwiązywanie problemów z mapy kodu dla kodu C i C++

Te elementy nie są obsługiwane dla kodu C i C++:

- Typy podstawowe nie pojawiają się w społeczności maps, które obejmują hierarchii nadrzędnej.

- Większość **Pokaż** elementy menu są niedostępne dla kodu C i C++.

Te problemy mogą wystąpić podczas tworzenia mapy kodu dla kodu C i C++:

|**Problem**|**Możliwa przyczyna**|**Rozdzielczość**|
|---------------|------------------------|--------------------|
|Nie można wygenerować mapy kodu.|Żadne projekty w rozwiązaniu nie zostały pomyślnie skompilowane.|Błędy kompilacji, które wystąpiły, a następnie ponownie wygenerować mapy.|
|Visual Studio przestaje odpowiadać podczas próby Generuj mapę kodu z **architektura** menu.|Plik bazy danych programu (.pdb) może być uszkodzony.<br /><br /> Plik .pdb przechowuje informacje debugowania, takie jak typ, metoda i informacje o pliku źródłowym.|Kompiluj rozwiązanie ponownie, a następnie spróbuj jeszcze raz.|
|Niektóre ustawienia dla bazy danych przeglądania IntelliSense są wyłączone.|Niektóre ustawienia IntelliSense może być wyłączone w programie Visual Studio **opcje** okno dialogowe.|Włącz te ustawienia.<br /><br /> Zobacz [opcje, Edytor tekstu, C/C++, zaawansowane](../ide/reference/options-text-editor-c-cpp-advanced.md).|
|Komunikat **nieznanych metod** pojawia się w węźle metody.<br /><br /> Ten problem występuje, ponieważ nie można rozpoznać nazwy metody.|Plik binarny może nie mieć podstawowej tabeli relokacji.|Włącz **/Fixed: No** opcji w konsolidatorze.|
||Plik bazy danych programu (.pdb) może nie być skompilowany.<br /><br /> Plik .pdb przechowuje informacje debugowania, takie jak typ, metoda i informacje o pliku źródłowym.|Włącz **/DEBUG** opcji w konsolidatorze.|
||Nie można otworzyć lub znaleźć pliku .pdb w oczekiwanych lokalizacjach.|Upewnij się, że plik .pdb istnieje w oczekiwanych lokalizacjach.|
||Informacje o debugowaniu pochodzą z pliku .pdb.|Jeśli **/pdbstripped** użyto opcji w konsolidatorze, zamiast tego zawiera cały plik PDB.|
||Obiekt wywołujący nie jest funkcją i jest albo osadzony w pliku binarnym, albo stanowi wskaźnik w sekcji danych.|Gdy obiekt wywołujący jest sekcją thunk, spróbuj użyć `_declspec(dllimport)` w celu uniknięcia thunk.|

## <a name="see-also"></a>Zobacz także

- [Zależności mapy z mapy kodu](../modeling/map-dependencies-across-your-solutions.md)