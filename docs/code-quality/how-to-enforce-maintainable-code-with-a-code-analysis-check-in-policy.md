---
title: 'Porady: wymuszanie kodu za pomocą zasad ewidencjonowania analizy kodu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6269b4839c552fa6a1e982226bbb311cb7d5e9d9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Porady: Wymuszanie kodu za pomocą zasad analizy kodu zaewidencjonowania

Deweloperzy mogą używać narzędzia metryki kodu do mierzenia stopnia złożoności i łatwości konserwacji ich kodu, ale nie można wywołać metryki kodu jako część zasad ewidencjonowania. Można jednak włączyć reguł analizy kodu, które pozwalają sprawdzić zgodność kodu ze standardami metryki kodu i wymuszania reguł za pomocą zasad ewidencjonowania. Aby uzyskać więcej informacji na temat metryki kodu, zobacz [kodu wartości metryk](../code-quality/code-metrics-values.md).

Można włączyć głębokość dziedziczenia, klasa sprzężenia, indeks łatwości utrzymania i złożoności wymuszanie kodu za za pomocą zasad ewidencjonowania analizy kodu. Wszystkie cztery te zasady znajdują się w kategorii "Utrzymanie reguły" w edytorze zasad analizy kodu.

Administratorzy kontroli wersji programu Team Foundation można dodać reguły utrzymanie analizy kodu do wymagań zasad ewidencjonowania. Te zaewidencjonowania zasady wymagają deweloperom przeprowadzanie analizy kodu, w oparciu o zmiany te reguły przed zainicjowaniem ewidencjonowania.

## <a name="to-open-the-code-analysis-policy-editor"></a>Aby otworzyć Edytor zasad analizy kodu

1. W **Team Explorer**, kliknij prawym przyciskiem myszy projektu zespołowego, kliknij przycisk **ustawienia projektu zespołowego**, a następnie kliknij przycisk **kontroli źródła**.

     **Kontroli źródła** zostanie wyświetlone okno dialogowe.

2. Na **zasad ewidencjonowania** , a następnie kliknij pozycję **Dodaj**.

     **Dodaj zasady ewidencjonowania** zostanie wyświetlone okno dialogowe.

3. W **zasad ewidencjonowania** listy, wybierz **analizy kodu** pole wyboru, a następnie kliknij przycisk **OK**.

     **Edytor zasad analizy kodu** zostanie wyświetlone okno dialogowe.

## <a name="to-enable-code-analysis-maintainability-rules"></a>Aby włączyć reguły utrzymanie analizy kodu

1. W **Edytor zasad analizy kodu** okna dialogowego, w obszarze **ustawienia reguły**, rozwiń węzeł **reguły utrzymanie** węzła.

2. Zaznacz pola wyboru dla następujących reguł:

    -   Głębokość dziedziczenia: **CA1501 AvoidExcessiveInheritance** — próg: ostrzeżenie na więcej niż 5 poziomach głębokości

    -   Złożoność: **CA1502 AvoidExcessiveComplexity** — próg: ostrzeżenie w więcej niż 25

    -   Indeks łatwości utrzymania: **CA1505 AvoidUnmaintainableCode** — próg: ostrzeżenie na mniej niż 20

    -   Sprzężenia klas: **CA1506 AvoidExcessiveClassCoupling** — próg: ostrzeżenie w więcej niż 80 dla klasy i ponad 30 metody

    Ponadto naruszenie reguły, aby zapobiec pomyślnego utworzenia kompilacji, wybierz **traktuje ostrzeżenie jako błąd** pole wyboru obok opis reguły.

3. Kliknij przycisk **OK**. Nowe zasady ewidencjonowania dotyczy teraz przyszłych zaewidencjonowania.

## <a name="see-also"></a>Zobacz także

- [Wartości metryk kodów](../code-quality/code-metrics-values.md)
- [Tworzenie i używanie zasad ewidencjonowania analizy kodu](../code-quality/creating-and-using-code-analysis-check-in-policies.md)