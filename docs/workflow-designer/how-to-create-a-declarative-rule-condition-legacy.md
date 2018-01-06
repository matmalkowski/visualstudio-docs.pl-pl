---
title: "Porady: tworzenie warunku reguły deklaratywne (starsze) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 57835632e03e8b871c29e2fec7d4b382722451e7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Porady: tworzenie warunku reguły deklaratywne (starsze)
W tym temacie opisano sposób zadeklarować warunek reguły za pomocą starszego [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] którego element docelowy [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] lub [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Instrukcja warunku daje w wyniku **True** lub **False**. Warunek reguły deklaratywne jest instrukcja warunku, który jest tworzony przy użyciu [okno dialogowe Edytor warunku reguły (starsze)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) i przechowywane w formacie XML z przepływem pracy. Może uwzględniać predykaty porównana stanu przepływu pracy i algebraiczną Boolean, łączącą wielu predykatów.  
  
 Warunki reguły deklaratywne są używane w następujących działań out-of-box Windows Workflow Foundation:  
  
-   [Grupy ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [Działanie ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [Działanie WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Aby utworzyć warunek reguły deklaratywne przy użyciu Edytor warunku reguły  
  
1.  W działaniu **właściwości** okna, kliknij przycisk **warunku** właściwości lub **UntilCondition** właściwości, w zależności od działania.  
  
2.  Wybierz **deklaratywne warunek reguły** z listy właściwości.  
  
3.  Rozwiń węzeł **warunku** lub **UntilCondition** właściwości.  
  
4.  Kliknij przycisk **ConditionName** właściwości.  
  
5.  Kliknij przycisk **ConditionName** wielokropka **[...]**  otworzyć **wybierz warunek** okno dialogowe.  
  
6.  Kliknij przycisk **nowy warunek** otworzyć **Edytor warunku reguły** okno dialogowe.  
  
7.  Wpisz wyrażenie warunku w **warunku** pola tekstowego.  
  
     Informacje o sposobie tworzenia warunku wyrażenia, zobacz [okno dialogowe Edytor warunku reguły (starsze)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).  
  
8.  Po zakończeniu tworzenia wyrażenie warunku kliknij **OK** aby zamknąć okno dialogowe i utworzyć warunek reguły z przypisaną nazwę.  
  
     **Wybierz warunek** zostanie otwarte okno dialogowe.  
  
     Aby uzyskać informacje o sposobie używania **wybierz warunek** okno dialogowe, zobacz [warunku okno dialogowe Wybieranie (starsze)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Działania przepływu pracy w starszej wersji](../workflow-designer/legacy-workflow-activities.md)   
 [Za pomocą grupy ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)   
 [Za pomocą działania IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075)   
 [Za pomocą działania replikatora](http://go.microsoft.com/fwlink?LinkID=65080)   
 [Przy użyciu podczas działania](http://go.microsoft.com/fwlink?LinkID=65091)   
 [Okno dialogowe Edytor warunku reguły (starsze)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [Wybierz warunek, okno dialogowe (starsze)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Za pomocą warunków w przepływach pracy](http://go.microsoft.com/fwlink?LinkID=65009)