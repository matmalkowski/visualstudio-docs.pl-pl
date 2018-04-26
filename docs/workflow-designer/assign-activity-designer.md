---
title: Projektant przepływu pracy — Projektant działań przypisania
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44d825d5d6ee36876c807ce067c71c1b10896623
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="assign-activity-designer"></a>Przypisz Projektant działań

**Przypisać** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Assign> działania.

## <a name="the-assign-activity"></a>Przypisz działania

<xref:System.Activities.Statements.Assign> Działania przypisuje wartość do zmiennej lub argumentu.

### <a name="using-the-assign-activity-designer"></a>Przy użyciu narzędzia Projektant działań przypisania

**Przypisać** Projektant działań można znaleźć w **podstawowych** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**kartę (można także wybrać **przybornika** z **widoku** menu lub CTRL + ALT + X.)

**Przypisać** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy w przypadku gdy zabezpieczając działania są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Porzucanie **przypisać** tworzy Projektant działań <xref:System.Activities.Statements.Assign> działania z domyślną **DisplayName** z przypisania. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **przypisać** Projektant działań lub **DisplayName** pola siatki właściwości.

### <a name="the-assign-properties"></a>Przypisz właściwości

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Assign> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości i niektóre z nich można edytowane na powierzchni projektanta przepływów pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.Assign> działania. Wartość domyślna to przypisanie. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagane, jest najlepszym rozwiązaniem jej użyć.|
|<xref:System.Activities.Statements.Assign.To%2A>|True|Zmienna lub argument, do którego <xref:System.Activities.Statements.Assign.Value%2A> jest przypisany. Wartość musi być prawidłowym identyfikatorem języka Visual Basic. Aby ustawić właściwości, wpisz wyrażenie języka Visual Basic w **do** polu na **przypisać** działania projektanta lub w siatce właściwości.|
|<xref:System.Activities.Statements.Assign.Value%2A>|True|Wartość, która jest przypisana do zmiennej. Aby ustawić <xref:System.Activities.Statements.Assign.Value%2A>, wpisz wyrażenie języka Visual Basic w **wartość** polu na **przypisać** działania projektanta lub w siatce właściwości.|

## <a name="see-also"></a>Zobacz także

- [Typy pierwotne](../workflow-designer/primitives-activity-designers.md)
- [Opóźnienie](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)