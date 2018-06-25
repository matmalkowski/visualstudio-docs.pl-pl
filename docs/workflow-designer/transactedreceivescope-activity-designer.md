---
title: Projektant przepływu pracy — Projektant działania TransactedReceiveScope
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97a4871f3f9f7726f8e0f62008c22aef5e22234e
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755147"
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope, projektant działań

**TransactedReceiveScope** Projektant służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.

## <a name="the-transactedreceivescope-activity"></a>Działania TransactedReceiveScope

<xref:System.ServiceModel.Activities.TransactedReceiveScope> Działania umożliwia przekazania transakcji do transakcji server utworzonych przez przepływ pracy lub dyspozytora.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Przy użyciu narzędzia Projektant działania TransactedReceiveScope

Dostęp **TransactedReceiveScope** Projektant działań w **wiadomości** kategorii **przybornika**. **TransactedReceiveScope** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie działania są zwykle umieszczane. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania z domyślną **DisplayName** z TransactedReceiveScope. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **TransactedReceiveScope** Projektant działań lub **DisplayName** pola siatki właściwości.

**TransactedReceiveScope** Projektant zawiera **żądania** i **treści** pola. Są one używane do konfigurowania <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> właściwość, która określa <xref:System.ServiceModel.Activities.Receive> działania i <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> właściwość, która określa innymi <xref:System.Activities.Activity>. <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> Tworzy transakcję. Następnie transakcji staje się otoczenia dla zakresu <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> tak, aby wszystkie działania w tym zakresie wykonuje w tej transakcji.

### <a name="the-transactedreceivescope-properties"></a>Właściwości TransactedReceiveScope

W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.TransactedReceiveScope> właściwości oraz opis korzystania z nich w projektancie. Te <xref:System.Activities.Activity.DisplayName%2A> właściwości można edytować w siatce właściwości lub na powierzchni projektanta przepływów pracy, ale inne należy edytować na powierzchni projektu.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalne przyjazna nazwa <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania. Wartość domyślna to TransactedReceiveScope.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nazwa nie jest ściśle wymagane, jest najlepszym rozwiązaniem, aby użyć nazwy wyświetlanej.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|Porzucania <xref:System.ServiceModel.Activities.Receive> działania do **żądania** bloku na powierzchni projektowej działania.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Porzucania <xref:System.Activities.Activity> do **treści** bloku na powierzchni projektowej działania.|

## <a name="see-also"></a>Zobacz także

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Odbieranie](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Wyślij](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)