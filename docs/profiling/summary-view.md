---
title: Widok podsumowania | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.view.summary
helpviewer_keywords:
- performance reports, summary view
- profiling tools reports, Summary view
- profiling tools, Summary view
- Summary view
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
caps.latest.revision: "37"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 552a2c66bd71d83ff1c8cd3453154c065d8bdb3d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="summary-view"></a>Widok podsumowania
Widok podsumowania Wyświetla informacje o wydajności najdroższych funkcji lub obiektów do uruchomienia profilowania. Ten widok udostępnia oś czasu wykresu i dwa lub więcej list najdroższych funkcji lub obiektów oparte na metryk wydajności metodę profilowania. Dane w tym widoku zależy od metody profilowania, która została użyta (próbkowania, Instrumentacji lub współbieżności) i czy został zebrany alokacji pamięci .NET.  
  
 Wszystkie widoki podsumowania oprócz widok podsumowania danych współbieżności wykres osi czasu, w widoku podsumowania przedstawia użycie procesora (CPU) PROFILOWANEGO aplikacji wraz z upływem czasu, który wystąpił profilowania.  
  
-   Jeśli określisz segment czasu na wykresie, możesz Analizuj ponownie dane dla tego segmentu lub powiększenie wyświetlania osi czasu, jak określony segment. Aby uzyskać więcej informacji, zobacz [porady: Filtr widoków raportu z podsumowania osi czasu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)  
  
-   Możesz kliknąć funkcji na liście Widok podsumowania, aby otworzyć widok szczegółów funkcji dla funkcji. Możesz również kliknąć prawym przyciskiem myszy funkcji innych opcji widoku.  
  
-   Aby zmodyfikować liczbę elementów, które są wyświetlane na listach widok podsumowania, otwórz **narzędzia** menu wskaż **opcje**, a następnie kliknij przycisk **narzędzi wydajności**. W obszarze **ustawienia ogólne**, zmodyfikuj **liczba funkcji w widoku Podsumowanie** ustawienie.  
  
## <a name="notifications-links"></a>Łącza powiadomienia  
 Po kliknięciu łącza na liście powiadomień, aby ustawić opcje wyświetlania raportu. Lista jest prawej osi wykresu.  
  
|||  
|-|-|  
|**Pokaż kod niezwiązany z użytkownikiem**<br /><br /> **Pokaż tylko mój kod**|Nie jest dostępna dla kodu natywnego lub danych, który został zebrany przy użyciu metody Instrumentacji profilowania. Przełączenie między wyświetlaniem tylko dane z kodu użytkownika (**Pokaż tylko mój kod**) i wyświetlanie danych z całego kodu, w tym kod systemu (**Pokaż kod niezwiązanego z użytkownikiem**). Domyślnie dane są ograniczone do kodu użytkownika. Aby zmienić ustawienia, zobacz [porady: Filtr profilowania narzędzia widoków raportu w celu wyświetlania tylko mój kod](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md).|  
|**Wskazówki dotyczące widoku**|Wyświetla ostrzeżenia reguły wydajności w **listy błędów** okna. Aby uzyskać więcej informacji, zobacz [przy użyciu reguł wydajności do analizowania danych](../profiling/using-performance-rules-to-analyze-data.md)|  
  
## <a name="report"></a>Raport  
 Po kliknięciu łącza na liście raportów można otworzyć różne widoki i do porównania, Zapisz lub filtrowanie raportu. Lista jest prawej osi wykresu.  
  
|||  
|-|-|  
|**Pokaż przycięte drzewo wywołań**|Wyświetla widok drzewa wywołań najdroższych ścieżek wykonywania. Aby uzyskać więcej informacji, zobacz [widok drzewa wywołań](../profiling/call-tree-view.md).|  
|**Pokaż linie gorąca**|Nie jest dostępny do profilowania dane zebrane przy użyciu metody instrumentacji. Wyświetla najdroższych wierszy kodu źródłowego w widoku wierszy. Aby uzyskać więcej informacji, zobacz [widok linii](../profiling/lines-view.md).|  
|**Porównywanie raportów**|Wyświetla **wybierz pliki analizy do porównania** okno dialogowe, w którym można określić inny plik danych profilowania do porównania z bieżącego pliku. Aby uzyskać więcej informacji, zobacz [porównywanie plików danych wydajności](../profiling/comparing-performance-data-files.md).|  
|**Eksportowanie danych raportu**|Wyświetla **Eksportowanie raportu** okno dialogowe, w którym można określić co najmniej jeden widok raportu można zapisać jako plik wartości rozdzielanych przecinkami (.csv) lub plików XML. Aby uzyskać więcej informacji, zobacz [porady: eksportowanie raportów narzędzi profilowania](http://msdn.microsoft.com/en-us/174b5bd3-df9b-4fd4-88d4-76032ab90451).|  
|**Zapisywanie raportu analizy**|Zapisuje bieżący plik danych profilowania jako plik vsps, który otwiera się szybciej w interfejsie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Aby uzyskać więcej informacji, zobacz [porady: zapisywanie przeanalizowane profilowania pliki danych](http://msdn.microsoft.com/en-us/0340ddde-caf4-48ac-8af3-d15dcdade556).|  
|**Filtrowanie danych raportu**|Wyświetla profilowania okienko filtru raportu, na której możesz określić kryteria, aby ograniczyć dane w widoku raportu. Aby uzyskać więcej informacji, zobacz [filtr widoku raportów wydajności](../profiling/performance-report-view-filter.md)|  
|**Przełącz pełny ekran**|Włącza/wyłącza tryb pełnoekranowy wyświetlania raportu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok podsumowania](../profiling/summary-view-sampling-data.md)   
 [Widok podsumowania](../profiling/summary-view-instrumentation-data.md)   
 [Widok podsumowania](../profiling/summary-view-dotnet-memory-data.md)