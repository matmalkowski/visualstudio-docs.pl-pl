---
title: Projektant przepływu pracy — działania CompensableActivity Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fdab42766fd20989831e446a45115d17b3ee28fd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31978664"
---
# <a name="compensableactivity-activity-designer"></a>Działanie CompensableActivity Projektant działań

**Działanie CompensableActivity** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.CompensableActivity> działania.

## <a name="the-compensableactivity-activity"></a>Działanie CompensableActivity działania
 <xref:System.Activities.Statements.CompensableActivity> Definiuje jednostkę pracy, które mogą być potwierdzone lub skompensowane po pomyślnym ukończeniu.

### <a name="using-the-compensableactivity-activity-designer"></a>Przy użyciu narzędzia Projektant działań działanie CompensableActivity
 **Działanie CompensableActivity** Projektant działań można znaleźć w **transakcji** kategorii **przybornika**. Aby otworzyć **przybornika**, wybierz pozycję **przybornika** karcie po lewej stronie projektanta przepływów pracy. Można także wybrać **narzędzi** z **widoku** menu lub naciśnij klawisze CTRL + ALT + X.

 **Działanie CompensableActivity** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy. Projektant działań wewnątrz można porzucić <xref:System.Activities.Statements.Sequence>. Projektant działań porzucenie tworzy <xref:System.Activities.Statements.CompensableActivity> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z działania CompensableActivity. Edytuj <xref:System.Activities.Activity.DisplayName%2A> wartość w nagłówku **działanie CompensableActivity** Projektant działań. Mogą być edytowane także w **DisplayName** pola siatki właściwości.

### <a name="the-compensableactivity-properties"></a>Działanie CompensableActivity właściwości
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.CompensableActivity> właściwości oraz opis korzystania z nich w projektancie. <xref:System.Activities.Activity.DisplayName%2A> i <xref:System.Activities.Activity%601.Result%2A> właściwości można edytować w siatce właściwości, ale inne właściwości, należy edytować na powierzchni projektanta przepływów pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalne przyjazna nazwa <xref:System.Activities.Statements.CompensableActivity> działania. Wartość domyślna to działanie CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Określa wartość zwracaną <xref:System.Activities.Statements.CompensableActivity>. Ta właściwość musi być edytowany w siatce właściwości.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Określa działania, dla których dostępny jest logiki kompensacji, anulowanie i potwierdzenia. Aby dodać <xref:System.Activities.Statements.CompensableActivity.Body%2A> działania, Porzuć działanie z **przybornika** do **treści** polu na **działanie CompensableActivity** Projektant działań. Dodaj tekst podpowiedzi "Upuść działanie tutaj".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Określa działania, która jest wykonywana w przypadku anulowania. Aby dodać działanie, Porzuć jego projektanta z **przybornika** do **CancellationHandler** polu na **działanie CompensableActivity** Projektant działań. Dodaj tekst podpowiedzi "Upuść tutaj działanie".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Określa działanie ma być wykonywana w przypadku kompensowanie dla <xref:System.Activities.Statements.CompensableActivity.Body%2A> działania. Ten program obsługi można jawnie wywołać przy użyciu <xref:System.Activities.Statements.Compensate> działania.<br /><br /> Aby dodać działanie, Porzuć jego Projektant działań z **przybornika** do **CompensationHandler** polu na **działanie CompensableActivity** Projektant działań. Dodaj tekst podpowiedzi "Upuść tutaj działanie".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Określa działanie do wykonania podczas potwierdzania <xref:System.Activities.Statements.CompensableActivity.Body%2A> działania. Ten program obsługi można jawnie wywołać przy użyciu <xref:System.Activities.Statements.Confirm> działania.<br /><br /> Aby dodać działanie, Porzuć jego Projektant działań z **przybornika** do **ConfirmationHandler** polu na **działanie CompensableActivity** Projektant działań. Dodaj tekst podpowiedzi "Upuść tutaj działanie".|

## <a name="see-also"></a>Zobacz także

- [Transakcja](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Wyrównania](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [Element TransactionScope](../workflow-designer/transactionscope-activity-designer.md)