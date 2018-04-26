---
title: Projektant przepływu pracy — okno dialogowe inicjowania korelacji
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93ce95c7a821d243af842170ba30ec82647933ab
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="initialize-correlation-dialog-box"></a>Inicjowanie korelacji — okno dialogowe

**Inicjowania korelacji** okno dialogowe służy do edycji w Projektancie przepływów pracy Windows <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> właściwość <xref:System.ServiceModel.Activities.InitializeCorrelation> działania. Aby uzyskać więcej informacji, zobacz [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) tematu.

 W poniższej tabeli opisano elementy interfejsu użytkownika **inicjowania korelacji** okno dialogowe.

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**Korelacja**|<xref:System.ServiceModel.Activities.CorrelationHandle> Korelacji zainicjować.|
|**Inicjowanie na**|Para klucza i wartości zawierający dane inicjowania. Odpowiada to <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> właściwości. Przykład parę klucza i wartości prawidłowe byłoby klucz o nazwie "OrderID" łączyć się z zmiennej o nazwie OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Aby uruchomić okno dialogowe inicjowania korelacji

-   Kliknij przycisk **widoku** na **InitializeCorrelation** działania projektanta lub wybierz opcję <xref:System.ServiceModel.Activities.InitializeCorrelation> działania w Projektancie przepływów pracy a następnie kliknij przycisk wielokropka obok przycisku <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> właściwości w siatki właściwości.

## <a name="see-also"></a>Zobacz także

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)