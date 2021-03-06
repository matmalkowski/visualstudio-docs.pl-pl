---
title: Send, Projektant działań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 95aa5a3bd0cefae930d2eb0023b6ddd7afbe14e7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42629919"
---
# <a name="send-activity-designer"></a>Send, projektant działań
**Wysyłania** projektanta działań służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.Send> działania.  
  
## <a name="the-send-activity"></a>Działanie wysyłania  
 A <xref:System.ServiceModel.Activities.Send> działanie służy do wysyłania komunikatu do usługi. A <xref:System.ServiceModel.Activities.ReceiveReply> działanie może być powiązana z <xref:System.ServiceModel.Activities.Send> działanie, które otrzymuje komunikat w ramach wymiany komunikatów żądań/odpowiedzi na komputerze klienckim.  
  
### <a name="using-the-send-activity-designer"></a>Za pomocą projektanta działań wysyłania  
 **Wysyłania** projektanta działań można znaleźć w **komunikatów** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** karty [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać **narzędzi** z **widoku** menu lub klawiszy CTRL + ALT + X.)  
  
 **Wysyłania** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działań są zazwyczaj umieszczone. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Send> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> z wysyłania. <xref:System.Activities.Activity.DisplayName%2A> Mogą być edytowane w nagłówku **wysyłania** projektanta działań lub **DisplayName** pola siatki właściwości.  
  
 Do utworzenia <xref:System.ServiceModel.Activities.ReceiveReply> działania i powiąż go do wybranych <xref:System.ServiceModel.Activities.Send> działania, kliknij prawym przyciskiem myszy **wysyłania** działania projektanta, kliknij przycisk **tworzenie ReceiveReply** element w menu kontekstowym i **ReceiveReplyForSend** pojawi się okno projektanta poniżej **wysyłania** projektanta. <xref:System.ServiceModel.Activities.ReceiveReply> Działania to działanie, które otrzymuje komunikat w ramach wymiany komunikatów żądań/odpowiedzi na komputerze klienckim. Może być konfigurowana przy użyciu **ReceiveReplyForSend** projektanta.  
  
 Alternatywnie **SendAndReceiveReply** Projektant szablonów w **komunikatów** kategorii **przybornika** może służyć do tworzenia pary wstępnie skonfigurowane <xref:System.ServiceModel.Activities.Send>i <xref:System.ServiceModel.Activities.ReceiveReply> działań. [!INCLUDE[crabout](../includes/crabout-md.md)] Korzystanie z **SendAndReceiveReply** i **ReceiveReplyForSend** szablonów, zobacz [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) tematu.  
  
### <a name="the-send-activity-properties"></a>Właściwości działań wysyłania  
 W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.Send> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości lub na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.ServiceModel.Activities.Send> działania. Wartość domyślna to Send. Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest bezwzględnie konieczne jest najlepszym rozwiązaniem, aby użyć jednego.|  
|<xref:System.ServiceModel.Activities.Send.OperationName%2A>|True|Nazwa operacji usługi wywołane przez to <xref:System.ServiceModel.Activities.Send> działania. Ta właściwość jest używana do konstruowania wartością domyślną dla **akcji** właściwość Jeśli **akcji** właściwość nie została jawnie ustawiona.|  
|<xref:System.ServiceModel.Activities.Send.ServiceContractName%2A>|True|Nazwa kontraktu usługi, która implementuje wywoływanie usługi.|  
|<xref:System.ServiceModel.Activities.Send.Content%2A>|False|Określa zawartość komunikatu lub parametr do odbierania. Może być albo <xref:System.ServiceModel.Activities.ReceiveMessageContent> działania lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działania. Edytuj tę właściwość, klikając przycisk wielokropka obok **zawartości** w siatce właściwości lub klikając **Definiuj...** przycisk obok **zawartości** etykiety na **Receive** powierzchni projektanta działań. Wyświetl oba **definicji zawartości** okna dialogowego. [!INCLUDE[crabout](../includes/crabout-md.md)] Użyj tego pola, zobacz [definicji zawartości, okno dialogowe](../workflow-designer/content-definition-dialog-box.md) tematu.|  
|<xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A>|False|Określa <xref:System.ServiceModel.Activities.CorrelationHandle> używana do rozsyłania wiadomości dla wystąpienia przepływu pracy odpowiednie.<br /><br /> Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> właściwości siatki właściwości, aby otworzyć **edytora wyrażeń** okno dialogowe. [!INCLUDE[crabout](../includes/crabout-md.md)] Zobacz Korzystanie z tego okna dialogowego [porady: używanie edytora wyrażeń](../workflow-designer/how-to-use-the-expression-editor.md) tematu.|  
|<xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A>|False|Określa kolekcję elementów <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które zainicjować wielu <xref:System.ServiceModel.Activities.CorrelationHandle> obiektów, które to skonfigurować <xref:System.ServiceModel.Activities.Send> działania w przepływie pracy. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> właściwości siatki właściwości, aby otworzyć **Dodaj inicjatory korelacji** okno dialogowe. [!INCLUDE[crabout](../includes/crabout-md.md)] za pomocą tego pola, zobacz [Dodawanie CorrelationInitializers, okno dialogowe](../workflow-designer/add-correlationinitializers-dialog-box.md) tematu.|  
|<xref:System.ServiceModel.Activities.Send.KnownTypes%2A>|False|Kolekcja znanych typów dla operacji usługowej ma zostać wywołana przez to <xref:System.ServiceModel.Activities.Send> działania. Ta właściwość powinna być używana w połączeniu z <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> właściwością <xref:System.Runtime.Serialization.DataContractSerializer>. Jest ignorowana, jeśli <xref:System.Xml.Serialization.XmlSerializer> jest używany.<br /><br /> Kliknij przycisk wielokropka obok **element KnownTypes** w siatce właściwości do wyświetlenia **Editor typu Kolekce** okna dialogowego za pomocą którego można dodawać odpowiednie typy.<br /><br /> Kliknij przycisk wielokropka obok **element KnownTypes** w siatce właściwości do wyświetlenia **Editor typu Kolekce** okno dialogowe, za pomocą którego można dodawać odpowiednie typy. [!INCLUDE[crabout](../includes/crabout-md.md)] za pomocą tego pola, zobacz [okno dialogowe Edytor kolekcji typów](../workflow-designer/type-collection-editor-dialog-box.md) tematu.|  
|<xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A>|True|Określa <xref:System.Net.Security.ProtectionLevel> dla wiadomości.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> oznacza, że tylko uwierzytelnianie.<br />2. <xref:System.Net.Security.ProtectionLevel> oznacza, że podpisywania danych do zapewnienia integralności przesyłanych danych.<br />3. <xref:System.Net.Security.ProtectionLevel> oznacza, że szyfrowania i podpisywania danych w celu zapewnienia poufności i integralności przesyłanych danych.|  
|<xref:System.ServiceModel.Activities.Send.SerializerOption%2A>|True|Serializator do użycia dla operacji usługowej ma zostać wywołana przez <xref:System.ServiceModel.Activities.Send> działania. Wartość domyślna to <xref:System.Runtime.Serialization.DataContractSerializer>, który serializuje i deserializuje wystąpienia typu do strumień XML lub dokumentu za pomocą kontraktu danych.|  
|<xref:System.ServiceModel.Activities.Send.Action%2A>|False|Określa nagłówek akcji w wiadomości. Jeśli nie jest jawnie ustawiona wartość ustawiona wartość domyślna: https://tempuri.org/{service przestrzeni nazw kontraktu} / {Nazwa kontraktu usługi} / {nazwa operacji}. Jeśli zostanie określony na <xref:System.ServiceModel.Activities.Send> działania <xref:System.ServiceModel.Activities.Receive> działania, który odbiera wiadomości musi mieć taką samą wartość, aby uzyskać komunikat, który ma być prawidłowo dostarczane.|  
|<xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A>||<xref:System.Security.Principal.TokenImpersonationLevel> Dozwolone dla odbiorcy wiadomości. Definiuje poziomy personifikacji zabezpieczeń, które będą zarządzały sposobem stopień, w którym proces serwera mogą działać w imieniu procesu klienta.<xref:System.Security.Principal.TokenImpersonationLevel> Wskazuje, czy nie został przypisany poziom personifikacji. <xref:System.Security.Principal.TokenImpersonationLevel> Wskazuje, że proces serwera nie można uzyskać informacje identyfikacyjne dotyczące klienta, i nie może on personifikować klienta. <xref:System.Security.Principal.TokenImpersonationLevel> Wskazuje, że proces serwera można uzyskać informacje o kliencie, takich jak identyfikatory zabezpieczeń i uprawnień, ale, nie może on personifikować klienta. Jest to przydatne w przypadku serwerów, które wyeksportowanie ich własnych obiektów, na przykład produkty bazy danych, które Eksportowanie tabel i widoków. Korzystając z informacji pobrane zabezpieczeń klienta, serwer może decyzje Weryfikacja dostępu do bez możliwości korzystania z innych usług, które korzystają z klienta, kontekstu zabezpieczeń. <xref:System.Security.Principal.TokenImpersonationLevel> Wskazuje, że proces serwera może personifikować kontekst zabezpieczeń klienta w systemie lokalnym. Serwer nie może personifikować klienta w systemach zdalnych. <xref:System.Security.Principal.TokenImpersonationLevel> Wskazuje, że proces serwera może personifikować klienta kontekstu zabezpieczeń w systemach zdalnych.|  
|<xref:System.ServiceModel.Activities.Send.Endpoint%2A>||<xref:System.ServiceModel.Endpoint> , <xref:System.ServiceModel.Activities.Send> Działanie wysyła komunikat do. Jeśli ta właściwość jest ustawiona <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> właściwość powinna być **null**.|  
|<xref:System.ServiceModel.Activities.Send.EndpointAddress%2A>||<xref:System.ServiceModel.EndpointAddress> Do jest wysyłana wiadomość.|  
|<xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A>||Nazwa konfiguracji punktu końcowego. Ta właściwość jest ustawiona, podczas konfigurowania punktu końcowego w pliku konfiguracji. Ta właściwość powinna być ustawiona nazwa podana w  **\<punktu końcowego >** elementu w pliku konfiguracji. Jeśli ta właściwość jest ustawiona, <xref:System.ServiceModel.Activities.Send.Endpoint%2A> właściwość powinna być **null**.|  
  
## <a name="see-also"></a>Zobacz też  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Odbieranie](../workflow-designer/receive-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)