---
title: Opcje kreślenia Tworzenie wykresów liczników dla testów obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, graphing counters
ms.assetid: 1969c20b-e0eb-48f6-a49f-a9090cd86008
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 7a5f87a83b8c743ae869a700618051e07c8c2e75
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750925"
---
# <a name="how-to-specify-plot-options-for-graphing-counters"></a>Porady: określanie opcji wykresu dla liczników sporządzających wykresy

**Wykreślenia opcje** okno dialogowe umożliwia zmianę koloru i wiersza styl kreślony licznik na wykresie. Można ustalić zakres na określoną wartość lub ustawić zakresu automatycznie dostosowana, na podstawie próbki danych.

![Okno dialogowe Opcje kreślenia](../test/media/ltest_plotoptions.png)

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