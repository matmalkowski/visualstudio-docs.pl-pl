---
title: "Projektant działań rethrow | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1a41dd3b640b53689f8eb3ef3c0a02cd3e191df7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="rethrow-activity-designer"></a>Rethrow Projektant działań
**Rethrow** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Rethrow> działania.  
  
## <a name="the-rethrow-activity"></a>Działanie Rethrow  
 <xref:System.Activities.Statements.Rethrow> Działania zgłasza wcześniej zwrócony wyjątek. To działanie może być używane tylko w <xref:System.Activities.Statements.Catch> obsługi w <xref:System.Activities.Statements.TryCatch> działania.  
  
### <a name="using-the-rethrow-activity-designer"></a>Przy użyciu narzędzia Projektant działania ReThrow  
 **Rethrow** Projektant działań można znaleźć w **obsługi błędu** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karcie po lewej stronie [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)  
  
 **Rethrow** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań zwykle są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.Rethrow> działania z domyślną **DisplayName** z Throw. <xref:System.Activities.Activity.DisplayName%2A> Wartość można edytować w nagłówku **Rethrow** Projektant działań lub **DisplayName** pola siatki właściwości.  
  
### <a name="the-rethrow-properties"></a>Właściwości Rethrow  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Rethrow> właściwości oraz opis korzystania z nich w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalne przyjazna nazwa <xref:System.Activities.Statements.Rethrow> działania. Wartość domyślna to Rethrow.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcja](../workflow-designer/collection-activity-designers.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)