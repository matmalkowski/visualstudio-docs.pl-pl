---
title: Projektant działań DoWhile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 911e6d6d94090ddcdd43fcd9511624e209f7c03c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680566"
---
# <a name="dowhile-activity-designer"></a>DoWhile, projektant działań
<xref:System.Activities.Statements.DoWhile> Działanie wykonuje działania zawarte w jego <xref:System.Activities.Statements.DoWhile.Body%2A> co najmniej raz, aż określony warunek ma **false**. Jeśli potrzebujesz działania zawarte w treści pętli do wykonania, zero lub więcej razy, użyj <xref:System.Activities.Statements.While> działania zamiast tego.  
  
## <a name="dowhile-properties-in-the-workflow-designer"></a>Właściwości DoWhile w Projektancie przepływu pracy  
 W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.DoWhile> właściwości działań i informacje dotyczące używania ich w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Działanie do wykonania, gdy wynikiem warunku jest **true**. Można dodać <xref:System.Activities.Statements.DoWhile.Body%2A> działania, listy działanie z przybornika do **treści** polu na **DoWhile** projektanta działań z tekst wskazówki "Upuść działanie tutaj".|  
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|Warunek do oceny po każdej iteracji pętli. Aby ustawić <xref:System.Activities.Statements.DoWhile.Condition%2A>, wpisz [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] wyrażenia w **warunek** polu na **DoWhile** działanie projektanta lub w siatce właściwości.|  
  
## <a name="see-also"></a>Zobacz też  
 [Podczas](../workflow-designer/while-activity-designer.md)   
 [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)