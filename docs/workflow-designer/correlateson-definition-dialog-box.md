---
title: Okno dialogowe definicji CorrelatesOn | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 930f291f68e62e70c4d2a03f490f84fd8d36f657
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="correlateson-definition-dialog-box"></a>Okno dialogowe definicji CorrelatesOn
**CorrelatesOn** okno dialogowe służy do edycji w Projektancie przepływów pracy Windows <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> właściwość <xref:System.ServiceModel.Activities.Receive> działania. Aby uzyskać więcej informacji, zobacz [Receive](../workflow-designer/receive-activity-designer.md) tematu.

 Korelację między <xref:System.ServiceModel.Activities.Receive> działań określa, jak różne usługi operations połączyć ze sobą w przepływie pracy.

 W poniższej tabeli opisano elementy interfejsu użytkownika **CorrelatesOn** okno dialogowe.

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**CorrelatesWith**|<xref:System.ServiceModel.Activities.CorrelationHandle> Używany do kierowania wiadomości do wystąpienia przepływu pracy odpowiednie.|
|**Kwerendy XPath**|Para klucza i wartości zawierający zapytania, używane do wyodrębniania danych korelacji wiadomości przychodzących. Odpowiada to <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> właściwości. Kwerendy XPath są zawarte w <xref:System.ServiceModel.MessageQuerySet> obiektu.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Aby uruchomić okno dialogowe CorrelatesOn
 **Receive** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań są zwykle umieszczane. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Receive> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> Receive. Wybierz **Receive** Projektant działań i kliknij przycisk wielokropka obok tekstu (kolekcja) dla **CorrelatesOn** właściwości w siatce właściwości **CorrelatesOn definicji**  okno dialogowe okna.

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Activities.Receive>
- [Dodawanie CorrelationInitializers, okno dialogowe](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Dodaj korelacji — okno dialogowe](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Inicjowanie korelacji, okno dialogowe](../workflow-designer/initialize-correlation-dialog-box.md)