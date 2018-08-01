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
ms.openlocfilehash: 5df33a8cf05e4ad73b1643e2948392e49a32356e
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39382324"
---
# <a name="how-to-specify-plot-options-for-graphing-counters"></a>Porady: Określ opcje dla liczników sporządzających wykresy wykresu

**Opcje wykresu** okno dialogowe umożliwia zmianę stylu linii wykreślona licznik na wykresie. Możesz również ustalić zakres na określonej wartości lub zakresu, które mają zostać automatycznie skorygowane, na podstawie próbki danych.

![Okno dialogowe Opcje wykresu](../test/media/ltest_plotoptions.png)

## <a name="to-specify-plotting-options-for-graphs"></a>Aby określić opcje wykreślania dla wykresów

1.  W **analizatora testu obciążenia**, wybierz **wykresów** na pasku narzędzi.

     Spowoduje to wyświetlenie wyników testów obciążenia w widoku wykresu.

2.  W legendzie, lub na wykresie, kliknij prawym przyciskiem myszy wiersza lub bieżący wiersz wykreślania licznika wydajności, dla którego chcesz zmienić opcję wykreślania, a następnie wybierz pozycję **Opcje wykresu**.

     **Opcje wykresu** Wyświetla okno dialogowe.

3.  Użyj **kolor** listy rozwijanej i wybierz kolor, którego chcesz użyć do kreślenia licznika wydajności.

4.  Użyj **styl** listy rozwijanej i wybierz styl, który chcesz użyć do kreślenia licznika wydajności.

5.  Wykonaj jedną z następujących czynności:

     Wybierz **automatycznie Dopasuj zakres** (ustawienie domyślne)

     \- lub —

     Wyczyść **automatycznie Dopasuj zakres** i użyj **zakres** listy rozwijanej, aby określić zakres, który chcesz użyć do kreślenia licznika wydajności.

6.  Wybierz **OK**.

     Zmienić opcje dla licznika wydajności jest wyświetlany na wykresie ze zmianami, które określiłeś.

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Porady: Tworzenie wykresów niestandardowych](../test/how-to-create-custom-graphs-in-load-test-results.md)
