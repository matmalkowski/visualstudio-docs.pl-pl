---
title: "Projektant działań DoWhile | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 041c63d45e70305495fd18ed595a31eee6772389
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="dowhile-activity-designer"></a>Projektant działań DoWhile
<xref:System.Activities.Statements.DoWhile> Działania wykonuje działania zawarte w jego <xref:System.Activities.Statements.DoWhile.Body%2A> co najmniej raz, aż określony warunek ma **false**. Jeśli potrzebujesz działania zawarte w treści pętli do wykonania zero lub więcej razy, użyj <xref:System.Activities.Statements.While> działania zamiast tego.  
  
## <a name="dowhile-properties-in-the-workflow-designer"></a>Właściwości DoWhile w Projektancie przepływów pracy  
 W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.DoWhile> właściwości działania i informacje dotyczące używania ich w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Działanie do wykonania, gdy wynikiem warunku jest **true**. Aby dodać <xref:System.Activities.Statements.DoWhile.Body%2A> działania, Porzuć działanie z przybornika do **treści** polu na **DoWhile** Projektant działań z tekstu podpowiedzi "Upuść tutaj działanie".|  
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Wartość true|Warunek do oceny po każdej iteracji pętli. Aby ustawić <xref:System.Activities.Statements.DoWhile.Condition%2A>, wpisz [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] wyrażenie w **warunku** polu na **DoWhile** działania projektanta lub w siatce właściwości.|  
  
## <a name="see-also"></a>Zobacz też  
 [While](../workflow-designer/while-activity-designer.md)   
 [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)