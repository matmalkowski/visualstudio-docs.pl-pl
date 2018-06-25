---
title: Projektant przepływu pracy — Definiowanie CorrelatesOn — okno dialogowe
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a7ed52f7898f10b5f13f55c27cba380334489871
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758137"
---
# <a name="correlateson-definition-dialog-box"></a>Definicja wyrażenia CorrelatesOn, okno dialogowe

**CorrelatesOn** okno dialogowe służy do edycji w Projektancie przepływów pracy <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> właściwość <xref:System.ServiceModel.Activities.Receive> działania. Aby uzyskać więcej informacji, zobacz [odbierania Projektant działań](../workflow-designer/receive-activity-designer.md).

Korelację między <xref:System.ServiceModel.Activities.Receive> działań określa, jak różne usługi operations połączyć ze sobą w przepływie pracy.

W poniższej tabeli opisano elementy interfejsu użytkownika **CorrelatesOn** okno dialogowe.

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**CorrelatesWith**|<xref:System.ServiceModel.Activities.CorrelationHandle> Używany do kierowania wiadomości do wystąpienia przepływu pracy odpowiednie.|
|**Kwerendy XPath**|Para klucza i wartości zawierający zapytania, używane do wyodrębniania danych korelacji wiadomości przychodzących. Ta wartość odpowiada <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> właściwości. Kwerendy XPath są zawarte w <xref:System.ServiceModel.MessageQuerySet> obiektu.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Aby uruchomić okno dialogowe CorrelatesOn

**Receive** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy, wszędzie tam, gdzie działania są zwykle umieszczane. Projektant działań porzucenie tworzy <xref:System.ServiceModel.Activities.Receive> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> Receive. Aby otworzyć **definicji CorrelatesOn** okno dialogowe, wybierz opcję **Receive** działania projektanta, a następnie w siatce właściwości, kliknij przycisk wielokropka obok tekstu kolekcji dla  **CorrelatesOn** właściwości.

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Activities.Receive>
- [Dodawanie CorrelationInitializers, okno dialogowe](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Dodaj korelacji — okno dialogowe](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Inicjowanie korelacji, okno dialogowe](../workflow-designer/initialize-correlation-dialog-box.md)