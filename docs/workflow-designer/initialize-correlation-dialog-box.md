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
ms.openlocfilehash: c3525eb8964ed603e40ba74f0c06b17b494390c7
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755843"
---
# <a name="initialize-correlation-dialog-box"></a>Inicjowanie korelacji, okno dialogowe

**Inicjowania korelacji** okno dialogowe służy do edycji w Projektancie przepływów pracy <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> właściwość <xref:System.ServiceModel.Activities.InitializeCorrelation> działania. Aby uzyskać więcej informacji, zobacz [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

W poniższej tabeli opisano elementy interfejsu użytkownika **inicjowania korelacji** okno dialogowe:

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**Korelacja**|<xref:System.ServiceModel.Activities.CorrelationHandle> Korelacji zainicjować.|
|**Inicjowanie na**|Para klucza i wartości zawierający dane inicjowania. Ta wartość odpowiada <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> właściwości. Przykład parę nieprawidłowy klucz/wartość jest klucz o nazwie "OrderID" łączyć się z zmiennej o nazwie OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Aby uruchomić okno dialogowe inicjowania korelacji

Kliknij przycisk **widoku** na **InitializeCorrelation** działania projektanta lub wybierz opcję <xref:System.ServiceModel.Activities.InitializeCorrelation> działania w Projektancie przepływów pracy. Następnie kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> właściwości w siatce właściwości.

## <a name="see-also"></a>Zobacz także

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)