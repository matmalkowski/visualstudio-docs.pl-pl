---
title: Projektant przepływu pracy — Jeśli Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 58adde57c6de49a4abb0456ba5c80df27a45b069
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971211"
---
# <a name="if-activity-designer"></a>Jeśli Projektant działań

<xref:System.Activities.Statements.If> Działania sprawdza warunek i wykonuje działania w zależności od wyników tej oceny. To działanie jest najbardziej przydatna, korzystając z procedur modelowania styl programowania. <xref:System.Activities.Statements.If> Działania mogą być zagnieżdżone wewnątrz <xref:System.Activities.Statements.Sequence> działania lub <xref:System.Activities.Statements.Parallel> działania, np. Jeśli używasz <xref:System.Activities.Statements.Flowchart> działania, rozważ użycie <xref:System.Activities.Statements.FlowDecision> działania zamiast tego.

## <a name="if-properties-in-the-workflow-designer"></a>Jeśli właściwości w Projektancie przepływów pracy

W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.If> właściwości działania i informacje dotyczące używania ich w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.If.Condition%2A>|True|Warunek, który określa działanie podrzędne, które można wykonać. Aby ustawić <xref:System.Activities.Statements.If.Condition%2A>, wpisz wyrażenie języka Visual Basic w **warunku** polu na **Jeśli** działania projektanta lub w siatce właściwości.|
|<xref:System.Activities.Statements.If.Else%2A>|False|Działanie do wykonania, gdy <xref:System.Activities.Statements.If.Condition%2A> jest **false**. Aby dodać działanie, które jest wykonywane przez <xref:System.Activities.Statements.If.Else%2A> gałęzi, Porzuć działania z **przybornika** do **Else** polu na **Jeśli** Projektant działań z tekstu podpowiedzi " Upuść działanie tutaj".|
|<xref:System.Activities.Statements.If.Then%2A>|False|Działanie do wykonania, gdy <xref:System.Activities.Statements.If.Condition%2A> jest **true**. Aby dodać działanie, które jest wykonywane przez <xref:System.Activities.Statements.If.Then%2A> gałęzi, Porzuć działania z **przybornika** do **następnie** polu na **Jeśli** Projektant działań z tekstu podpowiedzi " Upuść działanie tutaj".|

## <a name="see-also"></a>Zobacz także

- [Sekwencja](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)