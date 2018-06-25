---
title: Projektant przepływu pracy — Projektant działań opóźnienia
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31b632177ba941ad0e5ddb5700ae430573fd817d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758456"
---
# <a name="delay-activity-designer"></a>Delay, projektant działań

**Opóźnienie** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Delay> działania.

## <a name="the-delay-activity"></a>Działanie opóźnienia

<xref:System.Activities.Statements.Delay> Działania opóźnienie wykonywania przepływu pracy dla określonego przedziału czasu.

### <a name="use-the-delay-activity-designer"></a>Za pomocą projektanta działania opóźnienia

**Opóźnienie** Projektant działań można znaleźć w **podstawowych** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karcie projektanta przepływów pracy. Można także wybrać **przybornika** z **widoku** menu lub naciśnij klawisz **Ctrl**+**Alt** + **X**.

**Opóźnienie** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie działania są zwykle umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Projektant działań porzucenie tworzy <xref:System.Activities.Statements.Delay> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> opóźnienia. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **opóźnienie** Projektant działań lub **DisplayName** pola siatki właściwości.

### <a name="the-delay-properties"></a>Właściwości opóźnienia

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Delay> właściwości i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości i niektóre z nich można edytowane na powierzchni projektanta przepływów pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.Delay> działania. Wartość domyślna to opóźnienie. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagane, jest najlepszym rozwiązaniem jej użyć.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|Ilość czasu opóźnienia przepływ pracy. Ta właściwość jest ustawiana w siatce właściwości. Wpisz w jednym literału <xref:System.TimeSpan> w formacie 00:00:00 lub wyrażenie języka Visual Basic, aby określić ilość czasu.|

## <a name="see-also"></a>Zobacz także

- [Typy pierwotne](../workflow-designer/primitives-activity-designers.md)
- [Przypisz](../workflow-designer/assign-activity-designer.md)
- [Delay, projektant działań](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)