---
title: Okno dialogowe definicji zawartości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: c1ef7dfa925f0f658edb981725d2a5dd8847412b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42630172"
---
# <a name="content-definition-dialog-box"></a>Definicja zawartości, okno dialogowe
**Definicji zawartości** okno dialogowe jest używany w [!INCLUDE[wfd1](../includes/wfd1-md.md)] skonfigurować **zawartości** właściwości <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply> działania. [!INCLUDE[crabout](../includes/crabout-md.md)] Projektanci działań, które używają tego pola, zobacz [wysyłania](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), i [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) tematów.  
  
 W poniższej tabeli opisano elementy interfejsu użytkownika **inicjowanie korelacji** okno dialogowe.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Komunikat**|Określa komunikat, który zawartość **komunikatu danych** pole tekstowe wyrażenie i typu przy użyciu **typ komunikatu** pole listy rozwijanej. Domyślnie **definicji zawartości** używa <xref:System.ServiceModel.Activities.ReceiveMessageContent>, która oczekuje <xref:System.ServiceModel.Channels.Message> lub typu w definicji usługi przepływu pracy kontraktu komunikatu.|  
|**Parametry**|Kliknij przycisk **parametry** przycisk radiowy, aby użyć <xref:System.ServiceModel.Activities.ReceiveParametersContent>, którego oczekuje kontraktu danych. Użyj siatki danych, aby ustawić ogólnego zbiór <xref:System.Activities.OutArgument> których wartości są przypisane do parametrów zmiennych w przepływie pracy bieżącego par klucz/wartość.|  
  
 **Definicji zawartości** okno dialogowe jest używany przez **wysyłania**, **Receive**, **ReceiveAndSendReply**, i  **SendAndReceiveReply** projektantów. Uzyskiwanie dostępu do nich przypomina w każdym przypadku, a w przypadku odbierania służy tutaj, aby zilustrować procedurę.  
  
 **Receive** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działań są zazwyczaj umieszczone. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Receive> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> Receive. Wybierz **Receive** projektanta działań i kliknij przycisk wielokropka, obok tekstu (zawartość) dla **zawartości** właściwość w siatce właściwości **definicji zawartości**wyświetlane okno dialogowe.  
  
 Zawartość może być określone w **komunikat** sekcji <xref:System.ServiceModel.Activities.ReceiveMessageContent> działania lub w ramach **parametru** sekcji <xref:System.ServiceModel.Activities.ReceiveParametersContent> działania.  
  
## <a name="see-also"></a>Zobacz też  
 [Pomoc interfejsu użytkownika Projektanta przepływu pracy](../workflow-designer/workflow-designer-ui-help.md)