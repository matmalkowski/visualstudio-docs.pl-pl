---
title: Dodawanie i usuwanie liczników na wykresach w wynikach testów obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load test results graphs, adding counters
- load test results graph
- load test, results graph
- load test results, graphs
ms.assetid: 81536233-1962-40d9-9511-0b4633814d90
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 3293b526b3380d3052123d45f3fb7f6599f7b5f7
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751978"
---
# <a name="how-to-add-and-delete-counters-on-graphs-in-load-test-results"></a>Porady: dodawanie i usuwanie liczników na wykresach w wynikach testów obciążenia

Panel liczników umożliwia dodawanie liczników wydajności do wykresu.

 ![Licznik dodane do wykresu.](../test/media/ltest_selectcounter.png)

 **Zagadnienia dotyczące interwał próbkowania licznika wydajności**

 Wybierz wartość dla **częstotliwość próbkowania** właściwości w teście obciążenia Uruchom ustawienia oparte na długość testu obciążenia. Mniejszą częstotliwość próbkowania, np. domyślna wartość pięć sekund, wymaga więcej miejsca w bazie danych wyników testu obciążenia. Dłużej testów obciążenia zwiększenie częstotliwości próbkowania powoduje zmniejszenie ilości zbieranych danych. Aby uzyskać więcej informacji, zobacz [porady: określanie wielkości próbki](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

 Poniżej przedstawiono wskazówki dotyczące częstotliwości próbkowania:

|Czas trwania testu obciążenia|Zalecana częstotliwość próbkowania|
|------------------------|-----------------------------|
|\< 1 godzina|5 sekund|
|1 – 8 godzin|15 sekund|
|8 – 24 godziny|30 sekund|
|> 24 godziny|60 sekund|

 **Zagadnienia dotyczące szczegółów chronometrażu do zbierania danych percentyl, w tym**

 Brak właściwości w ustawieniach wykonywania w edytora testu obciążenia o nazwie **magazynowania szczegółów chronometrażu**. Jeśli **magazynowania szczegółów chronometrażu** właściwość jest włączona, a następnie czas wykonywania każdego poszczególnych testu, transakcji i strony podczas testu obciążenia będą przechowywane w repozytorium wyników testów obciążenia. Dzięki temu danych percentyl 90 i 95 ma być wyświetlany w analizatorze testów obciążenia w tabelach testy, transakcji i strony.

 Istnieją dwie opcje do włączania **magazynowania szczegółów chronometrażu** właściwość we właściwościach ustawień uruchamiania o nazwie **StatisticsOnly** i **AllIndividualDetails**. Za pomocą obu opcji wszystkie poszczególne testy, strony i transakcji jest mierzony i danych percentyl jest obliczana na podstawie danych poszczególnych czas. Różnica jest to, że z **StatisticsOnly** opcję zaraz po obliczeniu danych percentyl poszczególnych czas dane zostaną usunięte z repozytorium. Zmniejsza to ilość miejsca, który jest wymagany w repozytorium, gdy używasz szczegółów chronometrażu. Użytkownicy wersji advanced może być jednak przetwarzania danych szczegółów chronometrażu w inny sposób, przy użyciu narzędzia SQL. Jeśli tak, jest **AllIndividualDetails** opcja powinna być używana, dzięki czemu dane szczegółów chronometrażu są dostępne do przetworzenia. Ponadto jeśli właściwość jest ustawiona **AllIndividualDetails**, a następnie można analizowanie aktywności wirtualnego użytkownika za pomocą wykresu aktywności wirtualnego użytkownika w analizatorze testu obciążenia, po zakończeniu testu obciążenia uruchomione. Aby uzyskać więcej informacji, zobacz [analizowanie wirtualnego działań użytkownika w widoku szczegółów](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

Ilość miejsca w repozytorium wyników testów obciążenia do przechowywania danych szczegółów chronometrażu może być bardzo duży, zwłaszcza w przypadku testów obciążenia jest już uruchomiona. Ponadto czas przechowywania tych danych w repozytorium wyników testów obciążenia na końcu testu obciążenia jest dłużej, ponieważ te dane są przechowywane w agentach testu obciążenia do momentu zakończenia testu obciążenia wykonywania. Po zakończeniu testu obciążenia, dane są przechowywane w repozytorium. Domyślnie **magazynowania szczegółów chronometrażu** właściwość jest włączona. Jeśli jest to problem w środowisku do testowania, możesz ustawić **magazynowania szczegółów chronometrażu** do **Brak**.

Aby uzyskać więcej informacji, zobacz [porady: Określanie właściwości magazynowania szczegółów chronometrażu](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="to-display-a-particular-performance-counter-on-a-load-test-graph"></a>Aby wyświetlić konkretnego licznika wydajności na wykresie testu obciążenia

1.  Po zakończeniu testu obciążenia, lub po załadowaniu wyniku testu obciążenia Test analizatora w pasku narzędzi, wybierz opcję **wykresy**.

     **Liczniki** panel jest wyświetlany w widoku wykresu.

    > [!NOTE]
    > Panel liczników nie jest widoczny, jeśli **Pokaż panelu liczników** na pasku narzędzi.

2.  W panelu liczników rozwinąć węzły w hierarchii, do momentu znalezienia licznika wydajności, które mają być wyświetlane wyświetlanych w postaci graficznej.

     Na przykład, aby wyświetlić ilość dostępnej pamięci na komputerze, na którym są uruchomione testy, rozwiń węzeł **komputerów**, rozwiń węzeł dla komputera, a następnie rozwiń **pamięci**. Zobaczysz **dostępna pamięć (MB)** licznika.

3.  Wybierz wykres, na którym chcesz wyświetlić licznika wydajności.

4.  Kliknij prawym przyciskiem myszy licznik wydajności w **liczniki** panelu i wybierz **Pokaż licznik na wykresie**.

    > [!TIP]
    > Aby tymczasowo zatrzymać wyświetlanie danych licznika wydajności na wykresie, wyczyść pole wyboru dla licznika wydajności w legendzie. Dzięki temu statystyki min, max i średnia, które były analizowane bez wyświetlania linię trendu na wykresie. Może to być przydatne, jeśli wykres zawiera kilka nakładające się powierzchni licznika wydajności podczas analizowania problemów. Aby uzyskać więcej informacji, zobacz [przy użyciu legendy wykresu do analizowania testów obciążenia](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

5.  Aby usunąć dane licznika wydajności z wykresu, kliknij prawym przyciskiem myszy licznik wydajności w **licznika** kolumny legendy i wybierz **usunąć**.

     \- lub -

     Kliknij prawym przyciskiem myszy wiersza danych w wykresie i wybierz **usunąć**.

     \- lub -

     Wybierz licznik wydajności w **licznika** kolumny legendy lub dane wiersz na wykresie, a następnie naciśnij klawisz **usunąć** klucza.

    > [!NOTE]
    > Możesz również umieścić w legendzie, ale nie na wykresie licznika wydajności przy użyciu **dodać licznik w legendzie** polecenia.

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Porady: Tworzenie wykresów niestandardowych](../test/how-to-create-custom-graphs-in-load-test-results.md)