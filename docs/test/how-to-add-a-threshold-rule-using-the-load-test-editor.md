---
title: Dodawanie reguły progu obciążenia testowania w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, monitoring
- load tests, thresholds
- load tests, analyzing
- thresholds in load tests
ms.assetid: 3d8fac8f-426f-4155-9ced-f7cd4c79792c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: ede6e8d3dde3b8a6f76164b02457a98102bcbac7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>Porady: Dodawanie reguły progu za pomocą edytora testu obciążenia

Reguły progu w testach obciążenia porównaj wartość licznika wydajności z wartością stałą lub inną wartość licznika wydajności.

## <a name="to-add-a-threshold-rule"></a>Aby dodać reguły progu

1.  Otwórz testu obciążenia.

2.  W edytorze testu obciążenia, rozwiń węzeł **zbiorów liczników** węzła.

3.  Rozwiń jedno ze **kategorii licznika** w jednym z zestawów liczników. Na przykład można wybrać **LoadTest:Scenario**. Rozwiń węzeł.

4.  Kliknij prawym przyciskiem myszy jeden z liczników, na przykład **obciążenie użytkownikami**w obszarze **LoadTest:Scenario**. Wybierz **Dodawanie reguły progu**.

     **Dodawanie reguły progu** zostanie wyświetlone okno dialogowe.

5.  Są dostępne dwa typy zasad: porównanie stałej i licznik porównania. Wybierz odpowiedni typ i ustaw wartości.

    > [!NOTE]
    > Ustaw **alertu Jeśli za pośrednictwem** właściwości **True** do wskazywania powyżej wartości progowej problem, lub do **False** do wskazywania poniżej wartości progowej problem.

## <a name="see-also"></a>Zobacz także

- [Analizowanie naruszeń zasady progu](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)