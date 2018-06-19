---
title: Analizowanie wyników testów obciążenia w programie Visual Studio
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test results
- load tests, analyzing test results
- load tests, managing test results
ms.assetid: 8a4ba300-425d-447c-91d9-c53f4345feee
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 06c9125de718ddada277985513efdb5e0590e4c7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31968293"
---
# <a name="analyze-load-test-results-using-the-load-test-analyzer"></a>Analizowanie wyników testów obciążenia za pomocą analizatora testu obciążenia

Znajdź wąskich gardeł, zidentyfikować błędy i miar ulepszenia w aplikacji, korzystając z analizatora testu obciążenia. Analizowanie wyników testów obciążenia w następujący sposób:

-   Monitorowanie testu obciążenia, gdy jest uruchomiona.

-   Analizowanie testów obciążenia, po jego ukończeniu.

-   Wyświetlanie wyników z poprzedniego testu obciążenia.

Można również tworzyć raporty, pozwalające porównać dwa lub więcej raportów analizy trendów na udostępnianie uczestników. Zobacz [raportowanie wyników testów obciążenia do potrzeb porównań testów lub analizy trendów](../test/compare-load-test-results.md).

Określa, czy uruchomienie testu obciążenia programu Visual Studio Enterprise lub z wiersza polecenia i określa, czy uruchomić test obciążenia na pojedynczym komputerze lub na komputerze zdalnym, można wykonać te zadania.

## <a name="differences-between-analyzing-a-running-and-a-completed-load-test"></a>Różnice między analizowanie uruchomione i zakończonego testu obciążenia

 Po uruchomieniu testu obciążenia analizatora testu obciążenia wyświetla się w osobnej karcie wraz z nazwą testu obciążenia i czas rozpoczęcia testu (na przykład **LoadTest1 [godzina 12:40]**). Po uruchomieniu testu obciążenia mniejszy zestaw danych licznika wydajności jest zachowywana w pamięci. Ten zestaw danych można monitorować po uruchomieniu testu obciążenia. Po zakończeniu testu obciążenia można analizować pełny zestaw danych z bazy danych. Istnieją różnice w danych jest wyświetlane, gdy uruchomień testów obciążenia i dane, które można wyświetlić po obciążenia testu została ukończona. Na przykład 90 procent i 95 procent dane czasu odpowiedzi nie zostało obliczone, aż do zakończenia testu obciążenia. Pewne różnice występują także w funkcje narzędzi, które są dostępne do analizowania danych.

 Po uruchomieniu testu obciążenia, dostępne są dwa widoki: widok wykresów i tabel. Widok wykresów umożliwia wykres liczników wydajności, które są zbierane. Wyświetl tabele zapewnia informacje o poszczególnych testów, strony, transakcje i żądań, które są zbierane. Możesz również uzyskać tabelę, która zawiera błędy.

 Domyślnie po zakończeniu uruchomienia testu obciążenia wyświetlany jest widok podsumowania. Można przełączać się między widokami podsumowanie, wykresów, tabel i szczegóły za pomocą paska narzędzi. Analizatora testu obciążenia może zadokowane lub ustawić float przy użyciu techniki zwykle manipulowania okno programu Visual Studio. Podczas analizowania uruchomień testów obciążenia ukończone, może mieć wielu załadować Test analizatorów Otwórz w tym samym czasie, aby porównać uruchomień testów obciążenia różnych.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone — tematy|
|-----------|-----------------------|
|**Uzyskiwanie dostępu do wyników testu obciążenia:** po uruchomieniu testu obciążenia w edytorze testu obciążenia automatycznego otwierania wyników testu obciążenia i uruchamianie testu obciążenia jest wyświetlana w analizatorze testu obciążenia.|-   [Porady: dostęp do analizy wyników testu obciążenia](../test/how-to-access-load-test-results-for-analysis.md)|
|**Dodaj uwagi do analizy do testów obciążenia:** komentarze można dodawać do testów obciążenia podczas przeprowadzania analizy. Komentarze są przechowywane trwale, wraz z wyniku testu obciążenia. Możesz również wprowadzić opis wyświetlany w **opis** kolumny, która jest skojarzona z testu obciążenia w oknie dialogowym Otwieranie i zarządzanie wynikami testu w edytorze testu obciążenia.<br /><br /> Aby uzyskać więcej informacji, zobacz [porady: dostęp do wyników testu obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md).<br /><br /> Ponadto komentarze są wyświetlane podczas tworzenia wyników testu obciążenia raport programu Excel.<br /><br /> Aby uzyskać więcej informacji, zobacz [raportowanie wyników testów obciążenia do potrzeb porównań testów lub analizy trendów](../test/compare-load-test-results.md).|-   [Porady: dodawanie komentarzy podczas analizowania zakończonego testu obciążenia](../test/how-to-add-comments-on-a-completed-load-test.md)|
|**Analizowanie wyników testów obciążenia:** po uzyskujesz dostęp do danych uruchomienia testu obciążenia, można przeanalizować danych. Można wyświetlić podsumowanie testu obciążenia, aby szybko poznać wyniki. Podsumowanie testu obciążenia pokazuje klucza wyniki w formacie kompaktowym i łatwo odczytu.<br /><br /> Można drukować podsumowania testu obciążenia. Ułatwia to używane podczas komunikacji wyniki do uczestników.<br /><br /> Szczegóły wyników testu obciążenia można analizować przy użyciu wykresów i tabel w wynikach. Obejmują one błędy, stron, żądania, śledzenie programu SQL Server, testy, progi i transakcji.|-   [Podgląd podsumowania wyników testu obciążenia](../test/load-test-results-summary-overview.md)<br />-   [Porady: wyświetlanie czasu odpowiedzi strony Web](../test/how-to-view-web-page-response-time-in-a-load-test.md)<br />-   [Analizowanie naruszeń zasady progu](../test/analyze-threshold-rule-violations-in-load-tests.md)<br />-   [Analizowanie wyników testów obciążenia w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md)<br />-   [Analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)|
|**Analizowanie aktywności wirtualnego użytkownika w wynikach testów obciążenia do izolowania problemów z wydajnością:** wirtualnego wykres aktywności użytkownika można użyć do wizualizacji, użytkownicy wirtualni podczas testu obciążenia. Może to pomóc w izolowanie największego procesora CPU lub przerwy w żądań na sekundę i określić, które stron lub testy są uruchomione podczas te wartości szczytowe i porzucania.|-   [Analizowanie aktywności wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)|