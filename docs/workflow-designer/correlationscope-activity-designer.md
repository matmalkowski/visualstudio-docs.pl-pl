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
ms.openlocfilehash: b4b7eb7586eeb746bdeb3d28dfcc5fb14fe7bd6f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976608"
---
# <a name="correlationscope-activity-designer"></a>Projektant działań CorrelationScope

**CorrelationScope** Projektant działań służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.CorrelationScope> działanie, które umożliwia zarządzanie niejawne komunikatów działań podrzędnych za pomocą <xref:System.ServiceModel.Activities.CorrelationHandle> obiektu.

## <a name="the-correlationscope-activity"></a>Działanie CorrelationScope

<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> Właściwość określa <xref:System.ServiceModel.Activities.CorrelationHandle> używany do zarządzania wiadomości działań podrzędnych. <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive> działań zawartych w <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> są skonfigurowane do używania <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> właściwość zawierający <xref:System.ServiceModel.Activities.CorrelationScope> działanie korelacji.

### <a name="using-the-correlationscope-activity-designer"></a>Przy użyciu narzędzia Projektant działań CorrelationScope
 **CorrelationScope** Projektant działań można znaleźć w **wiadomości** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** karcie po lewej stronie projektanta przepływów pracy (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)

 **CorrelationScope** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.CorrelationScope> działania z domyślną **DisplayName** z CorrelationScope. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **CorrelationScope** Projektant działań lub **DisplayName** pole **właściwości** okna.

 Aby określić <xref:System.ServiceModel.Activities.CorrelationHandle> używany przez podrzędny działań dotyczących komunikatów, kliknij przycisk wielokropka obok **CorrelatesWith** w **właściwości** okno, aby wyświetlić **edytora wyrażeń**  okno dialogowe. Tej właściwości można ustawić w taki sposób, na powierzchni projektowej działania.

 Zakres w korelacji działania są określane przez usunięcie ich projektantów w **treści** polu w **CorrelationScope** projektanta.

### <a name="the-correlationscope-properties"></a>Właściwości CorrelationScope
 W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.CorrelationScope> właściwości oraz opis korzystania z nich w projektancie. Te właściwości mogą być edytowane w **właściwości** oknie lub na powierzchni projektanta projektanta przepływów pracy, a często w obu.

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