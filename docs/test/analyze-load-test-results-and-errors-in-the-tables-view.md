---
title: Analizowanie wyników testów obciążenia oraz błędów w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.pageresult
- vs.test.load.dialog.column
- vs.test.load.monitor.requestresult
- vs.test.load.monitor.testresult
- vs.test.load.monitor.table.view
- vs.test.load.monitor.agentresult
- vs.test.load.monitor.transactionresult
helpviewer_keywords:
- tables, Load Test Viewer options
- load test results, tables
- load tests, Load Test Viewer
- data [Visual Studio ALM], load test tables
- Load Test Viewer, tables
- load tests, results tables
ms.assetid: 0a84bda3-6051-45eb-9c7f-d57419e1f97d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 3820e1d7ef4294b4c46e0e7d0174a89dfe5b0e75
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="analyze-load-test-results-and-errors-in-the-tables-view-of-the-load-test-analyzer"></a>Analizowanie wyników testów obciążenia oraz błędów w widoku tabeli analizatora testu obciążenia

Podczas wyświetlania wyników uruchomienia testu obciążenia można wyświetlić różnych okienek, które zapewniają różne sposoby analizowania danych. Dane można wyświetlić jako wykresu, aby zobaczyć, jak zmieniają się w czasie, lub można wyświetlić dane jako tabele szczegółów.

Aby przełączyć do widoku tabeli, wybierz **tabel** na pasku narzędzi testu obciążenia. Aby przełączyć się z różnych tabel, należy użyć **tabeli** listy rozwijanej na pasku narzędzi nad siatki tabeli. W widoku tabeli można wyświetlić tabele do czterech naraz. Aby uzyskać więcej informacji, zobacz [tabele testu obciążenia kafelka](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#tile-load-test-tables) w tym temacie.

Większość wartości liczbowe wyświetlane w tabeli liczników wydajności kumulują się za pośrednictwem uruchomienia testu obciążenia całego. Kolumny o nazwie **ostatniego** są wyjątkiem i reprezentują wartość od ostatniego interwału próbkowania.

> [!NOTE]
> Kolumny o nazwie **ostatniego** są dostępne tylko podczas wykonywania testu obciążenia. Po zakończeniu testu obciążenia tych kolumn nie są dostępne.

 Większość tabel można sortować, wybierając tytuł kolumny, które mają być sortowane w. Domyślnie niektóre tabele nie są wyświetlane wszystkie dostępne kolumny. Można dodać kolumny do tabel, jeśli dostępnych kolumn. Aby dodać kolumny, kliknij prawym przyciskiem myszy tabeli, a następnie wybierz pozycję **Dodaj/Usuń kolumny**.

> [!NOTE]
> Do innych aplikacji, takich jak program Excel dodatkowe analizy można skopiować danych z tabeli.

## <a name="the-load-test-tables"></a>Tabele testu obciążenia

 W poniższej tabeli wymieniono tabele, które są dostępne do analizowania uruchomień testów obciążenia.

|Nazwa tabeli|Opis|
|----------------|-----------------|
|błędy|Wyświetla listę błędów, które wystąpiły podczas testu obciążenia. Aby uzyskać więcej informacji, zobacz [Table błędy](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-errors-table) w tym temacie i [analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|
|Strony|Zostanie wyświetlona lista stron dostęp podczas uruchomienia testu obciążenia. Niektóre dane w tej tabeli jest dostępna tylko po zakończeniu testu obciążenia. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie strony sieci Web odpowiedzi](../test/how-to-view-web-page-response-time-in-a-load-test.md).|
|żądania|Wyświetla szczegóły dotyczące poszczególnych żądań wystawiony podczas testu obciążenia. W tym wszystkie żądania HTTP i zależnych żądań, takich jak obrazy. Aby uzyskać więcej informacji, zobacz [Table żądań](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-requests-table) w tym temacie.|
|Śledzenie programu SQL Server|Wyświetla wyniki śledzenia SQL. Ta tabela jest dostępna tylko po zakończeniu testowania obciążenia i tylko wtedy, gdy śledzenia SQL został użyty podczas testu. Aby uzyskać więcej informacji, zobacz [Table danych śledzenia SQL](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table) w tym temacie.|
|Testy|Wyświetla szczegóły dla poszczególnych testów uruchomić podczas testu obciążenia. Aby uzyskać więcej informacji, zobacz [Table testy](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-tests-table) w tym temacie.|
|Progi|Wyświetla listę naruszeń zasady progu, które wystąpiły podczas testu obciążenia. Aby uzyskać więcej informacji, zobacz [analizowanie naruszeń zasady progu](../test/analyze-threshold-rule-violations-in-load-tests.md).|
|Transakcje|Wyświetla listę transakcji, które wystąpiły podczas uruchomienia testu obciążenia. Aby uzyskać więcej informacji, zobacz [Table transakcji](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-transactions-table) w tym temacie.|
|Agenci|Wyświetla tylko wtedy, gdy test obciążenia używa kontrolera testów i agentów testowych. Wyświetla listę agentów, które były używane podczas testu obciążenia. Agenci uwzględniono liczbę żądań, agent przetestowane i tych wniosków o ile nie powiodło się. Ponadto w tabeli agentów obejmuje liczba testów w mieszanki testów testów obciążenia, które agent przetestowane i tych, ile nie powiodło się.|
|Szczegóły testu|Wyświetla szczegóły testy objęte testu mieszanego dla testu obciążenia. Szczegóły zawierają nazwę testu, scenariusz, który test został w uruchomieniu testu, długość czasu, jaki zajęło testów do uruchomienia i wynik testu, wskazującą, czy test przekazany lub niepowodzenie. Jeśli test nie powiodła się, łącze znajduje się w **szczegóły** kolumny. Można wybrać łącza, co spowoduje przejście do edytora testów wydajności sieci Web z nieudanych żądań, które są wyróżnione.|

## <a name="collect-percentile-data"></a>Zbieranie danych percentyl

 Niektóre tabele testu obciążenia może zawierać dodatkowe kolumn, które obejmują percentyl danych i czasy odpowiedzi podzielić grup opartych na emulacji sieci. Domyślnie te dane nie są zbierane. Percentyl danych jest dostępna tylko podczas zapisywania wyników z bazą danych, a nie w przypadku, gdy zapiszesz lokalnie. Aby uzyskać więcej informacji, zobacz [Zarządzanie wyników testów obciążenia w repozytorium wyników testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md). Ponadto do zbierania tych danych w **edytora testu obciążenia**w obszarze **parametrów uruchomieniowych** węzła, wybierz konkretnym Uruchom węzła Ustawienia można zmienić. W **właściwości** okna, aby uzyskać **magazynowania szczegółów chronometrażu** właściwości, wybierz opcję **StatisticsOnly** lub **AllIndividualDetails**. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie strony sieci Web odpowiedzi](../test/how-to-view-web-page-response-time-in-a-load-test.md).

## <a name="the-requests-table"></a>W tabeli żądań

 **Żądań** tabeli są wyświetlane szczegóły dotyczące poszczególnych żądań wystawiony podczas testu obciążenia. W tym wszystkie żądania HTTP i zależnych żądań, takich jak obrazy. W tabeli wymieniono żądań przez testu oraz scenariusz, ponieważ jedno żądanie może obejmować wiele testów i scenariuszy.

 W poniższej tabeli wymieniono kolumn w **żądań** tabeli:

|Kolumny|Opis|Domyślnie widoczne|
|------------|-----------------|------------------------|
|**Żądanie**|Adres URL żądania. Na przykład home.html lub arrow.gif pomarańczowy.|Tak|
|**Scenariusz**|Nazwa scenariusza.|Tak|
|**Test**|Nazwa testu.|Tak|
|**Całkowita liczba**|Całkowita liczba to żądanie testu wydajności sieci Web wystawiony podczas testu obciążenia uruchamiane. Łączna obejmuje przekazany, jak i nieudane żądania, ale nie obejmuje żądań z pamięci podręcznej, ponieważ nie zostały przekazane do serwera sieci Web.|Tak|
|**Przekazany**|Ile razy żądanie zostało wydane i przekazany.|Nie|
|**Niepowodzenie**|Ile razy żądanie wystawiony i nie powiodło się. W tej kolumnie są wyświetlane jako hiperlinki. Można wybrać dowolne hiperłącze, aby wyświetlić listę poszczególnych problemów odnotowanych w **błędów testu obciążenia** okno dialogowe. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Tak|
|**W pamięci podręcznej**|Całkowita liczba powtórzeń żądania już był buforowany.|Nie|
|**Żądania na sekundę**|Szybkość na sekundę żądań podczas testu obciążenia.|Nie|
|**Przekazany na sekundę**|Szybkość na sekundę podczas testu obciążenia, wystąpień tego żądania, który przekazał żądanie.|Nie|
|**Nie powiodło się na sekundę**|Częstotliwość tego żądania podczas testu obciążenia, wystąpień tego żądania, które zakończyły się niepowodzeniem.|Nie|
|**Po raz pierwszy bajt**|Średni czas odebrania pierwszego bajtu odpowiedzi, mierzony od momentu w którym żądanie zostało wysłane do serwera sieci Web. Jednostki są sekund.|Nie|
|**Czas odpowiedzi**|Średni czas do odbioru całej odpowiedzi na żądanie, mierzony od momentu w którym żądanie zostało wysłane do serwera sieci Web. Jednostki są sekund.|Tak|
|**Długość zawartości**|Średnia długość zawartości odpowiedzi na żądanie. Jednostki są bajtów.|Tak|

## <a name="the-tests-table"></a>W tabeli testów

 **Testy** tabeli Wyświetla szczegóły dla poszczególnych testy uruchamiane podczas testu obciążenia. W tabeli wymieniono testy testu i scenariusz, ponieważ jeden test może być uwzględniony w wielu scenariuszach.

 W poniższej tabeli wymieniono kolumn w **testy** tabeli.

|Kolumny|Opis|Domyślnie widoczne|
|------------|-----------------|------------------------|
|**Test**|Nazwa testu.|Tak|
|**Scenariusz**|Nazwa scenariusza.|Tak|
|**Całkowita liczba**|Całkowita liczba razy uruchomienia testu w scenariuszu. W tym liczba testu przesłane i nie powiodło się.|Tak|
|**Przekazany**|Ile razy testu zostało uruchomione w tym scenariuszu i przekazany.|Tak|
|**Niepowodzenie**|Liczba razy uruchomienia w scenariuszu testu i nie powiodło się. W tej kolumnie są wyświetlane jako hiperlinki. Można wybrać dowolne hiperłącze, aby wyświetlić listę poszczególnych problemów odnotowanych w **błędów testu obciążenia** okno dialogowe. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Tak|
|**Tests/Sec**|Częstotliwość testu podczas testu obciążenia.|Tak|
|**Przekazany na sekundę**|Częstotliwość tego testu podczas uruchomienia wystąpień tego testu, który przekazał testu obciążenia.|Nie|
|**Nie powiodło się na sekundę**|Częstotliwość tego testu podczas testu obciążenia, wystąpień tego testu, który uległ awarii.|Nie|
|**Czas testu**|Średni czas do wykonania testu podczas testu obciążenia. Jednostki są sekund.|Tak|
|**Czas testu 90%**|90-wartość czasu testu.|Nie|
|**95% czasu testu**|95 wartość czasu testu.|Tak|
|**Żądania i testowanie**|Średnia liczba żądań w teście, jeśli jest wydajności sieci Web testu.|Nie|

## <a name="the-transactions-table"></a>W tabeli transakcji

 **Transakcji** tabeli przedstawiono listę transakcji, które wystąpiły podczas uruchomienia testu obciążenia. Transakcje odnoszą się do transakcji zdefiniowanych w teście wydajności sieci Web lub czasomierzy zdefiniowanych w teście jednostki. Transakcja nie odwołuje się do przeprowadzania transakcji bazodanowych.

 W poniższej tabeli wymieniono kolumn w **transakcji** tabeli.

> [!NOTE]
> Aby wyświetlić wszystkie kolumny, należy włączyć właściwości magazynowania szczegółów chronometrażu, który jest skojarzony z aktywnego ustawienia uruchamiania. Aby uzyskać więcej informacji, zobacz [porady: Określanie właściwości magazynowania szczegółów chronometrażu](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

|Kolumny|Opis|Widoczne bez szczegółów chronometrażu|
|------------|-----------------|------------------------------------|
|**Transakcja**|Nazwa transakcji.|Tak|
|**Scenariusz**|Nazwa scenariusza.|Tak|
|**Test**|Nazwa testu.|Tak|
|**Całkowita liczba**|Całkowita liczba transakcji, które odbyły się podczas testu obciążenia.|Tak|
|**Czas transakcji**|Czas do wykonania transakcji podczas uruchomienia testu obciążenia. Dla testów wydajności sieci Web, wziąć pod uwagę w obliczeniach zawarty jest czas. Jednostki są sekund.|Nie|
|**Czas odpowiedzi**|Czas odpowiedzi transakcji w teście wydajności sieci Web w uruchomieniu testu obciążenia. Czas odpowiedzi różni się od czasu transakcji w tym czas odpowiedzi nie zawiera żadnych Pomyśl czas, który wystąpił podczas wykonywania tej transakcji. Jednostki są sekund.|Nie|
|**Średnio Czas transakcji**|Średni czas trwania transakcji. Teraz obejmuje czasów reakcji. Na przykład jeśli masz trzech żądań i każdy ma czasu namysłu, teraz będzie zawierać te czasy reakcji i rzeczywisty czas do wykonania żądania.|Nie|
|**Średnio Czas odpowiedzi**|Średni czas odpowiedzi transakcji testu wydajności sieci Web w uruchomieniu testu obciążenia. Czas odpowiedzi różni się od czasu transakcji w tym czas odpowiedzi nie zawiera żadnych Pomyśl czas, który wystąpił podczas wykonywania tej transakcji. Jednostki są sekund.|Nie|
|**Minimalny czas odpowiedzi**|Nie ma czasów reakcji.|Nie|
|**Czas odpowiedzi maksymalna**|Nie ma czasów reakcji.|Nie|
|**Czas odpowiedzi środkowej**|Nie ma czasów reakcji.|Nie|
|**Czas odpowiedzi 90%**|90-wartość percentylu czasu transakcji. Nie ma czasów reakcji. **Uwaga:** różni się to od agenta Visual Studio Team System 2008 testu obciążenia, które są używane **90% czasu transakcji** wartość.|Nie|
|**95% czasu odpowiedzi**|95 wartość percentylu czasu transakcji. Nie ma czasów reakcji. **Uwaga:** różni się to od agenta Visual Studio Team System 2008 testu obciążenia, które są używane **95% czasu transakcji** wartość.|Nie|
|**Czas odpowiedzi (99%)**|99-ty percentyl wartość czasu transakcji. Nie ma czasów reakcji.|Nie|
|**Odchylenie standardowe czasu odpowiedzi**|Nie ma czasów reakcji.|Nie|

## <a name="the-errors-table"></a>W tabeli błędów

 Po uruchomieniu testu obciążenia można analizować występujące błędy. Analizowanie błędów i dostosowywania testów są ważnym elementem procesu testu obciążenia. Jeśli wystąpiły błędy, **błędy** hiperłącze jest wyświetlana na pasku stanu testu obciążenia i określa liczbę błędów, które wystąpiły. Aby wyświetlić tabelę błędy, wybierz polecenie hiperłącze.

 Błędy tabeli grup błędów, które wystąpiły podczas ładowania testów według typu i podtypu błędu. Istnieje również **całkowita** wiersza w tabeli, która określa całkowitą liczbę wszystkich błędów, które wystąpiły.

 W tabeli błędów zawiera następujące kolumny:

|Kolumny|Opis|Domyślnie widoczne|
|------------|-----------------|------------------------|
|Typ|Typ błędu. Na przykład HttpError.|Tak|
|SubType|Podtyp błędu. Na przykład LoadTestException.|Tak|
|Liczba|Liczba błędów tego typu, który wystąpił podczas testu obciążenia. W tej kolumnie są wyświetlane jako hiperlinki. Można wybrać dowolne hiperłącze, aby wyświetlić listę poszczególnych problemów.|Tak|
|Ostatni komunikat|Komunikat, który opisuje błąd. Na przykład 404 — NotFound.|Tak|

 Aby uzyskać więcej informacji, zobacz [Praca z tabelami testu obciążenia](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

### <a name="drilling-down-to-the-error-list"></a>Przechodzenie do listy błędów

Błędy tabeli grup błędów według typu i podtypu błędu. Aby wyświetlić tabelę poszczególnych problemów, możesz wyświetlić **błędów testu obciążenia** okno dialogowe. Aby wyświetlić okno dialogowe, wybierz hiperłącze w **liczba** kolumny w tabeli błędów. Można również wyświetlić okno dialogowe przez kliknięcie prawym przyciskiem myszy wiersz w tabeli błędów, który jest wypełniony, a następnie wybierając **błędy**.

> [!NOTE]
> Zbierane są tylko pierwszych 1000 wystąpień dowolnej kombinacji typu i podtypu błędu. Po wyświetleniu **błędów testu obciążenia** okno dialogowe, zobaczysz maksymalnie 1000 pierwszego wystąpienia tego błędu.

**Błędów testu obciążenia** tabela zawiera następujące kolumny:

|Kolumny|Opis|
|------------|-----------------|
|**Czas**|Czas podczas ładowania testów, w którym wystąpił błąd.|
|**Agent**|Nazwa komputera agenta, na którym wystąpił błąd. Jest to ważne w przypadku uruchamiania testów obciążenia za pomocą kontrolerów testów i agentów testowych. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).|
|**Test**|Nazwa wydajności sieci Web testu, w którym wystąpił błąd.|
|**Scenariusz**|Nazwa scenariusza, w którym wystąpił błąd.|
|**Żądanie**|Adres URL żądania, w którym wystąpił błąd.|
|**Typ**|Typ błędu. Na przykład HttpError.|
|**SubType**|Podtyp błędu. Na przykład LoadTestException.|
|**Tekst**|Tekst komunikatu o błędzie. Na przykład 404 — NotFound.|
|**Stos**|W tej kolumnie są puste lub słowo **stosu** jest formatowana jako hiperłącze. Można wybrać hiperłącza do przeglądania śladu stosu błędu.|
|**Szczegóły**|W tej kolumnie są puste lub słowo **TestLog** jest formatowana jako hiperłącze. To łącze ułatwia odizolowanie błędy w teście obciążenia. Na przykład wybranie **TestLog** link błędu żądania testu wydajności sieci Web będzie otwarcie wyników dla testu wydajności sieci Web w wydajności sieci Web testów Podgląd wyników i zaznacz błąd żądania.|

> [!NOTE]
> Tabeli można sortować, klikając nagłówki kolumn.

## <a name="the-sql-trace-data-table"></a>Tabela danych śledzenia SQL

Można zbierać dane śledzenia SQL podczas testu obciążenia do dalszej analizy. Zbieranie danych śledzenia umożliwia zidentyfikowanie najwolniej uruchomione zapytania i procedur przechowywanych w bazie danych programu SQL Server testowana.

Jeśli włączone jest śledzenie SQL, plik jest tworzony podczas uruchomienia testu obciążenia zawierającego dane śledzenia. Te dane są automatycznie zapisywane w magazynu wyników testów obciążenia na końcu uruchomienia testu i pliku śledzenia zostaną usunięte. Analizowanie danych śledzenia w **śledzenia SQL** tabeli po zakończeniu testu obciążenia.

### <a name="to-view-sql-trace-data"></a>Aby wyświetlić dane śledzenia SQL

1. W analizatorze testów obciążenia, wybierz **tabel** na pasku narzędzi, aby upewnić się, że jest wyświetlana siatka tabeli.

2. W **tabeli** listy rozwijanej wybierz pozycję **śledzenia SQL**.

3. Dane śledzenia, które zostały zebrane podczas przebiegu jest wyświetlany w siatce. W tabeli wymieniono najwolniej uruchomionej operacji SQL posortowane według czasu trwania z najmniejszą u góry. Zazwyczaj **czas trwania** kolumna jest pierwszą kolumnę do sprawdzenia. Dane są wyświetlane w milisekundach.

   Kolumny wyświetlane są następujące:

    - Event — klasa

    - Czas trwania

    - CPU

    - Odczytuje

    - Zapisuje

    - TextData

    - StartTime

    - EndTime

   Jeśli chcesz śledzić zdarzenia SQL innych niż określone w tych kolumn danych, można skonfigurować własne niestandardowe śledzenia SQL przy użyciu narzędzia SQL Profiler, niezależnie od programu Visual Studio.

## <a name="tile-load-test-tables"></a>Tabele testu obciążenia kafelka

Podczas przeglądania wyników uruchomienia testu obciążenia można wyświetlić jako tabele szczegółowe dane. Aby przełączyć do widoku tabeli, wybierz **tabel** na pasku narzędzi testu obciążenia. Tabele, które są dostępne są błędy, stron, żądania, śledzenie programu SQL Server, testy, progi i transakcji. Aby uzyskać więcej informacji, zobacz [Praca z tabelami testu obciążenia](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

W widoku tabeli można wyświetlić maksymalnie cztery tabel w czasie bez tabel nakładających się.

### <a name="to-tile-tables"></a>Na kafelku tabel

1. Na pasku narzędzi analizatora testu obciążenia, wybierz **tabel**.

     Otwiera widok tabeli. Układ domyślny to dwa panele poziomej.

2. Na pasku narzędzi analizatora testu obciążenia wybierz przycisk Układ, a następnie wybierz jedną z następujących opcji:

    - Jednego panelu

    - Dwa panele pozioma

    - Trzy panele pozioma

    - Cztery panele pozioma

3. Aby przełączyć się z różnych tabel, należy użyć listy rozwijanej powyżej siatki tabeli w każdym panelu.

    > [!NOTE]
    > Nie można wyświetlić tej samej tabeli w panelu więcej niż jeden. Jeśli zmienisz tabeli wyświetlane w panelu co do tabeli już wyświetlane w panelu innego tabele przełącznika paneli.

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Porady: dostęp do analizy wyników testu obciążenia](../test/how-to-access-load-test-results-for-analysis.md)
- [Analizowanie wyników testów obciążenia w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analizowanie naruszeń zasady progu](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Zarządzenie wynikami testów obciążenia w repozytorium wyników testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Podgląd podsumowania wyników testu obciążenia](../test/load-test-results-summary-overview.md)