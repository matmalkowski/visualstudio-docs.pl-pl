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
ms.openlocfilehash: cb64626034c8c9bf03875385a80ebc417bf05dcb
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204066"
---
# <a name="how-to-analyze-threshold-violations-using-the-counters-panel-in-load-test-analyzer"></a>Porady: analizowanie naruszeń progu za pomocą panelu liczników w analizatorze testu obciążenia

**Liczniki** panel jest widoczny w widokach wykresy i tabele w **analizatora testu obciążenia** gdy uruchomiony jest test obciążeniowy lub podczas analizy wyniku testu obciążeniowego. Zobacz [z wynikami testów obciążeniowych analizy w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md), [analizowanie wyników testów obciążenia oraz błędów w widoku tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) i [instrukcje: dostęp do wyników testów obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md).

 Naruszenia progu są skojarzone z specyficzne liczniki wydajności i wskazywać, że licznik wydajności przekracza lub spadła poniżej wartości progowej zestawu. Ikony w **liczniki** panelu komunikacji naruszenia progu.

 ![Węzeł komputera w panelu liczników](../test/media/ltest_compnode.png)

 Ikona naruszenia progu są propagowane z węzła drzewa, w którym licznik nieudanych znajduje się w folderze głównym. Ikona ostrzega o tym użytkownika, to naruszenie na licznik, który może nie być widoczna w drzewie, ponieważ nie została rozwinięta drzewa. Przykład ikony można zobaczyć w **węzeł komputery** w **liczniki** panelu na poprzedniej ilustracji.

 Ikona będzie jedną z następujących czynności:

 ![Nie naruszenie progu](../test/media/icon_ltest_1.gif) Nie naruszenie progu.

 ![Naruszenie progu krytycznego w ostatnim interwale](../test/media/icon_ltest_2.gif) Naruszenie progu krytycznego podczas ostatniego interwału.

 ![Naruszenie progu krytycznego na wcześniejsze interwału](../test/media/icon_ltest_3.gif) Naruszenie progu krytycznego podczas poprzedniego interwału.

 ![Naruszenie progu ostrzegawczego w ostatnim interwale](../test/media/icon_ltest_4.gif) Naruszenie progu ostrzegawczego podczas ostatniego interwału.

 ![Naruszenie progu ostrzegawczego na wcześniejsze interwału](../test/media/icon_ltest_5.gif) Naruszenie progu ostrzegawczego podczas poprzedniego interwału.

## <a name="to-analyze-threshold-violations-in-the-counters-panel"></a>Aby analizować naruszenie progowe w panelu Liczniki.

1.  Po zakończeniu testu obciążeniowego lub po załadowaniu wynik testu, na pasku narzędzi analizatora testu obciążeniowego, wybrać **wykresów** lub **tabel**.

     **Liczniki** panelu pojawiają się w widoku wykresy lub w widoku tabele.

2.  Jeśli **liczniki** panel nie jest widoczny, wybierz polecenie **Pokaż Panel liczników** na pasku narzędzi.

     Każdy węzeł, który zawiera naruszenie progowe, będzie zawierał jedną z ikon wymienionych powyżej.

3.  Rozwiń węzeł, który zawiera ikonę progu, takie jak **komputerów** węzła, jak pokazano na poprzedniej ilustracji, pod tytułem "Węzeł komputerów w panelu liczników z naruszeniem progowym". W dalszym ciągu rozwijaj węzeł, aż osiągniesz licznik wydajności, z naruszeniem progowym. Na przykład ilustracja pokazuje niedziałające wystąpienie z **Microsoft maszyny wirtualnej nie powiodło się niedziałającej karty sieciowej magistrali**.

4.  (Opcjonalnie) Kliknij prawym przyciskiem myszy licznik wydajności z naruszeniem progowym i wybierz jedną z następujących opcji:

    -   **Pokaż licznik na wykresie**: W widoku wykresu licznika wydajności zostaną dodane i wyróżnione na wybranym wykresie. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

        > [!NOTE]
        > Ikona naruszenia progowego może też być wyświetlana na wykresie, w widoku wykresu. Ikona progu pojawia się na wykresie obok punktu danych, w którym wystąpiło naruszenie progu. Aby to zrobić, wybierz **Pokaż legendę** listy rozwijanej na pasku narzędzi i wybierz **Pokaż naruszenie progowe na wykresie**.

    -   **Pokaż licznik na legendzie**: W legendzie, licznik wydajności zostaną dodane i wybrane. Aby uzyskać więcej informacji, zobacz [analizowanie testów obciążenia przy użyciu legendy wykresu](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

    -   **Dodaj wykres**:

    1.  **Wprowadź nazwę wykresu** zostanie wyświetlone okno dialogowe.

    2.  W **nazwa wykresu** polu tekstowym wpisz nazwę dla nowego wykresu, a następnie wybierz **OK**.

    3.  (Opcjonalnie) Ponownie kliknij prawym przyciskiem myszy licznik wydajności, a następnie wybierz pozycję **Pokaż licznik na wykresie**.

         Aby uzyskać więcej informacji, zobacz [porady: Tworzenie wykresów niestandardowych](../test/how-to-create-custom-graphs-in-load-test-results.md).

5.  (Opcjonalnie) Jeśli analizujesz naruszenie progowe w zakończonym wyniku testu obciążeniowego, należy rozważyć użycie funkcji powiększenia, w widoku wykresu. Aby uzyskać więcej informacji, zobacz [porady: powiększanie obszaru wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

    > [!TIP]
    > Jeśli jakieś naruszenie progowe zostały wykryte podczas przebiegu testu obciążeniowego, łącze pod tytułem "threshold," liczbę naruszeń, w tym będą znajdować się we **analizatora testu obciążenia** pasek stanu. Można wybrać łącze, aby wyświetlić wszystkie naruszenia progowe w **progi** tabeli w widoku tabele.

## <a name="see-also"></a>Zobacz także

- [Za pomocą panelu liczników w widokach wykresy i tabele](../test/counters-panel-in-load-test-analyzer.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)