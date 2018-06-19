---
title: Projektant przepływu pracy — upewnij się, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 21a4c1b31769387470d58f27a060d4e3ec7ae70c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31972062"
---
# <a name="confirm-activity-designer"></a>Upewnij się, Projektant działań

**Potwierdź** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Confirm> działania.

## <a name="the-confirm-activity"></a>Działanie Confirm
 <xref:System.Activities.Statements.Confirm> Działania jawnie wywołuje <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> dla działania zawarte w <xref:System.Activities.Statements.CompensableActivity>. Jeśli <xref:System.Activities.Statements.Confirm> działanie nie jest używane w ramach <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, lub <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> z <xref:System.Activities.Statements.CompensableActivity>, a następnie podaj <xref:System.Activities.Statements.Confirm.Target%2A> właściwości.

 <xref:System.Activities.Statements.CompensationToken> Określonego przez <xref:System.Activities.Statements.Compensate.Target%2A> umożliwia jawnie potwierdzić lub kompensacji <xref:System.Activities.Statements.CompensableActivity> po <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> zostało pomyślnie ukończone.

### <a name="using-the-confirm-activity-designer"></a>Przy użyciu potwierdzić Projektant działań
 **Potwierdź** Projektant działań można znaleźć w **transakcji** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karcie po lewej stronie projektanta przepływów pracy (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)

 **Potwierdź** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie działania są zwykle umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.Confirm> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> o potwierdzenie. <xref:System.Activities.Activity.DisplayName%2A> Wartość może być edytowany w nagłówku **Potwierdź** Projektant działań lub **DisplayName** pola siatki właściwości.

### <a name="the-confirm-properties"></a>Upewnij się, właściwości
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Confirm> właściwości oraz opis korzystania z nich w projektancie. <xref:System.Activities.Activity.DisplayName%2A> Właściwości można edytować w siatce właściwości lub na powierzchni projektanta przepływów pracy, ale <xref:System.Activities.Statements.Confirm.Target%2A> należy edytować właściwości w siatce właściwości.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalne przyjazna nazwa <xref:System.Activities.Statements.CancellationScope> działania. Wartość domyślna to potwierdzić.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|True|Określa <xref:System.Activities.InArgument%601> zawierający <xref:System.Activities.Statements.CompensationToken> dla tego <xref:System.Activities.Statements.Confirm> działania.|

## <a name="see-also"></a>Zobacz także

- [Transakcja](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Działanie CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Wyrównania](../workflow-designer/compensate-activity-designer.md)
- [Element TransactionScope](../workflow-designer/transactionscope-activity-designer.md)