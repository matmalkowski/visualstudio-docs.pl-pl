---
title: "Filtrowanie widoków raportów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, configuring
ms.assetid: 820cf192-7fd6-4bee-9a51-aa69154aca85
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b4e82450286d5da47a11217401ebbc17133530b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="filtering-report-views"></a>Filtrowanie widoków raportów
Filtry można stosować do profilowania pliki danych, aby ograniczyć dane profilowania, który jest wyświetlany w widokach raport o wydajności i wyeksportowane pliki raportu. Można ograniczyć raportu do danych między wartości sygnatur czasowych, i umożliwia ograniczenie danych do określonych procesów i wątków. Można zapisać do pliku filtrów i utworzenie filtru na inny plik danych profilowania przez zaimportowanie zapisany filtr.  
  
 Można również ograniczyć raport do segmentu czasu za pomocą graficznego osi czasu w widoku Podsumowanie. Zobacz [porady: filtrowanie widoków raportu z podsumowania osi czasu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
 Aby wykluczyć z raportu systemu i kod innych firm, zobacz [porady: Filtr profilowania narzędzia widoków raportu w celu wyświetlania tylko mój kod](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-profiler-report-filter"></a>Aby utworzyć filtr raportów profilera  
  
1.  Jeśli nie zostanie wyświetlone okno Filtr widoku raportów wydajności, kliknij przycisk **Pokaż filtru** na pasku narzędzi w widoku raportu wydajności.  
  
     Filtr widoku raportów wydajności znajduje się tabela. Każdy wiersz w tabeli reprezentuje klauzuli filtru. Możesz dodać dowolną liczbę klauzul do filtru.  
  
2.  Dla każdej klauzuli, który chcesz dodać do filtru wybierz lub wprowadź wartości w polach następującego wiersza.  
  
    |Pole|Opis|  
    |-----------|-----------------|  
    |**I/lub**|Wybierz **i** Jeśli klauzulę i dalej klauzula musi być true na zgodny wynik. Wybierz **lub** Jeśli klauzulę lub klauzuli dalej może być true na zgodny wynik.|  
    |**Pole**|Wybierz pole raportu można użyć w klauzuli filtru na wyświetlonej liście pól danych.|  
    |**Operator**|Wybierz operator, który określa relacji, który ma w klauzuli między pola i wartości.<br /><br /> = Równa się<br /><br /> <> Nie równa się<br /><br /> < Mniej niż<br /><br /> > Większa niż<br /><br /> < = mniejsza niż lub równe<br /><br /> > = większe lub równe|  
    |**Wartość**|Wybierz lub wprowadź wartość do wyszukania. Niektóre pola listy dostępnych wartości dla pola.|  
  
3.  
  
#### <a name="to-create-a-profiler-report-filter-from-the-marks-report-view"></a>Aby utworzyć filtr raportów profilera z widoku raportu znaków  
  
1.  Wybierz **znaczniki** z **bieżący widok** listy na pasku narzędzi w widoku raportu wydajności.  
  
     Zostanie wyświetlony raport profilera znaków.  
  
2.  Wybierz ETW lub próbkowania nawet, który ma być używany jako punkt początkowy raportu.  
  
3.  Naciśnij i przytrzymaj klawisz CTRL i kliknij zdarzenie, które ma być używany jako punkt końcowy raportu.  
  
4.  Kliknij prawym przyciskiem myszy, a następnie kliknij jedną z następujących opcji:  
  
    -   **Dodaj filtr do znaczników** tworzy klauzul filtru, korzystających z kolumny Oznacz jako pole filtru.  
  
    -   **Dodaj filtr do sygnatury czasowe** tworzy klauzul filtru, korzystających z kolumny znaczników czasu w milisekundach jako pole filtru.  
  
     Istnieją dwie opcje filtrowania bieżący plik danych w tej samej punktu początkowego i końcowego. Jedną z opcji może lepszym rozwiązaniem byłoby eksportowania filtr, aby użyć innych raportów.  
  
#### <a name="to-load-an-existing-filter-from-a-file"></a>Aby załadować istniejący filtr z pliku  
  
1.  Kliknij na pasku narzędzi w widoku raportu wydajności **Filtr importu**.  
  
     **Ładowanie filtru** zostanie wyświetlone okno dialogowe.  
  
2.  Określ lokalizację i nazwę pliku filtru (.vspf) do załadowania.  
  
#### <a name="to-execute-a-filter"></a>Aby wykonać filtru  
  
-   Kliknij na pasku narzędzi w widoku raportu wydajności **wykonania filtru**.  
  
#### <a name="to-stop-a-filter-that-is-taking-too-long-to-execute"></a>Aby zatrzymać filtr, który trwa zbyt długo, można wykonać  
  
-   Kliknij na pasku narzędzi w widoku raportu wydajności **zatrzymać filtru**.  
  
#### <a name="to-remove-a-filter-on-a-report-view"></a>Aby usunąć filtr w widoku raportu  
  
1.  Usuń wiersze klauzule filtr widoku raportów wydajności.  
  
2.  Kliknij na pasku narzędzi w widoku raportu wydajności **wykonania filtru**.  
  
#### <a name="to-save-a-filter-to-a-file"></a>Aby zapisać filtr do pliku  
  
1.  Kliknij na pasku narzędzi w widoku raportu wydajności **wyeksportować filtru**.  
  
     **Zapisywanie filtru** zostanie wyświetlone okno dialogowe.  
  
2.  Określ lokalizację i nazwę pliku filtru (.vspf), aby zapisać.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie wydajności widoków raportów narzędzi](../profiling/customizing-performance-tools-report-views.md)