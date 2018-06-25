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
ms.openlocfilehash: 282ba94c026b885cb6f8250b33beb98616376e8d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755814"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply, projektant szablonów

**SendAndReceiveReply** szablon zostanie użyty do utworzenia pary wstępnie skonfigurowane <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań. Działania są częścią <xref:System.Activities.Statements.Sequence> działania i są skorelowane w ramach wymiany komunikatów żądań i odpowiedzi na kliencie.

## <a name="the-sendandreceivereply-template"></a>Szablon SendAndReceiveReply

Dodawanie **SendAndReceiveReply** szablonu realizuje trzy funkcje oprócz tworzenia <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań w ramach <xref:System.Activities.Statements.Sequence> działania:

- Konfiguruje <xref:System.ServiceModel.Activities.Send.OperationName%2A> i <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> właściwości <xref:System.ServiceModel.Activities.Send> działania.

- Wiąże <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> właściwość <xref:System.ServiceModel.Activities.ReceiveReply> działanie <xref:System.ServiceModel.Activities.Send> działania.

- Tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> jako zmienną w działaniu nadrzędnym.

### <a name="use-the-sendandreceivereply-template-designer"></a>Używany jest Projektant szablonów SendAndReceiveReply

Dostęp **SendAndReceiveReply** Projektant działań w **wiadomości** kategorii **przybornika**. **SendAndReceiveReply** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie działania są zwykle umieszczane. Projektant działań porzucenie tworzy <xref:System.ServiceModel.Activities.Send> działanie, które można skonfigurować za pomocą **wysyłania** Projektant działań i skorelowane <xref:System.ServiceModel.Activities.ReceiveReply> które można skonfigurować za pomocą **ReceiveReplyForSend** projektanta.

Aby uzyskać więcej informacji o korzystaniu z **wysyłania** projektanta, aby skonfigurować <xref:System.ServiceModel.Activities.Send> działania, zobacz [wysyłania](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Właściwości ReceiveReply

W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.ReceiveReply> właściwości i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre można edytowane na powierzchni projektanta przepływów pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalne przyjazna nazwa <xref:System.ServiceModel.Activities.ReceiveReply> działania. Wartość domyślna to ReceiveReplyForSend.<br /><br /> Mimo że użycie wartości innych niż domyślne dla przyjaznych <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem, najlepiej użyć tych wartości.|
|<xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>|True|Odwołanie do <xref:System.ServiceModel.Activities.Send> działania łączyć się z tym <xref:System.ServiceModel.Activities.ReceiveReply> działania. Ta właściwość nie może być **null**. <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działania są używane razem na kliencie do modelu wzorzec przesyłania komunikatów żądań i odpowiedzi. Ta właściwość określa, która <xref:System.ServiceModel.Activities.Send> parę działania. W projektancie, nie można edytować tej właściwości, ponieważ jest on automatycznie powiązany z <xref:System.ServiceModel.Activities.Send> działania, z której jest tworzony <xref:System.ServiceModel.Activities.ReceiveReply> działania.|
|<xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>|False|Określa zawartość komunikatu lub parametr do odbierania. Może być albo <xref:System.ServiceModel.Activities.ReceiveMessageContent> działania lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działania. Edytować tej właściwości, klikając przycisk wielokropka obok pola **zawartości** pole w siatce właściwości lub przez kliknięcie przycisku **Definiuj** znajdujący się obok **zawartości** etykiety na **Receive** działania powierzchnię projektanta. Wyświetl obie **definicję zawartości** okna dialogowego. Aby uzyskać więcej informacji na temat używania tego pola, zobacz [definicji zawartości, okno dialogowe](../workflow-designer/content-definition-dialog-box.md).|
|<xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A>|False|Określa kolekcję <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które zainicjować wielu <xref:System.ServiceModel.Activities.CorrelationHandle> obiektów, które to skonfigurować <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> właściwości siatki właściwości, aby otworzyć **dodać inicjatorów korelacji** okno dialogowe. Aby uzyskać więcej informacji na temat używania tego pola, zobacz [CorrelationInitializers okno dialogowe Dodawanie](../workflow-designer/add-correlationinitializers-dialog-box.md).|
|<xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>|False|Określa akcję nagłówek wiadomości. Jeśli nie jest jawnie ustawiona, jej domyślnie przyjmowana jest wartość:<br /><br /> **https://tempuri.org/{service Zwiń przestrzeni nazw} / {Nazwa kontraktu usługi} / {nazwa operacji}.**|

## <a name="see-also"></a>Zobacz także

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Odbieranie](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Wyślij](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)