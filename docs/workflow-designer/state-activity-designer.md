---
title: "Stan Projektant działań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
caps.latest.revision: "5"
ms.author: sdanie
manager: erikre
ms.openlocfilehash: 22e9e9c6f31923eb097b34eab19e61762fb2956b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="state-activity-designer"></a>Projektant działań stanu
A <xref:System.Activities.Statements.State> reprezentuje stan, w którym mogą mieć automatu stanów.  
  
## <a name="using-the-state-activity-designer"></a>Przy użyciu narzędzia Projektant stanu działania  
 Aby dodać <xref:System.Activities.Statements.State> do przepływu pracy, przeciągnij **stanu** Projektant działań z **automatu stanów** sekcji **przybornika** i upuść ją na do <xref:System.Activities.Statements.StateMachine> działanie na [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] powierzchni. A <xref:System.Activities.Statements.State> działania mogą być upuszczone na <xref:System.Activities.Statements.StateMachine> i przejść, dodane później; lub przejście może zostać utworzony jako <xref:System.Activities.Statements.State> działanie zostało porzucone. Aby dodać <xref:System.Activities.Statements.State> działania i utworzyć przejście w jednym kroku, przeciągnij **stanu** działania z **automatu stanów** sekcji **przybornika** i aktywuj go innym Stan w Projektancie przepływów pracy. Gdy przeciąganego <xref:System.Activities.Statements.State> znajduje się nad innym <xref:System.Activities.Statements.State>, cztery trójkąty pojawi się wokół innych <xref:System.Activities.Statements.State>. Jeśli <xref:System.Activities.Statements.State> jest przerywane na jedną z czterech trójkąty, jest ona dodawana do automatu stanów i utworzeniu przejście ze źródła <xref:System.Activities.Statements.State> porzuconych docelowego <xref:System.Activities.Statements.State>. Aby uzyskać więcej informacji, zobacz [przejścia](../workflow-designer/transition-activity-designer.md).  
  
### <a name="state-activity-properties-in-the-workflow-designer"></a>Właściwości stanu aktywności w Projektancie przepływów pracy  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.State> właściwości, które można ustawić za pomocą projektanta przepływów pracy i w tym artykule opisano, jak są używane w projektancie. Niektóre z tych właściwości można edytować w siatce właściwości i niektóre można edytowane na powierzchnię projektanta.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.State> Projektant działań w nagłówku. Wartość domyślna to **stanu**. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku Projektant działań. <xref:System.Activities.Statements.State.DisplayName%2A> Jest używany w nadrzędnych, który jest wyświetlany w górnej części projektanta przepływów pracy.<br /><br /> Mimo że <xref:System.Activities.Statements.State.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem jej użyć.|  
|<xref:System.Activities.Statements.State.Entry%2A>|False|Określa akcję wykonywaną, gdy ten stan jest optymalizowane pod. Gdy <xref:System.Activities.Statements.State> działania jest rozwinięty, tę wartość można ustawić przez przeciągnięcie działania z **przybornika** i upuszczanie go na **wpis** sekcji stanu.|  
|<xref:System.Activities.Statements.State.Exit%2A>|False|Określa akcję wykonywaną, gdy ten stan jest optymalizowane od. Gdy <xref:System.Activities.Statements.State> działania jest rozwinięty, tę wartość można ustawić przez przeciągnięcie działania z **przybornika** i upuszczanie go na **zakończenia** sekcji stanu.|  
|<xref:System.Activities.Statements.State.Transitions%2A>|False|Wyświetla listę możliwości przejścia, które pochodzą ze <xref:System.Activities.Statements.State>. Każdy element na liście znajduje się łącze do skojarzonego <xref:System.Activities.Statements.Transition> i miejsce docelowe <xref:System.Activities.Statements.State>. Kliknięcie łącza przechodzi do rozwiniętego widoku Projektanta <xref:System.Activities.Statements.Transition> lub <xref:System.Activities.Statements.State>.|  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [Stan końcowy](../workflow-designer/finalstate-activity-designer.md)   
 [Przejścia](../workflow-designer/transition-activity-designer.md)