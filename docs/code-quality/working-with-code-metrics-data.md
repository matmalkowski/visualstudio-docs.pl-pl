---
title: Wyniki metryk w programie Visual Studio Code | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 198e4b6d0ba2f3517cf907007cc544ca2e154013
ms.sourcegitcommit: f36eb7f989efbdbed0d0a087afea8ffe27d8ca15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="working-with-code-metrics-data"></a>Praca z metrykami kodów

**Wyników metryk kodów** okno wyświetla dane, które jest generowany przez analizę metryki kodu. Aby uzyskać więcej informacji na temat wartości danych metryki kodu, zobacz [wartości metryk kodów](../code-quality/code-metrics-values.md).

## <a name="displaying-code-metrics-results"></a>Wyświetlanie wyników metryk kodów

**Wyników metryk kodów** okno jest wyświetlane automatycznie, gdy Generowanie wyników metryk kodów. W dowolnym momencie można również wyświetlić okno.

### <a name="to-display-the-code-metrics-results-window"></a>Aby wyświetlić okno wyników metryk kodów

- Na **Analizuj** menu, wybierz **Windows** > **wyników metryk kodów**.

   \-lub -

- Na **widoku** menu, wybierz **inne okna** > **wyników metryk kodów**.

   **Wyników metryk kodów** okno jest wyświetlane, nawet jeśli go nie zawiera wyników.

### <a name="to-view-code-metrics-details"></a>Aby wyświetlić szczegóły metryk kodu

Jeśli wyniki metryk kodów zostały wygenerowane, rozwiń drzewo w **hierarchii** kolumny.

## <a name="filtering-code-metrics-results"></a>Filtrowanie wyników metryk kodów

Możesz filtrować wyniki, które są wyświetlane w **wyników metryk kodów** okna przy użyciu na pasku narzędzi u góry. Na przykład można wyświetlić tylko wyniki, które mają indeks łatwości utrzymania poniżej 65.

**Filtru** pola rozwijanego zawiera nazwy kolumny wyniki. Jeśli filtr jest zdefiniowana, jest ona dodawana do dolnej części listy wraz z wcięcia. Lista może zawierać dziesięć ostatnich filtry, które zostały zdefiniowane.

### <a name="to-filter-the-code-metrics-results"></a>Aby filtrować wyniki metryk kodów

1.  Z **filtru** listy, wybierz nazwę kolumny.

2.  W **Min**, wpisz wartość minimalna, który będzie wyświetlany.

3.  W **Max**, wpisz wartość maksymalna, który będzie wyświetlany.

4.  Kliknij przycisk **Zastosuj filtr** przycisku.

5.  Aby wyświetlić szczegóły wyniku, rozwiń węzeł drzewa hierarchii.

## <a name="adding-removing-and-rearranging-data-columns"></a>Dodawanie, usuwanie i zmienianie rozmieszczenia kolumn danych

Można dodać lub usunąć wyniki kolumny z **wyników metryk kodów** okna. Ponadto możesz zmienić kolejność kolumn wyników, aby były wyświetlane w kolejności, która ma.

### <a name="to-remove-a-column"></a>Aby usunąć kolumnę

1. Kliknij przycisk **Dodaj/Usuń kolumny** przycisku.

     \-- lub kliknij prawym przyciskiem myszy nagłówek dowolnej kolumny, a następnie kliknij przycisk **Dodaj/Usuń kolumny**.

1. W **Dodaj/Usuń kolumny** okno dialogowe, wyczyść pole wyboru dla kolumny, które chcesz usunąć, a następnie kliknij przycisk **OK**.

### <a name="to-add-a-previously-removed-column"></a>Aby dodać kolumnę wcześniej usuniętych

1. Kliknij przycisk **Dodaj/Usuń kolumny** przycisku.

     \-lub -

     Kliknij prawym przyciskiem myszy nagłówek dowolnej kolumny, a następnie kliknij przycisk **Dodaj/Usuń kolumny**.

1. W **Dodaj/Usuń kolumny** oknie dialogowym zaznacz pole wyboru dla kolumny, które chcesz dodać, a następnie kliknij przycisk **OK**.

### <a name="to-rearrange-columns"></a>Aby zmienić kolejność kolumn

1. Kliknij przycisk **Dodaj/Usuń kolumny** przycisku.

     \-lub -

     Kliknij prawym przyciskiem myszy nagłówek dowolnej kolumny, a następnie kliknij przycisk **Dodaj/Usuń kolumny**.

1. W **Dodaj/Usuń kolumny** oknie dialogowym Wybierz kolumnę, którą chcesz przenieść, a następnie kliknij przycisk strzałki w górę i Strzałka w dół.

1. Jeśli kolumna zostanie umieszczona w miejscu, kliknij przycisk **OK**.

## <a name="copying-data-to-the-clipboard-or-excel"></a>Kopiowanie danych do Schowka lub programu Excel

Można wybrać i skopiować wybranego wiersza danych metryki kodu do Schowka jako ciąg tekstowy zawierający jedną linię nazwy i wartości wszystkich kolumn danych. Możesz również kliknąć **Otwórz zaznaczenie w programie Microsoft Excel** Aby wyeksportować wszystkie wyniki metryki kodu do arkusz kalkulacyjny programu Excel.

## <a name="creating-a-work-item-based-on-code-metric-results"></a>Tworzenie elementu roboczego w oparciu o wyniki metryki kodu

Można utworzyć [programu Visual Studio Team Services (VSTS)](/vsts/index) powoduje elementu roboczego, który jest oparty na **wyniki metryki kodu** okna. Po utworzeniu elementu roboczego programu Visual Studio automatycznie wprowadzi tytuł w **tytuł** dane metryk pola i kodu w ramach **historii** kartę.

Aby uzyskać więcej informacji na temat programu VSTS elementów roboczych, zobacz [elementy robocze](/vsts/work/work-items/index).

### <a name="to-create-a-work-item-based-on-a-result"></a>Aby utworzyć element roboczy na podstawie wyniku

1.  Kliknij prawym przyciskiem myszy wynik.

2.  Wskaż **Utwórz element roboczy**, a następnie kliknij typ elementu roboczego, w którym chcesz utworzyć (**usterki**, **zadań**, itd).

3.  Ukończ formularza elementu roboczego wypełnić wszystkie wymagane pola.

4.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko** można zapisać elementu roboczego.

### <a name="to-create-a-bug-based-on-a-result"></a>Można utworzyć na podstawie wyniku usterki

1.  Kliknij przycisk wyników, aby go wybrać.

2.  Kliknij przycisk **Tworzenie elementu roboczego** przycisku.

3.  Ukończ formularza elementu roboczego wypełnić wszystkie wymagane pola.

4.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko** można zapisać elementu roboczego.

## <a name="see-also"></a>Zobacz także

[Wartości metryk kodów](../code-quality/code-metrics-values.md)  
[Instrukcje: Generowanie danych metryk kodu](../code-quality/how-to-generate-code-metrics-data.md)