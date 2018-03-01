---
title: "Projektant działań CancellationScope | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: c6e9206eff3eaaeb3b5a79bb8457738c21af05c7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cancellationscope-activity-designer"></a>Projektant działań CancellationScope
**CancellationScope** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.CancellationScope> działania.  
  
## <a name="the-cancellationscope-activity"></a>Działanie CancellationScope  
 <xref:System.Activities.Statements.CancellationScope> Działania można określić działanie logiki wykonywania i anulowania dla tego działania.  
  
### <a name="using-the-cancellationscope-activity-designer"></a>Przy użyciu narzędzia Projektant działań CancellationScope  
 **CancellationScope** Projektant działań można znaleźć w **transakcji** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**  karcie [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)  
  
 **CancellationScope** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań zwykle są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.CancellationScope> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z CancellationScope. <xref:System.Activities.Activity.DisplayName%2A> Wartość można edytować w nagłówku **CancellationScope** Projektant działań lub **DisplayName** pola siatki właściwości.  
  
### <a name="the-cancellationscope-properties"></a>Właściwości CancellationScope  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.CancellationScope> właściwości oraz opis korzystania z nich w projektancie. <xref:System.Activities.Activity.DisplayName%2A> Właściwości można edytować w siatce właściwości, ale inne właściwości, należy edytować na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalne przyjazna nazwa <xref:System.Activities.Statements.CancellationScope> działania. Wartość domyślna to CancellationScope. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagane, jest najlepszym rozwiązaniem jej użyć.|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Wartość true|Określa działania, które anulowania podano logiki. Aby dodać <xref:System.Activities.Statements.CancellationScope.Body%2A> działania, Porzuć działanie z **przybornika** do **treści** pole na **CancellationScope** Projektant działań z tekstu podpowiedzi "upuść Działanie tutaj".|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Wartość true|Określa działania, która jest wykonywana w przypadku anulowania. Aby dodać <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> działania, Porzuć działanie z **przybornika** do **CancellationHandler** polu na **CancellationScope** Projektant działań ze wskazówką tekst "Upuść tutaj działanie".|  
  
## <a name="see-also"></a>Zobacz też  
 [Transakcji](../workflow-designer/transaction-activity-designers.md)   
 [Działanie CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Wyrównania](../workflow-designer/compensate-activity-designer.md)   
 [Upewnij się](../workflow-designer/confirm-activity-designer.md)   
 [Element TransactionScope](../workflow-designer/transactionscope-activity-designer.md)