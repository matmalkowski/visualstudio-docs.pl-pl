---
title: "Wyślij Projektant działań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 6b3e4d7b00691d7ea2c86a81d0d2880b9f7366bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="send-activity-designer"></a>Projektant działań wysyłania
**Wysyłania** Projektant działań służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.Send> działania.  
  
## <a name="the-send-activity"></a>Działanie wysyłania  
 A <xref:System.ServiceModel.Activities.Send> to działanie służy do wysyłania komunikatu do usługi. A <xref:System.ServiceModel.Activities.ReceiveReply> działania może być powiązana z <xref:System.ServiceModel.Activities.Send> działania, który odbiera wiadomości w ramach wymiany komunikatów żądań i odpowiedzi na kliencie.  
  
### <a name="using-the-send-activity-designer"></a>Przy użyciu narzędzia Projektant działań wysyłania  
 **Wysyłania** Projektant działań można znaleźć w **wiadomości** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** Karta w [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)  
  
 **Wysyłania** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań są zwykle umieszczane. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Send> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z wysyłania. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **wysyłania** Projektant działań lub **DisplayName** pola siatki właściwości.  
  
 Można utworzyć <xref:System.ServiceModel.Activities.ReceiveReply> działania i powiązać ją z wybranym <xref:System.ServiceModel.Activities.Send> działania, kliknij prawym przyciskiem myszy **wysyłania** działania projektanta, kliknij przycisk **utworzyć ReceiveReply** elementu w menu kontekstowym i **ReceiveReplyForSend** projektanta pojawia się poniżej **wysyłania** projektanta. <xref:System.ServiceModel.Activities.ReceiveReply> Działania jest działaniem, który odbiera wiadomości w ramach wymiany komunikatów żądań i odpowiedzi na kliencie. Mogą być skonfigurowane przy użyciu **ReceiveReplyForSend** projektanta.  
  
 Alternatywnie **SendAndReceiveReply** Projektant szablonów w **wiadomości** kategorii **przybornika** można utworzyć pary wstępnie skonfigurowane <xref:System.ServiceModel.Activities.Send>i <xref:System.ServiceModel.Activities.ReceiveReply> działań. [!INCLUDE[crabout](../test/includes/crabout_md.md)]Korzystanie z **SendAndReceiveReply** i **ReceiveReplyForSend** szablony, zobacz [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) tematu.  
  
### <a name="the-send-activity-properties"></a>Właściwości działania wysyłania  
 W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.Send> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości lub na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.ServiceModel.Activities.Send> działania. Wartość domyślna to Send. Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem jej użyć.|  
|<xref:System.ServiceModel.Activities.Send.OperationName%2A>|Wartość true|Nazwa operacji usługi o nazwie to <xref:System.ServiceModel.Activities.Send> działania. Ta właściwość jest używana do konstruowania wartością domyślną dla **akcji** właściwości Jeśli **akcji** właściwość nie jest jawnie ustawiona.|  
|<xref:System.ServiceModel.Activities.Send.ServiceContractName%2A>|Wartość true|Nazwa kontraktu usługi, który implementuje wywoływanie usługi.|  
|<xref:System.ServiceModel.Activities.Send.Content%2A>|False|Określa zawartość komunikatu lub parametr do odbierania. Może być albo <xref:System.ServiceModel.Activities.ReceiveMessageContent> działania lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działania. Edytowanie tej właściwości, klikając przycisk wielokropka obok **zawartości** w siatce właściwości lub klikając **Definiuj...**  przycisk obok **zawartości** etykiety na **Receive** działania powierzchnię projektanta. Wyświetl obie **definicję zawartości** okna dialogowego. [!INCLUDE[crabout](../test/includes/crabout_md.md)]Użyj tego pola, zobacz [definicji zawartości, okno dialogowe](../workflow-designer/content-definition-dialog-box.md) tematu.|  
|<xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A>|False|Określa <xref:System.ServiceModel.Activities.CorrelationHandle> używana do kierowania wiadomości z wystąpieniem przepływu pracy odpowiednie.<br /><br /> Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> właściwości siatki właściwości, aby otworzyć **edytora wyrażeń** okno dialogowe. [!INCLUDE[crabout](../test/includes/crabout_md.md)]Korzystanie z tego okna dialogowego, zobacz [porady: używanie edytora wyrażeń](../workflow-designer/how-to-use-the-expression-editor.md) tematu.|  
|<xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A>|False|Określa kolekcję <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które zainicjować wielu <xref:System.ServiceModel.Activities.CorrelationHandle> obiektów, które to skonfigurować <xref:System.ServiceModel.Activities.Send> działania w przepływie pracy. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> właściwości siatki właściwości, aby otworzyć **dodać inicjatorów korelacji** okno dialogowe. [!INCLUDE[crabout](../test/includes/crabout_md.md)]przy użyciu tego pola, zobacz [CorrelationInitializers okno dialogowe Dodawanie](../workflow-designer/add-correlationinitializers-dialog-box.md) tematu.|  
|<xref:System.ServiceModel.Activities.Send.KnownTypes%2A>|False|Kolekcji znanych typów dla operacji usługi ma zostać wywołana przez to <xref:System.ServiceModel.Activities.Send> działania. Tej właściwości należy użyć w połączeniu z <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> ustawioną właściwość <xref:System.Runtime.Serialization.DataContractSerializer>. Jest ignorowana, jeśli <xref:System.Xml.Serialization.XmlSerializer> jest używany.<br /><br /> Kliknij przycisk wielokropka obok **element KnownTypes** w siatce właściwości do wyświetlenia **edytora kolekcji typu** okna dialogowego, z którym można dodać odpowiednie typy.<br /><br /> Kliknij przycisk wielokropka obok **element KnownTypes** w siatce właściwości do wyświetlenia **edytora kolekcji typu** okno dialogowe, z którym można dodać odpowiednie typy. [!INCLUDE[crabout](../test/includes/crabout_md.md)]przy użyciu tego pola, zobacz [okno dialogowe Edytor kolekcji typu](../workflow-designer/type-collection-editor-dialog-box.md) tematu.|  
|<xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A>|Wartość true|Określa <xref:System.Net.Security.ProtectionLevel> dla wiadomości.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> oznacza tylko uwierzytelnianie.<br />2. <xref:System.Net.Security.ProtectionLevel> oznacza podpisywania danych do zapewnienia integralności danych przesyłanych.<br />3. <xref:System.Net.Security.ProtectionLevel> oznacza szyfrowania i podpisywania danych, aby zapewnić poufności i integralności danych przesyłanych.|  
|<xref:System.ServiceModel.Activities.Send.SerializerOption%2A>|Wartość true|Serializator do użycia dla operacji usługi ma zostać wywołana przez <xref:System.ServiceModel.Activities.Send> działania. Wartość domyślna to <xref:System.Runtime.Serialization.DataContractSerializer>, który serializuje i deserializuje wystąpienia typu w strumieniu XML lub dokument za pomocą kontraktu danych.|  
|<xref:System.ServiceModel.Activities.Send.Action%2A>|False|Określa akcję nagłówek wiadomości. Jeśli nie jest jawnie ustawiona wartość domyślnie: https://tempuri.org/ {przestrzeń nazw kontraktu usługi} / {Nazwa kontraktu usługi} / {nazwa operacji}. Jeśli zostanie określony na <xref:System.ServiceModel.Activities.Send> działania, <xref:System.ServiceModel.Activities.Receive> działania, który odbiera wiadomości musi mieć taką samą wartość komunikat, który ma być prawidłowo dostarczane.|  
|<xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A>||<xref:System.Security.Principal.TokenImpersonationLevel> Dozwolone dla odbiorcy wiadomości. Definiuje poziomy personifikacji zabezpieczeń, które będą zarządzały sposobem stopnia, do którego proces serwera mogą działać w imieniu procesu klienta. <xref:System.Security.Principal.TokenImpersonationLevel> wskazuje, że poziom personifikacji nie jest przypisany. <xref:System.Security.Principal.TokenImpersonationLevel>Wskazuje, że proces serwera nie można uzyskać informacje umożliwiające identyfikację klienta i nie można spersonifikować klienta. <xref:System.Security.Principal.TokenImpersonationLevel>Wskazuje, że proces serwera można uzyskać informacji o kliencie, takie jak identyfikatory zabezpieczeń i uprawnienia, ale że nie można personifikować klienta. Jest to przydatne w przypadku serwerów, które wyeksportować własne obiektów, na przykład produkty bazy danych, które wyeksportować tabel i widoków. Korzystając z informacji pobrane zabezpieczeń klienta, serwera podjęcie decyzji dotyczących sprawdzania poprawności dostępu bez możliwości korzystania z innych usług, które korzystają z kontekstu zabezpieczeń klienta. <xref:System.Security.Principal.TokenImpersonationLevel>Wskazuje, że proces serwera może personifikować klienta kontekstu zabezpieczeń w systemie lokalnym. Serwer nie może spersonifikować klienta zdalnego w systemach. <xref:System.Security.Principal.TokenImpersonationLevel>Wskazuje, że proces serwera może personifikować klienta kontekstu zabezpieczeń w systemach zdalnych.|  
|<xref:System.ServiceModel.Activities.Send.Endpoint%2A>||<xref:System.ServiceModel.Endpoint> Który <xref:System.ServiceModel.Activities.Send> działanie wysyła komunikat do. Jeśli ta właściwość jest ustawiona <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> właściwość powinna być **null**.|  
|<xref:System.ServiceModel.Activities.Send.EndpointAddress%2A>||<xref:System.ServiceModel.EndpointAddress> Jest wysłanie wiadomości.|  
|<xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A>||Nazwa konfiguracji punktu końcowego. Ta właściwość jest ustawiana podczas konfigurowania punktu końcowego w pliku konfiguracji. Ta właściwość powinna być równa nazwy podanej w  **\<punktu końcowego >** elementu w pliku konfiguracji. Jeśli ta właściwość jest ustawiona, <xref:System.ServiceModel.Activities.Send.Endpoint%2A> właściwość powinna być **null**.|  
  
## <a name="see-also"></a>Zobacz też  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Odbieranie](../workflow-designer/receive-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)