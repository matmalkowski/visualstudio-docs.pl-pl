---
title: "Przypisz Projektant działań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: bb816aee41f86e2cbdc71e93b78f1a9e09249a00
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="assign-activity-designer"></a>Przypisz Projektant działań
**Przypisać** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Assign> działania.  
  
## <a name="the-assign-activity"></a>Przypisz działania  
 <xref:System.Activities.Statements.Assign> Działania przypisuje wartość do zmiennej lub argumentu.  
  
### <a name="using-the-assign-activity-designer"></a>Przy użyciu narzędzia Projektant działań przypisania  
 **Przypisać** Projektant działań można znaleźć w **podstawowych** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**kartę (można także wybrać **przybornika** z **widoku** menu lub CTRL + ALT + X.)  
  
 **Przypisać** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni gdziekolwiek działań zwykle są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.Assign> działania z domyślną **DisplayName** z przypisania. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **przypisać** Projektant działań lub **DisplayName** pola siatki właściwości.  
  
### <a name="the-assign-properties"></a>Przypisz właściwości  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Assign> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości i niektóre z nich można edytowane na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.Assign> działania. Wartość domyślna to przypisanie. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagane, jest najlepszym rozwiązaniem jej użyć.|  
|<xref:System.Activities.Statements.Assign.To%2A>|Wartość true|Zmienna lub argument, do którego <xref:System.Activities.Statements.Assign.Value%2A> jest przypisany. Musi to być prawidłowy identyfikator języka Visual Basic. Aby ustawić właściwości, wpisz wyrażenie języka Visual Basic w **do** polu na **przypisać** działania projektanta lub w siatce właściwości.|  
|<xref:System.Activities.Statements.Assign.Value%2A>|Wartość true|Wartość, która jest przypisana do zmiennej. Aby ustawić <xref:System.Activities.Statements.Assign.Value%2A>, wpisz wyrażenie języka Visual Basic w **wartość** polu na **przypisać** działania projektanta lub w siatce właściwości.|  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy podstawowe](../workflow-designer/primitives-activity-designers.md)   
 [Opóźnienie](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)