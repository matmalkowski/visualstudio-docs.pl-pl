---
title: "Panel liczników analizowanie testów obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, counters panel
ms.assetid: e1a388d7-5d33-4631-931a-5653ac4aefdc
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 9e693872784519f5cdcacbd0691b6f69334af22e
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="use-the-counters-panel-in-graphs-view-and-tables-view"></a>Za pomocą panelu liczników w widoku wykresów i tabel

Panel liczników jest widoczny w widokach Wykresy i Tabele w Analizatorze testu obciążeniowego, gdy uruchomiony jest test obciążeniowy lub podczas analizy wyniku testu obciążeniowego. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md), [analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) i [porady: dostęp do wyników testu obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md).

Panel liczników przedstawia widok strukturalnych wszystkie liczniki wydajności, które zostały zebrane podczas testu obciążenia. Możesz wyświetlić lub ukryć panel liczników, wybierając **Pokaż panelu liczników** na narzędzi analizatora testu obciążenia.

Liczniki są zorganizowane w strukturze drzewa, w którym węzłów liści są wystąpienia licznika wydajności, które mogą zostać wyświetlone na wykresie.

Panel liczników oferuje następujące funkcje:

-   Komunikuje się informacji naruszenie progu.

-   Wybór liczniki dla wykresów.

-   Widok drzewa strukturalnych wszystkie liczniki wydajności zebrane podczas testu obciążenia. z następujących gałęzi głównej:

    -   **Ogólny:** zawiera podsumowanie danych licznika wydajności dla każdego agenta testowego i testu obciążenia całego.

    -   **Nazwa scenariusza:** gałęzie etykietą nazwy scenariusza testu obciążenia w drzewie licznika wydajności zawierają wystąpienia licznika testu obciążenia w wszystkie skojarzone z scenariusza testu obciążenia określonej. Większość liczników testu obciążenia są zagnieżdżone w obrębie gałąź scenariusza.

         Gałąź scenariusz zawiera węzły testu wydajności sieci Web. Węzły testu wydajności sieci Web zawiera strony, żądania i transakcji węzłów. Wszystkie węzły liści WE ta struktura jest licznika wydajności, które można dodać do wykresu.

    -   **Komputery:** zawiera wszystkie wystąpienia licznika testu obciążenia z systemem innym niż pogrupowane według komputera. Gałęzi komputery zawiera węzeł dla każdego komputera, który jest skojarzony z kontrolerem testów obciążenia określona w sekcji role aktualnie wybrane ustawienia testu. Aby uzyskać więcej informacji, zobacz [kontrolery testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md).

         Każdy węzeł komputera zawiera zestaw kategorii licznika wydajności zebrane z tego komputera. Kategorie zawierają liczniki i liczniki zawierać nazwy wystąpień liczników wydajności.

    -   **Błędy:** zawiera wszystkie błędy wykryte podczas testu obciążenia. Węzeł błędów zawiera kilka węzłów błąd podkategorię. Podkategorie są specyficzne dla różnych typów błędów, na przykład, wyjątków i błędów HTTP.

### <a name="scenario-name-node-in-counters-panel"></a>Scenariusz nazwa węzła w panelu liczników

|||
|-|-|
|![Licznik panelu scenariusz nazwa węzła](../test/media/ltest__namenode.png)|1. W tym węźle są wyświetlane wszystkie liczniki wydajności skojarzonego z Scenario1 testu obciążenia.<br />2. Wszystkie testy scenariusza znajdują się pod węzłem scenariusza. Etykieta wskazuje nazwę testu.<br />3. Węzły liści w węźle testu są liczniki przypadek testowy testu obciążenia, gdzie nazwa wystąpienia licznika to nazwa testu.<br />4. Załaduj wszystkie wystąpienia licznika strony testu skojarzone z gałęzi testu wydajności sieci Web. W tym węźle testu obciążenia tempie wystąpień liczników skojarzony ze stroną logowania UZYSKAĆ (nazwy raportowania) testu wydajności sieci IBuyBrowse Web w Scenario1 testu obciążenia są zawarte w tym miejscu.<br />5. Węzły liści w węźle strony są załadować liczników strony testu.<br />6. Wszystkie obciążenia licznik żądania testu, który wystąpienia skojarzony z testem wydajności sieci Web są zawarte w gałęzi testu wydajności sieci Web. W tym węźle wszystkie żądania wystąpienia liczników skojarzony z żądaniem logowania UZYSKAĆ (nazwy raportowania) testu wydajności sieci IBuyBrowse Web w Scenario1 o testu obciążenia zawartych w tym miejscu.<br />7. Węzły liści w węźle żądania są załadować liczników żądania testu.<br />8. Wszystkie obciążenia testu transakcji licznika wystąpienia skojarzony z testem wydajności sieci Web są zawarte w gałęzi testu wydajności sieci Web. W tym węźle wszystkich wystąpień liczników transakcji skojarzyć z transakcji o nazwie Transaction1 testu wydajności sieci IBuyBrowse Web w Scenraio1 testu obciążenia są zawarte w tym miejscu.<br />9. Węzły liści w węźle transakcji są załadować liczników transakcji testu.<br />10. Węzeł testu jednostki.|

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone — tematy|
|-----------|-----------------------|
|**Dodaj więcej liczniki wydajności do wykresu, w widoku wykresu:** panelu w liczniki można dodać różne rodzaje danych do wykresu testu obciążenia przez dodanie większej liczby liczników wydajności na wykresie.|-   [Porady: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**Analizowanie wszelkie progi określone w teście obciążenia, które zostały naruszone:** panelu liczników Wyświetla ikony reprezentujące naruszenia progu, które można następnie dodać do tabel i wykresów do dalszej analizy.|-   [Porady: analizowanie naruszeń progu za pomocą panelu liczników](../test/analyze-threshold-rule-violations-in-load-tests.md)|
|**Analizowanie błędów, które zostały wykryte podczas testu obciążenia:** panelu liczników zawiera węzeł błędy, która zawiera błąd kategorie i podkategorie, takich jak błędy HTTP, które można dodawać błędów do wykresy do dalszej analizy.|-   [Porady: analizowanie błędów za pomocą panelu liczników](../test/how-to-analyze-errors-using-the-counters-panel.md)|

## <a name="performance-counter-sampling-interval-considerations"></a>Zagadnienia dotyczące interwał próbkowania licznika wydajności

Wybierz wartość dla **częstotliwość próbkowania** właściwości w teście obciążenia Uruchom ustawienia oparte na długość testu obciążenia. Mniejszą częstotliwość próbkowania, np. domyślna wartość pięć sekund, wymaga więcej miejsca w bazie danych wyników testu obciążenia. Dłużej testów obciążenia zwiększenie częstotliwości próbkowania powoduje zmniejszenie ilości zbieranych danych. Aby uzyskać więcej informacji, zobacz [porady: określanie wielkości próbki](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Poniżej przedstawiono wskazówki dotyczące częstotliwości próbkowania:

|Czas trwania testu obciążenia|Zalecana częstotliwość próbkowania|
|------------------------|-----------------------------|
|\< 1 godzina|5 sekund|
|1 – 8 godzin|15 sekund|
|8 – 24 godziny|30 sekund|
|> 24 godziny|60 sekund|

## <a name="considerations-for-including-timing-details-to-collect-percentile-data"></a>Zagadnienia dotyczące szczegółów chronometrażu do zbierania danych percentyl, w tym

Brak właściwości w ustawieniach wykonywania w edytora testu obciążenia o nazwie **magazynowania szczegółów chronometrażu**. Jeśli **magazynowania szczegółów chronometrażu** właściwość jest włączona, a następnie czas wykonywania każdego poszczególnych testu, transakcji i strony podczas testu obciążenia jest przechowywany w repozytorium wyników testów obciążenia. Dzięki temu danych percentyl 90 i 95 ma być wyświetlany w analizatorze testów obciążenia w tabelach testy, transakcji i strony.

Istnieją dwie opcje do włączania **magazynowania szczegółów chronometrażu** właściwości we właściwościach ustawień uruchamiania:**StatisticsOnly** i **AllIndividualDetails**. Za pomocą obu opcji wszystkie poszczególne testy, strony i transakcji jest mierzony i danych percentyl jest obliczana na podstawie danych poszczególnych czas. Różnica jest to, że z **StatisticsOnly** opcję zaraz po obliczeniu danych percentyl poszczególnych czas dane zostaną usunięte z repozytorium. Zmniejsza to ilość miejsca, który jest wymagany w repozytorium, gdy używasz szczegółów chronometrażu. Użytkownicy wersji advanced może być jednak przetwarzania danych szczegółów chronometrażu w inny sposób, przy użyciu narzędzia SQL. Jeśli tak, jest **AllIndividualDetails** opcja powinna być używana, dzięki czemu dane szczegółów chronometrażu są dostępne do przetworzenia. Ponadto jeśli właściwość jest ustawiona **AllIndividualDetails**, a następnie można analizowanie aktywności wirtualnego użytkownika za pomocą wykresu aktywności wirtualnego użytkownika w analizatorze testu obciążenia, po zakończeniu testu obciążenia uruchomione. Aby uzyskać więcej informacji, zobacz [analizowanie wirtualnego działań użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

Ilość miejsca, która jest wymagana w repozytorium wyników testów obciążenia do przechowywania danych szczegółów chronometrażu może być duży, zwłaszcza w przypadku testów obciążenia jest już uruchomiona. Ponadto czas przechowywania tych danych w repozytorium wyników testów obciążenia na końcu testu obciążenia jest dłużej, ponieważ te dane są przechowywane w agentach testu obciążenia do momentu zakończenia testu obciążenia wykonywania. Po zakończeniu testu obciążenia, dane są przechowywane w repozytorium. Domyślnie **magazynowania szczegółów chronometrażu** właściwość jest włączona. Jeśli jest to problem w środowisku do testowania, możesz ustawić **magazynowania szczegółów chronometrażu** do **Brak**.

Aby uzyskać więcej informacji, zobacz [porady: Określanie właściwości magazynowania szczegółów chronometrażu](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)