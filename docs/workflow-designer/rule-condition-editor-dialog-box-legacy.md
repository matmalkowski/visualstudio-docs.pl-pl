---
title: "Okno dialogowe Edytor warunku reguły (starsze) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords:
- Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: a4f38bed7fc164fd5283b98afe780bc81a6a7265
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Okno dialogowe Edytor warunku reguły (starsze)
W tym temacie opisano sposób użycia **Edytor warunku reguły** okno dialogowe w starszych [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]. Użyj starszego [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] konieczność docelowy: [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] lub [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Tworzenie i modyfikowanie warunków reguł deklaratywne przy użyciu **Edytor warunku reguły** okno dialogowe. Te warunki reguły są widoczne jako właściwości na wykonywanie następujących czynności out-of-box Windows Workflow Foundation:  
  
-   [Grupy ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [Działanie ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [Działanie WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
 Możesz uzyskać dostępu do **Edytor warunku reguły** okno dialogowe przy użyciu [warunku okno dialogowe Wybieranie (starsze)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
 W poniższej tabeli opisano elementy interfejsu użytkownika **Edytor warunku reguły** okno dialogowe.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Warunek:**|Wprowadź wyrażenie dla warunku reguły.|  
|**OK**|Kliknij, aby zapisać warunek reguły.|  
  
## <a name="entering-condition-expressions"></a>Wprowadzanie warunku wyrażenia  
 Wyrażenie warunku jest wprowadzana jako tekst. Możesz wpisać **to.** w edytorze, aby odwoływać się do pola, właściwości i metody używane w przepływie pracy przy użyciu menu przypominającej IntelliSense. Lub nazwa elementu członkowskiego przepływu pracy można wpisać bezpośrednio. Operatory logiczne można dodać do warunku, takich jak AND, OR i NOT. Można również dodać predykatów. Predykat jest operator binarny i dwóch argumentów operacji. Operatory binarne obsługiwane są  **==** ,  **>** ,  **\<** ,  **>=** , i  **<=** . Obsługiwane argumenty operacji są wartości stałej, funkcja arytmetyczne i zakresami publiczne elementy członkowskie.  
  
 Można określić typ do porównania i możesz porównać **null** lub ciąg pusty. Zagnieżdżone wywołania do elementów członkowskich mogą być wykonywane na zmienna, która zawiera typ złożony, na przykład `this.Address.State == "WA"`.  
  
 Edytor warunku reguły obsługuje następujące operatory:  
  
-   Operatory relacyjne: ==, =,! =  
  
-   Operatory porównania: <, \<=, >, > =  
  
-   Operatory arytmetyczne: +, -, *, /, MOD  
  
-   Operatory logiczne: I, & &, OR &#124; &#124; a nie,!  
  
-   Operatory bitowe: & &#124;  
  
 Kolejność wykonywania wyrażenia następuje reguły pierwszeństwa operatora C#.  
  
 Edytor warunku reguły obsługuje następujące wyrażenia liczbowego:  
  
 this.i == 1D (jest rozpoznawana jako 1.0)  
  
 this.i == 1E1 (jest rozpoznawana jako 10.0)  
  
 this.i == 1L (jest rozpoznawana jako long)  
  
 this.i == 1-M (jest rozpoznawana jako wartości dziesiętnej)  
  
 this.i == 1F (jest rozpoznawana jako pojedynczy)  
  
 this.i == 1U (jest rozpoznawana jako unsigned int)  
  
 Aby uzyskać więcej informacji o warunkach, zobacz [za pomocą warunków w przepływach pracy](http://go.microsoft.com/fwlink?LinkID=65009).  
  
## <a name="see-also"></a>Zobacz też  
 [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)   
 [Grupy ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)   
 [Działanie ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)   
 [Działanie WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)   
 [Wybierz warunek, okno dialogowe (starsze)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Za pomocą warunków w przepływach pracy](http://go.microsoft.com/fwlink?LinkID=65009)   
 [Starsza wersja projektanta pomocy interfejsu użytkownika programu Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)