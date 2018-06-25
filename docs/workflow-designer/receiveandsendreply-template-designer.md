---
title: Projektant przepływu pracy — Projektant szablonów ReceiveAndSendReply
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: acfe9f80a5125ef13996e7cd8ec88a35cfb83211
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756389"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply, projektant szablonów

**ReceiveAndSendReply** szablon zostanie użyty do utworzenia pary wstępnie skonfigurowane <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań. Działania są częścią <xref:System.Activities.Statements.Sequence> działania i są skorelowane w ramach wymiany komunikatów żądań i odpowiedzi na serwerze.

## <a name="the-receiveandsendreply-template"></a>Szablon ReceiveAndSendReply

Dodawanie **ReceiveAndSendReply** szablonu realizuje trzy funkcje oprócz tworzenia <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań z <xref:System.Activities.Statements.Sequence> działania:

- Konfiguruje <xref:System.ServiceModel.Activities.Receive.OperationName%2A> i <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> właściwości <xref:System.ServiceModel.Activities.Receive> działania.

- Wiąże <xref:System.ServiceModel.Activities.SendReply.Request%2A> właściwość <xref:System.ServiceModel.Activities.Receive> działanie <xref:System.ServiceModel.Activities.Send> działania.

- Tworzy <xref:System.ServiceModel.Activities.CorrelationHandle> jako zmienną w działaniu nadrzędnym.

### <a name="use-the-receiveandsendreply-template-designer"></a>Używany jest Projektant szablonów ReceiveAndSendReply

Dostęp **ReceiveAndSendReply** Projektant działań w **wiadomości** kategorii **przybornika**. **ReceiveAndSendReply** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie działania są zwykle umieszczane. Projektant działań porzucenie tworzy <xref:System.ServiceModel.Activities.Receive> działanie, które można skonfigurować za pomocą **wysyłania** Projektant działań i skorelowane <xref:System.ServiceModel.Activities.SendReply> który można skonfigurować przy użyciu projektanta SendReplyToReceive.

Aby uzyskać więcej informacji o korzystaniu z **Receive** projektanta, aby skonfigurować <xref:System.ServiceModel.Activities.Receive> działania, zobacz [odbierania Projektant działań](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Właściwości SendReply

W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.SendReply> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre można edytowane na powierzchni projektanta przepływów pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalne przyjazna nazwa <xref:System.ServiceModel.Activities.SendReply> działania. Wartość domyślna to SendReplyToReceive.<br /><br /> Mimo że użycie wartości innych niż domyślne dla przyjaznych <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem, najlepiej użyć tych wartości.|
|<xref:System.ServiceModel.Activities.SendReply.Request%2A>|True|Odwołanie do <xref:System.ServiceModel.Activities.Receive> działania łączyć się z tym <xref:System.ServiceModel.Activities.SendReply> działania. Ta właściwość nie może być **null**. <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działania są używane razem na serwerze do modelu wzorzec przesyłania komunikatów żądań i odpowiedzi. Ta właściwość określa, która <xref:System.ServiceModel.Activities.Send> parę działania. W projektancie, nie można edytować tej właściwości, ponieważ jest on automatycznie powiązany z <xref:System.ServiceModel.Activities.Send> działania, z której jest tworzony <xref:System.ServiceModel.Activities.SendReply> działania.|
|<xref:System.ServiceModel.Activities.SendReply.Content%2A>|False|Określa zawartość komunikatu lub parametr do odbierania. Może być albo <xref:System.ServiceModel.Activities.ReceiveMessageContent> działania lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działania. Edytować tej właściwości, klikając przycisk wielokropka obok pola **zawartości** pole w siatce właściwości lub przez kliknięcie przycisku **Definiuj** znajdujący się obok **zawartości** etykiety na  **Odbieranie** działania powierzchnię projektanta. Wyświetl obie **definicję zawartości** okna dialogowego. Aby uzyskać więcej informacji na temat używania tego pola, zobacz [definicji zawartości, okno dialogowe](../workflow-designer/content-definition-dialog-box.md) tematu.|
|<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>|False|Określa kolekcję <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które zainicjować wielu <xref:System.ServiceModel.Activities.CorrelationHandle> obiektów, które to skonfigurować <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> właściwości siatki właściwości, aby otworzyć **dodać inicjatorów korelacji** okno dialogowe. Aby uzyskać więcej informacji na temat używania tego pola, zobacz [CorrelationInitializers okno dialogowe Dodawanie](../workflow-designer/add-correlationinitializers-dialog-box.md) tematu.|
|<xref:System.ServiceModel.Activities.SendReply.Action%2A>|False|Określa akcję nagłówek wiadomości. Jeśli nie jest jawnie ustawiona, jej domyślnie przyjmowana jest wartość:<br /><br /> **https://tempuri.org/{service Zwiń przestrzeni nazw} / {Nazwa kontraktu usługi} / {nazwa operacji}**|
|<xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>|False|Określa, czy wystąpienie przepływu pracy powinna zostać utrwalony przed wysłaniem komunikatu odpowiedzi. Wartość domyślna to **false**.|

## <a name="see-also"></a>Zobacz także

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Odbieranie](../workflow-designer/receive-activity-designer.md)
- [Wyślij](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)