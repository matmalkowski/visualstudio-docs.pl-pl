---
title: "Projektant działań elementu FlowDecision | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 3e3fd48f33e5499f7a67aed02c7b732ebe6b3b7b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="flowdecision-activity-designer"></a>Projektant działań elementu FlowDecision
<xref:System.Activities.Statements.FlowDecision> Węzeł jest węzłem warunkowego udostępniający gałąź przepływu sterowania do jednej z dwóch rozwiązań alternatywnych, na podstawie tego, czy określony warunek jest spełniony. Jeśli przepływ wymaga więcej niż dwa oddziały, należy użyć <xref:System.Activities.Statements.FlowSwitch%601> zamiast tego.  
  
## <a name="the-flowdecision-node"></a>Węzeł elementu FlowDecision  
 Użyj <xref:System.Activities.Statements.FlowDecision> podczas przepływu można rozgałęzionych na dwie ścieżki. A <xref:System.Activities.Statements.FlowDecision> węzeł ma <xref:System.Activities.Statements.FlowDecision.Condition%2A> i <xref:System.Activities.Statements.FlowNode> skojarzone z każdym z dwóch możliwych wyników: <xref:System.Activities.Statements.FlowDecision.True%2A> lub <xref:System.Activities.Statements.FlowDecision.False%2A>. <xref:System.Activities.Statements.FlowDecision.Condition%2A> Jest obliczane i wartość tej oceny określa następnej <xref:System.Activities.Statements.FlowNode> do przetworzenia w ciągu <xref:System.Activities.Statements.Flowchart>.  
  
### <a name="using-the-flowdecision-designer"></a>Przy użyciu narzędzia Projektant elementu FlowDecision  
 **Elementu FlowDecision** designer znajduje się w **schemat blokowy** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** Karta na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)  
  
 **Elementu FlowDecision** projektanta mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni w **schemat blokowy** Projektant działań. Spowoduje to utworzenie <xref:System.Activities.Statements.FlowDecision> etykietą **decyzji** w <xref:System.Activities.Statements.Flowchart> działania. Myszy przez projektanta i **True** i **False** kwadratowe dla dwóch gałęziach uchwytów.  
  
 Po przeciąganie **elementu FlowDecision** projektanta i innych projektantów na **schemat blokowy**, węzły mogą być połączone ze sobą, aby określić kolejność wykonywania. Utwórz łącze między węzłem źródła (w tym **True** i **False** gałęzi z **elementu FlowDecision**) i do węzła docelowego myszą projektanta węzła źródłowego i uchwytów kwadratowe na każdej stronie. Jednym z kwadratowych uchwytów kliknij i przeciągnij go, przytrzymując przycisk myszy, aby jeden dojść, które jest wyświetlany w podobny sposób wokół docelowego węzła, gdy mysz nad nim. Zwolnij przycisk myszy, a tworzone jest połączenie między te dwa węzły, które jest reprezentowany jako strzałka z projektanta źródła do projektanta docelowego.  
  
 Wyrażenie, które stany <xref:System.Activities.Statements.FlowDecision.Condition%2A> można wpisać w **warunku** pole **właściwości** okna, klikając, gdy tekst podpowiedzi mówi "Wprowadź wyrażenia języka VB.".  
  
### <a name="the-flowdecision-properties"></a>Właściwości elementu FlowDecision  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.FlowDecision> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchnię projektanta.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|Wartość true|Warunek, który określa ścieżkę, która przyjmuje sterowanie przepływem.|  
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|Ścieżka wykonywaną przez sterowanie przepływem, jeśli <xref:System.Activities.Statements.FlowDecision.Condition%2A> jest spełniony.|  
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|Ścieżka wykonywaną przez sterowanie przepływem, jeśli <xref:System.Activities.Statements.FlowDecision.Condition%2A> nie jest spełniony.|  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat blokowy](../workflow-designer/flowchart-activity-designers.md)   
 [Schemat blokowy](../workflow-designer/flowchart-activity-designer.md)   
 [Elementu FlowSwitch\<T >](../workflow-designer/flowswitch-t-activity-designer.md)