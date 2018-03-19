---
title: "Analizowanie testów obciążenia błędów za pomocą panelu liczników w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- Load Test Analyzer, counters panel
ms.assetid: 981b4f1e-505a-4078-a06d-58ae17d996b4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 055925fd626e03df6e80fe02647fc2c1ca67d6ad
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-analyze-errors-using-the-counters-panel"></a>Porady: analizowanie błędów za pomocą panelu liczników

Panel liczników jest widoczny w widokach Wykresy i Tabele w Analizatorze testu obciążeniowego, gdy uruchomiony jest test obciążeniowy lub podczas analizy wyniku testu obciążeniowego. Aby uzyskać więcej informacji, zobacz [analizowanie wyników testów obciążenia w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md), [analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) i [porady: dostęp do wyników testu obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md).

 **Błędy** węzeł w panelu liczników zawiera wszystkie błędy, które zostały wykryte podczas testu obciążenia. Węzeł błędów zawiera podkategorii błąd kilka węzłów, które są specyficzne dla różnych typów błędów. Na przykład **wyjątki** i **błędy HTTP**.

 ![Panel liczników błąd węzła](../test/media/ltest_errornode.png "LTest_ErrorNode")

## <a name="to-analyze-errors-in-the-counters-panel"></a>Do analizowania błędów w panelu liczników

1.  Po zakończeniu testu obciążenia, lub po załadowaniu wyniku testu obciążenia Test analizatora w pasku narzędzi, wybrać **wykresy** lub **tabel**.

     **Liczniki** panelu są wyświetlane w widoku tabeli lub widoku wykresu.

2.  Panel liczników nie jest widoczny, jeśli **Pokaż panelu liczników** na pasku narzędzi.

3.  Rozwiń węzeł **błędy** i wybierz kategorię błędu lub błąd podkategorii przewidzianą do analizy.

4.  Kliknij prawym przyciskiem myszy błąd i wybierz jedną z następujących opcji:

    -   **Pokaż licznik na wykresie**: W widoku wykresu błąd zostanie dodany i wyróżnione na wybranego wykresu. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

    -   **Pokaż licznik w legendzie**: błąd zostanie dodany i zaznaczone w legendzie. Aby uzyskać więcej informacji, zobacz [przy użyciu legendy wykresu do analizowania testów obciążenia](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

    -   **Dodaj wykres**:

    1.  **Wprowadź nazwę wykresu** zostanie wyświetlone okno dialogowe.

    2.  W **nazwa wykresu** polu tekstowym, wpisz nazwę nowego wykresu, a następnie wybierz pozycję **OK**.

    3.  (Opcjonalnie) Ponownie kliknij prawym przyciskiem myszy błąd, a następnie wybierz **Pokaż licznik na wykresie**.

         Aby uzyskać więcej informacji, zobacz [porady: Tworzenie wykresów niestandardowych](../test/how-to-create-custom-graphs-in-load-test-results.md).

5.  (Opcjonalnie) Jeśli analizowania wystąpił błąd w wyniku testu obciążenia ukończone, rozważ użycie funkcji powiększenia znajduje się w wykresy. Aby uzyskać więcej informacji, zobacz [porady: powiększanie obszaru wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

    > [!TIP]
    > Jeśli błędy zostały wykryte podczas testu obciążenia, łącze zatytułowany znalezionych błędów wraz z liczbą będzie wyświetlany na pasku stanu analizatora testu obciążenia. Można wybrać łącze, aby wyświetlić wszystkie błędy w **błędy** tabeli widoku tabeli.

## <a name="see-also"></a>Zobacz także

- [Za pomocą panelu liczników w widoku wykresów i tabel](../test/counters-panel-in-load-test-analyzer.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)