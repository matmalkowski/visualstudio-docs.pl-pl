---
title: Projektant przepływu pracy — Projektant działań Throw
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02bb94ad17b78b1264129b8a5ba00a964edbd2f2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974659"
---
# <a name="throw-activity-designer"></a>Throw Projektant działań

**Throw** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Throw> działania.

## <a name="the-throw-activity"></a>Działanie Throw
 <xref:System.Activities.Statements.Throw> Działania zgłasza wyjątek.

### <a name="using-the-throw-activity-designer"></a>Przy użyciu narzędzia Projektant działań Throw
 **Throw** Projektant działań można znaleźć w **obsługi błędu** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karcie po lewej stronie projektanta przepływów pracy (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)

 **Throw** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie działania są zwykle umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.Throw> działania z domyślną **DisplayName** z Throw. <xref:System.Activities.Activity.DisplayName%2A> Wartość można edytować w nagłówku **Throw** Projektant działań lub **DisplayName** pola siatki właściwości. <xref:System.Activities.Statements.Throw.Exception%2A> Należy edytować właściwości na siatce właściwości.

### <a name="the-throw-properties"></a>Właściwości Throw
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Throw> właściwości oraz opis korzystania z nich w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalne przyjazna nazwa <xref:System.Activities.Statements.Throw> działania. Wartość domyślna to Throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Aby zgłosić wyjątek. Ten wyjątek musi pochodzić od <xref:System.Exception>. Aby określić wyjątek, wpisz wyrażenie języka Visual Basic w siatce właściwości.|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw, projektant działań](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)