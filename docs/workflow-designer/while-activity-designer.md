---
title: "Projektant działań while | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: f232d8e6c4a1dab9000b8f0e0f3037d083acbbef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="while-activity-designer"></a>Podczas gdy Projektant działań
<xref:System.Activities.Statements.While> Działania wykonuje działania zawarte w jego <xref:System.Activities.Statements.While.Body%2A> podczas określonego <xref:System.Activities.Statements.While.Condition%2A> daje w wyniku **true**. Nigdy nie może wykonać zawarte działanie. Jeśli chcesz, aby zawarte działanie ma być wykonywana co najmniej raz, użyj <xref:System.Activities.Statements.DoWhile> działania zamiast tego.  
  
## <a name="while-properties-in-workflow-designer"></a>Podczas właściwości w Projektancie przepływów pracy  
 W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.While> właściwości działania i w tym artykule opisano, jak są używane w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.While> Projektant działań w nagłówku. Wartość domyślna to podczas. Wartość można edytować w **właściwości** okna lub bezpośrednio w nagłówku projektanta działania.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem jej użyć.|  
|<xref:System.Activities.Statements.While.Body%2A>|False|Zawiera działanie do wykonania podczas <xref:System.Activities.Statements.While.Condition%2A> daje w wyniku **true**.|  
|<xref:System.Activities.Statements.While.Condition%2A>|Wartość true|Zawiera [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] wyrażenie, które jest obliczane, aby określić, czy działania w <xref:System.Activities.Statements.While.Body%2A> jest wykonywana.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)   
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)