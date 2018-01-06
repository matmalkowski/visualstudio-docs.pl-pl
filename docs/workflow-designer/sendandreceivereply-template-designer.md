---
title: "Projektant szablonów SendAndReceiveReply | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 314ff5252b426610b9a50327fe6754b2a953908c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sendandreceivereply-template-designer"></a>Projektant szablonów SendAndReceiveReply
**SendAndReceiveReply** szablon zostanie użyty do utworzenia pary wstępnie skonfigurowane <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań w ramach <xref:System.Activities.Statements.Sequence> działanie, które są skorelowane w ramach wymiany komunikatów żądań i odpowiedzi wzorzec na kliencie.  
  
## <a name="the-sendandreceivereply-template"></a>Szablon SendAndReceiveReply  
 Dodawanie **SendAndReceiveReply** szablonu realizuje trzy funkcje oprócz tworzenia <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań w ramach <xref:System.Activities.Statements.Sequence> działania:  
  
1.  Konfiguruje <xref:System.ServiceModel.Activities.Send.OperationName%2A>, <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> właściwości <xref:System.ServiceModel.Activities.Send> działania.  
  
2.  Wiąże <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> właściwość <xref:System.ServiceModel.Activities.ReceiveReply> działanie <xref:System.ServiceModel.Activities.Send> działania.  
  
3.  Tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> jako zmienną w działaniu nadrzędnym.  
  
### <a name="using-the-sendandreceivereply-template-designer"></a>Przy użyciu narzędzia Projektant SendAndReceiveReply szablonu  
 **SendAndReceiveReply** Projektant działań można znaleźć w **wiadomości** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**  karcie na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)  
  
 **SendAndReceiveReply** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań są zwykle umieszczane. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Send> działanie, które można skonfigurować za pomocą **wysyłania** Projektant działań i skorelowane <xref:System.ServiceModel.Activities.ReceiveReply> które można skonfigurować za pomocą **ReceiveReplyForSend** projektanta.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]przy użyciu **wysyłania** projektanta, aby skonfigurować <xref:System.ServiceModel.Activities.Send> działania, zobacz [wysyłania](../workflow-designer/send-activity-designer.md) tematu.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]przy użyciu **ReceiveReplyForSend** projektanta, aby skonfigurować <xref:System.ServiceModel.Activities.ReceiveReply> działania, zobacz następującą sekcję.  
  
### <a name="properties-of-receivereply"></a>Właściwości ReceiveReply  
 W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.ReceiveReply> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości i niektóre mogą być edytowane [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]powierzchnię projektanta.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalne przyjazna nazwa <xref:System.ServiceModel.Activities.ReceiveReply> działania. Wartość domyślna to ReceiveReplyForSend.<br /><br /> Mimo że użycie wartości innych niż domyślne dla przyjaznych <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem, aby użyć tych wartości.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>|Wartość true|Odwołanie do <xref:System.ServiceModel.Activities.Send> działania łączyć się z tym <xref:System.ServiceModel.Activities.ReceiveReply> działania. Ta właściwość nie może być **null**. <xref:System.ServiceModel.Activities.Send>i <xref:System.ServiceModel.Activities.ReceiveReply> działania są używane razem na kliencie do modelu wzorzec przesyłania komunikatów żądań i odpowiedzi. Ta właściwość określa, która <xref:System.ServiceModel.Activities.Send> parę działania. W projektancie, nie można edytować tej właściwości, ponieważ jest on automatycznie powiązany z <xref:System.ServiceModel.Activities.Send> działania, z której jest tworzony <xref:System.ServiceModel.Activities.ReceiveReply> działania.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>|False|Określa zawartość komunikatu lub parametr do odbierania. Może być albo <xref:System.ServiceModel.Activities.ReceiveMessageContent> działania lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działania. Edytowanie tej właściwości, klikając przycisk wielokropka obok **zawartości** w siatce właściwości lub klikając **Definiuj...**  przycisk obok **zawartości** etykiety na **Receive** działania powierzchnię projektanta. Wyświetl obie **definicję zawartości** okna dialogowego. [!INCLUDE[crabout](../test/includes/crabout_md.md)]Użyj tego pola, zobacz [definicji zawartości, okno dialogowe](../workflow-designer/content-definition-dialog-box.md) tematu.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A>|False|Określa kolekcję <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które zainicjować wielu <xref:System.ServiceModel.Activities.CorrelationHandle> obiektów, które to skonfigurować <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> właściwości siatki właściwości, aby otworzyć **dodać inicjatorów korelacji** okno dialogowe. [!INCLUDE[crabout](../test/includes/crabout_md.md)]przy użyciu tego pola, zobacz [CorrelationInitializers okno dialogowe Dodawanie](../workflow-designer/add-correlationinitializers-dialog-box.md) tematu.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>|False|Określa akcję nagłówek wiadomości. Jeśli nie jest jawnie ustawiona wartość domyślnie:<br /><br /> **https://tempuri.org/ {przestrzeń nazw kontraktu usługi} / {Nazwa kontraktu usługi} / {nazwa operacji}.**|  
  
## <a name="see-also"></a>Zobacz też  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Odbieranie](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Wyślij](../workflow-designer/send-activity-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)