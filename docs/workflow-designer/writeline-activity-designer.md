---
title: Projektant przepływu pracy — Projektant działań WriteLine
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9b77ab2b9effc305469b3a4e489342f496a89997
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755953"
---
# <a name="writeline-activity-designer"></a>WriteLine, projektant działań

**WriteLine** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.WriteLine> działania.

## <a name="the-writeline-activity"></a>Działanie WriteLine

<xref:System.Activities.Statements.WriteLine> Działania zapisuje tekst w określonym <xref:System.IO.TextWriter> obiektu. Jeśli nie <xref:System.IO.TextWriter> jest określony, <xref:System.Activities.Statements.WriteLine> zapisuje tekst do konsoli.

### <a name="using-the-writeline-activity-designer"></a>Przy użyciu narzędzia Projektant działań WriteLine

Dostęp **WriteLine** Projektant działań w **podstawowych** kategorii **przybornika**. **WriteLine** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie działania są zwykle umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.WriteLine> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z WriteLine. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **WriteLine** Projektant działań lub **DisplayName** pola siatki właściwości.

### <a name="the-writeline-properties"></a>Właściwości WriteLine

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.WriteLine> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości i niektóre z nich można edytowane na powierzchni projektanta przepływów pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.WriteLine> działania. Wartość domyślna to WriteLine. Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem jest użycie jednego.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Tekst do zapisu. Aby ustawić właściwości, wpisz wyrażenie języka Visual Basic w **tekst** polu na **WriteLine** działania projektanta lub w siatce właściwości.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|<xref:System.IO.TextWriter> Do której <xref:System.Activities.Statements.WriteLine> zapisuje <xref:System.Activities.Statements.WriteLine.Text%2A>. Wartość domyślna to konsoli.|

## <a name="see-also"></a>Zobacz także

- [Typy pierwotne](../workflow-designer/primitives-activity-designers.md)
- [Przypisz](../workflow-designer/assign-activity-designer.md)
- [Opóźnienie](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)