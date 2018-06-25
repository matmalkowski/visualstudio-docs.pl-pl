---
title: Projektant przepływu pracy — okno dialogowe definicję zawartości
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cc434e35755b04054d1e24da97e8a4699af7df0e
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757954"
---
# <a name="content-definition-dialog-box"></a>Definicja zawartości, okno dialogowe

**Definicję zawartości** okno dialogowe służy do konfigurowania w Projektancie przepływów pracy **zawartości** właściwości <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply> działania. Aby uzyskać więcej informacji na temat projektantów działań, które używają tego pola, zobacz [wysyłania](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), i [SendAndReceiveReply ](../workflow-designer/sendandreceivereply-template-designer.md) tematów.

W poniższej tabeli opisano elementy interfejsu użytkownika **inicjowania korelacji** okno dialogowe:

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**Komunikat**|Określa komunikat, który zawartości z **komunikatu danych** pole tekstowe wyrażenie i typu przy użyciu **typ komunikatu** pole listy rozwijanej. Domyślnie **definicję zawartości** używa <xref:System.ServiceModel.Activities.ReceiveMessageContent>, która oczekuje <xref:System.ServiceModel.Channels.Message> lub typu w definicji usługi przepływu pracy kontraktu komunikatu.|
|**Parametry**|Kliknij przycisk **parametry** przycisk radiowy, aby użyć <xref:System.ServiceModel.Activities.ReceiveParametersContent>, która oczekuje kontraktu danych. Użyj siatki danych, aby ustawić ogólnego Kolekcja <xref:System.Activities.OutArgument> pary, których wartości są przypisane do parametrów zmiennych w przepływie pracy bieżącego klucza i wartości.|

**Definicję zawartości** okno dialogowe jest używany przez **wysyłania**, **Receive**, **ReceiveAndSendReply**, i  **SendAndReceiveReply** projektantów. Uzyskiwanie dostępu do nich jest podobnie w każdym przypadku i jest tu używany w przypadku odbierania ilustrujący procedury.

**Receive** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie działania są zwykle umieszczane. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Receive> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> Receive. Wybierz **Receive** Projektant działań i kliknij przycisk wielokropka obok tekstu (zawartość) dla **zawartości** właściwości w siatce właściwości **definicję zawartości**okno dialogowe okna.

Zawartość może być określone w **komunikat** sekcji <xref:System.ServiceModel.Activities.ReceiveMessageContent> działania lub w **parametru** sekcji <xref:System.ServiceModel.Activities.ReceiveParametersContent> działania.

## <a name="see-also"></a>Zobacz także

- [Pomoc interfejsu użytkownika Projektanta przepływu pracy](../workflow-designer/workflow-designer-ui-help.md)