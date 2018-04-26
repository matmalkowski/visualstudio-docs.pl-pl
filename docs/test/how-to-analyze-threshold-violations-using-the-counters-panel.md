---
title: Naruszenia progu dla testów obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, threshold violations
ms.assetid: 0126d7b7-0538-4ea9-9046-6556654b3b9d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 483a591e190efa557ffff42c958c18171269e7ea
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-analyze-threshold-violations-using-the-counters-panel-in-load-test-analyzer"></a>Porady: analizowanie naruszeń progu za pomocą panelu liczników w analizatorze testów obciążenia

Panel liczników jest widoczny w widokach Wykresy i Tabele w Analizatorze testu obciążeniowego, gdy uruchomiony jest test obciążeniowy lub podczas analizy wyniku testu obciążeniowego. Zobacz [analizowanie wyników testów obciążenia w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md), [analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) i [porady: dostęp do wyników testu obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md).

 Naruszenia progu są skojarzone z konkretnych licznikach wydajności i wskazywać, że licznik wydajności przekroczony lub spadła poniżej ustaw wartość progu. Ikony w panelu liczników komunikacji naruszenia progu.

 ![Panel liczników komputera węzła](../test/media/ltest_compnode.png "LTest_CompNode")

 Ikona naruszenie progu jest przenoszone z węzła drzewa, w którym licznik nieudanych znajduje się w katalogu głównym. Ikona ostrzega o tym użytkownika, to naruszenie na licznika, który może nie być widoczne w drzewie, ponieważ nie zostały rozszerzone drzewa. Przykład ikony są widoczne w **węzła komputerów** w panelu liczników na poprzedniej ilustracji.

 Ikona będzie jedną z następujących czynności:

 ![Nie naruszenie progu](../test/media/icon_ltest_1.gif "Icon_LTest_1") nie naruszenie progu.

 ![Naruszenie progu krytycznego na ostatniego interwału](../test/media/icon_ltest_2.gif "Icon_LTest_2") naruszenie progu krytycznego podczas ostatniego interwału.

 ![Naruszenie progu krytycznego dla poprzedniego interwału](../test/media/icon_ltest_3.gif "Icon_LTest_3") naruszenie progu krytycznego podczas poprzedniego interwału.

 ![Naruszenie progu ostrzegawczego w ostatnim interwale](../test/media/icon_ltest_4.gif "Icon_LTest_4") naruszenie progu ostrzegawczego podczas ostatniego interwału.

 ![Naruszenie progu ostrzegawczego dla poprzedniego interwału](../test/media/icon_ltest_5.gif "Icon_LTest_5") naruszenie progu ostrzegawczego podczas poprzedniego interwału.

## <a name="to-analyze-threshold-violations-in-the-counters-panel"></a>Aby analizować naruszenie progowe w panelu Liczniki.

1.  Po zakończeniu testu obciążenia, lub po załadowaniu wyniku testu obciążenia Test analizatora w pasku narzędzi, wybrać **wykresy** lub **tabel**.

     Panel Liczniki zostanie wyświetlony w widoku Wykresy lub w widoku Tabele.

2.  Panel liczników nie jest widoczny, jeśli **Pokaż panelu liczników** na pasku narzędzi.

     Każdy węzeł, który zawiera naruszenie progowe, będzie zawierał jedną z ikon wymienionych powyżej.

3.  Rozwiń węzeł, który zawiera ikonę próg, takie jak **komputery** węzła, jak pokazano na poprzedniej ilustracji zatytułowany "Węzeł komputerów w panelu liczników o naruszenie progu." W dalszym ciągu rozwijaj węzeł, aż osiągniesz licznik wydajności, z naruszeniem progowym. Na przykład na ilustracji przedstawiono nie powiodło się wystąpienia **karty sieciowej magistrali nie powiodło się maszyny wirtualnej Microsoft**.

4.  (Opcjonalnie) Kliknij prawym przyciskiem myszy licznik wydajności z naruszeniem progowym i wybierz jedną z następujących opcji:

    -   **Pokaż licznik na wykresie**: W widoku wykresu zostanie dodany i wyróżnione na wykresie wybranego licznika wydajności. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

        > [!NOTE]
        > Ikona naruszenia progowego może też być wyświetlana na wykresie, w widoku wykresu. Ikona próg pojawia się na wykresie obok punkt danych, w którym wystąpiło naruszenie progu. Aby to zrobić, wybierz **Pokaż legendę** listy rozwijanej na pasku narzędzi i wybierz **Pokaż naruszenia progowe na wykresie**.

    -   **Pokaż licznik w legendzie**: W legendzie, licznik wydajności zostanie dodany i wybrane. Aby uzyskać więcej informacji, zobacz [przy użyciu legendy wykresu do analizowania testów obciążenia](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

    -   **Dodaj wykres**:

    1.  **Wprowadź nazwę wykresu** zostanie wyświetlone okno dialogowe.

    2.  W **nazwa wykresu** polu tekstowym, wpisz nazwę nowego wykresu, a następnie wybierz pozycję **OK**.

    3.  (Opcjonalnie) Ponownie kliknij prawym przyciskiem myszy licznik wydajności i wybierz **Pokaż licznik na wykresie**.

         Aby uzyskać więcej informacji, zobacz [porady: Tworzenie wykresów niestandardowych](../test/how-to-create-custom-graphs-in-load-test-results.md).

5.  (Opcjonalnie) Jeśli analizujesz naruszenie progowe w zakończonym wyniku testu obciążeniowego, należy rozważyć użycie funkcji powiększenia, w widoku wykresu. Aby uzyskać więcej informacji, zobacz [porady: powiększanie obszaru wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

    > [!TIP]
    > Jeśli zostały wykryte jakieś naruszenie progowe podczas przebiegu testu obciążeniowego, pojawi się łącze pod tytułem „threshold violations”, i będzie zawierało liczbę naruszeń, na pasku stanu analizatora testu obciążeniowego. Można wybrać łącze, aby wyświetlić wszystkie naruszenia progu w **progi** tabeli widoku tabeli.

## <a name="see-also"></a>Zobacz także

- [Za pomocą panelu liczników w widoku wykresów i tabel](../test/counters-panel-in-load-test-analyzer.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)