---
title: "Projektant działań odbierania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 7c02cf726cbf575eae9c389186846855ee1206c4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="receive-activity-designer"></a>Odbieranie Projektant działań
**Receive** Projektant działań służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.Receive> działania. A <xref:System.ServiceModel.Activities.Receive> działania jest działaniem, który odbiera komunikat, który może być wbudowany typ takich jak <xref:System.ServiceModel.Channels.Message>, <xref:System.IO.Stream> lub <xref:System.Xml.Linq.XElement>, lub kontrakt danych zdefiniowanym przez aplikację, kontraktu komunikatu lub klasy XML, który można serializować.  
  
## <a name="the-receive-activity"></a>Działanie odbierania  
 <xref:System.ServiceModel.Activities.Receive> Działania mogą odbierać pojedynczy element lub wielu elementów w zależności od typu odbierać zawartość używane. A <xref:System.ServiceModel.Activities.SendReply> działania może być powiązana z <xref:System.ServiceModel.Activities.Receive> działania, który odbiera wiadomości w ramach wymiany komunikatów żądań i odpowiedzi w usłudze.  
  
### <a name="using-the-receive-activity-designer"></a>Przy użyciu odbierania Projektant działań  
 **Receive** Projektant działań można znaleźć w **wiadomości** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karcie na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)  
  
 **Receive** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań są zwykle umieszczane. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Receive> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> Receive. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **Receive** Projektant działań lub **DisplayName** pola siatki właściwości.  
  
 Można utworzyć <xref:System.ServiceModel.Activities.SendReply> działania i powiązać ją z wybranym <xref:System.ServiceModel.Activities.Receive> działania, kliknij prawym przyciskiem myszy **Receive** działania projektanta, kliknij przycisk **utworzyć SendReply** elementu w menu kontekstowym i **SendReplyToReceive** projektanta pojawia się poniżej **Receive** projektanta. <xref:System.ServiceModel.Activities.SendReply> Działania jest działanie powodujące wysłanie komunikatu odpowiedzi w ramach wymiany komunikatów żądań i odpowiedzi usługi. Mogą być skonfigurowane przy użyciu **SendReplyToReceive** projektanta.  
  
 Alternatywnie **ReceiveAndSendReply** Projektant szablonów w **wiadomości** kategorii **przybornika** można utworzyć pary wstępnie skonfigurowane <xref:System.ServiceModel.Activities.Receive>i <xref:System.ServiceModel.Activities.SendReply> działania. [!INCLUDE[crabout](../test/includes/crabout_md.md)]Korzystanie z **ReceiveAndSendReply** i **SendReplyToReceive** szablonu, zobacz [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) tematu.  
  
### <a name="the-receive-activity-properties"></a>Właściwości działania odbierania  
 W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.Receive> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości lub na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni. Jest wymagana tylko właściwość <xref:System.ServiceModel.Activities.Receive.OperationName%2A> właściwości.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.ServiceModel.Activities.Receive> działania. Wartość domyślna to Receive.<br /><br /> Mimo że użycie wartości innych niż domyślne dla przyjaznych <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem, aby użyć tych wartości.|  
|<xref:System.ServiceModel.Activities.Receive.OperationName%2A>|Wartość true|Określa nazwę operacji usługi implementowanych przez ten <xref:System.ServiceModel.Activities.Receive> działania. Ta właściwość jest używana do konstruowania wartością domyślną dla **akcji** właściwości Jeśli **akcji** właściwość nie jest jawnie ustawiona.|  
|<xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>|False|Określa nazwę kontraktu usługi. Ta właściwość jest używana do grupy operacji usługi pojedynczej usługi umowy. Wszystkie <xref:System.ServiceModel.Activities.Receive> działań, które mają taki sam <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> są zgrupowane w ten sam kontrakt usługi (typ portu WSDL). Wartość domyślna to w pełni kwalifikowaną nazwą CLR działania najwyższego poziomu (root).|  
|<xref:System.ServiceModel.Activities.Receive.Content%2A>|False|Określa zawartość komunikatu lub parametr do odbierania. Może być albo <xref:System.ServiceModel.Activities.ReceiveMessageContent> działania lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działania. Edytowanie tej właściwości, klikając przycisk wielokropka obok **zawartości** w siatce właściwości lub klikając **Definiuj...**  przycisk obok **zawartości** etykiety na **Receive** działania powierzchnię projektanta. Wyświetl obie **definicję zawartości** okna dialogowego. [!INCLUDE[crabout](../test/includes/crabout_md.md)]Użyj tego pola, zobacz [definicji zawartości, okno dialogowe](../workflow-designer/content-definition-dialog-box.md) tematu.|  
|<xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>|False|Określa korelacji między <xref:System.ServiceModel.Activities.Receive> działania w operacji usługi przepływu pracy z <xref:System.ServiceModel.MessageQuerySet> obiektu. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> właściwości siatki właściwości, aby otworzyć **definicji CorrelatesOn** okno dialogowe. [!INCLUDE[crabout](../test/includes/crabout_md.md)]Korzystanie z tego okna dialogowego, zobacz [definicji zawartości, okno dialogowe](../workflow-designer/content-definition-dialog-box.md) tematu.|  
|<xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A>|False|Określa <xref:System.ServiceModel.Activities.CorrelationHandle> używana do kierowania wiadomości z wystąpieniem przepływu pracy odpowiednie.<br /><br /> Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> właściwości siatki właściwości, aby otworzyć **edytora wyrażeń** okno dialogowe. [!INCLUDE[crabout](../test/includes/crabout_md.md)]Korzystanie z tego okna dialogowego, zobacz [porady: używanie edytora wyrażeń](../workflow-designer/how-to-use-the-expression-editor.md) tematu.|  
|<xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>|False|Określa kolekcję <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które zainicjować wielu <xref:System.ServiceModel.Activities.CorrelationHandle> obiektów, które to skonfigurować <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> właściwości siatki właściwości, aby otworzyć **dodać inicjatorów korelacji** okno dialogowe. [!INCLUDE[crabout](../test/includes/crabout_md.md)]przy użyciu tego pola, zobacz [CorrelationInitializers okno dialogowe Dodawanie](../workflow-designer/add-correlationinitializers-dialog-box.md) tematu.|  
|<xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A>|False|Określa wartość, która określa, czy nowe wystąpienie przepływu pracy jest tworzony przetworzyć komunikatu, jeśli komunikat nie jest skorelowany z istniejącym wystąpieniem przepływu pracy. Jeśli wartość jest równa **true**, nowe wystąpienie przepływu pracy jest tworzony przetworzyć komunikatu, gdy komunikat nie jest skorelowany z istniejącym wystąpieniem przepływu pracy.|  
|<xref:System.ServiceModel.Activities.Receive.KnownTypes%2A>|False|Określa zbiór znanych typów dla operacji usługi implementowanych przez ten <xref:System.ServiceModel.Activities.Receive> działania. Tej właściwości należy użyć w połączeniu z <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> ustawioną właściwość <xref:System.Runtime.Serialization.DataContractSerializer>. Jest ignorowana, jeśli <xref:System.Xml.Serialization.XmlSerializer> jest używany.<br /><br /> Kliknij przycisk wielokropka obok **element KnownTypes** w siatce właściwości do wyświetlenia **edytora kolekcji typu** okno dialogowe, z którym można dodać odpowiednie typy. [!INCLUDE[crabout](../test/includes/crabout_md.md)]przy użyciu tego pola, zobacz [okno dialogowe Edytor kolekcji typu](../workflow-designer/type-collection-editor-dialog-box.md) tematu.|  
|<xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A>|False|Określa <xref:System.Net.Security.ProtectionLevel> dla wiadomości.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> oznacza tylko uwierzytelnianie.<br />2. <xref:System.Net.Security.ProtectionLevel> oznacza podpisywania danych do zapewnienia integralności danych przesyłanych.<br />3. <xref:System.Net.Security.ProtectionLevel> oznacza szyfrowania i podpisywania danych, aby zapewnić poufności i integralności danych przesyłanych.|  
|<xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>|False|Określa typ serializatora do użycia dla operacji usługi implementowane przez <xref:System.ServiceModel.Activities.Receive> działania. Wartość domyślna to <xref:System.Runtime.Serialization.DataContractSerializer>, który serializuje i deserializuje wystąpienia typu w strumieniu XML lub dokument, który używa kontraktu danych. <xref:System.Xml.Serialization.XmlSerializer> Można także jeśli większą kontrolę jest wymagane przez kod XML.|  
|<xref:System.ServiceModel.Activities.Receive.Action%2A>|False|Określa akcję nagłówek wiadomości. Jeśli nie jest jawnie ustawiona wartość domyślnie: https://tempuri.org/ {przestrzeń nazw kontraktu usługi} / {Nazwa kontraktu usługi} / {nazwa operacji}.|  
  
## <a name="see-also"></a>Zobacz też  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Wyślij](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)