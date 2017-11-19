---
title: "Projektant działań kompensacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7fa3d16f87f6c81f0f9a4abfb961754ce7882f4c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="compensate-activity-designer"></a>Projektant działań wyrównania
**Compensate** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Compensate> działania.  
  
## <a name="the-compensate-activity"></a>Działanie Compensate  
 <xref:System.Activities.Statements.Compensate> Działania jawnie wywołuje <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> dla działania zawarte w <xref:System.Activities.Statements.CompensableActivity>. Jeśli <xref:System.Activities.Statements.Compensate> działanie nie jest używane w ramach <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, lub <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> z <xref:System.Activities.Statements.CompensableActivity>, a następnie podaj <xref:System.Activities.Statements.Compensate.Target%2A> właściwości.  
  
 <xref:System.Activities.Statements.CompensationToken> Określonego przez <xref:System.Activities.Statements.Compensate.Target%2A> umożliwia jawnie potwierdzić lub kompensacji <xref:System.Activities.Statements.CompensableActivity> po <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> zostało pomyślnie ukończone.  
  
### <a name="using-the-compensate-activity-designer"></a>Przy użyciu kompensacji Projektant działań  
 **Compensate** Projektant działań można znaleźć w **transakcji** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** karcie po lewej stronie [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)  
  
 **Compensate** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań zwykle są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.Compensate> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z Compensate. <xref:System.Activities.Activity.DisplayName%2A> Wartość można edytować w nagłówku **Compensate** Projektant działań lub **DisplayName** pola siatki właściwości.  
  
### <a name="the-compensate-properties"></a>Kompensacji właściwości  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.CancellationScope> właściwości oraz opis korzystania z nich w projektancie. <xref:System.Activities.Activity.DisplayName%2A> Właściwości można edytować w siatce właściwości lub na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni, ale <xref:System.Activities.Statements.Compensate.Target%2A> należy edytować właściwości w siatce właściwości.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalne przyjazna nazwa <xref:System.Activities.Statements.Compensate> działania. Wartość domyślna to Compensate.|  
|<xref:System.Activities.Statements.Compensate.Target%2A>|Wartość true|Określa <xref:System.Activities.InArgument%601> zawierający <xref:System.Activities.Statements.CompensationToken> dla tego <xref:System.Activities.Statements.Compensate> działania.|  
  
## <a name="see-also"></a>Zobacz też  
 [Transakcji](../workflow-designer/transaction-activity-designers.md)   
 [Działanie CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Projektant działań wyrównania](../workflow-designer/compensate-activity-designer.md)   
 [Upewnij się](../workflow-designer/confirm-activity-designer.md)   
 [Element TransactionScope](../workflow-designer/transactionscope-activity-designer.md)