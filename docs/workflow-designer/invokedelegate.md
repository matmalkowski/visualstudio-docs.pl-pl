---
title: InvokeDelegate | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 93e41d98b156b6314158a1cc99e368092b0cf494
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="invokedelegate"></a>InvokeDelegate
**InvokeDelegate** Projektant służy do tworzenia i konfigurowania <xref:System.Activities.Statements.InvokeDelegate> działania.

## <a name="the-invokedelegate-activity"></a>Działanie InvokeDelegate
 <xref:System.Activities.Statements.InvokeDelegate> Wywołuje Delegat publiczny.

### <a name="using-the-invokedelegate-activity-designer"></a>Przy użyciu narzędzia Projektant działań InvokeDelegate
 **InvokeDelegate** Projektant działań można znaleźć w **podstawowych** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** kartę [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub klawiszy CTRL + ALT + X.)

 **InvokeDelegate** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni gdziekolwiek działań zwykle są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.InvokeDelegate> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z InvokeDelegate. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **InvokeDelegate** Projektant działań lub **DisplayName** pola siatki właściwości.

### <a name="the-invokedelegate-properties"></a>Właściwości InvokeDelegate
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.InvokeDelegate> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości i niektóre mogą być edytowane [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]powierzchnię projektanta.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.InvokeDelegate> działania. Wartość domyślna to InvokeDelegate.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem jej użyć.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Nazwa <xref:System.Activities.ActivityDelegate> wywoływana, gdy działanie wykonuje. Tej właściwości można edytować na powierzchnię projektanta. Jest to wymagane właściwości.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Kolekcja argument wywoływany delegat. Klucze są nazwy obiektów parametru na <xref:System.Activities.ActivityDelegate> i argumentów, których wyrażenia są oceniane i przypisane do odpowiednich obiektów parametru wartości. Siatki właściwości, kliknij przycisk wielokropka w **DelegateArguments** pola, wyświetla **DelegateArguments** okna dialogowego, aby można było ustawić tę właściwość. Kliknij przycisk **utworzyć Argument** pole, aby dodać argumentów.|

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Definiowanie i stosowanie delegowania działania w Projektancie przepływu pracy](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)