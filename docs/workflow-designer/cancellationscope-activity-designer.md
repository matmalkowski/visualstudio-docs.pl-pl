---
title: Projektant przepływu pracy — Projektant działań CancellationScope
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a0f9a40434821294384154ddcbbfebbd0a7885eb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="cancellationscope-activity-designer"></a>Projektant działań CancellationScope

**CancellationScope** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.CancellationScope> działania.

## <a name="the-cancellationscope-activity"></a>Działanie CancellationScope
 <xref:System.Activities.Statements.CancellationScope> Działania można określić działanie logiki wykonywania i anulowania dla tego działania.

### <a name="using-the-cancellationscope-activity-designer"></a>Przy użyciu narzędzia Projektant działań CancellationScope
 **CancellationScope** Projektant działań można znaleźć w **transakcji** kategorii **przybornika**. Aby otworzyć **przybornika**, wybierz pozycję **przybornika** karcie projektanta przepływów pracy. Można także wybrać **narzędzi** z **widoku** menu lub naciśnij klawisze CTRL + ALT + X.

 **CancellationScope** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie działania są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Porzucanie **CancellationScope** tworzy Projektant działań <xref:System.Activities.Statements.CancellationScope> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z CancellationScope. Edytuj <xref:System.Activities.Activity.DisplayName%2A> wartość w nagłówku **CancellationScope** Projektant działań. Można również edytować go w **DisplayName** pola siatki właściwości.

### <a name="the-cancellationscope-properties"></a>Właściwości CancellationScope
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.CancellationScope> właściwości oraz opis korzystania z nich w projektancie. <xref:System.Activities.Activity.DisplayName%2A> Właściwości można edytować w siatce właściwości, ale inne właściwości, należy edytować na powierzchni projektanta przepływów pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalne przyjazna nazwa <xref:System.Activities.Statements.CancellationScope> działania. Wartość domyślna to CancellationScope. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagane, jest najlepszym rozwiązaniem jej użyć.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Określa działania, które anulowania podano logiki. Aby dodać <xref:System.Activities.Statements.CancellationScope.Body%2A> działania, Porzuć działanie z **przybornika** do **treści** polu na **CancellationScope** Projektant działań. Dodaj tekst wskazówki "Upuść tutaj działanie".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Określa działania, która jest wykonywana w przypadku anulowania. Aby dodać <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> działania, Porzuć działanie z **przybornika** do **CancellationHandler** polu na **CancellationScope** Projektant działań. Dodaj tekst wskazówki "Upuść tutaj działanie".|

## <a name="see-also"></a>Zobacz także

- [Transakcja](../workflow-designer/transaction-activity-designers.md)
- [Działanie CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Wyrównania](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [Element TransactionScope](../workflow-designer/transactionscope-activity-designer.md)