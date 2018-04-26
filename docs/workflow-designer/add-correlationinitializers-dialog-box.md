---
title: Okno dialogowe właściwości CorrelationInitializers Dodawanie projektanta przepływów pracy —
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc122840607b62a966e5224662ec2d557e5c8ed5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="add-correlationinitializers-dialog-box"></a>Okno dialogowe właściwości CorrelationInitializers Dodawanie

**Dodać inicjatorów korelacji** okno dialogowe służy do konfigurowania w Projektancie przepływów pracy Windows **CorrelationInitializers** właściwości <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply> działań. Aby uzyskać więcej informacji na temat projektantów działań, które używają tego pola, zobacz [wysyłania](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), i [SendAndReceiveReply ](../workflow-designer/sendandreceivereply-template-designer.md) tematów.

Inicjatory korelacji w kolekcji określony za pomocą tego okna dialogowego można zainicjować następujące korelacji między działaniami komunikatów:

- oparte na zapytaniach
- kontekst
- Kontekst wywołania zwrotnego
- "żądanie-odpowiedź"

W poniższej tabeli opisano elementy interfejsu użytkownika **dodać inicjatorów korelacji** okno dialogowe:

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**Dodaj inicjatora**|Kliknij przycisk **zainicjować Dodaj** pole, aby dodać dodatkowe inicjatora kolekcji.|
|**Typ korelacji**|Określa typ inicjatora korelacji. Istnieją cztery typy do wyboru:<br /><br /> 1. Inicjatora korelacji wywołania zwrotnego, aby określić <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2. Inicjatora korelacji kontekstu, aby określić <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3. Inicjatora korelacji "żądanie-odpowiedź", aby określić <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4. Inicjatora korelacji zapytań, aby określić <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Aby edytować **CorrelationType**<br /><br /> 1. Karta do określonego wiersza w **dodać inicjatora** DataGrid.<br />2. Aby ustawić fokus na **CorrelationTypeComboBox**, naciśnij klawisz **Ctrl**+**kartę**.<br />3. Naciśnij klawisze Alt + Strzałka w dół, aby wyskakujące **ComboBox** i go edytować.|
|**Kwerendy XPath**|Para klucza i wartości zawierający zapytania, używane do wyodrębniania danych korelacji wiadomości przychodzących i wychodzących. Ta lista jest prawidłowy tylko w przypadku korzystania z <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> typów.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Aby uruchomić okno dialogowe Dodawanie inicjatorów korelacji

 **Dodać inicjatorów korelacji** okno dialogowe jest używany przez **wysyłania**, **Receive**, **ReceiveAndSendReply**, i  **SendAndReceiveReply** projektantów. Uzyskiwanie dostępu do nich przypomina w każdym przypadku i przypadku, która obejmuje **Receive** Projektant służy w tym miejscu ilustrujący procedury.

 **Receive** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie są umieszczone działania. Porzucanie **Receive** tworzy Projektant działań <xref:System.ServiceModel.Activities.Receive> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> Receive. Wybierz **Receive** Projektant działań i kliknij przycisk wielokropka obok tekstu (kolekcja) dla **CorrelationInitializers** właściwości w siatce właściwości **Dodaj Inicjatory korelacji** okno dialogowe okna.

## <a name="see-also"></a>Zobacz także

- [Dodaj korelacji — okno dialogowe](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Inicjowanie korelacji, okno dialogowe](../workflow-designer/initialize-correlation-dialog-box.md)