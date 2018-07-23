---
title: Panel liczników do analizowania testów obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, counters panel
ms.assetid: e1a388d7-5d33-4631-931a-5653ac4aefdc
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 2b85d2d20f4400e252cbfd19ea169c7b27b2aecf
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176882"
---
# <a name="use-the-counters-panel-in-graphs-view-and-tables-view"></a>Za pomocą panelu liczników w widokach wykresy i tabele

**Liczniki** panel jest widoczny w widokach wykresy i tabele w analizatorze testu obciążeniowego, gdy uruchomiony jest test obciążeniowy lub podczas analizy wyniku testu obciążeniowego. Aby uzyskać więcej informacji, zobacz [w widoku wykresu z wynikami testów obciążeniowych analizy](../test/analyze-load-test-results-in-the-graphs-view.md), [analizowanie wyników testów obciążenia oraz błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) i [jak: dostęp do wyników testów obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md).

**Liczniki** panelu pojawiają się ze strukturą widoku wszystkich liczników wydajności, które zostały zebrane podczas testu obciążeniowego. Możesz pokazać lub ukryć **liczniki** panel, wybierając **Pokaż Panel liczników** na **analizatora testu obciążenia** paska narzędzi.

Liczniki są zorganizowane w postaci struktury drzewiastej, gdzie węzły liści są wystąpienia liczników wydajności, które można przedstawić graficznie —.

Panel liczników oferuje następujące funkcje:

-   Komunikuje się informacje o naruszenie progu.

-   Wybór liczniki dla wykresów.

-   Widok drzewa strukturze wszystkie liczniki wydajności zebrane podczas testu obciążenia za pomocą następujących gałęzi głównej:

    -   **Ogólny:** zawiera podsumowanie danych licznika wydajności dla każdego agenta testowego i całego testu obciążeniowego.

    -   **Nazwa scenariusza:** gałęzie opatrzone etykietami nazw scenariuszy testu obciążeniowego w drzewie liczników wydajności zawierają wystąpienia liczników testu obciążeniowego w wszystkie skojarzone z określonym scenariuszem testu obciążeniowego. Większość liczników testu obciążenia są zagnieżdżone w obrębie gałęzi scenariusza.

         Gałąź scenariusz zawiera węzły testów wydajności sieci web. Węzły testów wydajności sieci web zawiera strony, żądań i transakcji węzłów. Dowolny węzeł liścia w tej strukturze jest licznika wydajności, które mogą być dodawane do wykresu.

    -   **Komputery:** zawiera wszystkie wystąpienia liczników niezwiązanych z testem obciążeniowym, pogrupowane według komputerów. Gałęzi komputery zawiera węzeł dla każdego komputera, który jest skojarzony z kontrolerem testów obciążenia, które są określone w sekcji role aktualnie wybrane ustawienia testu. Aby uzyskać więcej informacji, zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).

         Każdy węzeł komputera zawiera zestaw kategorii licznika wydajności zbierane z tego komputera. Kategorie zawierają liczniki i liczniki zawierać nazwy wystąpienia licznika wydajności.

    -   **Błędy:** zawiera wszystkie błędy wykryte podczas testu obciążeniowego. Węzeł błędów zawiera kilka węzłów błąd podkategorii. Podkategorie są specyficzne dla różnych rodzajów błędów, na przykład, wyjątki i błędy protokołu HTTP.

### <a name="scenario-name-node-in-counters-panel"></a>Scenariusz nazwę węzła w panelu liczników

|Panel liczników|Opis|
|-|-|
|![Licznik panelu scenariusz nazwa węzła](../test/media/ltest__namenode.png)|1. W tym węźle są wyświetlane wszystkie liczniki wydajności skojarzone z Scenario1 testu obciążeniowego.<br />2. Wszystkie testy scenariusza znajdują się pod węzłem scenariusza. Etykieta wskazuje nazwę testu.<br />3. Węzły liści, w obszarze węzła testu są liczniki przypadek testowy testu obciążenia, gdzie nazwa wystąpienia licznika jest nazwa testu.<br />4. Załaduj wszystkie wystąpienia liczników strony testu skojarzone z gałęzią testu wydajności sieci web. W tym węźle testu obciążeniowego tempie wystąpienia liczników skojarzony ze stroną logowania Pobierz (nazwa raportowania) dla testu wydajności sieci web IBuyBrowse w Scenario1 testu obciążeniowego są zawarte w tym miejscu.<br />5. Węzły liści, w węźle strony są załadować liczniki testu.<br />6. Wszystkie obciążenia licznik żądań testu, którego wystąpienia skojarzone z testem wydajności sieci web znajdują się w gałęzi testu wydajności sieci web. W tym węźle wszystkie żądania wystąpienia liczników skojarzony z żądaniem logowania Pobierz (nazwa raportowania) z testem wydajności sieci web IBuyBrowse w o Scenario1 testu obciążeniowego opisanych w tym miejscu.<br />7. Węzły liści, w węźle żądania są załadować liczniki żądania testu.<br />8. Wszystkich transakcji wystąpienia liczników testu obciążeniowego skojarzone z testem wydajności sieci web są zawarte w gałęzi testu wydajności sieci web. W tym węźle wszystkie wystąpienia liczników transakcji skojarzyć z transakcji o nazwie Transaction1 testu wydajności sieci web IBuyBrowse w Scenraio1 testu obciążeniowego są zawarte w tym miejscu.<br />9. Węzły liści, w węźle transakcji są załadować liczniki transakcji testu.<br />10. Węzeł testu jednostki.|

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-----------|-----------------------|
|**Dodawanie większej liczby liczników wydajności do wykresu w widoku wykresu:** w **liczniki** panelu, można dodać różne rodzaje danych do wykresu testu obciążeniowego przez dodanie większej liczby liczników wydajności na wykresie.|-   [Porady: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**Analizowanie wszelkich wartości progowych określonych w teście obciążenia, które zostały naruszone:** **liczniki** panel wyświetla ikony przedstawiające naruszenia progów, które można następnie dodać do tabel i wykresów do dalszej analizy.|-   [Porady: analizowanie naruszeń progu za pomocą panelu liczników](../test/analyze-threshold-rule-violations-in-load-tests.md)|
|**Analizuj wszystkie błędy, które zostały wykryte podczas przebiegu testu obciążeniowego:** **liczniki** panelu posiada węzeł błędów, która zawiera błąd kategorie i podkategorie, takie jak błędy HTTP, które służą do dodania błędów do wykresów dla dalszej analizy.|-   [Porady: analizowanie błędów za pomocą panelu liczników](../test/how-to-analyze-errors-using-the-counters-panel.md)|

## <a name="performance-counter-sampling-interval-considerations"></a>Zagadnienia interwału próbkowania licznika wydajności

Wybierz wartość dla **częstotliwość próbkowania** uruchomieniowe właściwości w teście obciążenia, na podstawie długości testu obciążenia. Mniejsza częstotliwość próbkowania, np. wartość domyślna pięć sekund, wymaga więcej miejsca w bazie danych wyników testu obciążenia. Dla dłuższych testów obciążenia zwiększenie częstotliwości próbkowania zmniejsza ilość zbieranych danych. Aby uzyskać więcej informacji, zobacz [porady: określanie wielkości próbki](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Oto niektóre wytyczne dotyczące częstotliwości próbkowania:

|Czas trwania testu obciążenia|Zalecana częstotliwość próbkowania|
|------------------------|-----------------------------|
|\< 1 godzina|5 sekund|
|1 - 8 godzin|15 sekund|
|8 - 24 godziny|30 sekund|
|> 24 godziny|60 sekund|

## <a name="considerations-for-including-timing-details-to-collect-percentile-data"></a>Zagadnienia dotyczące szczegółowych informacji o czasie do zbierania danych percentyl, w tym

Jest właściwością w ustawieniach uruchamiania w edytorze testu obciążenia o nazwie **przechowywanie informacji**. Jeśli **przechowywanie informacji** właściwość jest włączona, a następnie to czas na wykonanie każdego indywidualnego testu, transakcji i strony podczas testu obciążeniowego jest przechowywany w repozytorium wyników testu obciążenia. Dzięki temu danych percentyla 90 i 95 w analizatorze testów obciążenia w tabelach testy, transakcji i strony.

Istnieją dwie możliwości włączenia **przechowywanie informacji** właściwości we właściwościach parametrów uruchomieniowych: **StatisticsOnly** i **AllIndividualDetails**. Niezależnie od wybranej opcji wszystkie poszczególne testy, strony i transakcje są upłynął limit czasu i percentyli są obliczane na podstawie danych o poszczególnych chronometrażach. Różnica polega na tym, wraz z **StatisticsOnly** opcji tak szybko, jak została obliczona danych percentyl, o poszczególnych chronometrażach, dane są usuwane z repozytorium. Zmniejsza to ilość miejsca wymaganego w repozytorium, użyj szczegółów chronometrażu. Jednak użytkownicy zaawansowani może być do przetwarzania danych szczegółów chronometrażu w inny sposób, przy użyciu narzędzi SQL. Jeśli tak, jest **AllIndividualDetails** tak, aby dane szczegółowe chronometrażu były dostępne dla tego przetwarzania, należy użyć opcji. Ponadto jeśli właściwość jest ustawiona **AllIndividualDetails**, następnie można analizować aktywności wirtualnego użytkownika za pomocą **wirtualnego aktywności użytkownika** wykresu w analizatorze testu obciążenia po zakończeniu testu obciążenia Zakończono już działa. Aby uzyskać więcej informacji, zobacz [analizowanie aktywności wirtualnego użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

Ilość miejsca wymaganego w repozytorium wyników testu obciążenia do przechowywania szczegółowych danych o chronometrażu mogą być duże, szczególnie w przypadku uruchamiania dłuższych testów obciążenia. Ponadto czas przechowywania tych danych w repozytorium wyników testów obciążeniowych na koniec testu obciążenia jest dłuższy, ponieważ te dane są przechowywane w agentach testowych obciążenia do momentu zakończenia testów obciążenia. Po zakończeniu testu obciążenia, dane są przechowywane w repozytorium. Domyślnie **przechowywanie informacji** właściwość jest włączona. Jeśli jest to problem dla środowiska testowego, warto ustawić **przechowywanie informacji** do **Brak**.

Aby uzyskać więcej informacji, zobacz [porady: Określanie właściwości magazynowania szczegółów chronometrażu](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)