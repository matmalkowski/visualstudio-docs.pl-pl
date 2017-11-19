---
title: "Okno dialogowe definicji zawartości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: "3"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: fa0276e284f84eb6514fc407c9ce9be9cf24d8c4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="content-definition-dialog-box"></a>Okno dialogowe definicję zawartości
**Definicję zawartości** okno dialogowe jest używany w [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] skonfigurować **zawartości** właściwości <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply> działania. [!INCLUDE[crabout](../test/includes/crabout_md.md)]Zobacz projektantów działań, które używają tego pola [wysyłania](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), i [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) tematy.  
  
 W poniższej tabeli opisano elementy interfejsu użytkownika **inicjowania korelacji** okno dialogowe.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Komunikat**|Określa komunikat, który zawartości z **komunikatu danych** pole tekstowe wyrażenie i typu przy użyciu **typ komunikatu** pole listy rozwijanej. Domyślnie **definicję zawartości** używa <xref:System.ServiceModel.Activities.ReceiveMessageContent>, która oczekuje <xref:System.ServiceModel.Channels.Message> lub typu w definicji usługi przepływu pracy kontraktu komunikatu.|  
|**Parametry**|Kliknij przycisk **parametry** przycisk radiowy, aby użyć <xref:System.ServiceModel.Activities.ReceiveParametersContent>, która oczekuje kontraktu danych. Użyj siatki danych, aby ustawić ogólnego Kolekcja <xref:System.Activities.OutArgument> pary, których wartości są przypisane do parametrów zmiennych w przepływie pracy bieżącego klucza i wartości.|  
  
 **Definicję zawartości** okno dialogowe jest używany przez **wysyłania**, **Receive**, **ReceiveAndSendReply**, i  **SendAndReceiveReply** projektantów. Uzyskiwanie dostępu do nich jest podobnie w każdym przypadku i jest tu używany w przypadku odbierania ilustrujący procedury.  
  
 **Receive** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań są zwykle umieszczane. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Receive> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> Receive. Wybierz **Receive** Projektant działań i kliknij przycisk wielokropka obok tekstu (zawartość) dla **zawartości** właściwości w siatce właściwości **definicję zawartości**okno dialogowe okna.  
  
 Zawartość może być określone w **komunikat** sekcji <xref:System.ServiceModel.Activities.ReceiveMessageContent> działania lub w **parametru** sekcji <xref:System.ServiceModel.Activities.ReceiveParametersContent> działania.  
  
## <a name="see-also"></a>Zobacz też  
 [Pomocy interfejsu użytkownika projektanta przepływów pracy](../workflow-designer/workflow-designer-ui-help.md)