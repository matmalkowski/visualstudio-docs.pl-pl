---
title: "Praca z metrykami kodów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 39d45f5d43819dc418b6378d34a19e6af1d8ee12
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="working-with-code-metrics-data"></a>Praca z metrykami kodów
**Wyników metryk kodów** okno wyświetla dane, które jest generowany przez analizę metryki kodu. Aby uzyskać więcej informacji na temat wartości danych metryki kodu, zobacz [wartości metryk kodów](../code-quality/code-metrics-values.md).  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Okno wyników metryk kodów](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)  
  
-   [Wyświetlanie wyników metryk kodów](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)  
  
-   [Filtrowanie wyników metryk kodów](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)  
  
-   [Dodawanie, usuwanie i zmienianie rozmieszczenia kolumn danych](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)  
  
-   [Kopiowanie danych do Schowka lub programu Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)  
  
-   [Tworzenie elementu roboczego w oparciu o wyniki metryki kodu](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)  
  
##  <a name="BKMK_CodeMetricsResultsWindow"></a>Okno wyników metryk kodów  
 **Wyników metryk kodów** okien został narzędzi u góry i u kolumny do wyświetlenia wyników obliczeń.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Hierarchii**|**Hierarchii** kolumna zawiera widok drzewa hierarchii kodu, który można rozwinąć lub zwinąć poziom szczegółowości, który chcesz wyświetlić. Pozostałe kolumny zawierają wyników obliczeń. Można ukryć lub porządkowanie kolumn wyników można dowolnie.|  
|**Łatwość konserwacji**|**Utrzymanie** kolumna zawiera ikonę oprócz wyników liczbowych. Zielona ikona wskazuje stosunkowo wysoki stopień łatwość utrzymania. Żółta ikona wskazuje umiarkowane stopień łatwość utrzymania. Czerwona ikona wskazuje niski łatwość utrzymania, a punkt potencjalne problemy. Wskaźniki kolorów te odpowiadają kategorii ważności, które są używane przez reguły programu FxCop AvoidUnmaintainableCode. Ta zasada wyzwala błąd, jeśli indeks łatwości utrzymania jest niższa niż 10, ostrzeżenie, jeśli indeks jest między 10 i 20, a błąd ani ostrzeżenia, jeśli indeks jest większy niż 20. Indeks łatwości utrzymania jest syntezy trzy metryk: złożoność cyklomatyczną o wierszy kodu i złożoność obliczeniową. Wartości nie jest wyrażona w jednostkach.|  
  
##  <a name="BKMK_DisplayingCodeMetricsResults"></a>Wyświetlanie wyników metryk kodów  
 Zostanie wyświetlone okno wyników metryk kodów automatycznie, gdy Generowanie wyników metryk kodów. W dowolnym momencie można również wyświetlić okno.  
  
#### <a name="to-display-the-code-metrics-results-window"></a>Aby wyświetlić okno wyników metryk kodów  
  
-   Na **Analizuj** menu, kliknij przycisk **Windows** , a następnie kliknij przycisk **wyników metryk kodów**.  
  
     \-lub -  
  
-   Na **widoku** menu wskaż **inne okna** , a następnie kliknij przycisk **wyników metryk kodów**.  
  
     Zostanie wyświetlone okno wyników metryk kodów, nawet wtedy, gdy go nie zawiera wyników.  
  
#### <a name="to-view-code-metrics-details"></a>Aby wyświetlić szczegóły metryk kodu  
  
-   Jeśli wyniki metryk kodów zostały wygenerowane, rozwiń drzewo w **hierarchii** kolumny.  
  
##  <a name="BKMK_FilteringCodeMetricsResults"></a>Filtrowanie wyników metryk kodów  
 Możesz filtrować wyniki, które są wyświetlane w **wyników metryk kodów** okna przy użyciu na pasku narzędzi u góry. Na przykład można wyświetlić tylko wyniki, które mają indeks łatwości utrzymania poniżej 65.  
  
 **Filtru** pola rozwijanego zawiera nazwy kolumny wyniki. Jeśli filtr jest zdefiniowana, jest ona dodawana do dolnej części listy wraz z wcięcia. Lista może zawierać dziesięć ostatnich filtry, które zostały zdefiniowane.  
  
#### <a name="to-filter-the-code-metrics-results"></a>Aby filtrować wyniki metryk kodów  
  
1.  Z **filtru** listy, wybierz nazwę kolumny.  
  
2.  W **Min**, wpisz wartość minimalna, który będzie wyświetlany.  
  
3.  W **Max**, wpisz wartość maksymalna, który będzie wyświetlany.  
  
4.  Kliknij przycisk **Zastosuj filtr** przycisku.  
  
5.  Aby wyświetlić szczegóły wyniku, rozwiń węzeł drzewa hierarchii.  
  
##  <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a>Dodawanie, usuwanie i zmienianie rozmieszczenia kolumn danych  
 Można dodać lub usunąć wyniki kolumny z **wyników metryk kodów** okna. Ponadto możesz zmienić kolejność kolumn wyników, aby były wyświetlane w kolejności, która ma.  
  
#### <a name="to-remove-a-column"></a>Aby usunąć kolumnę  
  
1.  Kliknij przycisk **Dodaj/Usuń kolumny** przycisku.  
  
     \-lub -  
  
     Kliknij prawym przyciskiem myszy nagłówek dowolnej kolumny, a następnie kliknij przycisk **Dodaj/Usuń kolumny**.  
  
2.  W **Dodaj/Usuń kolumny** okno dialogowe, wyczyść pole wyboru dla kolumny, które chcesz usunąć, a następnie kliknij przycisk **OK**.  
  
#### <a name="to-add-a-previously-removed-column"></a>Aby dodać kolumnę wcześniej usuniętych  
  
1.  Kliknij przycisk **Dodaj/Usuń kolumny** przycisku.  
  
     \-lub -  
  
     Kliknij prawym przyciskiem myszy nagłówek dowolnej kolumny, a następnie kliknij przycisk **Dodaj/Usuń kolumny**.  
  
2.  W **Dodaj/Usuń kolumny** oknie dialogowym zaznacz pole wyboru dla kolumny, które chcesz dodać, a następnie kliknij przycisk **OK**.  
  
#### <a name="to-rearrange-columns"></a>Aby zmienić kolejność kolumn  
  
1.  Kliknij przycisk **Dodaj/Usuń kolumny** przycisku.  
  
     \-lub -  
  
     Kliknij prawym przyciskiem myszy nagłówek dowolnej kolumny, a następnie kliknij przycisk **Dodaj/Usuń kolumny**.  
  
2.  W **Dodaj/Usuń kolumny** oknie dialogowym Wybierz kolumnę, którą chcesz przenieść, a następnie kliknij przycisk strzałki w górę i Strzałka w dół.  
  
3.  Jeśli kolumna zostanie umieszczona w miejscu, kliknij przycisk **OK**.  
  
##  <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a>Kopiowanie danych do Schowka lub programu Excel  
 Można wybrać i skopiować wybranego wiersza danych metryki kodu do Schowka jako ciąg tekstowy zawierający jedną linię nazwy i wartości wszystkich kolumn danych. Możesz również kliknąć **Otwórz listę w programie Microsoft Excel** Aby wyeksportować wszystkie wyniki metryki kodu do arkusz kalkulacyjny programu Excel  
  
##  <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a>Tworzenie elementu roboczego w oparciu o wyniki metryki kodu  
 Można utworzyć [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] powoduje elementu roboczego, który jest oparty na **wyniki metryki kodu** okna. Po utworzeniu elementu roboczego [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie wprowadzi tytuł w **tytuł** dane metryk pola i kodu w ramach **historii** kartę.  
  
 Aby uzyskać więcej informacji na temat tworzenia elementów roboczych, zobacz [utworzyć elementu roboczego &#91; przekierowanie &#93;](http://msdn.microsoft.com/en-us/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).  
  
#### <a name="to-create-a-work-item-based-on-a-result"></a>Aby utworzyć element roboczy na podstawie wyniku  
  
1.  Kliknij prawym przyciskiem myszy wynik.  
  
2.  Wskaż **Utwórz element roboczy**, a następnie kliknij typ elementu roboczego, w którym chcesz utworzyć (**usterki**, **zadań**, itd).  
  
3.  Ukończ formularza elementu roboczego wypełnić wszystkie wymagane pola.  
  
4.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko** można zapisać elementu roboczego.  
  
#### <a name="to-create-a-bug-based-on-a-result"></a>Można utworzyć na podstawie wyniku usterki  
  
1.  Kliknij przycisk wyników, aby go wybrać.  
  
2.  Kliknij przycisk **Tworzenie elementu roboczego** przycisku.  
  
3.  Ukończ formularza elementu roboczego wypełnić wszystkie wymagane pola.  
  
4.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko** można zapisać elementu roboczego.  
  
## <a name="see-also"></a>Zobacz też  
 [Mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)   
 [Porady: generowanie metryk kodów](../code-quality/how-to-generate-code-metrics-data.md)