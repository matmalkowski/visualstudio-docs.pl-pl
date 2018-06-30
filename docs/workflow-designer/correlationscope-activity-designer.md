---
title: Projektant przepływu pracy — Projektant działań CorrelationScope
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eae1f0d61492eba29b442d0fbfb22b77377228fc
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117065"
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope, projektant działań

**CorrelationScope** Projektant działań służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.CorrelationScope> działanie, które umożliwia zarządzanie niejawne komunikatów działań podrzędnych za pomocą <xref:System.ServiceModel.Activities.CorrelationHandle> obiektu.

## <a name="the-correlationscope-activity"></a>Działanie CorrelationScope

<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> Właściwość określa <xref:System.ServiceModel.Activities.CorrelationHandle> używany do zarządzania wiadomości działań podrzędnych. <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive> działań zawartych w <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> są skonfigurowane do używania <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> właściwość zawierający <xref:System.ServiceModel.Activities.CorrelationScope> działanie korelacji.

### <a name="use-the-correlationscope-activity-designer"></a>Za pomocą projektanta CorrelationScope działania

**CorrelationScope** Projektant działań można znaleźć w **wiadomości** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** karcie po lewej stronie projektanta przepływów pracy. Można także wybrać **przybornika** z **widoku** menu lub naciśnij klawisz **Ctrl**+**Alt** + **X**.

**CorrelationScope** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.CorrelationScope> działania z domyślną **DisplayName** z CorrelationScope. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **CorrelationScope** Projektant działań lub **DisplayName** pole **właściwości** okna.

Aby określić <xref:System.ServiceModel.Activities.CorrelationHandle> używany przez podrzędny działań dotyczących komunikatów, kliknij przycisk wielokropka obok **CorrelatesWith** w **właściwości** okno, aby wyświetlić **wyrażenia Edytor** okno dialogowe. Tej właściwości można ustawić w taki sposób, na powierzchni projektowej działania.

Zakres w korelacji działania są określane przez usunięcie ich projektantów w **treści** polu w **CorrelationScope** projektanta.

### <a name="the-correlationscope-properties"></a>Właściwości CorrelationScope

W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.CorrelationScope> właściwości oraz opis korzystania z nich w projektancie. Te właściwości mogą być edytowane w **właściwości** oknie lub na powierzchni projektanta przepływów pracy, a często w obu.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalne przyjazna nazwa <xref:System.ServiceModel.Activities.InitializeCorrelation> działania.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Określa <xref:System.ServiceModel.Activities.CorrelationHandle> używany do zarządzania wiadomości działań podrzędnych. Jeśli ta właściwość nie jest ustawiona <xref:System.ServiceModel.Activities.CorrelationScope> tworzy niejawny <xref:System.ServiceModel.Activities.CorrelationHandle> automatycznie.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Określa działań w zakresie korelacji.|

## <a name="see-also"></a>Zobacz także

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Odbieranie](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Wyślij](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)