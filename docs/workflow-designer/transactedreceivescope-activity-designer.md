---
title: "Projektant działań TransactedReceiveScope | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 20dce7d4b3dc306c7bcd4f83a1f4e8fea10c6a94
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="transactedreceivescope-activity-designer"></a>Projektant działań TransactedReceiveScope
**TransactedReceiveScope** Projektant służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.  
  
## <a name="the-transactedreceivescope-activity"></a>Działania TransactedReceiveScope  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> Działania umożliwia przekazania transakcji do transakcji server utworzonych przez przepływ pracy lub dyspozytora.  
  
### <a name="using-the-transactedreceivescope-activity-designer"></a>Przy użyciu narzędzia Projektant działania TransactedReceiveScope  
 **TransactedReceiveScope** Projektant działań można znaleźć w **wiadomości** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**  karcie na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)  
  
 **TransactedReceiveScope** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań są zwykle umieszczane. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania z domyślną **DisplayName** z TransactedReceiveScope. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **TransactedReceiveScope** Projektant działań lub **DisplayName** pola siatki właściwości.  
  
 **TransactedReceiveScope** Projektant zawiera **żądania** i **treści** pola. Są one używane do konfigurowania <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> właściwość, która określa <xref:System.ServiceModel.Activities.Receive> działania i <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> właściwość, która określa innymi <xref:System.Activities.Activity>. <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> Tworzy transakcję. Następnie transakcji staje się otoczenia dla zakresu <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> tak, aby wszystkie działania w tym zakresie wykonuje w tej transakcji.  
  
### <a name="the-transactedreceivescope-properties"></a>Właściwości TransactedReceiveScope  
 W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.TransactedReceiveScope> właściwości oraz opis korzystania z nich w projektancie. Te <xref:System.Activities.Activity.DisplayName%2A> właściwości można edytować w siatce właściwości lub na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni, ale inne należy edytować na powierzchni projektu.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalne przyjazna nazwa <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania. Wartość domyślna to TransactedReceiveScope.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nazwa nie jest ściśle wymagane, jest najlepszym rozwiązaniem, aby użyć nazwy wyświetlanej.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Wartość true|Porzucania <xref:System.ServiceModel.Activities.Receive> działania do **żądania** bloku na powierzchni projektowej działania.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Porzucania <xref:System.Activities.Activity> do **treści** bloku na powierzchni projektowej działania.|  
  
## <a name="see-also"></a>Zobacz też  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Odbieranie](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Wyślij](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)