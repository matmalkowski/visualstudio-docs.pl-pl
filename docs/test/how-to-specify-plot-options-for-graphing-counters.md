---
title: "Wykreślenia opcje Tworzenie wykresów liczników dla testów obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, graphing counters
ms.assetid: 1969c20b-e0eb-48f6-a49f-a9090cd86008
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 00860a262573491a358c0f992577f48fc3480d93
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-specify-plot-options-for-graphing-counters"></a>Porady: określanie opcji wykresu dla liczników sporządzających wykresy

**Wykreślenia opcje** okno dialogowe umożliwia zmianę koloru i wiersza styl kreślony licznik na wykresie. Można ustalić zakres na określoną wartość lub ustawić zakresu automatycznie dostosowana, na podstawie próbki danych.

![Okno dialogowe Opcje wykreślenia](../test/media/ltest_plotoptions.png "LTest_PlotOptions")

## <a name="to-specify-plotting-options-for-graphs"></a>Umożliwia określenie opcji kreślenia wykresów

1.  Załadowanie testów analizatora, wybierz **wykresy** na pasku narzędzi testu obciążenia.

     Spowoduje to wyświetlenie wyników testów obciążenia w widoku wykresu.

2.  W legendzie lub wykres, kliknij prawym przyciskiem myszy wiersz lub bieżącego wiersza kreślenia licznika wydajności, dla którego chcesz zmienić opcję kreślenia, a następnie wybierz **wykreślenia opcje**.

     **Wykreślenia opcje** Wyświetla okno dialogowe.

3.  Użyj **kolor** listy rozwijanej i wybierz kolor, którego chcesz użyć do kreślenia licznika wydajności.

4.  Użyj **styl** listy rozwijanej i wybierz styl, który ma być używany do kreślenia licznika wydajności.

5.  Wykonaj jedną z następujących czynności:

     Wybierz **automatycznie Dostosuj zakres** (ustawienie domyślne)

     \- lub -

     Wyczyść **automatycznie Dostosuj zakres** i użyj **zakres** listy rozwijanej, aby określić zakres, który ma być używany do kreślenia licznika wydajności.

6.  Wybierz **OK**.

     Zmienić opcje dla licznika wydajności jest wyświetlane na wykresie ze zmianami, które określiłeś.

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Porady: Tworzenie wykresów niestandardowych](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [Analizowanie wyników testów obciążenia w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md)