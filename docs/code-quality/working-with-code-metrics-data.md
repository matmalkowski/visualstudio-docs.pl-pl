---
title: Okno wyników metryk kodów w programie Visual Studio
ms.date: 12/12/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40e265e5bdc453ec658de16f288e9c184979975f
ms.sourcegitcommit: 28909340cd0a0d7cb5e1fd29cbd37e726d832631
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44321258"
---
# <a name="using-the-code-metrics-results-window"></a>W oknie wyników metryk kodów

**Wyników metryk kodów** okna wyświetla dane, który jest generowany podczas analizy metryki kodu. Aby uzyskać więcej informacji na temat wartości danych metryk kodu zobacz [kodu wartości metryk](../code-quality/code-metrics-values.md).

## <a name="displaying-code-metrics-results"></a>Wyświetlanie wyników metryk kodów

**Wyników metryk kodów** okno jest wyświetlane automatycznie, gdy Generowanie wyników metryk kodów. Możesz również wyświetlić okna, w dowolnym momencie.

### <a name="to-display-the-code-metrics-results-window"></a>Aby wyświetlić okno wyników metryk kodów

- Na **analizy** menu, wybierz **Windows** > **wyników metryk kodów**.

   \- lub —

- Na **widoku** menu, wybierz **Windows inne** > **wyników metryk kodów**.

**Wyników metryk kodów** okno jest wyświetlane, nawet wtedy, gdy zawiera on żadnych wyników.

### <a name="to-view-code-metrics-details"></a>Aby wyświetlić szczegóły metryk kodu

Jeśli zostały wygenerowane wyników metryk kodów, rozwiń drzewo w **hierarchii** kolumny.

## <a name="filtering-code-metrics-results"></a>Filtrowanie wyników metryk kodów

Można filtrować wyniki, które są wyświetlane w **wyników metryk kodów** okna za pomocą paska narzędzi u góry. Na przykład możesz chcieć wyświetlić tylko wyniki, które mają indeks łatwości utrzymania poniżej 65.

**Filtru** pole listy rozwijanej zawiera nazwy kolumn, wyniki. Po zdefiniowaniu filtru jest dodawany do dolnej części listy wraz z wcięciem. Lista może zawierać dziesięć ostatnich filtrów, które zostały zdefiniowane.

### <a name="to-filter-the-code-metrics-results"></a>Do filtrowania wyników metryk kodów

1.  Z **filtru** , wybierz nazwę kolumny na liście.

2.  W **Min**, wpisz wartość minimalna, który będzie wyświetlany.

3.  W **Max**, wpisz wartość maksymalna ma być wyświetlany.

4.  Kliknij przycisk **Zastosuj filtr** przycisku.

5.  Aby wyświetlić szczegóły wyniku, rozwiń drzewo hierarchii.

## <a name="adding-removing-and-rearranging-data-columns"></a>Dodawanie, usuwanie i zmienianie rozmieszczenia kolumn danych

Można dodać lub usunąć wyniki kolumny z **wyników metryk kodów** okna. Ponadto, aby były wyświetlane w kolejności, w którym chcesz można zmienić kolejność kolumn wyników.

### <a name="to-remove-a-column"></a>Aby usunąć kolumnę

1. Kliknij przycisk **Dodaj/Usuń kolumny** przycisku.

     \- - lub kliknij prawym przyciskiem myszy nagłówek dowolnej kolumny, a następnie kliknij przycisk **Dodaj/Usuń kolumny**.

1. W **Dodaj/Usuń kolumny** okno dialogowe, wyczyść pole wyboru dla kolumny, które chcesz usunąć, a następnie kliknij przycisk **OK**.

### <a name="to-add-a-previously-removed-column"></a>Aby dodać kolumnę wcześniej usuniętych

1. Kliknij przycisk **Dodaj/Usuń kolumny** przycisku.

     \- lub —

     Kliknij prawym przyciskiem myszy nagłówek dowolnej kolumny, a następnie kliknij przycisk **Dodaj/Usuń kolumny**.

1. W **Dodaj/Usuń kolumny** okna dialogowego pole, zaznacz pole wyboru dla kolumny, które chcesz dodać, a następnie kliknij przycisk **OK**.

### <a name="to-rearrange-columns"></a>Aby zmienić kolejność kolumn

1. Kliknij przycisk **Dodaj/Usuń kolumny** przycisku.

     \- lub —

     Kliknij prawym przyciskiem myszy nagłówek dowolnej kolumny, a następnie kliknij przycisk **Dodaj/Usuń kolumny**.

1. W **Dodaj/Usuń kolumny** okna dialogowego Wybierz kolumnę, którą chcesz przenieść, a następnie kliknij przycisk strzałki w górę lub strzałkę w dół.

1. Jeśli kolumna zostanie umieszczona w miejscu, kliknij przycisk **OK**.

## <a name="copying-data-to-the-clipboard-or-excel"></a>Kopiowanie danych do Schowka lub programu Excel

Można wybrać i skopiować wybrany wiersz danych metryki kodu do Schowka jako ciąg tekstowy, który zawiera jeden wiersz dla nazwy i wartości wszystkich kolumn danych. Możesz również kliknąć **Otwórz zaznaczenie w programie Microsoft Excel** Aby wyeksportować wszystkie wyniki metryki kodu do arkusza kalkulacyjnego programu Excel.

## <a name="creating-a-work-item-based-on-code-metric-results"></a>Tworzenie elementu roboczego, w oparciu o wyniki metryk kodu

Możesz utworzyć [tablice Azure](/azure/devops/boards/index?view=vsts) skutkuje elementu roboczego, który jest oparty na **wyniki metryki kodu** okna. Po utworzeniu elementu roboczego programu Visual Studio automatycznie wprowadzi tytuł w **tytuł** dane metryk pola i kodu pod **historii** kartę.

Aby uzyskać więcej informacji na temat tablic Azure elementów roboczych, zobacz [elementów roboczych](/azure/devops/boards/work-items/index?view=vsts).

### <a name="to-create-a-work-item-based-on-a-result"></a>Aby utworzyć element roboczy na podstawie wyniku

1.  Kliknij prawym przyciskiem myszy wynik.

2.  Wskaż **Utwórz element pracy**, a następnie kliknij typ elementu roboczego, w której chcesz utworzyć (**usterki**, **zadań**, i tak dalej).

3.  Wykonaj formularz elementu roboczego, wypełniając we wszystkich wymaganych polach.

4.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko** można zapisać elementu roboczego.

### <a name="to-create-a-bug-based-on-a-result"></a>Aby utworzyć usterkę, na podstawie wyniku

1.  Kliknij wynik, aby go zaznaczyć.

2.  Kliknij przycisk **Utwórz element roboczy** przycisku.

3.  Wykonaj formularz elementu roboczego, wypełniając we wszystkich wymaganych polach.

4.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko** można zapisać elementu roboczego.

## <a name="see-also"></a>Zobacz także

- [Wartości metryk kodów](../code-quality/code-metrics-values.md)
- [Porady: generowanie danych metryk kodu](../code-quality/how-to-generate-code-metrics-data.md)