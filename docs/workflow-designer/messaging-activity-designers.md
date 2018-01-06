---
title: "Wiadomości projektantów działań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 897e63cf-a42f-4edd-876f-c4ccfffaf6d6
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 481d9e577989b1bd75cea22e0faab6d8a1cc64cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="messaging-activity-designers"></a>Projektanci działań do obsługi komunikatów
Komunikatów projektantów działań są używane do tworzenia i konfigurowania działania obsługi komunikatów, które wysyłania i odbierania [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] wiadomości z poziomu [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplikacji. [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] Wprowadza pięć działania obsługi wiadomości i [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] zawiera dwa nowe projektantów szablonu umożliwiające zarządzanie wiadomości w przepływie pracy. Tematy zawarte w tej sekcji i wymienione w poniższej tabeli zawierają wskazówki dotyczące sposobu używania [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] projektantów działań i szablonu.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Obsługa wiadomości|Opis|  
|----------------------|-----------------|  
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|Tworzy i konfiguruje <xref:System.ServiceModel.Activities.CorrelationScope> działanie, które umożliwia zarządzanie niejawne wiadomości działań z elementu podrzędnego <xref:System.ServiceModel.Activities.CorrelationHandle> obiektu.|  
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|Tworzy i konfiguruje <xref:System.ServiceModel.Activities.InitializeCorrelation> działanie, które służy do inicjowania korelacji bez wysyłania i odbierania wiadomości.|  
|[Odbieranie](../workflow-designer/receive-activity-designer.md)|Tworzy i konfiguruje <xref:System.ServiceModel.Activities.Receive> działania, który odbiera wiadomości z usługi.|  
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|Tworzy parę wstępnie skonfigurowane <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań w ramach <xref:System.Activities.Statements.Sequence> działania.|  
|[Wyślij](../workflow-designer/send-activity-designer.md)|Tworzy i konfiguruje <xref:System.ServiceModel.Activities.Send> działanie, które wysyła komunikat do usługi.|  
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|Tworzy parę wstępnie skonfigurowane <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań w ramach <xref:System.Activities.Statements.Sequence> działania.|  
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|Tworzy i konfiguruje <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania, która umożliwia przepływu transakcji w przepływie pracy.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Activities.Activity>  
  
 <xref:System.ServiceModel.Activities.CorrelationScope>  
  
 <xref:System.ServiceModel.Activities.Receive>  
  
 <xref:System.ServiceModel.Activities.Send>  
  
 <xref:System.ServiceModel.Activities.ReceiveReply>  
  
 <xref:System.ServiceModel.Activities.SendReply>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Dla innych typów projektantów działań zobacz następujące tematy.  
  
 [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)  
  
 [Używanie projektantów działań](../workflow-designer/using-the-activity-designers.md)  
  
 [Schemat blokowy](../workflow-designer/flowchart-activity-designers.md)  
  
 [Środowisko uruchomieniowe](../workflow-designer/runtime-activity-designers.md)  
  
 [Typy pierwotne](../workflow-designer/primitives-activity-designers.md)  
  
 [Transakcja](../workflow-designer/transaction-activity-designers.md)  
  
 [Kolekcja](../workflow-designer/collection-activity-designers.md)  
  
 [Obsługa błędów](../workflow-designer/error-handling-activity-designers.md)  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 [Używanie projektantów działań](../workflow-designer/using-the-activity-designers.md)