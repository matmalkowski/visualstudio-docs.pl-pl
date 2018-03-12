---
title: "Projektant działań działanie CompensableActivity | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c45a0f2638a3d1fc5b6f4dc536cf051751c9c897
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2018
---
# <a name="compensableactivity-activity-designer"></a>Działanie CompensableActivity Projektant działań
**Działanie CompensableActivity** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.CompensableActivity> działania.

## <a name="the-compensableactivity-activity"></a>Działanie CompensableActivity działania
 <xref:System.Activities.Statements.CompensableActivity> Definiuje jednostkę pracy, które mogą być potwierdzone lub skompensowane po pomyślnym ukończeniu.

### <a name="using-the-compensableactivity-activity-designer"></a>Przy użyciu narzędzia Projektant działań działanie CompensableActivity
 **Działanie CompensableActivity** Projektant działań można znaleźć w **transakcji** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**  karcie po lewej stronie [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)

 **Działanie CompensableActivity** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań zwykle są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.CompensableActivity> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z działania CompensableActivity. <xref:System.Activities.Activity.DisplayName%2A> Wartość można edytować w nagłówku **działanie CompensableActivity** Projektant działań lub **DisplayName** pola siatki właściwości.

### <a name="the-compensableactivity-properties"></a>Działanie CompensableActivity właściwości
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.CompensableActivity> właściwości oraz opis korzystania z nich w projektancie. <xref:System.Activities.Activity.DisplayName%2A> i <xref:System.Activities.Activity%601.Result%2A> właściwości można edytować w siatce właściwości, ale inne właściwości, należy edytować na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalne przyjazna nazwa <xref:System.Activities.Statements.CompensableActivity> działania. Wartość domyślna to działanie CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Określa wartość zwracaną <xref:System.Activities.Statements.CompensableActivity>. Ta właściwość musi być edytowany w siatce właściwości.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Określa działania, dla których dostępny jest logiki kompensacji, anulowanie i potwierdzenia. Aby dodać <xref:System.Activities.Statements.CompensableActivity.Body%2A> działania, Porzuć działanie z **przybornika** do **treści** pole na **działanie CompensableActivity** Projektant działań z tekstu podpowiedzi "upuść działanie tutaj".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Określa działania, która jest wykonywana w przypadku anulowania. Aby dodać działanie, Porzuć jego projektanta z **przybornika** do **CancellationHandler** polu na **działanie CompensableActivity** Projektant działań z tekstu podpowiedzi "upuść Działanie tutaj".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Określa działanie ma być wykonywana w przypadku kompensowanie dla <xref:System.Activities.Statements.CompensableActivity.Body%2A> działania. Ten program obsługi można jawnie wywołać przy użyciu <xref:System.Activities.Statements.Compensate> działania.<br /><br /> Aby dodać działanie, Porzuć jego Projektant działań z **przybornika** do **CompensationHandler** polu na **działanie CompensableActivity** Projektant działań z tekstu podpowiedzi " Upuść działanie tutaj".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Określa działanie do wykonania podczas potwierdzania <xref:System.Activities.Statements.CompensableActivity.Body%2A> działania. Ten program obsługi można jawnie wywołać przy użyciu <xref:System.Activities.Statements.Confirm> działania.<br /><br /> Aby dodać działanie, Porzuć jego Projektant działań z **przybornika** do **ConfirmationHandler** polu na **działanie CompensableActivity** Projektant działań z tekstu podpowiedzi " Upuść działanie tutaj".|

## <a name="see-also"></a>Zobacz także

- [Transakcja](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Wyrównania](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [Element TransactionScope](../workflow-designer/transactionscope-activity-designer.md)