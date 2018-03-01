---
title: "Projektant działań elementu TransactionScope | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 9c9b9ab609825a68edc4e2862d64bdd7cb830202
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="transactionscope-activity-designer"></a>Projektant działań elementu TransactionScope
**TransactionScope** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.TransactionScope> działania.  
  
## <a name="the-transactionscope-activity"></a>Działania TransactionScope  
 <xref:System.Activities.Statements.TransactionScope> Działania wykonuje zawarte działanie w ramach jednej transakcji. Zatwierdza transakcji, gdy <xref:System.Activities.Statements.TransactionScope.Body%2A> działania i innych uczestników w transakcji została ukończona pomyślnie.  
  
### <a name="using-the-transactionscope-activity-designer"></a>Przy użyciu narzędzia Projektant działania TransactionScope  
 **TransactionScope** Projektant działań można znaleźć w **transakcji** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**  karcie [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)  
  
 **TransactionScope** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań zwykle są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.TransactionScope> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> elementu TransactionScope. <xref:System.Activities.Activity.DisplayName%2A> Wartość można edytować w nagłówku **TransactionScope** Projektant działań lub **DisplayName** pola siatki właściwości.  
  
### <a name="the-transactionscope-properties"></a>Właściwości elementu TransactionScope  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.TransactionScope> właściwości oraz opis korzystania z nich w projektancie. <xref:System.Activities.Activity.DisplayName%2A> i <xref:System.Activities.Statements.TransactionScope.Body%2A> właściwości można edytować na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni. Jednak inne właściwości, należy edytować na siatce właściwości.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalne przyjazna nazwa <xref:System.Activities.Statements.TransactionScope> działania. Wartość domyślna to element TransactionScope. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagane, jest najlepszym rozwiązaniem jej użyć.|  
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|Wartość true|Określa działania, które można wykonać w ramach jednej transakcji. Aby dodać <xref:System.Activities.Statements.TransactionScope.Body%2A> działania, Porzuć działanie z **przybornika** do **treści** polu na **TransactionScope** Projektant działań z tekstu podpowiedzi "Upuść działanie w tym miejscu".|  
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|Wartość true|Określa <xref:System.Transactions.IsolationLevel> dla tego <xref:System.Activities.Statements.TransactionScope>.|  
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Określa interwał (w formacie 00:00:00, co oznacza godziny: minuty: sekundy) ukończyć transakcję. Wartość domyślna to 1 minuta (00: 01:00).|  
|[System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure](https://msdn.microsoft.com/library/system.activities.statements.transactionscope.abortinstanceontransactionfailure.aspx)|Wartość true|Określa wartość, która wskazuje, czy przepływ pracy powinien przerwany, jeśli transakcja jest przerywana.|  
  
## <a name="see-also"></a>Zobacz też  
 [Transakcji](../workflow-designer/transaction-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)   
 [Działanie CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Wyrównania](../workflow-designer/compensate-activity-designer.md)   
 [Upewnij się](../workflow-designer/confirm-activity-designer.md)