---
title: Analizowanie użycia pamięci w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 04/25/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 38f4457146f8373ad0e4ce3a5477c98a43424538
ms.sourcegitcommit: 064f8678f4a918e1dce60285090a9803d37dc34b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2018
---
# <a name="profile-memory-usage-in-visual-studio"></a>Użycie pamięci profil w programie Visual Studio
Wyszukiwanie przecieków pamięci i nieefektywne pamięci podczas debugowania kodu z debugera zintegrowane **użycie pamięci** narzędzia diagnostycznego. Narzędzie umożliwia wykorzystanie pamięci, należy wykonać co najmniej jeden *migawki* zarządzanego i natywnego pamięci sterty ułatwi zrozumienie wpływu użycia pamięci typy obiektów. Można zbierać migawki .NET, Tryb natywny lub mieszane (.NET i natywnego) aplikacji.  
  
 Poniżej przedstawiono graficzne **narzędzia diagnostyczne** okna (dostępnej w programie Visual Studio 2015 Update 1 lub nowszy):  
  
 ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
 Mimo że można zbierać migawki pamięci w dowolnym momencie w **użycie pamięci** narzędzia, debuger programu Visual Studio można użyć do kontrolowania sposobu wykonuje aplikacji podczas badania problemów z wydajnością. Ustawianie punktów przerwania, wykonywanie krok po kroku, Przerwij wszystkie i inne akcje debuger może pomóc skupić się z badania wydajności ścieżki kodu, które są najbardziej odpowiednie. Wykonanie tych czynności uruchomionej aplikacji można wyeliminować szumu z kodu, który nie interesują użytkownika i może znacznie zmniejszyć ilość czasu, jaki zajmuje zdiagnozować problem.  
  
 Można także użyć narzędzia pamięci poza debugerem. Zobacz [użycia pamięci bez debugowania](../profiling/memory-usage-without-debugging2.md).  
  
> [!NOTE]
>  **Niestandardowe Obsługa alokatora** natywnej pamięci profilera polega na zbieranie alokacji [ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) dane zdarzeń emitowane przez w czasie wykonywania.  Allocators — w CRT i zestaw Windows SDK ma zostały adnotacji na poziomie źródła, dzięki czemu można przechwycić swoje dane alokacji.  Jeśli piszesz własne allocators —, a następnie ozdobione wszystkie funkcje, które zwraca wskaźnik do pamięci sterty nowoprzydzielonych [__declspec](/cpp/cpp/declspec)(alokatora), jak pokazano w następującym przykładzie myMalloc:  
>   
>  `__declspec(allocator) void* myMalloc(size_t size)` 

W tym samouczku obejmują:

> [!div class="checklist"]
> * Twórz migawki pamięci
> * Analizowanie danych użycia pamięci

## <a name="collect-memory-usage-data"></a>Zbieranie danych użycia pamięci

1.  Otwórz projekt, który ma być debugowania w programie Visual Studio i ustaw punkt przerwania w aplikacji w momencie, gdy ma się rozpocząć badanie użycia pamięci.

    Jeśli masz obszar, w którym podejrzewasz problem pamięci, należy ustawić pierwszy punkt przerwania przed wystąpieniem problemu pamięci.

    > [!TIP]
    >  Ponieważ może być wyzwaniem profilu pamięci interesującego często przydzielanie przez aplikację i zwalnia pamięć operacji przechwytywania, ustaw punkty przerwania na początek i koniec operacji (lub kroków operacji) można znaleźć dokładnie punktu pamięć zmianie. 

2.  Ustaw punkt przerwania drugi na końcu funkcji lub regionu, kodu, który chcesz przeanalizować (lub po wystąpieniu problemu podejrzanych pamięci).
  
3.  **Narzędzia diagnostyczne** okna pojawiają się automatycznie, jeśli wyłączono go. Aby wyświetlić okno ponownie, kliknij przycisk **Debug / Windows / Pokaż narzędzia diagnostyczne**.

4.  Wybierz **użycie pamięci** z **wybierz narzędzia** ustawienie na pasku narzędzi.

     ![Pokaż narzędzia diagnostyczne](../profiling/media/DiagToolsSelectTool.png "DiagToolsSelectTool")

5.  Kliknij przycisk **Debug / Rozpocznij debugowanie** (lub **Start** na pasku narzędzi lub **F5**).

     Po zakończeniu ładowania aplikacji zostanie wyświetlony widok podsumowania narzędzi diagnostycznych.

     ![Karta Podsumowanie narzędzi diagnostycznych](../profiling/media/DiagToolsSummaryTab.png "DiagToolsSummaryTab")

     > [!NOTE]
     >  Ponieważ zbieranie danych mogą wpłynąć na wydajność debugowania aplikacji natywnych lub trybu mieszanego pamięci, migawki pamięci są domyślnie wyłączone. Aby włączyć migawek w aplikacjach native lub w trybie mieszanym, Uruchom sesję debugowania (klawisz skrótu: **F5**). Gdy **narzędzia diagnostyczne** zostanie wyświetlone okno, wybierz kartę użycie pamięci, a następnie wybierz pozycję **profilowanie sterty**.  
     >   
     >  ![Włącz migawki](../profiling/media/dbgdiag_mem_mixedtoolbar_enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")  
     >   
     >  Zatrzymaj (klawisz skrótu: **Shift + F5**) i uruchom ponownie debugowanie.  

6.  Aby wykonać migawki na początku sesję debugowania, wybierz pozycję **wykonać migawki** na **użycie pamięci** paska narzędzi. (Warto ustawić punkt przerwania w tym miejscu również.)

    ![Wykonać migawki](../profiling/media/dbgdiag_mem_mixedtoolbar_takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot") 
     
     > [!TIP]
     >  Aby utworzyć linię bazową dla porównania pamięci, należy wziąć pod uwagę migawki na początku sesji debugowania.  

6.  Uruchom scenariusz, który spowoduje, że pierwszy punkt przerwania do trafiony.

7.  Gdy debuger jest wstrzymana na pierwszy punkt przerwania, wybierz **wykonać migawki** na **użycie pamięci** paska narzędzi.  

8.  Naciśnij klawisz F5, aby uruchomić aplikację na drugi punkt przerwania.

9.  Teraz Utwórz kolejną migawkę.

     W tym momencie można rozpocząć do analizowania danych.    
  
## <a name="analyze-memory-usage-data"></a>Analizowanie danych użycia pamięci
Te wiersze tabeli podsumowania użycia pamięci wymieniono migawek, które miały podczas sesji debugowania i zawiera łącza do bardziej szczegółowych widoków.

![Tabela podsumowująca pamięci](../profiling/media/dbgdiag_mem_summarytable.png "DBGDIAG_MEM_SummaryTable")

 Nazwa kolumny są zależne od trybu debugowania, możesz wybrać we właściwościach projektu: .NET native lub mieszane (.NET i natywnego).  
  
-   **Obiektów (Diff)** i **alokacji (Diff)** kolumn wyświetlany liczbę obiektów w .NET i natywnej pamięci, gdy migawki.  
  
-   **Rozmiar stosu (Diff)** kolumny wskazuje liczbę bajtów w .NET i stert macierzystych 

Po wykonaniu migawki wielu komórek tabelę z podsumowaniem obejmują zmiany w wartości między migawki wiersza i poprzednią migawkę.  

Do analizy użycia pamięci, kliknij jeden z łącza, które otwiera szczegółowych raportów użycia pamięci:  

-   Aby wyświetlić szczegóły różnicy między bieżącą migawką i poprzednią migawkę, wybierz łącze Zmień strzałki w lewo (![zwiększenie użycia pamięci](../profiling/media/prof-tour-mem-usage-up-arrow.png "zwiększenie użycia pamięci")). Czerwona strzałka wskazuje wzrost użycia pamięci i zieloną strzałkę, aby wskazuje zmniejszenie.

    > [!TIP]
    >  Zidentyfikować problemy z pamięcią szybciej, raporty różnicowy są sortowane według typów obiektów, które najbardziej w ogólna liczba wzrosła (kliknij łącze Zmień w **obiektów (Diff)** kolumny) lub większa najbardziej w całkowity rozmiar sterty (kliknij Zmień łącze w **rozmiar stosu (Diff)** kolumny).

-   Aby wyświetlić szczegóły wybranej migawki, kliknij łącze nie został zmieniony. 
  
 Raport jest wyświetlany w osobnym oknie.   
  
### <a name="managed-types-reports"></a>Zarządzane typy raportów  
 Wybierz łącze bieżącego **obiektów (Diff)** lub **alokacji (Diff)** komórka w tabeli podsumowania użycia pamięci.  
  
 ![Raport typu zarządzanego debugera &#45; ścieżki do katalogu głównego](../profiling/media/dbgdiag_mem_managedtypesreport_pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")  
  
 Górne okienko przedstawia liczbę i rozmiar typów w migawce, takich jak rozmiar wszystkich obiektów, do których odwołuje się typ (**rozmiarze włącznie**).  
  
 **Ścieżki do katalogu głównego** drzewa w dolnym okienku Wyświetla obiekty, które odwołują się do typu wybranego w górnym okienku. Moduł zbierający elementy bezużyteczne .NET Framework czyści pamięci dla obiekt tylko wtedy, gdy ostatniego typu, która została zwolniona.  
  
 **Odwołuje się do typów** drzewa Wyświetla odwołań, które są przechowywane w typu wybranego w górnym okienku.  
  
 ![Zarządzane eferenced typów widoku raportu](../profiling/media/dbgdiag_mem_managedtypesreport_referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")  
  
 Aby wyświetlić wystąpienie typu wybranego w górnym okienku, wybierz ![ikona wystąpienia](../profiling/media/dbgdiag_mem_instanceicon.png "DBGDIAG_MEM_InstanceIcon") ikony.  
  
 ![Wystąpienia widoku](../profiling/media/dbgdiag_mem_managedtypesreport_instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")  
  
 **Wystąpień** widoku wystąpień wybranego obiektu są wyświetlane w migawce w górnym okienku. Ścieżki do katalogu głównego i odwołuje się do typów w okienku wyświetlania obiektów, które odwołują się do wybranego wystąpienia i typy, które odwołuje się do wybranego wystąpienia. Po zatrzymaniu debugera w momencie, gdy migawki ustawieniu kursora komórkę wartość, aby wyświetlić wartości obiektów w etykietce narzędzia.  
  
### <a name="native-type-reports"></a>Typ macierzysty raportów  
 Wybierz łącze bieżącego **alokacji (Diff)** lub **rozmiar stosu (Diff)** komórka w tabeli podsumowania użycia pamięci z **narzędzia diagnostyczne** okna.  
  
 ![Natywny typ widoku](../profiling/media/dbgdiag_mem_native_typesview.png "DBGDIAG_MEM_Native_TypesView")  
  
 **Typów widoku** Wyświetla liczbę i rozmiar typów w migawce.  
  
-   Wybierz ikonę wystąpień (![ikonę wystąpienia w kolumnie Typ obiektu](../profiling/media/dbg_mma_instancesicon.png "DBG_MMA_InstancesIcon")) wybranego typu do wyświetlenia informacji o obiektach wybranego typu w migawce.  
  
     **Wystąpień** widoku obejmuje każde wystąpienie wybranego typu. Wybranie wystąpienia powoduje wyświetlenie stos wywołań, które spowodowało utworzenie wystąpienia w **stosu wywołań alokacji** okienka.  
  
     ![Wystąpienia widoku](../profiling/media/dbgdiag_mem_native_instances.png "DBGDIAG_MEM_Native_Instances")  
  
-   Wybierz **widoku stosy** w **trybu wyświetlania** listy, aby zobaczyć stos alokacji dla wybranego typu.  
  
     ![Stosów widoku](../profiling/media/dbgdiag_mem_native_stacksview.png "DBGDIAG_MEM_Native_StacksView")  
  
### <a name="change-diff-reports"></a>Zmień raportów (Diff)  
  
-   Wybierz łącze Zmień w komórce tabeli podsumowania **użycie pamięci** karcie na **narzędzia diagnostyczne** okna.  
  
     ![Wybierz grupę zmian &#40;dif&#41;raport f](../profiling/media/dbgdiag_mem_choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")  
  
-   Wybierz migawki w **Porównaj z** raport zarządzanym lub macierzystym listy.  
  
     ![Wybierz z listy Porównaj z migawki](../profiling/media/dbgdiag_mem_choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")  
  
 Raport o zmianach dodaje kolumn (oznaczone **(Diff)**) do wyświetlania różnicy między wartością migawki podstawowej i migawki porównawczy podstawowej raportu. Poniżej przedstawiono wygląd raportu różnicowego natywnego typu widoku:  
  
 ![Typy natywne różnicowego Veiw](../profiling/media/dbgdiag_mem_native_typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")  
  
## <a name="blogs-and-videos"></a>Blogi i filmy wideo  

|         |         |
|---------|---------|
|  ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo")  |    [Obejrzyj film](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171) przy użyciu narzędzia diagnostyczne, które pokazuje, jak Analiza użycia pamięci i procesora w Visual Studio 2017 r. |

 [Analizowanie Procesora i pamięci podczas debugowania](https://blogs.msdn.microsoft.com/visualstudio/2016/02/15/analyze-cpu-memory-while-debugging/)  
  
 [Visual C++ Blog: Pamięci profilowania w programie Visual C++ 2015](https://blogs.msdn.microsoft.com/vcblog/2015/10/21/memory-profiling-in-visual-c-2015/)  

## <a name="next-steps"></a>Następne kroki

W tym samouczku kiedy znasz już jak zbieranie i analizowanie danych użycia pamięci. Jeśli została już ukończona [samouczek profilera](../profiling/profiling-feature-tour.md), możesz pobrać krótki przegląd sposobu analizy użycia procesora CPU w aplikacjach.

> [!div class="nextstepaction"]
> [Analizowanie użycia procesora CPU](../profiling/beginners-guide-to-performance-profiling.md) 