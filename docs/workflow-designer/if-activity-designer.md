---
title: "Jeśli Projektant działań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3d3928330558c3d611decd2a87498d33fd6482ce
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="if-activity-designer"></a>Jeśli Projektant działań
<xref:System.Activities.Statements.If> Działania sprawdza warunek i wykonuje działania w zależności od wyników tej oceny. To działanie jest najbardziej przydatna, korzystając z procedur modelowania styl programowania. <xref:System.Activities.Statements.If> Działania mogą być zagnieżdżone wewnątrz <xref:System.Activities.Statements.Sequence> działania lub <xref:System.Activities.Statements.Parallel> działania, np. Jeśli używasz <xref:System.Activities.Statements.Flowchart> działania, rozważ użycie <xref:System.Activities.Statements.FlowDecision> działania zamiast tego.  
  
## <a name="if-properties-in-the-workflow-designer"></a>Jeśli właściwości w Projektancie przepływów pracy  
 W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.If> właściwości działania i informacje dotyczące używania ich w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.If.Condition%2A>|Wartość true|Warunek, który określa działanie podrzędne, które można wykonać. Aby ustawić <xref:System.Activities.Statements.If.Condition%2A>, wpisz [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] wyrażenie w **warunku** polu na **Jeśli** działania projektanta lub w siatce właściwości.|  
|<xref:System.Activities.Statements.If.Else%2A>|False|Działanie do wykonania, gdy <xref:System.Activities.Statements.If.Condition%2A> jest **false**. Aby dodać działanie, które jest wykonywane przez <xref:System.Activities.Statements.If.Else%2A> gałęzi, Porzuć działania z **przybornika** do **Else** polu na **Jeśli** Projektant działań z tekstu podpowiedzi " Upuść działanie tutaj".|  
|<xref:System.Activities.Statements.If.Then%2A>|False|Działanie do wykonania, gdy <xref:System.Activities.Statements.If.Condition%2A> jest **true**. Aby dodać działanie, które jest wykonywane przez <xref:System.Activities.Statements.If.Then%2A> gałęzi, Porzuć działania z **przybornika** do **następnie** polu na **Jeśli** Projektant działań z tekstu podpowiedzi " Upuść działanie tutaj".|  
  
## <a name="see-also"></a>Zobacz też  
 [Sekwencja](../workflow-designer/sequence-activity-designer.md)   
 [Równoległe](../workflow-designer/parallel-activity-designer.md)   
 [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)