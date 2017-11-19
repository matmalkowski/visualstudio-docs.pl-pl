---
title: "Projektant działań while | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: b70e0c66813c474d5711538843da93a669df88d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
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