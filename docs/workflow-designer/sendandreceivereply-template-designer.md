---
title: Projektant przepływu pracy — Projektant szablonów SendAndReceiveReply
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c6a4749ed138b22ac3d600befad01ef1776478e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976269"
---
# <a name="sendandreceivereply-template-designer"></a>Projektant szablonów SendAndReceiveReply

**SendAndReceiveReply** szablon zostanie użyty do utworzenia pary wstępnie skonfigurowane <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań w ramach <xref:System.Activities.Statements.Sequence> działanie, które są skorelowane w ramach wymiany komunikatów żądań i odpowiedzi wzorzec na kliencie.

## <a name="the-sendandreceivereply-template"></a>Szablon SendAndReceiveReply

Dodawanie **SendAndReceiveReply** szablonu realizuje trzy funkcje oprócz tworzenia <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań w ramach <xref:System.Activities.Statements.Sequence> działania:

1.  Konfiguruje <xref:System.ServiceModel.Activities.Send.OperationName%2A>, <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> właściwości <xref:System.ServiceModel.Activities.Send> działania.

2.  Wiąże <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> właściwość <xref:System.ServiceModel.Activities.ReceiveReply> działanie <xref:System.ServiceModel.Activities.Send> działania.

3.  Tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> jako zmienną w działaniu nadrzędnym.

### <a name="using-the-sendandreceivereply-template-designer"></a>Przy użyciu narzędzia Projektant SendAndReceiveReply szablonu
 **SendAndReceiveReply** Projektant działań można znaleźć w **wiadomości** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**  karty w Projektancie przepływów pracy (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)

 **SendAndReceiveReply** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie działania są zwykle umieszczane. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Send> działanie, które można skonfigurować za pomocą **wysyłania** Projektant działań i skorelowane <xref:System.ServiceModel.Activities.ReceiveReply> które można skonfigurować za pomocą **ReceiveReplyForSend** projektanta.

 Aby uzyskać więcej informacji o korzystaniu z **wysyłania** projektanta, aby skonfigurować <xref:System.ServiceModel.Activities.Send> działania, zobacz [wysyłania](../workflow-designer/send-activity-designer.md) tematu.

 Aby uzyskać więcej informacji o korzystaniu z **ReceiveReplyForSend** projektanta, aby skonfigurować <xref:System.ServiceModel.Activities.ReceiveReply> działania, zobacz następującą sekcję.

### <a name="properties-of-receivereply"></a>Właściwości ReceiveReply
 W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.ReceiveReply> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości i niektóre mogą być edytowane na powierzchni Designerdesigner przepływu pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalne przyjazna nazwa <xref:System.ServiceModel.Activities.ReceiveReply> działania. Wartość domyślna to ReceiveReplyForSend.<br /><br /> Mimo że użycie wartości innych niż domyślne dla przyjaznych <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem, aby użyć tych wartości.|
|<xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>|True|Odwołanie do <xref:System.ServiceModel.Activities.Send> działania łączyć się z tym <xref:System.ServiceModel.Activities.ReceiveReply> działania. Ta właściwość nie może być **null**. <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działania są używane razem na kliencie do modelu wzorzec przesyłania komunikatów żądań i odpowiedzi. Ta właściwość określa, która <xref:System.ServiceModel.Activities.Send> parę działania. W projektancie, nie można edytować tej właściwości, ponieważ jest on automatycznie powiązany z <xref:System.ServiceModel.Activities.Send> działania, z której jest tworzony <xref:System.ServiceModel.Activities.ReceiveReply> działania.|
|<xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>|False|Określa zawartość komunikatu lub parametr do odbierania. Może być albo <xref:System.ServiceModel.Activities.ReceiveMessageContent> działania lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działania. Edytowanie tej właściwości, klikając przycisk wielokropka obok **zawartości** w siatce właściwości lub klikając **Definiuj...**  przycisk obok **zawartości** etykiety na **Receive** działania powierzchnię projektanta. Wyświetl obie **definicję zawartości** okna dialogowego. Aby uzyskać więcej informacji na temat używania tego pola, zobacz [definicji zawartości, okno dialogowe](../workflow-designer/content-definition-dialog-box.md) tematu.|
|<xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A>|False|Określa kolekcję <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które zainicjować wielu <xref:System.ServiceModel.Activities.CorrelationHandle> obiektów, które to skonfigurować <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> właściwości siatki właściwości, aby otworzyć **dodać inicjatorów korelacji** okno dialogowe. Aby uzyskać więcej informacji na temat używania tego pola, zobacz [CorrelationInitializers okno dialogowe Dodawanie](../workflow-designer/add-correlationinitializers-dialog-box.md) tematu.|
|<xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>|False|Określa akcję nagłówek wiadomości. Jeśli nie jest jawnie ustawiona wartość domyślnie:<br /><br /> **https://tempuri.org/{service Zwiń przestrzeni nazw} / {Nazwa kontraktu usługi} / {nazwa operacji}.**|

## <a name="see-also"></a>Zobacz także

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Odbieranie](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Wyślij](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)