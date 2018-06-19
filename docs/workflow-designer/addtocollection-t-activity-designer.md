---
title: Projektant przepływu pracy — AddToCollection<T> Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b32df48f79d60500cb23a40c5273ceeedfc9c56
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976705"
---
# <a name="addtocollectiont-activity-designer"></a>AddToCollection\<T > Projektant działań

**AddToCollection\<T >** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.AddToCollection%601> działania.

## <a name="the-addtocollectiont-activity"></a>AddToCollection\<T > działania

<xref:System.Activities.Statements.AddToCollection%601> Działania dodaje element do kolekcji.

### <a name="using-the-addtocollectiont-activity-designer"></a>Przy użyciu AddToCollection\<T > Projektant działań

**AddToCollection\<T >** Projektant działań można znaleźć w **kolekcji** kategorii **przybornika**, które jest dostępne po kliknięciu  **Przybornik** karcie projektanta przepływów pracy (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)

**AddToCollection\<T >** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie działania są umieszczone, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Porzucanie **AddToCollection\<T >** tworzy Projektant działań <xref:System.Activities.Statements.AddToCollection%601> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z AddToCollection < Int32\>. (Domyślnie *elementu TypeArgument* jest **Int32**. Elementu TypeArgument można zmienić w siatce właściwości.) <xref:System.Activities.Activity.DisplayName%2A> Wartość można edytować w nagłówku **AddToCollection < T\>**  Projektant działań lub **DisplayName** pola siatki właściwości. Inne właściwości, należy edytować na siatce właściwości.

### <a name="the-addtocollectiont-properties"></a>AddToCollection\<T > Właściwości

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.AddToCollection%601> właściwości oraz opis korzystania z nich w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.AddToCollection%601> działania. Wartość domyślna to AddToCollection < Int32\>. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagane, jest najlepszym rozwiązaniem jej użyć.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|Element do dodania do kolekcji\<T >. Ten element jest typu *T*, która jest typu *elementu TypeArgument*. Aby określić elementu, wpisz w wyrażeniu języka Visual Basic w siatce właściwości.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|Kolekcja, do której można dodać elementu. Ta kolekcja jest typu **implementację interfejsu ICollection < elementu TypeArgument\>**. Aby określić kolekcji, wpisz wyrażenie języka Visual Basic w siatce właściwości.|
|*TypeArgument*|True|Typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601>. Domyślnie to *elementu TypeArgument* ustawiono typ **Int32**. Aby zmienić typ, zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T > Projektant działań](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)