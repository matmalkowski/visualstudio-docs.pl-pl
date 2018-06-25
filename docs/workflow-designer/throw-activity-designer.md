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
ms.openlocfilehash: 71cf547a1ea3599de8926e40ca5a43f3bdea0f71
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758324"
---
# <a name="throw-activity-designer"></a>Throw, projektant działań

**Throw** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Throw> działania.

## <a name="the-throw-activity"></a>Działanie Throw

<xref:System.Activities.Statements.Throw> Działania zgłasza wyjątek.

### <a name="using-the-throw-activity-designer"></a>Przy użyciu narzędzia Projektant działań Throw

Dostęp **Throw** Projektant działań w **obsługi błędu** kategorii **przybornika**.

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