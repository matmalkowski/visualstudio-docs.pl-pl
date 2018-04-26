---
title: 'Projektant przepływu pracy — porady: Użyj nadrzędnych'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 92f3e35d4182297601741bd603aa3c5a17e54d67
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-use-breadcrumb-navigation"></a>Porady: Użyj nadrzędnych

Istnieją trzy sposoby zmianę zestawu działań, które są wyświetlane w Projektancie przepływów pracy systemu Windows:

1.  Kliknij dwukrotnie, aby przejść do szczegółów celu działania podrzędnego.

2.  Kliknij przycisk paska stron nadrzędnych można przejść do działanie nadrzędne.

3.  Rozwiń lub Zwiń działań w miejscu.

## <a name="using-breadcrumb-navigation"></a>Za pomocą stron nadrzędnych

1.  Kliknij dwukrotnie działanie projektanta przepływów pracy, aby zmienić działanie główne klikniętej działania. Działanie klikniętej jest następnie pełni rozwinięty w katalogu głównym i jego obiektów nadrzędnych są wyświetlane na pasku stron nadrzędnych. Jest to czasem nazywane przechodzenia na wyższy poziom do lub z działania.

2.  Aby przejść do elementu nadrzędnego bieżącego działania głównego, kliknij działanie na pasku stron nadrzędnych.

## <a name="expanding-or-collapsing-an-activity-in-place"></a>Rozwijanie lub zwijanie działania w miejscu

1.  Kliknij cudzysłów ostrokątny w działaniu rozwija lub zwija działania w miejscu.

2.  Po zmianie stanu rozszerzenia stanu po kliknięciu przycisku Nowy stan rozszerzenia jest zapisany w języku XAML.

    > [!WARNING]
    > Nie wszystkie działania można rozszerzać w miejscu. Istnieją dwa przypadki, gdy działanie nie może być rozwinięty w miejscu: albo element nadrzędny działania nie zezwala na jego elementów podrzędnych do wyodrębnienia w miejscu, (na przykład działania w elemencie Schemat blokowy nie może być rozwinięty w miejscu), lub nie zezwala na siebie Projektant działań można rozwinąć w miejscu. Mimo że żaden z projektantami działań uwzględnione w Projektancie przepływów pracy nie ma ostatnie zachowanie, niektóre działania niestandardowe mogą działać to zachowanie.

## <a name="expanding-all-or-collapsing-all-activities"></a>Wszystkie rozwijanie lub zwijanie wszystkich działań

1.  Użyj **Rozwiń wszystkie** i **Zwiń wszystkie** przycisków w interfejsie użytkownika, aby rozwinąć lub zwinąć wszystkie działania w katalogu głównym bieżącej stron nadrzędnych. Należy pamiętać, że wszystkie rozwijanie i zwijanie, wszystkie są globalne stanów. Oznacza to, że podczas działania głównego przy użyciu nadrzędnych, rozwiń wszystkie zmiany lub Zwiń wszystkie stan będzie się powtarzał dopiero po kliknięciu przycisku **przywrócić**.

2.  Po zostały zastosowane wszystkie rozwiń lub Zwiń wszystkie stanu, możesz kliknąć **przywrócić** przycisku, który pojawia się, aby powrócić do przeglądania stanu wcześniej zastosowane do każdego działania.

    > [!WARNING]
    > Jeśli działanie, takich jak <xref:System.Activities.Statements.Flowchart>, zrezygnowała z rozwiń w miejscu, funkcje związane z **Rozwiń wszystko** i **Zwiń wszystkie** przycisków jest wyłączona na **schematu blokowego**  projektanta. Aby uzyskać więcej informacji na temat **schemat blokowy** projektanta, zobacz [schemat blokowy](../workflow-designer/flowchart-activity-designer.md) tematu.

    > [!WARNING]
    > Rozwiń wszystko również ma wpływ specjalne **przełącznika** i **TryCatch** projektantów działań. Po kliknięciu **Rozwiń wszystkie**, są wyświetlane wszystkie przypadki przełącznika i wszystkie bloki try/catch/finally. Kliknięcie przycisku **przywrócić** lub **Zwiń wszystkie** zwraca te projektantów ich stan domyślny, w którym można kliknąć poszczególne przypadku/zablokowanych, aby wyświetlić jego zawartość.