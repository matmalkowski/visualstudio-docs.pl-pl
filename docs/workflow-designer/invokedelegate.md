---
title: Projektant przepływu pracy — InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: e3d802000bede1a654b088fb80b134a36a0185be
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758530"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate** Projektant służy do tworzenia i konfigurowania <xref:System.Activities.Statements.InvokeDelegate> działania.

## <a name="the-invokedelegate-activity"></a>Działanie InvokeDelegate

<xref:System.Activities.Statements.InvokeDelegate> Wywołuje Delegat publiczny.

### <a name="use-the-invokedelegate-activity-designer"></a>Za pomocą projektanta InvokeDelegate działania

Dostęp **InvokeDelegate** Projektant działań w **podstawowych** kategorii **przybornika**. **InvokeDelegate** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy w przypadku gdy zabezpieczając działania są zwykle umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Projektant działań porzucenie tworzy <xref:System.Activities.Statements.InvokeDelegate> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z InvokeDelegate. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **InvokeDelegate** Projektant działań lub **DisplayName** pola siatki właściwości.

### <a name="the-invokedelegate-properties"></a>Właściwości InvokeDelegate

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.InvokeDelegate> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre można edytowane na powierzchni projektanta przepływów pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.InvokeDelegate> działania. Wartość domyślna to InvokeDelegate.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem, najlepiej użyć jednego.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Nazwa <xref:System.Activities.ActivityDelegate> wywoływana, gdy działanie wykonuje. Ta właściwość może być edytowany na powierzchnię projektanta i jest wymagane.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Kolekcja argument wywoływany delegat. Klucze są nazwy obiektów parametru na <xref:System.Activities.ActivityDelegate>, a ich wartości są argumentów, których wyrażenia są oceniane i przypisane do odpowiednich obiektów parametru. Aby wyświetlić **DelegateArguments** okna dialogowego, w którym można ustawić tę właściwość, kliknij przycisk wielokropka **DelegateArguments** pole siatki właściwości. Kliknij przycisk **utworzyć Argument** pole, aby dodać argumentów.|

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Definiowanie i stosowanie delegowania działania w Projektancie przepływu pracy](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)