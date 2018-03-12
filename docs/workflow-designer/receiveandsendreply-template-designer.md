---
title: "Projektant szablonów ReceiveAndSendReply | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4c1236f8c3f86362ba49aa4b985dcc601a66c476
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2018
---
# <a name="receiveandsendreply-template-designer"></a>Projektant szablonów ReceiveAndSendReply

**ReceiveAndSendReply** szablon zostanie użyty do utworzenia pary wstępnie skonfigurowane <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań w ramach <xref:System.Activities.Statements.Sequence> działanie, które są skorelowane w ramach wymiany komunikatów żądań i odpowiedzi wzorzec na serwerze.

## <a name="the-receiveandsendreply-template"></a>Szablon ReceiveAndSendReply
 Dodawanie **ReceiveAndSendReply** szablonu realizuje trzy funkcje oprócz tworzenia <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań z <xref:System.Activities.Statements.Sequence> działania:

1.  Konfiguruje <xref:System.ServiceModel.Activities.Receive.OperationName%2A>, <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> właściwości <xref:System.ServiceModel.Activities.Receive> działania.

2.  Wiąże <xref:System.ServiceModel.Activities.SendReply.Request%2A> właściwość <xref:System.ServiceModel.Activities.Receive> działanie <xref:System.ServiceModel.Activities.Send> działania.

3.  Tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> jako zmienną w działaniu nadrzędnym.

### <a name="using-the-receiveandsendreply-template-designer"></a>Przy użyciu narzędzia Projektant ReceiveAndSendReply szablonu
 **ReceiveAndSendReply** Projektant działań można znaleźć w **wiadomości** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**  karcie [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)

 **ReceiveAndSendReply** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań są zwykle umieszczane. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Receive> działanie, które można skonfigurować za pomocą **wysyłania** Projektant działań i skorelowane <xref:System.ServiceModel.Activities.SendReply> który można skonfigurować przy użyciu projektanta SendReplyToReceive.

 Aby uzyskać więcej informacji o korzystaniu z **Receive** projektanta, aby skonfigurować <xref:System.ServiceModel.Activities.Receive> działania, zobacz [Receive](../workflow-designer/receive-activity-designer.md) tematu.

 Aby uzyskać więcej informacji o korzystaniu z **SendReplyToReceive** projektanta, aby skonfigurować <xref:System.ServiceModel.Activities.SendReply> działania, zobacz następującą sekcję.

### <a name="properties-of-sendreply"></a>Właściwości SendReply
 W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.SendReply> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości i niektóre mogą być edytowane [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchnię projektanta.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalne przyjazna nazwa <xref:System.ServiceModel.Activities.SendReply> działania. Wartość domyślna to SendReplyToReceive.<br /><br /> Mimo że użycie wartości innych niż domyślne dla przyjaznych <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem, aby użyć tych wartości.|
|<xref:System.ServiceModel.Activities.SendReply.Request%2A>|True|Odwołanie do <xref:System.ServiceModel.Activities.Receive> działania łączyć się z tym <xref:System.ServiceModel.Activities.SendReply> działania. Ta właściwość nie może być **null**. <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działania są używane razem na serwerze do modelu wzorzec przesyłania komunikatów żądań i odpowiedzi. Ta właściwość określa, która <xref:System.ServiceModel.Activities.Send> parę działania. W projektancie, nie można edytować tej właściwości, ponieważ jest on automatycznie powiązany z <xref:System.ServiceModel.Activities.Send> działania, z której jest tworzony <xref:System.ServiceModel.Activities.SendReply> działania.|
|<xref:System.ServiceModel.Activities.SendReply.Content%2A>|False|Określa zawartość komunikatu lub parametr do odbierania. Może być albo <xref:System.ServiceModel.Activities.ReceiveMessageContent> działania lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działania. Edytowanie tej właściwości, klikając przycisk wielokropka obok **zawartości** w siatce właściwości lub klikając **Definiuj...**  przycisk obok **zawartości** etykiety na **Receive** działania powierzchnię projektanta. Wyświetl obie **definicję zawartości** okna dialogowego. Aby uzyskać więcej informacji na temat używania tego pola, zobacz [definicji zawartości, okno dialogowe](../workflow-designer/content-definition-dialog-box.md) tematu.|
|<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>|False|Określa kolekcję <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które zainicjować wielu <xref:System.ServiceModel.Activities.CorrelationHandle> obiektów, które to skonfigurować <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> właściwości siatki właściwości, aby otworzyć **dodać inicjatorów korelacji** okno dialogowe. Aby uzyskać więcej informacji na temat używania tego pola, zobacz [CorrelationInitializers okno dialogowe Dodawanie](../workflow-designer/add-correlationinitializers-dialog-box.md) tematu.|
|<xref:System.ServiceModel.Activities.SendReply.Action%2A>|False|Określa akcję nagłówek wiadomości. Jeśli nie jest jawnie ustawiona wartość domyślnie:<br /><br /> **https://tempuri.org/ {przestrzeń nazw kontraktu usługi} / {Nazwa kontraktu usługi} / {nazwa operacji}**|
|<xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>|False|Określa, czy wystąpienie przepływu pracy powinna zostać utrwalony przed wysłaniem komunikatu odpowiedzi. Wartość domyślna to **false**.|

## <a name="see-also"></a>Zobacz także

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Odbieranie](../workflow-designer/receive-activity-designer.md)
- [Wyślij](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)