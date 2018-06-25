---
title: Projektant przepływu pracy — Projektant działania Rethrow
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24c13b629047b73b3f3ee15f2fc25a0120a2c177
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755258"
---
# <a name="rethrow-activity-designer"></a>Rethrow, projektant działań

**Rethrow** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Rethrow> działania.

## <a name="the-rethrow-activity"></a>Działanie Rethrow

<xref:System.Activities.Statements.Rethrow> Działania zgłasza wcześniej zwrócony wyjątek. To działanie może być używane tylko w <xref:System.Activities.Statements.Catch> obsługi w <xref:System.Activities.Statements.TryCatch> działania.

### <a name="use-the-rethrow-activity-designer"></a>Za pomocą projektanta działania ReThrow

Dostęp **Rethrow** Projektant działań w **obsługi błędu** kategorii **przybornika**. **Rethrow** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie działania są zwykle umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Projektant działań porzucenie tworzy <xref:System.Activities.Statements.Rethrow> działania z domyślną **DisplayName** z Throw. <xref:System.Activities.Activity.DisplayName%2A> Wartość można edytować w nagłówku **Rethrow** Projektant działań lub **DisplayName** pola siatki właściwości.

### <a name="the-rethrow-properties"></a>Właściwości Rethrow

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Rethrow> właściwości oraz opisano, jak są używane w Projektancie:

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalne przyjazna nazwa <xref:System.Activities.Statements.Rethrow> działania. Wartość domyślna to Rethrow.|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)