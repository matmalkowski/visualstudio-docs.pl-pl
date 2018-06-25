---
title: Projektant przepływu pracy — Projektant działań elementu FlowDecision
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 08c8aadb3c452a59f1b44cd030331164384d23bb
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758340"
---
# <a name="flowdecision-activity-designer"></a>FlowDecision, projektant działań

<xref:System.Activities.Statements.FlowDecision> Węzeł jest węzłem warunkowego udostępniający gałąź przepływu sterowania do jednej z dwóch rozwiązań alternatywnych, na podstawie tego, czy określony warunek jest spełniony. Jeśli przepływ wymaga więcej niż dwa oddziały, należy użyć <xref:System.Activities.Statements.FlowSwitch%601> zamiast tego.

## <a name="the-flowdecision-node"></a>Węzeł elementu FlowDecision

Użyj <xref:System.Activities.Statements.FlowDecision> podczas przepływu można rozgałęzionych na dwie ścieżki. A <xref:System.Activities.Statements.FlowDecision> węzeł ma <xref:System.Activities.Statements.FlowDecision.Condition%2A> i <xref:System.Activities.Statements.FlowNode> skojarzone z każdym z dwóch możliwych wyników: <xref:System.Activities.Statements.FlowDecision.True%2A> lub <xref:System.Activities.Statements.FlowDecision.False%2A>. <xref:System.Activities.Statements.FlowDecision.Condition%2A> Jest obliczane i wartość tej oceny określa następnej <xref:System.Activities.Statements.FlowNode> do przetworzenia w ciągu <xref:System.Activities.Statements.Flowchart>.

### <a name="using-the-flowdecision-designer"></a>Przy użyciu narzędzia Projektant elementu FlowDecision

**Elementu FlowDecision** designer znajduje się w **schemat blokowy** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** Karta w Projektancie przepływów pracy. Można także wybrać **przybornika** z **widoku** menu lub naciśnij klawisz **Ctrl**+**Alt** + **X**.

**Elementu FlowDecision** projektanta mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy w ramach **schemat blokowy** Projektant działań. Spowoduje to utworzenie <xref:System.Activities.Statements.FlowDecision> etykietą **decyzji** w <xref:System.Activities.Statements.Flowchart> działania. Myszy przez projektanta i **True** i **False** kwadratowe dla dwóch gałęziach uchwytów.

Po przeciąganie **elementu FlowDecision** projektanta i innych projektantów na **schemat blokowy**, węzły mogą być połączone ze sobą, aby określić kolejność wykonywania. Utwórz łącze między węzłem źródła (w tym **True** i **False** gałęzi z **elementu FlowDecision**) i do węzła docelowego myszą projektanta węzła źródłowego i uchwytów kwadratowe na każdej stronie. Jednym z kwadratowych uchwytów kliknij i przeciągnij go, przytrzymując przycisk myszy, aby jeden dojść, które jest wyświetlany w podobny sposób wokół docelowego węzła, gdy mysz nad nim. Zwolnij przycisk myszy, a tworzone jest połączenie między te dwa węzły, które jest reprezentowany jako strzałka z projektanta źródła do projektanta docelowego.

Wyrażenie, które stany <xref:System.Activities.Statements.FlowDecision.Condition%2A> można wpisać w **warunku** pole **właściwości** okna, klikając, gdy tekst podpowiedzi mówi "Wprowadź wyrażenia języka VB.".

### <a name="the-flowdecision-properties"></a>Właściwości elementu FlowDecision

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.FlowDecision> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchnię projektanta.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|Warunek, który określa ścieżkę, która przyjmuje sterowanie przepływem.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|Ścieżka wykonywaną przez sterowanie przepływem, jeśli <xref:System.Activities.Statements.FlowDecision.Condition%2A> jest spełniony.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|Ścieżka wykonywaną przez sterowanie przepływem, jeśli <xref:System.Activities.Statements.FlowDecision.Condition%2A> nie jest spełniony.|

## <a name="see-also"></a>Zobacz także

- [Schemat blokowy](../workflow-designer/flowchart-activity-designers.md)
- [Schemat blokowy](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)