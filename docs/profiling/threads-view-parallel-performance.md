---
title: Wątków (Parallel Performance) widok | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ccb86d36429f8695222f69fbf6d78635a338bfe5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="threads-view-parallel-performance"></a>Widok wątków (Parallel Performance)
**Widok wątków** jest najbardziej szczegółowy i bogate widokiem Concurrency Visualizer (wybierz **Analizuj** > **Concurrency Visualizer** można uruchomić CONCURRENCY visualizer). Korzystając z tego widoku, można ustalić, czy wątki są wykonywanie lub blokuje z powodu synchronizacji, we/wy lub innego powodu.  
  
 Podczas analizy profilu Concurrency Visualizer sprawdza, czy wszystkie zdarzenia przełączenie kontekstu systemu operacyjnego dla każdego wątku aplikacji. Przełączenia kontekstu może wystąpić z wielu powodów, takich jak te:  
  
-   Wątek jest zablokowany na podstawowy synchronizacji.  
  
-   Wygasa quantum wątku.  
  
-   Wątek wysyła żądanie operacji We/Wy blokowania.  
  
 Widok wątków przypisuje kategorię każdego przełączenie kontekstu po zatrzymaniu wątku wykonywania. Kategorie są wyświetlane w legendzie w lewej dolnej części widoku. Narzędzia Concurrency Visualizer działaniach kategoryzuje zdarzenia przełączenie kontekstu przez wyszukiwanie dobrze znanych interfejsów API blokowania stos wywołań wątku. Jeśli nie zostanie odnaleziony odpowiednik stosu wywołań Przyczyna oczekiwania, która jest dostarczana przez [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] jest używany. Jednak [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] kategorii może być oparty na szczegóły implementacji i może nie odzwierciedlać zamiar użytkownika. Na przykład [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] raporty Przyczyna oczekiwania dotyczące blokowania na natywnego cienki czytnika — moduł zapisujący blokady jako operacji We/Wy zamiast synchronizacji. W większości przypadków można zidentyfikować przyczynę blokowania zdarzenia, sprawdzając stosy wywołań odpowiadające przełącznik kontekst zdarzenia.  
  
 Widok wątki pokazuje też zależności między wątkami. Na przykład jeśli identyfikator wątku, który jest zablokowany na obiekt synchronizacji można wyszukać wątku odblokowującego go, a po odblokowaniu go jeden z nich, można sprawdzić działanie w stosie wywołań dla tego wątku w punkcie.  
  
 Podczas wykonywania wątków Concurrency Visualizer służy do zbierania próbek. W widoku wątków można analizować kodu, które zostały wykonane przez jeden lub więcej wątków w trakcie segmentu wykonania. Można również sprawdzić blokowania raporty i raporty, które profilu stosu wywołań drzewa wykonania.  
  
## <a name="usage"></a>Użycie  
 Poniżej przedstawiono kilka sposobów, w których można używać widoku wątków:  
  
-   Identyfikowanie przyczyn, dlaczego niektórych fazach wykonywania interfejsu użytkownika (UI) aplikacji nie odpowiada.  
  
-   Określ ilość czasu, który ma poświęcony blokuje synchronizacji, we/wy błędów stron i inne zdarzenia.  
  
-   Zidentyfikuj stopień konfliktów z innymi procesami, które są wykonywane w systemie.  
  
-   Identyfikowanie problemów równoważenia obciążenia do wykonywania równoległego.  
  
-   Identyfikowanie przyczyn skalowalność, która jest nieoptymalne lub nieistniejącą (na przykład, dlatego nie zwiększyć wydajność aplikacji równoległe, gdy są dostępne rdzenie logiczne).  
  
-   Zrozumienie stopień współbieżność w aplikacji, aby pomóc w paralelizacja.  
  
-   Zrozumienie zależności między wątków roboczych i ścieżek krytycznych wykonywania.  
  
## <a name="examining-specific-time-intervals-and-threads"></a>Badanie w określonych odstępach czasu i wątków  
 Widok wątki pokazuje osi czasu. Można powiększanie i przesuwanie w osi czasu w celu zbadania w określonych odstępach czasu i wątki aplikacji. Na osi x to czasu i na osi y to kilka kanałów:  
  
-   Dwa kanały we/wy dla każdego dysku w systemie, jeden kanał dla odczytów i jeden dla operacji zapisu.  
  
-   Kanał dla każdego wątku w procesie.  
  
-   Kanały znacznika, jeśli występują zdarzenia znacznika w śledzeniu. Kanały znacznika początkowo są wyświetlane w polu kanały wątku wygenerowanych tych zdarzeń.  
  
-   Kanały procesora GPU.  
  
 Oto ilustrację widok wątki:  
  
 ![Widok wątków](../profiling/media/threadsviewnarrowing.png "ThreadsViewNarrowing")  
Widok wątków  
  
 Początkowo wątki są sortowane w kolejności, w której zostały utworzone, dzięki czemu wątku głównego aplikacji jest pierwszy. Opcja sortowania w lewym górnym rogu widoku sortowania wątków kryterium innego (na przykład przez większość wykonywania pracy wykonanej).  
  
 Można ukryć wątków, które nie działają pracy przez zaznaczenie ich nazw, w kolumnie po lewej stronie, a następnie wybierając **Ukryj wątki wybrane** przycisk na pasku narzędzi. Firma Microsoft zaleca, aby ukryć wątków, które są całkowicie zablokowane, ponieważ ich statystyki są zbędne i można clog — raporty.  
  
 Aby zidentyfikować dodatkowe wątki, aby ukryć w legendzie active wybierz **na podsumowanie wątku** raport dotyczący **raport profilu** kartę. Wyświetla wykres podziału wykonywania, na którym pokazuje stan wątków dla aktualnie wybranego okresu. Niektóre poziomach powiększenia niektórych wątków nie może być wyświetlany. W takim przypadku elipsy są wyświetlane po prawej stronie.  
  
 Po wybraniu przedział czasu i niektóre wątki w nim, można rozpocząć analizy wydajności.  
  
## <a name="analysis-tools"></a>Narzędzia do analizy  
 W tej sekcji opisano, raportów i innych narzędzi do analizy.  
  
### <a name="thread-blocking-details"></a>Szczegóły blokuje wątku  
 Aby uzyskać informacje dotyczące blokowania zdarzenia w określonym regionie w wątku, wskaźnik w danym regionie, aby wyświetlić etykietkę. Zawiera informacje, takie jak kategorii, godzina rozpoczęcia region czas blokowania i blokowania interfejsu API, jeśli istnieje. Jeśli wybierzesz blokowania region, stosu w danym momencie zostanie wyświetlony w okienku u dołu wraz z tych samych informacji, który jest wyświetlany w etykietce narzędzia. Sprawdzając stos wywołań, można określić podstawowej Przyczyna zdarzeń blokuje wątku. Wybierając segmentu i badanie bieżącej karty można znaleźć dodatkowych procesów i informacji o wątku.  
  
 Ścieżka wykonywania może mieć wiele zdarzeń blokowania. Należy zbadać te według kategorii blokowania, aby obszarów problemów można znaleźć szybciej. Wystarczy wybrać jedną z blokowaniem kategorii w legendzie po lewej stronie.  
  
### <a name="dependencies-between-threads"></a>Zależności między wątkami  
 Narzędzia Concurrency Visualizer można wyświetlić zależności między wątkami procesu pozwoli określić zablokowanych wątek próbował i Dowiedz się, jakie inne wątku włączona do wykonania. Aby ustalić, który wątek odblokowany inny wątek, wybierz odpowiednie segment blokujący. Jeśli narzędzia Concurrency Visualizer można określić odblokowywania wątku, rysuje linię między odblokowywania wątku i wykonywania segmentu, znajdujący się na segment blokujący. Ponadto **stosu Unblocking** karta zawiera stos wywołań istotne.  
  
### <a name="thread-execution-details"></a>Szczegóły wykonanie wątku  
 Na wykresie oś czasu wątku zielony segmentów pokazują, gdy było wykonywane kodu. Możesz uzyskać bardziej szczegółowe informacje dotyczące wykonywania segmentu.  
  
 Po wybraniu punktu w segmencie wykonywania Concurrency Visualizer szuka tego punktu w czasie w stosie wywołań odpowiednich i następnie wyświetla czarny karetkę powyżej wybranego punktu w segmencie wykonywania oraz sam stos wywołań na  **Bieżący stos** kartę. Możesz wybrać wiele punktów w segmencie wykonywania.  
  
> [!NOTE]
>  Narzędzia Concurrency Visualizer nie mogą mieć możliwość rozpoznania zaznaczenia w segmencie wykonywania. Zazwyczaj dzieje, gdy czas trwania segmentu jest mniejsza niż 1 milisekundy.  
  
 Aby uzyskać profil wykonania wszystkie włączone (odkrywanie) wątków w aktualnie wybranego zakresu czasu, należy wybrać **wykonywania** przycisk active legendy.  
  
### <a name="timeline-graph"></a>Oś czasu wykresu  
 Oś czasu wykresu zawiera działanie wszystkie wątki w procesie i wszystkie urządzenia dysk fizyczny na hoście. Wyświetla zdarzenia procesora GPU działania i znacznika.  Możesz powiększać Aby wyświetlić więcej szczegółów lub out, aby wyświetlić dłuższy interwał czasu. Można również wybrać punktów na wykresie, aby uzyskać szczegółowe informacje o kategorii, godziny rozpoczęcia, czas trwania i stanów stosu wywołań.  
  
 Na wykresie oś czasu kolor wskazuje stan wątku w danym momencie. Na przykład wykonywały segmentów zielony, segmentów red zostały zablokowane na synchronizacji żółty segmentów zostały przeniesiona i purpurowa segmentów nie prowadzą We/Wy urządzenia. Ten widok służy do sprawdzenia saldo pracy między wątków, które są zaangażowane w równoległej pętli lub równoczesnych zadań. Jeśli wątek trwa dłużej niż inne, pracy może być równowagi. Aby poprawić wydajność programu rozkładając pracy bardziej równomiernie między wątki, można użyć te informacje.  
  
 Jeśli tylko jeden wątek jest zielony, (w trakcie wykonywania) w punkcie w czasie, aplikacja może nie mogły zalet współbieżność w systemie. Oś czasu wykresu można użyć do sprawdzenia zależności między wątków i danych czasowych relacje między blokuje i zablokowane wątki. Aby zmienić kolejność wątków, wybierz wątku, a następnie na pasku narzędzi wybierz górę lub w dół przycisku. Aby ukryć wątków, wybierz je, a następnie wybierz **Ukryj wątki** przycisku.  
  
### <a name="profile-reports"></a>Profilu, raportów  
 Poniżej oś czasu wykresu jest profil osi czasu i okienko, w którym znajdują się karty dla różnych raportach. Raporty są automatycznie aktualizowane po zmianie widoku wątków. Dla dużych śladów okienko raportów mogą być niedostępne, gdy aktualizacje są obliczane. Każdy raport zawiera dwa dostosowania filtru: noise redukcji i tylko mój kod. Użyj redukcji szumu filtrowanie wpisy drzewa wywołań gdzie jest zużywany czas mały. Wartość domyślna filtru to % 2, ale można dostosować od 0 do 99 procent. Zaznacz, aby wyświetlić tylko drzewo wywołań kodu **tylko mój kod** pole wyboru. Aby wyświetlić wszystkie wywołania drzewa, usunąć jej zaznaczenia.  
  
#### <a name="profile-report"></a>Raport profilu  
 Na tej karcie zawiera raporty, które odpowiadają wpisy w aktywna Legenda. Aby wyświetlić raport, wybierz jeden z wpisów.  
  
#### <a name="current-stack"></a>Bieżący stos  
 Ta karta przedstawia stos wywołań dla wybranego punktu na konkretny segment wątku na wykresie osi czasu. Stosy wywołań są usuwane, aby pokazać tylko działanie, które jest powiązane z programu.  
  
#### <a name="unblocking-stack"></a>Stos odblokowań  
 Zobacz, który wątek odblokowany wybranego wątku i jakie wierszu kodu Wybierz **stosu Unblocking** kartę.  
  
#### <a name="execution"></a>Wykonanie  
 Wykonanie przedstawia podział czasu poświęconego aplikacji podczas wykonywania.  
  
 Aby odnaleźć wiersza kodu, w którym jest zużywany czas wykonywania, rozwiń drzewo wywołań, a następnie, w menu skrótów dla wpisu drzewa wywołań wybierz **Wyświetl źródło** lub **wyświetlanie wywołań witryn**. **Wyświetl źródło** lokalizuje wykonanego wiersza kodu. **Wyświetlanie wywołań witryn** lokalizuje wiersz kodu, który wywołał wykonanego wiersza kodu. Jeśli tylko jedna lokacja wywołania istnieje, zostanie wyróżniona jego wiersz kodu. Jeśli istnieje wiele witryn wywołanie, można wybrać jeden w oknie dialogowym zostanie wyświetlona, a następnie wybierz pozycję **przejdź do źródła** przycisk, aby wyróżnić wywołanie kodu lokacji. Często jest najbardziej przydatne zlokalizować miejsce wywołania z najbardziej wystąpień i/lub najwięcej czasu. Aby uzyskać więcej informacji, zobacz [raport profilu wykonania](../profiling/execution-profile-report.md).  
  
#### <a name="synchronization"></a>Synchronizacja  
 Raport synchronizacji zawiera wywołań, które są odpowiedzialne za bloki synchronizacji, oraz agregacji blokuje razy każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas synchronizacji](../profiling/synchronization-time.md).  
  
#### <a name="io"></a>WE/WY  
 We/Wy przedstawia wywołania, które są odpowiedzialne za bloków We/Wy, wraz z agregacji blokuje razy każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas operacji We/Wy (Widok wątków)](../profiling/i-o-time-threads-view.md).  
  
#### <a name="sleep"></a>uśpienia  
 Raport stanu uśpienia zawiera wywołań, które są odpowiedzialne za bloki uśpienia, wraz z agregacji blokuje razy każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas uśpienia](../profiling/sleep-time.md).  
  
#### <a name="memory-management"></a>Zarządzanie pamięcią  
 Raport zarządzania pamięci zawiera wywołań, w którym wystąpił bloków zarządzania pamięci, wraz z agregacji blokuje razy każdego stosu wywołań. Te informacje służą do identyfikacji obszarów, które mają problemy kolekcji nadmiernego stronicowania lub pamięci.  Aby uzyskać więcej informacji, zobacz [czas zarządzania pamięcią](../profiling/memory-management-time.md).  
  
#### <a name="preemption"></a>Wywłaszczanie  
 Raport wywłaszczanie zawiera wystąpienia, w którym procesów w systemie wywłaszczone bieżący proces i wątki poszczególnych, które zastąpione wątków w bieżącym procesie. Można użyć tych informacji do identyfikacji procesów i wątków, które są najbardziej odpowiedzialne za wywłaszczanie. Aby uzyskać więcej informacji, zobacz [czas Wywłaszczania](../profiling/preemption-time.md).  
  
#### <a name="ui-processing"></a>Przetwarzanie interfejsu użytkownika  
 Raport przetwarzania interfejsu użytkownika zawiera wywołania, które są zobowiązani do interfejsu użytkownika, przetwarzania bloków, wraz z agregacji blokuje razy każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas przetwarzania interfejsu użytkownika](../profiling/ui-processing-time.md).  
  
#### <a name="per-thread-summary"></a>Na podsumowanie wątku  
 Ta karta przedstawia widok kolumny oznaczone kolorami całkowity czas czy każdy wątek w procesie, zablokowany, we/wy i innych stanów. Kolumny są oznaczane etykietami na dole. Po zmodyfikowaniu poziom powiększenia na wykresie osi czasu jest automatycznie aktualizowany na tej karcie. Niektóre poziomach powiększenia niektórych wątków nie może być wyświetlany. W takim przypadku elipsy są wyświetlane po prawej stronie. Jeśli nie ma wątku, który ma, można ukryć inne wątki. Aby uzyskać więcej informacji, zobacz [na wątku raport z podsumowaniem](../profiling/per-thread-summary-report.md).  
  
#### <a name="disk-operations"></a>Operacje dysków  
 Ta karta przedstawia procesów i wątków były wykonywane w imieniu bieżącego procesu, które pliki są dotknięciu (na przykład bibliotek DLL, które zostały załadowane), odczytano liczbę bajtów i inne informacje We/Wy dysku. Ten raport służy do oceny czasu poświęcana podczas uzyskiwania dostępu do plików podczas wykonywania, szczególnie w przypadku, gdy proces wydaje się być powiązany we/wy. Aby uzyskać więcej informacji, zobacz [raport dotyczący operacji na dysku](../profiling/disk-operations-report-threads-view.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Concurrency Visualizer](../profiling/concurrency-visualizer.md)