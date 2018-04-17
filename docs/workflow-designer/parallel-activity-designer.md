---
title: Projektant działań równoległych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1c3f24af736dfd3762de7942ba1f52442dfd20c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="parallel-activity-designer"></a>Projektant działań równoległych
<xref:System.Activities.Statements.Parallel> Działania jest wykonywany współbieżnie zbiór działań podrzędnych.

## <a name="the-parallel-activity"></a>Działanie równoległe
 <xref:System.Activities.Statements.Parallel> Działania przechowuje działania podrzędne w <xref:System.Activities.Statements.Parallel.Branches%2A> kolekcji. Użyj <xref:System.Activities.Statements.Parallel> działania zamiast <xref:System.Activities.Statements.Sequence> działanie w przypadku niektórych działań podrzędnych może bezczynności.

 <xref:System.Activities.Statements.Parallel> Działanie ma <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> właściwość, która zawiera określonego przez użytkownika [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] wyrażenia. <xref:System.Activities.Statements.Parallel> Działanie ocenia tej właściwości po zakończeniu każdej gałęzi. Jeśli daje w wyniku **True**, a następnie <xref:System.Activities.Statements.Parallel> kończy działanie bez wykonywania innych działów. Jeśli <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> nie zwraca **True**, a następnie <xref:System.Activities.Statements.Parallel> zakończeniu działania, gdy wszystkie działania podrzędne zostaną zakończone.

### <a name="using-the-parallel-activity-designer"></a>Przy użyciu narzędzia Projektant działania równoległego
 **Równoległych** Projektant działań można znaleźć w **przepływ sterowania** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karcie po lewej stronie [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)

 **Równoległych** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni wszędzie tam, gdzie projektantów działań są zazwyczaj umieszczone, na przykład wewnątrz **Sekwencji** Projektant działań. Po usunięcie go do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], tworzy <xref:System.Activities.Statements.Parallel> działania, która domyślnie zawiera <xref:System.Activities.Activity.DisplayName%2A> z **równoległych**

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