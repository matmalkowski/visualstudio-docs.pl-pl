---
title: Analizuj test obciążeniowy błędów za pomocą panelu liczników w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Analyzer, counters panel
ms.assetid: 981b4f1e-505a-4078-a06d-58ae17d996b4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: e7ccd21e5432003de7ec3b03bf94716802846bd4
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204339"
---
# <a name="how-to-analyze-errors-using-the-counters-panel"></a>Porady: analizowanie błędów za pomocą panelu liczników

**Liczniki** panel jest widoczny w widokach wykresy i tabele w **analizatora testu obciążenia** gdy uruchomiony jest test obciążeniowy lub podczas analizy wyniku testu obciążeniowego. Aby uzyskać więcej informacji, zobacz [w widoku wykresu z wynikami testów obciążeniowych analizy](../test/analyze-load-test-results-in-the-graphs-view.md), [analizowanie wyników testów obciążenia oraz błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) i [jak: dostęp do wyników testów obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md).

 **Błędy** w węźle **liczniki** panelu zawiera wszystkie błędy, które zostały wykryte podczas testu obciążeniowego. **Błędy** węzeł zawiera kilka węzłów Podkategoria błędów, które są specyficzne dla różnych rodzajów błędów. Na przykład **wyjątki** i **błędy HTTP**.

 ![Węzeł błędu panelu liczników](../test/media/ltest_errornode.png)

## <a name="to-analyze-errors-in-the-counters-panel"></a>Do analizowania błędów w panelu liczników

1.  Po zakończeniu testu obciążeniowego lub po załadowaniu wynik testu, na pasku narzędzi analizatora testu obciążeniowego, wybrać **wykresów** lub **tabel**.

     **Liczniki** panelu pojawiają się w widoku wykresy lub w widoku tabele.

2.  Jeśli **liczniki** panel nie jest widoczny, wybierz polecenie **Pokaż Panel liczników** na pasku narzędzi.

3.  Rozwiń **błędy** i wybierz kategorię błąd lub błąd Podkategoria, którą chcesz analizować.

4.  Kliknij prawym przyciskiem myszy błąd, a następnie wybierz jedno z następujących opcji:

    -   **Pokaż licznik na wykresie**: W widoku wykresy błąd zostanie dodany i wyróżnione na wybranym wykresie. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

    -   **Pokaż licznik na legendzie**: błąd zostanie dodany i zaznaczone w legendzie. Aby uzyskać więcej informacji, zobacz [analizowanie testów obciążenia przy użyciu legendy wykresu](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

    -   **Dodaj wykres**:

    1.  **Wprowadź nazwę wykresu** zostanie wyświetlone okno dialogowe.

    2.  W **nazwa wykresu** polu tekstowym wpisz nazwę dla nowego wykresu, a następnie wybierz **OK**.

    3.  (Opcjonalnie) Ponownie kliknij prawym przyciskiem myszy błąd, a następnie wybierz pozycję **Pokaż licznik na wykresie**.

         Aby uzyskać więcej informacji, zobacz [porady: Tworzenie wykresów niestandardowych](../test/how-to-create-custom-graphs-in-load-test-results.md).

5.  (Opcjonalnie) Jeśli analizujesz błąd w zakończonym wyniku testu obciążeniowego, należy rozważyć użycie funkcji powiększenia, znajduje się w wykresy. Aby uzyskać więcej informacji, zobacz [porady: powiększanie obszaru wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

    > [!TIP]
    > Jeśli błędy zostały wykryte podczas przebiegu testu obciążeniowego, łącze pod tytułem wraz z liczbą znalezione błędy będą znajdować się we **analizatora testu obciążenia** pasek stanu. Można wybrać łącze, aby wyświetlić wszystkie błędy w **błędy** tabeli w widoku tabele.

## <a name="see-also"></a>Zobacz także

- [Za pomocą panelu liczników w widokach wykresy i tabele](../test/counters-panel-in-load-test-analyzer.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)