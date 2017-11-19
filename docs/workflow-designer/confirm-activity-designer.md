---
title: "Upewnij się, Projektant działań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3d1255b210bdb68868b4bc2ee0e38475da840429
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="confirm-activity-designer"></a>Upewnij się, Projektant działań
**Potwierdź** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Confirm> działania.  
  
## <a name="the-confirm-activity"></a>Działanie Confirm  
 <xref:System.Activities.Statements.Confirm> Działania jawnie wywołuje <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> dla działania zawarte w <xref:System.Activities.Statements.CompensableActivity>. Jeśli <xref:System.Activities.Statements.Confirm> działanie nie jest używane w ramach <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, lub <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> z <xref:System.Activities.Statements.CompensableActivity>, a następnie podaj <xref:System.Activities.Statements.Confirm.Target%2A> właściwości.  
  
 <xref:System.Activities.Statements.CompensationToken> Określonego przez <xref:System.Activities.Statements.Compensate.Target%2A> umożliwia jawnie potwierdzić lub kompensacji <xref:System.Activities.Statements.CompensableActivity> po <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> zostało pomyślnie ukończone.  
  
### <a name="using-the-confirm-activity-designer"></a>Przy użyciu potwierdzić Projektant działań  
 **Potwierdź** Projektant działań można znaleźć w **transakcji** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karcie po lewej stronie [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)  
  
 **Potwierdź** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań zwykle są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.Confirm> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> o potwierdzenie. <xref:System.Activities.Activity.DisplayName%2A> Wartość może być edytowany w nagłówku **Potwierdź** Projektant działań lub **DisplayName** pola siatki właściwości.  
  
### <a name="the-confirm-properties"></a>Upewnij się, właściwości  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Confirm> właściwości oraz opis korzystania z nich w projektancie. <xref:System.Activities.Activity.DisplayName%2A> Właściwości można edytować w siatce właściwości lub na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni, ale <xref:System.Activities.Statements.Confirm.Target%2A> należy edytować właściwości w siatce właściwości.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalne przyjazna nazwa <xref:System.Activities.Statements.CancellationScope> działania. Wartość domyślna to potwierdzić.|  
|<xref:System.Activities.Statements.Confirm.Target%2A>|Wartość true|Określa <xref:System.Activities.InArgument%601> zawierający <xref:System.Activities.Statements.CompensationToken> dla tego <xref:System.Activities.Statements.Confirm> działania.|  
  
## <a name="see-also"></a>Zobacz też  
 [Transakcji](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [Działanie CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Wyrównania](../workflow-designer/compensate-activity-designer.md)   
 [Element TransactionScope](../workflow-designer/transactionscope-activity-designer.md)