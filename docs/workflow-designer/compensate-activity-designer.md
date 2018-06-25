---
title: Projektant przepływu pracy — kompensacji Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1bca40a093f228f22919b7734e387a4bc191316c
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756373"
---
# <a name="compensate-activity-designer"></a>Compensate, projektant działań

**Compensate** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Compensate> działania.

## <a name="the-compensate-activity"></a>Działanie Compensate

<xref:System.Activities.Statements.Compensate> Działania jawnie wywołuje <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> dla działania zawarte w <xref:System.Activities.Statements.CompensableActivity>. Jeśli <xref:System.Activities.Statements.Compensate> działanie nie jest używane w ramach <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, lub <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> z <xref:System.Activities.Statements.CompensableActivity>, a następnie podaj <xref:System.Activities.Statements.Compensate.Target%2A> właściwości.

<xref:System.Activities.Statements.CompensationToken> Określonego przez <xref:System.Activities.Statements.Compensate.Target%2A> umożliwia jawnie potwierdzić lub kompensacji <xref:System.Activities.Statements.CompensableActivity> po <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> zostało pomyślnie ukończone.

### <a name="using-the-compensate-activity-designer"></a>Przy użyciu kompensacji Projektant działań

**Compensate** Projektant działań można znaleźć w **transakcji** kategorii **przybornika**. Aby otworzyć **przybornika**, wybierz pozycję **przybornika** karcie po lewej stronie projektanta przepływów pracy. Można także wybrać **przybornika** z **widoku** menu lub naciśnij klawisz **Ctrl**+**Alt** + **X**.

**Compensate** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie działania są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Projektant działań porzucenie tworzy <xref:System.Activities.Statements.Compensate> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z Compensate. <xref:System.Activities.Activity.DisplayName%2A> Wartość można edytować w nagłówku **Compensate** Projektant działań lub **DisplayName** pola siatki właściwości.

### <a name="the-compensate-properties"></a>Kompensacji właściwości

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.CancellationScope> właściwości oraz opis korzystania z nich w projektancie. <xref:System.Activities.Activity.DisplayName%2A> Właściwości można edytować w siatce właściwości lub na powierzchni projektanta przepływów pracy. Edytuj <xref:System.Activities.Statements.Compensate.Target%2A> właściwości w siatce właściwości.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalne przyjazna nazwa <xref:System.Activities.Statements.Compensate> działania. Wartość domyślna to Compensate.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|Określa <xref:System.Activities.InArgument%601> zawierający <xref:System.Activities.Statements.CompensationToken> dla tego <xref:System.Activities.Statements.Compensate> działania.|

## <a name="see-also"></a>Zobacz także

- [Transakcja](../workflow-designer/transaction-activity-designers.md)
- [Działanie CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate, projektant działań](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [Element TransactionScope](../workflow-designer/transactionscope-activity-designer.md)