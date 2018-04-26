---
title: Projektant przepływu pracy — Projektant działań równoległych
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c2315c27bc0a35ac1dc839b5fd98003105d92bd4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="parallel-activity-designer"></a>Projektant działań równoległych

<xref:System.Activities.Statements.Parallel> Działania jest wykonywany współbieżnie zbiór działań podrzędnych.

## <a name="the-parallel-activity"></a>Działanie równoległe

<xref:System.Activities.Statements.Parallel> Działania przechowuje działania podrzędne w <xref:System.Activities.Statements.Parallel.Branches%2A> kolekcji. Użyj <xref:System.Activities.Statements.Parallel> działania zamiast <xref:System.Activities.Statements.Sequence> działanie w przypadku niektórych działań podrzędnych może bezczynności.

<xref:System.Activities.Statements.Parallel> Działanie ma <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> właściwość, która zawiera użytkownika określone wyrażenie języka Visual Basic. <xref:System.Activities.Statements.Parallel> Działanie ocenia tej właściwości po zakończeniu każdej gałęzi. Jeśli daje w wyniku **True**, a następnie <xref:System.Activities.Statements.Parallel> kończy działanie bez wykonywania innych działów. Jeśli <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> nie zwraca **True**, a następnie <xref:System.Activities.Statements.Parallel> zakończeniu działania, gdy wszystkie działania podrzędne zostaną zakończone.

### <a name="using-the-parallel-activity-designer"></a>Przy użyciu narzędzia Projektant działania równoległego

**Równoległych** Projektant działań można znaleźć w **przepływ sterowania** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karcie po lewej stronie projektanta przepływów pracy (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)

**Równoległych** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie na przykład projektantów działań zazwyczaj są umieszczone wewnątrz **Sekwencji** Projektant działań. Po usunięcie go w Projektancie przepływów pracy, tworzy <xref:System.Activities.Statements.Parallel> działania, która domyślnie zawiera <xref:System.Activities.Activity.DisplayName%2A> z **równoległych**

Aby dodać działanie <xref:System.Activities.Statements.Parallel.Branches%2A> kolekcji działania równoległego, przeciągnij niektórych Projektant działań z **przybornika** i upuść ją na trójkąt wewnątrz **równoległych** Projektant działań. Trójkąty części bocznej działań zawartych w gałęzi. Powtarzając tej procedury można dodać dodatkowe działania. Działania można można zmienić kolejności przez przeciąganie i upuszczanie je w ramach **równoległych** Projektant działań.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Właściwości działania równoległe w Projektancie przepływów pracy

Poniższa tabela zawiera właściwości działania równoległe i opisuje, jak są używane w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę wyświetlaną projektanta działania w nagłówku. Wartość domyślna to **równoległych**. Wartość może być opcjonalnie edytowany w **właściwości** siatki lub bezpośrednio w nagłówku projektanta działania.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Zawiera kolekcję działań podrzędnych do wykonania.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Oceniane po zakończeniu gałęzi. Jeśli daje w wyniku **True**, następnie zaplanowanego czasu gałęzie zostały anulowane. Jeśli ta właściwość nie jest ustawiona lub daje w wyniku **False**, gdy wszystkie działania podrzędne zostaną zakończone ukończeniu działania. Wartość domyślna to **null**.|

## <a name="see-also"></a>Zobacz także

- [Sekwencja](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)