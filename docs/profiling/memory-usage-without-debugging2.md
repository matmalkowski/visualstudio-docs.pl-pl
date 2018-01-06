---
title: "Analizowanie użycia pamięci bez debugowania programu VS | Dokumentacja firmy Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e8f4ae16436143999b0a459ba4b039e796f42111
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2018
---
# <a name="analyze-memory-usage-without-the-visual-studio-debugger"></a>Analizowanie użycia pamięci bez debuger programu Visual Studio
Można użyć **użycie pamięci** narzędzia bez debugowania wykonać następujące czynności  
  
-   Monitorowanie aplikacji wykorzystanie pamięci do prawej w programie Visual Studio podczas opracowywania scenariusza.  
  
-   Utwórz szczegółowych migawek stanu pamięci aplikacji.  
  
-   Porównaj migawek, aby znaleźć przyczynę problemy z pamięcią.  
  
 W tym temacie opisano sposób analizowania aplikacji Windows Universal XAML za pomocą narzędzia użycia pamięci. Jeśli chcesz Analiza użycia pamięci w aplikacji uniwersalnych systemu Windows, które JavaScript i HTML, zobacz [Analizowanie użycia pamięci (JavaScript)](http://msdn.microsoft.com/library/windows/apps/jj819176.aspx).  
  
##  <a name="BKMK_Start_a_Memory_Usage_diagnostic_session"></a>Uruchom sesję diagnostyki użycia pamięci  
  
1.  Otwórz projekt C# uniwersalnych systemu Windows w programie Visual Studio.  
  
2.  Na pasku menu wybierz **Debug / profilera wydajności...** .  
  
3.  Wybierz **użycie pamięci** , a następnie wybierz **Start** u dołu strony.  
  
     ![Uruchom sesję diagnostyki użycia pamięci](../profiling/media/memuse_start_diagnosticssession.png "MEMUSE_Start_DiagnosticsSession")  
  
##  <a name="BKMK_Monitor_memory_use"></a>Monitorowanie użycia pamięci  
 Chociaż można używać **użycie pamięci** narzędzie do generowania szczegółowe raporty, które służy do znajdowania i rozwiązywania problemów, należy również służy do pamięci w czasie rzeczywistym skutki scenariusza aktywnie projektujesz.  
  
 Po uruchomieniu sesji diagnostycznej uruchamia aplikację i **narzędzia diagnostyczne** okna wykres oś czasu aplikacji wykorzystanie pamięci.  
  
 ![Strona omówienia użycia pamięci](../profiling/media/memuse__reportoverview.png "MEMUSE__ReportOverview")  
  
 Oś czasu wykresu zawiera wahań pamięci aplikacji, podczas jego wykonywania. Nagłego na wykresie zwykle wskazują, że kod jest zbieranie lub tworzenie danych i odrzucanie ją po zakończeniu przetwarzania. Duże wartości szczytowe wskazują obszary, które można zoptymalizować. Więcej potencjalnie jest wzrost zużycia pamięci, która nie jest zwracany, ponieważ może to oznaczać wykorzystanie pamięci nieefektywne lub nawet przeciek pamięci.  
  
###  <a name="BKMK_Close_a_monitoring_session"></a>Zamykanie sesji monitorowania  
 ![Zatrzymaj zbieranie](../profiling/media/memuse__stopcollection.png "MEMUSE__StopCollection")  
  
 Aby zatrzymać sesji monitorowania bez tworzenia raportu, zamknij okna diagnostyki. Aby wygenerować raport po wykonaniu migawki pamięci, należy wybrać **zatrzymać**.  
  
##  <a name="BKMK_Take_snapshots_to_analyze_the_memory_state_of_your_app"></a>Twórz migawki pamięci stanu aplikacji  
 Jeśli użytkownik stwierdzi, problem pamięci, który chcesz zbadać, można wykonać migawki podczas sesji diagnostycznej do przechwytywania obiektów w pamięci w szczególności momentach. Ponieważ aplikacja używa wielu różnych typów obiektów, możesz skoncentrować się analizy na jednym ze scenariuszy. Jest również dobrym rozwiązaniem do uzyskania migawki linii bazowej aplikacji przed wyświetleniem problem pamięci, kolejną migawkę po pierwszym wystąpieniu problemu i co najmniej jednej migawki dodatkowe Jeśli można powtarzać tego scenariusza.  
  
 Aby zebrać migawki, należy uruchomić nowej sesji diagnostycznej. Wybierz **wykonać migawki** kiedy zachodzi potrzeba przechwytywania danych pamięci. Aby wygenerować raport, należy wybrać **zatrzymać**.  
  
##  <a name="BKMK_Memory_Usage_overview_page"></a>Strona omówienia użycia pamięci  
 Po zatrzymaniu zbierania danych narzędzie użycie pamięci zatrzymuje aplikację i wyświetla Przegląd raport.  
  
 ![Strona omówienia użycia pamięci](../profiling/media/memuse__reportoverview.png "MEMUSE__ReportOverview")  
  
###  <a name="BKMK_Memory_Usage_snapshot_views"></a>Widoki migawki użycia pamięci  
 Widoki migawki umożliwia otwarcie szczegółowe raporty w nowych okien programu Visual Studio. Istnieją dwa rodzaje migawki widoków:  
  
-   A [migawki szczegółowe raporty](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_details_reports) zawiera typy i wystąpienia w jednej migawki.  
  
-   A [migawki raportów różnicowego (diff)](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_difference__diff__reports) porównuje typy i wystąpienia w dwóch migawki.  
  
 ![Wyświetl łącza migawki](../profiling/media/memuse__snapshotview_numbered.png "MEMUSE__SnapshotView_Numbered")  
  
 Ponumerowane elementy w obraz widoku migawki są łącza, które otwierają widoków raportów użycia pamięci.  
  
|||  
|-|-|  
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Tekst łącza wyświetlany całkowita liczba bajtów w pamięci, jeśli migawki.<br /><br /> Wybierz ten link, aby wyświetlić raport szczegóły migawki posortowanej według całkowity rozmiar wystąpienia typu.|  
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|Tekst łącza wyświetlany całkowita liczba obiektów w pamięci, jeśli migawki.<br /><br /> Wybierz ten link, aby wyświetlić raport szczegóły migawki, które jest posortowane według liczby wystąpień typów.|  
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Tekst łącza pokazano różnicę między łączny rozmiar obiektów w pamięci w tej chwili tej migawki i łączny rozmiar poprzednią migawkę.<br /><br /> Jeśli rozmiar pamięci to migawka jest większy niż poprzedniego i liczbą ujemną, gdy rozmiar jest mniejszy, tekstu łącza jest liczbą dodatnią. Tekst łącza **linii bazowej** wskazuje, że ta migawka jest pierwszy w sesji diagnostycznej; **Różnica nie** wskazuje, że różnica wynosi zero.<br /><br /> Wybierz to łącze, aby wyświetlić raport różnicowego migawki posortowanej według różnicy całkowity rozmiar wystąpień typów.|  
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Tekst łącza pokazano różnicę między całkowita liczba obiektów pamięci w tej migawce, a liczba obiektów w poprzednią migawkę.<br /><br /> Wybierz ten link, aby wyświetlić migawki raportu różnicowego, który jest sortowana według różnicy w łącznej liczbie wystąpień typów.|  
  
##  <a name="BKMK_Snapshot_reports"></a>Raporty migawki  
 ![Użycie pamięci migawki raportu](../profiling/media/memuse_snapshotreport_all.png "MEMUSE_SnapshotReport_All")  
  
###  <a name="BKMK_Snapshot_report_trees"></a>Migawki raportu drzewa  
  
####  <a name="BKMK_Managed_Heap"></a>Sterta zarządzana  
 Drzewo stercie zarządzanej [drzewa zarządzanej sterty (szczegóły migawki)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_details_) i [drzewa zarządzanej sterty (diff migawki)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_diff_) Pokaż typy i wystąpienia w raporcie. Wybierając typ lub wystąpienie Wyświetla **ścieżki do katalogu głównego** i **odwołania do obiektów** drzew dla wybranego elementu.  
  
####  <a name="BKMK_Paths_to_Root"></a>Ścieżki do katalogu głównego  
 [Ścieżki do katalogu głównego drzewa (szczegóły migawki)](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_details_) i [ścieżki do katalogu głównego drzewa (diff migawki)](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_diff_) Pokaż łańcucha obiektów, które odwołują się do typu lub wystąpienia. Moduł zbierający elementy bezużyteczne .NET Framework czyści pamięci dla obiekt tylko wtedy, gdy wszystkie odwołania do niego zostały wydane.  
  
####  <a name="BKMK_Referenced_Objects"></a>Obiekty  
 [Drzewa odwołuje się do obiektów (szczegóły migawki)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_details_) i [drzewa odwołuje się do obiektów (diff migawki)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_diff_) wyświetlić obiekty, do których odwołuje się do wybranego typu lub wystąpienia.  
  
###  <a name="BKMK_Object_Type_and_Instance_fields"></a>Pola typu obiektu i wystąpienia  
 Gdy **typ obiektu** wpis ma wpisy podrzędne, można wybrać ikonę strzałki, aby je wyświetlić. Jeśli kolor **typ obiektu** niebieski tekst, użytkownik może przejść do obiektu w pliku kodu źródłowego. Plik źródłowy jest otwarty w osobnym oknie.  
  
 Nazwy są unikatowe identyfikatory, które są generowane przez narzędzie użycie pamięci.  
  
 Jeśli zauważysz typu, który nie może łatwo zidentyfikować lub jeśli nie wiesz, jak zostało ono uwzględnione w kodzie, jest prawdopodobnie obiekt z .NET Framework, systemu operacyjnego lub kompilatora wyświetlający narzędziu użycie pamięci, ponieważ zostało ono uwzględnione w formie własność łańcucha obiekty.  
  
###  <a name="BKMK_Report_tree_filters_"></a>Filtry drzewa raportu  
 Większość aplikacji zawierają zaskakująco dużej liczby typów, z których większość nie są bardzo interesujące Deweloper aplikacji. **Użycie pamięci** narzędzie definiuje dwa filtry, których można użyć, aby ukryć większość tych typów w **zarządzanej sterty** i **ścieżki do katalogu głównego** drzewa. Drzewo można również filtrować według nazwy typu.  
  
 ![Opcje sortowania i filtrowania](../profiling/media/memuse_sortandfilter.png "MEMUSE_SortAndFilter")  
  
####  <a name="BKMK_Filter"></a>Filtr  
 Wprowadź ciąg w **filtru** pole, aby ograniczyć drzewa Wyświetla typy, które zawierają określony tekst. Filtr nie jest rozróżniana wielkość liter i rozpoznaje określonego ciągu w dowolnej części nazwy typu.  
  
####  <a name="BKMK_Collapse_Small_Objects"></a>Zwiń małych obiektów  
 Po zastosowaniu filtru typy, których **rozmiar (w bajtach)** jest mniejszy niż 0,5% całkowitego rozmiaru pamięci migawki są ukryte w **zarządzanej sterty** listy.  
  
####  <a name="BKMK_Just_My_Code"></a>Tylko mój kod  
 **Tylko mój kod** filtru ukrywa największą liczbą wystąpień, które zostały wygenerowane przez kod zewnętrzny. Zewnętrzne typy należą do firmy przez system operacyjny lub składników Framework lub są generowane przez kompilator.  
  
##  <a name="BKMK_Snapshot_details_reports"></a>Raporty szczegóły migawki  
 Raport szczegóły migawki umożliwia skupić się na jednej migawki z sesji diagnostycznej. Aby otworzyć raport szczegóły, wybierz jedną z łącza w widoku migawki, jak pokazano na poniższej ilustracji. Łącza Otwórz ten sam raport; Jedyna różnica polega na początkową kolejność sortowania **zarządzanej sterty** drzewa w raporcie. W obu przypadkach można zmienić kolejność sortowania, po otwarciu raportu.  
  
 ![Łącza do migawki raportu w widoku migawki](../profiling/media/memuse_snapshotview_snapshotdetailslinks.png "MEMUSE_SnapshotView_SnapshotDetailsLinks")  
  
-   **MB** łącze sortuje raport według **całkowity rozmiar (w bajtach)** kolumny.  
  
-   **Obiektów** łącze sortuje raport według **liczba** kolumny.  
  
###  <a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a>Zarządzane drzewo stercie (szczegóły migawki)  
 **Zarządzanej sterty** drzewa zawiera typy obiektów, które są przechowywane w pamięci. Można rozwinąć nazwę typu, aby wyświetlić dziesięć największy wystąpienia typu posortowane według rozmiaru. Wybierając typ lub wystąpienie Wyświetla **ścieżki do katalogu głównego** i **odwołania do obiektów** drzew dla wybranego elementu.  
  
 ![Zarządzane drzewo stercie](../profiling/media/memuse__snapshotdetails_managedheaptree.png "MEMUSE__SnapshotDetails_ManagedHeapTree")  
  
|||  
|-|-|  
|**Typ obiektu**|Nazwa wystąpienia typu lub obiektu.|  
|**Liczba**|Liczba wystąpień obiektu tego typu. Liczba ma zawsze numer 1 dla wystąpienia.|  
|**Rozmiar (w bajtach)**|Dla typu, rozmiaru wszystkie wystąpienia typu migawki pamięci, z wyłączeniem rozmiar obiekty należące do wystąpienia.<br /><br /> Wystąpienie typu, rozmiaru obiektu, z wyłączeniem rozmiar obiektów zawartych w wystąpieniu. wystąpienia.|  
|**Całkowity rozmiar (w bajtach)**|Rozmiar wystąpienia typu lub rozmiaru pojedynczego wystąpienia, takich jak rozmiar zawartych w nim obiektów.|  
  
###  <a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a>Ścieżki do katalogu głównego drzewa (szczegóły migawki)  
 **Ścieżki do katalogu głównego drzewa** zawiera łańcuch obiektów, które odwołują się do typu lub wystąpienia. Moduł zbierający elementy bezużyteczne .NET Framework czyści pamięci dla obiekt tylko wtedy, gdy wszystkie odwołania do niego zostały wydane.  
  
 ![Ścieżki do katalogu głównego drzewa dla typów](../profiling/media/memuse_snapshotdetails_type_pathstoroottree.png "MEMUSE_SnapshotDetails_Type_PathsToRootTree")  
  
 Podczas wyświetlania typu w **ścieżki do katalogu głównego** drzewa, wyświetlana jest liczba obiektów typów, które zawierają odwołania do tego typu w **liczebności referencyjnej** kolumny. Kolumna nie jest widoczna podczas analizowania wystąpienia.  
  
###  <a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a>Przywoływany drzewa obiektów (szczegóły migawki)  
 **Odwołania do obiektów** drzewa zawiera obiekty, do których odwołuje się do wybranego typu lub wystąpienia.  
  
 ![Przywoływany drzewa Objjects dla wystąpień](../profiling/media/memuse_snapshotdetails_referencedobjects_instance.png "MEMUSE_SnapshotDetails_ReferencedObjects_Instance")  
  
|||  
|-|-|  
|**Typ obiektu / wystąpienia**|Nazwa wystąpienia typu lub obiektu.|  
|**Rozmiar (w bajtach)**|Dla typu, rozmiaru wszystkich wystąpień tego typu, z wyłączeniem rozmiar obiektów zawartych w typie.<br /><br /> W przypadku wystąpienia rozmiar obiektu, z wyłączeniem rozmiar obiektów zawartych w tym obiekcie.|  
|**Całkowity rozmiar (w bajtach)**|Całkowity rozmiar wystąpienia typu lub rozmiaru wystąpienia, takich jak rozmiar zawartych w nim obiektów.|  
  
##  <a name="BKMK_Snapshot_difference__diff__reports"></a>Raporty migawki różnica (diff)  
 Migawki raportu różnicowego (diff) zawiera zmiany między podstawowym migawki i migawki, która została wykonana bezpośrednio przed. Aby otworzyć raport różnicowego, wybierz jedną z łącza w widoku migawki, jak pokazano na poniższej ilustracji. Łącza Otwórz ten sam raport; Jedyna różnica polega na początkową kolejność sortowania **zarządzanej sterty** drzewa w raporcie. Po otwarciu raportu, można zmienić kolejności sortowania.  
  
 ![Łącza do różnica raportu w widoku migawki](../profiling/media/memuse_snapshotview_snapshotdifflinks.png "MEMUSE_SnapshotView_SnapshotDiffLinks")  
  
-   **MB** łącze sortuje raport według **całkowity rozmiar (w bajtach)** kolumny.  
  
-   **Obiektów** łącze sortuje raport według **liczba** kolumny.  
  
###  <a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a>Zarządzane drzewa sterty (diff migawki)  
 **Zarządzanej sterty** drzewa zawiera typy obiektów, które są przechowywane w pamięci. Można rozwinąć nazwę typu, aby wyświetlić dziesięć największy wystąpienia typu posortowane według rozmiaru. Wybierając typ lub wystąpienie Wyświetla **ścieżki do katalogu głównego** i **odwołania do obiektów** drzew dla wybranego elementu.  
  
 ![Zarządzane drzewa sterty dla typu w raporcie różnica](../profiling/media/memuse_snapshotdiff_type_heap.png "MEMUSE_SnapshotDiff_Type_Heap")  
  
 Zwróć uwagę, że **liczba**, **rozmiar (w bajtach)**, i **całkowity rozmiar (w bajtach)** kolumny mają zostanie zwinięty obrazu.  
  
|||  
|-|-|  
|**Typ obiektu**|Nazwa wystąpienia typu lub obiektu.|  
|**Liczba**|Liczba wystąpień typu podstawowego migawki. **Liczba** ma zawsze numer 1 dla wystąpienia.|  
|**Liczba różnicowego**|Dla typu różnicę w liczbie wystąpień typu podstawowego migawki i poprzednią migawkę. To pole jest puste w przypadku wystąpienia.|  
|**Rozmiar (w bajtach)**|Rozmiar obiektów w migawce głównej, z wyłączeniem rozmiar obiekty znajdujące się w obiektach. Dla typu **rozmiar (w bajtach)** i **całkowity rozmiar (w bajtach)** są sumy rozmiary wystąpienia typu.|  
|**Diff całkowity rozmiar (w bajtach)**|Dla typu różnicę w całkowity rozmiar wystąpienia typu podstawowego migawki i poprzednią migawkę, z wyłączeniem rozmiar obiekty należące do wystąpienia. To pole jest puste w przypadku wystąpienia.|  
|**Całkowity rozmiar (w bajtach)**|Rozmiar obiektów w migawce podstawowego, takich jak rozmiar obiekty znajdujące się w obiektach.|  
|**Diff całkowity rozmiar (w bajtach)**|Dla typu rozróżnia rozmiar wszystkich wystąpień tego typu podstawowego migawki i poprzednią migawkę, takich jak rozmiar obiekty znajdujące się w obiektach. To pole jest puste w przypadku wystąpienia.|  
  
###  <a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a>Ścieżki do katalogu głównego drzewa (diff migawki)  
 **Ścieżki do katalogu głównego drzewa** zawiera łańcuch obiektów, które odwołują się do typu lub wystąpienia. Moduł zbierający elementy bezużyteczne .NET Framework czyści pamięci dla obiekt tylko wtedy, gdy wszystkie odwołania do niego zostały wydane.  
  
 ![Ścieżki do katalogu głównego drzewa dla wystąpień w widoku różnic](../profiling/media/memuse_snapshotdiff_pathstoroot_instance_all.png "MEMUSE_SnapshotDiff_PathsToRoot_Instance_All")  
  
###  <a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a>Przywoływany drzewa obiektów (diff migawki)  
 **Odwołania do obiektów** drzewa zawiera obiekty, do których odwołuje się do typu podstawowego lub wystąpienia.  
  
 ![Przywoływany drzewa Objjects dla wystąpień](../profiling/media/memuse_snapshotdetails_referencedobjects_instance.png "MEMUSE_SnapshotDetails_ReferencedObjects_Instance")  
  
|||  
|-|-|  
|**Typ obiektu / wystąpienia**|Nazwa wystąpienia typu lub obiektu.|  
|**Rozmiar (w bajtach)**|W przypadku wystąpienia rozmiar obiektu w migawce głównej, z wyłączeniem rozmiar obiektów zawartych w wystąpieniu.<br /><br /> Dla typu całkowitego rozmiaru wystąpień typu podstawowego migawki, z wyłączeniem rozmiar obiektów zawartych w wystąpieniu.|  
|**Całkowity rozmiar (w bajtach)**|Rozmiar obiektów w migawce podstawowego, takich jak rozmiar obiekty znajdujące się w obiektach.|  
  
## <a name="see-also"></a>Zobacz też  
 [Pamięć języka JavaScript](../profiling/javascript-memory.md)  
 [Profilowanie w programie Visual Studio](../profiling/index.md)  
 [Przegląd funkcji profilowania](../profiling/profiling-feature-tour.md)  
 [Najlepsze praktyki wydajności dla aplikacji platformy uniwersalnej systemu Windows przy użyciu języka C++, C# i Visual Basic](http://msdn.microsoft.com/library/windows/apps/hh750313.aspx)   
 [Diagnozowanie problemów związanych z pamięci za pomocą nowego narzędzia użycia pamięci w programie Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=394706)