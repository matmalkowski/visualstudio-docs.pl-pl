---
title: Korzystanie z legendy wykresu do analizowania testów obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Analyzer, graphs view legend
- load tests, graphs view legend
ms.assetid: 0f6ba8e4-1343-419c-8a9f-240cf50efed7
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 065e50b123ccf4ac96ba6bec89db74bb51990f58
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751404"
---
# <a name="using-the-graphs-view-legend-to-analyze-load-tests"></a>Korzystanie z legendy wykresu podczas przeprowadzania analizy testów obciążenia

Widok wykresów analizatora testu obciążenia, zawierają panel legendy, który wyświetla informacje dla każdego licznika wydajności, który jest skojarzony z aktualnie zaznaczonym wykresem.

![Widok wykresów — Legenda](../test/media/load_viewlegend.png)

Następujące informacje są zawarte wewnątrz legendy:

-   **Pokaż na wykresie:** Użyj pól wyboru, aby określić, czy wiersz dla określonego licznika, takich jak **obciążenie użytkownikami** lub **błędy na sekundę**, są kreślone na wykresie. Zaznacz pole wyboru, jeśli chcesz wiersza do wykreślenia na wykresie. Wyczyść pole wyboru, aby usunąć linię kreślenia z wykresu. Jeśli linia podziału zostanie usunięta, statystyki licznika będą nadal wyświetlane w legendzie.

-   **Zakres:** tej kolumnie są wyświetlane zakresu osi y licznika wydajności. Domyślnie ta wartość zostanie automatycznie Dostosuj jako zakres zmian danych przykładowych. Automatycznie skorygowany zakres, zawsze będzie następną potęgą liczby 10, większą niż maksymalna wartość. Obejmuje to negatywne potęgi dziesięciu. Wykres może zawierać wiele liczników, każdy z innym zakresem. Z tego powodu, oś y nie jest oznaczona żadnym określonym zakresem, ale zamiast tego, jest oznaczona wartościami z zakresu 0-100, które reprezentują procent całkowitego zakresu, dla każdego licznika. Na przykład dla licznika o zakresie 1000 punkt danych 60 na osi y będzie odpowiadać wartości 600 dla tego licznika.

    > [!NOTE]
    > Można wyłączyć korekty wartości zakresu automatyczne blokowanie zakresu na określoną wartość. Gdy zakres jest zablokowany, wszystkie wartości przekraczające zakres, są wyświetlane jako maksymalna wartość, określona w górnej części wykresu. Użyj **wykreślenia opcje** okno dialogowe, aby zablokować z zakresu od określonej wartości. Aby uzyskać więcej informacji, zobacz [porady: Określanie opcji wykreślenia Tworzenie wykresów liczników](../test/how-to-specify-plot-options-for-graphing-counters.md).

-   **Licznik:** cztery kolumny o nazwie **licznika**, **wystąpienia**, **kategorii**, i **komputera** razem jednoznacznie Zidentyfikuj licznika wydajności.

-   **Kolor:** **kolor** kolumna zawiera styl linii kreślony wiersza licznika wydajności. Użyj **wykreślenia opcje** okno dialogowe, aby zmienić kolor lub wiersza styl licznika wydajności na wykresie. **Wykreślenia opcje** okno dialogowe jest dostępne w menu skrótów legendy. Aby uzyskać więcej informacji, zobacz [porady: Określanie opcji wykreślenia Tworzenie wykresów liczników](../test/how-to-specify-plot-options-for-graphing-counters.md).

-   **Statystyki:** **Min**, **Max**, **Avg** i **ostatniego** kolumny zawierają odpowiednich statystyki dotyczące wydajności Licznik. Te wartości odpowiadają dane, które są wyświetlane na widoczne obszaru wykresu. Na przykład jeśli powiększysz region przebiegu, statystyki legendy będą odzwierciedlać wartości, tylko dla powiększonego obszaru. Kolumna "Ostatni" jest wartość licznika wydajności na ostatnio wykonanych interwału próbkowania.

    > [!NOTE]
    > Ostatnia kolumna wyświetla się tylko w legendzie analizatora testu obciążeniowego podczas uruchomienia testu obciążeniowego.

     Aby uzyskać więcej informacji, zobacz [porady: powiększanie obszaru wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

Zaznaczenie elementu w legendzie, wykonuje następujące czynności:

-   Umożliwia elementu do usunięcia z wykresu i legenda. Albo kliknij element prawym przyciskiem myszy i wybierz **usunąć**, lub naciśnij klawisz **usunąć** klucza.

-   Prezentuje kreślony wiersza na wykresie.

-   Powoduje, że siatka danych wyświetlić dane dla wybranego elementu.

-   Zapewnia dostęp do **wykreślenia opcje** okno dialogowe licznika.

> [!TIP]
> Można użyć **rozwijanej Opcje wykresu** przycisku w pasku narzędzi i wybierz analizatora testu obciążenia **Pokaż legendę** do wyświetlenia lub ukrycia **legendy** panelu, z którym skojarzony jest Widok wykresu.

## <a name="see-also"></a>Zobacz także

- [Porady: Określanie opcji wykresu dla liczników sporządzających wykresy](../test/how-to-specify-plot-options-for-graphing-counters.md)
- [Porady: powiększanie obszaru wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
- [Analizowanie wyników testów obciążenia w widoku wykresu](../test/analyze-load-test-results-in-the-graphs-view.md)