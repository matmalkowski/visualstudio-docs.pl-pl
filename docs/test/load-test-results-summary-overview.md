---
title: Ładowanie omówienie podsumowania wyników testu w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.summary.view
helpviewer_keywords:
- load test results, summary
- load tests, summary in analyzer
- load tests, results summary
- Load Test Viewer, summary
- load tests, summary in Load Test Viewer
ms.assetid: 326b6c3c-5378-452b-8ca3-ba5a06ab3d41
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 001f7f866437807565bc83a8ad3a4dd809dd4100
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="load-test-results-summary-overview"></a>Podsumowanie wyników testów obciążenia — Przegląd

Po uruchomieniu testu obciążenia, można wyświetlić podsumowanie testu obciążenia, aby szybko poznać wyniki. Podsumowanie testu obciążenia zapewnia klucza wyniki w compact i łatwo odczytać formatu. Pozwala również na drukowanie podsumowania testu obciążenia. Ułatwia to używane podczas komunikacji wyniki do uczestników. Podsumowanie testu obciążenia jest również domyślny widok po otwarciu wyniku testu obciążenia z testu obciążenia wcześniej wykonywania. Aby uzyskać więcej informacji, zobacz [porady: dostęp do wyników testu obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md).

 ![Widok podsumowania](../test/media/ltest_summaryview.png "LTest_SummaryView")

## <a name="the-load-test-summary"></a>Podsumowanie testu obciążenia

Podsumowanie testu obciążenia jest podzielony na sekcje. Sekcje początkowej pojawiają się u góry podsumowania i są zawsze widoczne. Podczas wyświetlania podsumowania testu obciążenia pierwszego są następujące elementy:

- Informacje o uruchomienia testu

- Ogólne wyniki

- Kluczowe statystyki: 5 najwolniejszych stron z góry

- Kluczowe statystyki: 5 najwolniejszych testów z góry

- Kluczowe statystyki: 5 najwolniejszych operacji SQL z góry

    > [!NOTE]
    > W sekcji operacji SQL jest wyświetlana tylko wtedy, gdy jest włączone śledzenie SQL w teście obciążenia.

Sekcje zamknięcia znajdują się na końcu podsumowania i może zostać zwinięty aby zaoszczędzić miejsce. Następujące elementy są wyświetlane na końcu podsumowania testu obciążenia:

- Wyniki tekstu

- Strona z wynikami

- Wyniki transakcji

- System w obszarze zasoby testów

- Kontroler i zasobów agenta

- błędy

## <a name="test-run-information"></a>Informacje o uruchomienia testu

Uruchomienie testu sekcji informacji zawiera ogólne informacje o przebiegu, włącznie z nazwą testu, rozpoczęcia i zakończenia oraz kontrolera uruchomionego testu. Ta sekcja zawiera również opcjonalny opis uruchomienia umożliwiającego dodawanie po uruchomieniu testu obciążenia.

## <a name="overall-results"></a>Ogólne wyniki

Ogólny sekcji wyników zawiera podsumowania wyników testu, w tym liczbę żądań na sekundę, całkowita liczba nieudanych żądań, Średni czas odpowiedzi i strony Średni czas.

## <a name="key-statistic-top-5-slowest-pages"></a>Kluczowe statystyki: 5 najwolniejszych stron z góry

Najwolniejsze sekcja strony zawiera pierwsze 5 najwolniejszych stron w teście obciążenia. Adres URL i czas ładowania strony są wyświetlane na każdej stronie. Strony są wymienione w kolejności malejącej. Można wybrać adres URL strony, aby otworzyć **stron** tabeli i Sprawdź więcej szczegółów na tej stronie. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie strony sieci Web odpowiedzi](../test/how-to-view-web-page-response-time-in-a-load-test.md).

Wartość percentylu **95% czasu strony (s)** raport zakończenie 95% stron w czasie krótszym niż ten czas w sekundach.

## <a name="key-statistic-top-5-slowest-tests"></a>Kluczowe statystyki: 5 najwolniejszych testów z góry

Najwolniejsze sekcji testy zawiera top 5 najwolniejszych testów w teście obciążenia. Nazwa testu oraz średni czas testu są wyświetlane dla każdego z testów. Testy są wymienione w kolejności malejącej. Można wybrać nazwę testu, aby otworzyć **testy** tabeli i Sprawdź więcej szczegółów dla tego testu. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

Wartość percentylu **95% czasu testu (s)** zgłosić, że 95% testy wykonane w czasie krótszym niż ten czas w sekundach.

## <a name="key-statistic-top-5-slowest-sql-operations"></a>Kluczowe statystyki: 5 najwolniejszych operacji SQL z góry

Włączenie śledzenia SQL w teście obciążenia najwolniejsze sekcji zapytania zawiera najpopularniejsze 5 najwolniejszych kwerendy w teście obciążenia. Nazwa operacji i czas trwania są wyświetlane dla każdego z testów. Czas trwania jest wyświetlany w mikrosekundach programu SQL Server 2005 lub milisekund (SQL Server 2000 lub starszym). Testy są wymienione w kolejności malejącej według czasu trwania. Można wybrać nazwę działania, aby otworzyć **śledzenia SQL** tabeli i Sprawdź więcej szczegółów dla tej operacji. Aby uzyskać więcej informacji, zobacz [Table danych śledzenia SQL](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table).

## <a name="test-results"></a>Wyniki tekstu

Sekcja wyników testu zawiera listę wszystkich testów i scenariusze w teście obciążenia. Nazwa testu, scenariusz, ile razy, że zostało wykonane, ile razy nie powiodło się oraz średni czas testu są wyświetlane. Można wybrać nazwę testu, aby otworzyć **testy** tabeli i Sprawdź więcej szczegółów dla tego testu. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Można zwijać i rozwijać w tej sekcji, wybierając strzałkę w lewo tytuł sekcji.

## <a name="page-results"></a>Strona z wynikami

Sekcja wyniki strona zawiera listę wszystkich stron sieci Web w teście obciążenia. Adres URL, scenariusz, nazwa testu, czas średni strony i liczby są wyświetlane. Można wybrać adres URL strony, aby otworzyć **stron** tabeli i Sprawdź więcej szczegółów na tej stronie. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie strony sieci Web odpowiedzi](../test/how-to-view-web-page-response-time-in-a-load-test.md).

> [!NOTE]
> Można zwijać i rozwijać w tej sekcji, wybierając strzałkę w lewo tytuł sekcji.

## <a name="transaction-results"></a>Wyniki transakcji

Sekcja wyników transakcji zawiera listę wszystkich transakcji w teście obciążenia. Nazwa transakcji, scenariusza testu, czas odpowiedzi, czas, który upłynął i liczba są wyświetlane. Można wybrać nazwę transakcji, aby otworzyć **transakcji** tabeli i Sprawdź więcej szczegółów dla tej transakcji. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Można zwijać i rozwijać w tej sekcji, wybierając strzałkę w lewo tytuł sekcji.

Wartości percentylu raportu transakcji następujące informacje:

-   Zakończono 90% wszystkich transakcji w mniej niż \<czasu > sekund.

-   Zakończono 95% wszystkich transakcji w mniej niż \<czasu > sekund.

## <a name="system-under-test-resources"></a>System w obszarze zasoby testów

System sekcji Zasoby testu zawiera listę komputerów, które są zbiór komputerów docelowych, dla których wygenerowane obciążenie. W tym dowolnego komputera, z którego można zebrać zbiorów liczników niż agenta lub kontrolera. Nazwa komputera % czasu procesora i pamięci są wyświetlane. Można wybrać nazwę komputera, aby otworzyć **testowanym systemie** wykres i Sprawdź użycie zasobów w czasie. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Można zwijać i rozwijać w tej sekcji, wybierając strzałkę w lewo tytuł sekcji.

## <a name="controller-and-agent-resources"></a>Kontroler i zasobów agenta

Sekcja Zasoby kontrolera i agenta zawiera listę komputerów, które są używane do uruchomienia testu. Nazwa komputera % czasu procesora i pamięci są wyświetlane. Można wybrać nazwę komputera, aby otworzyć **kontroler i agenty** wykres i Sprawdź użycie zasobów w czasie. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Można zwijać i rozwijać w tej sekcji, wybierając strzałkę w lewo tytuł sekcji.

## <a name="errors"></a>błędy

W sekcji błędy zawiera listę wszystkich błędów, które wystąpiły podczas testu obciążenia. Wyświetlane są typu i podtypu błąd, liczba i ostatniego komunikatu. Możesz wybrać błąd, aby otworzyć **błędy** tabeli i Sprawdź więcej szczegółów dla tego błędu. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) i [porady: analizowanie błędów za pomocą panelu liczników](../test/how-to-analyze-errors-using-the-counters-panel.md).

> [!NOTE]
> Można zwijać i rozwijać w tej sekcji, wybierając strzałkę w lewo tytuł sekcji.

## <a name="printing-a-summary"></a>Drukowanie podsumowanie

Podsumowanie testu obciążenia można wydrukować, wybierając **drukowanie** menu skrótów w podsumowaniu. Wyświetl podgląd wydruku pierwszy, wybierając **Podgląd wydruku** menu skrótów w podsumowaniu. Pozwala również na drukowanie bezpośrednio na ekranie podglądu.

## <a name="see-also"></a>Zobacz także

- [Analizowanie naruszeń zasady progu](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)