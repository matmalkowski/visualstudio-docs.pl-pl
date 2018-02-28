---
title: "Projektant działań throw | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: f9af95a8aeb509554cb613edb848c2987543f1e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="throw-activity-designer"></a>Throw Projektant działań
**Throw** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Throw> działania.  
  
## <a name="the-throw-activity"></a>Działanie Throw  
 <xref:System.Activities.Statements.Throw> Działania zgłasza wyjątek.  
  
### <a name="using-the-throw-activity-designer"></a>Przy użyciu narzędzia Projektant działań Throw  
 **Throw** Projektant działań można znaleźć w **obsługi błędu** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karcie po lewej stronie [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)  
  
 **Throw** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań zwykle są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.Throw> działania z domyślną **DisplayName** z Throw. <xref:System.Activities.Activity.DisplayName%2A> Wartość można edytować w nagłówku **Throw** Projektant działań lub **DisplayName** pola siatki właściwości. <xref:System.Activities.Statements.Throw.Exception%2A> Należy edytować właściwości na siatce właściwości.  
  
### <a name="the-throw-properties"></a>Właściwości Throw  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Throw> właściwości oraz opis korzystania z nich w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalne przyjazna nazwa <xref:System.Activities.Statements.Throw> działania. Wartość domyślna to Throw.|  
|<xref:System.Activities.Statements.Throw.Exception%2A>|Wartość true|Aby zgłosić wyjątek. Ten wyjątek musi pochodzić od <xref:System.Exception>. Aby określić wyjątek, wpisz wyrażenie języka Visual Basic w siatce właściwości.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcja](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw Projektant działań](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)