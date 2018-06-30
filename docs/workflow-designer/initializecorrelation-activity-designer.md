---
title: Projektant przepływu pracy — Projektant działań InitializeCorrelation
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b210b5e0d3d0f3638e78331d9db093f7e86079e
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117176"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation, projektant działań

**InitializeCorrelation** Projektant działań służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.InitializeCorrelation> działania. <xref:System.ServiceModel.Activities.InitializeCorrelation> Działania ustanawia korelacja wiadomości przed wysłaniem lub ich odbierania.

## <a name="the-initializecorrelation-activity"></a>Działanie InitializeCorrelation

<xref:System.ServiceModel.Activities.InitializeCorrelation> To działanie służy do inicjowania korelacji bez wysyłania i odbierania wiadomości. Zwykle korelacji zainicjowano przy wysyłaniu lub odbieraniu wiadomości. Jeśli przed wysłanego lub odebranego komunikatu, należy ustanowić korelacji, użyj <xref:System.ServiceModel.Activities.InitializeCorrelation> zainicjować korelacji.

### <a name="using-the-initializecorrelation-activity-designer"></a>Przy użyciu narzędzia Projektant działań InitializeCorrelation

Dostęp **InitializeCorrelation** Projektant działań w **wiadomości** kategorii **przybornika**.

**InitializeCorrelation** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy. Projektant działań porzucenie tworzy <xref:System.ServiceModel.Activities.InitializeCorrelation> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z InitializeCorrelation. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **InitializeCorrelation** Projektant działań lub **DisplayName** pole **właściwości** okna.

<xref:System.ServiceModel.Activities.CorrelationHandle> Może być Określa **korelacji** w **właściwości** okno na **InitializeCorrelation** działania powierzchnię projektanta.

Aby wyświetlić **inicjowania korelacji** okno dialogowe, w którym można określić dojścia korelacji i par klucz wartość używaną do inicjalizacji, kliknij przycisk wielokropka obok **CorrelationData** pole w **właściwości** okna. Lub zaznacz tekst podpowiedzi "View..." na **InitializeCorrelation** działania powierzchnię projektanta. Aby uzyskać więcej informacji na temat używania tego okna dialogowego, zobacz [okno dialogowe Edytor kolekcji typu](../workflow-designer/type-collection-editor-dialog-box.md) artykułu.

### <a name="the-initializecorrelation-properties"></a>Właściwości InitializeCorrelation

W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.InitializeCorrelation> właściwości i opisano sposób ich używania w projektancie. Te właściwości można edytować w **właściwości** oknie lub na powierzchni projektanta przepływów pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.ServiceModel.Activities.InitializeCorrelation> działania. Wartość domyślna to InitializeCorrelation.<br /><br /> Mimo że użycie wartości innych niż domyślne dla przyjaznych <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, jest zalecane.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> Używanego do kojarzenia działań przepływu pracy w korelacji.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Słownik danych korelacji odnosi się komunikaty do wystąpienia przepływu pracy.<br /><br /> Użyj **inicjowania korelacji** okno dialogowe, aby skonfigurować <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Aby uzyskać więcej informacji na temat używania tego okna dialogowego, zobacz [okno dialogowe Edytor kolekcji typu](../workflow-designer/type-collection-editor-dialog-box.md) artykułu.|

## <a name="see-also"></a>Zobacz także

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Odbieranie](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Wyślij](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)