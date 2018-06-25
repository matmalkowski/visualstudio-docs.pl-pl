---
title: Projektant przepływu pracy — ClearCollection<T> Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2422f7165e3f00e4059bc593c129c7723daed2f
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757899"
---
# <a name="clearcollectiont-activity-designer"></a>ClearCollection\<T > Projektant działań

**ClearCollection\<T >** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.ClearCollection%601> działania.

## <a name="the-clearcollectiont-activity"></a>ClearCollection\<T > działania

<xref:System.Activities.Statements.ClearCollection%601> Działania usuwa wszystkie elementy dla określonej kolekcji.

### <a name="using-the-clearcollectiont-activity-designer"></a>Przy użyciu ClearCollection\<T > Projektant działań

**ClearCollection\<T >** Projektant działań można znaleźć w **kolekcji** kategorii **przybornika**, które jest dostępne po kliknięciu  **Przybornik** karcie projektanta przepływów pracy. Można także wybrać **przybornika** z **widoku** menu lub naciśnij klawisz **Ctrl**+**Alt** + **X**.

**ClearCollection\<T >** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie działania są umieszczone, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Projektant działań porzucenie tworzy <xref:System.Activities.Statements.ClearCollection%601> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z ClearCollection < Int32\>. (Domyślnie *elementu TypeArgument* jest **Int32**. Elementu TypeArgument można zmienić w siatce właściwości.) <xref:System.Activities.Activity.DisplayName%2A> Wartość można edytować w nagłówku **ClearCollection < T\>**  Projektant działań lub **DisplayName** pola siatki właściwości. Inne właściwości, należy edytować na siatce właściwości.

### <a name="the-clearcollectiont-properties"></a>ClearCollection\<T > Właściwości

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.ClearCollection%601> właściwości oraz opis korzystania z nich w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalne przyjazna nazwa <xref:System.Activities.Statements.ClearCollection%601> działania. Wartość domyślna to ClearCollection < Int32\>. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagane, jest najlepszym rozwiązaniem jej użyć.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Określa kolekcję można wyczyścić elementów. Ta kolekcja jest typu **ICollection\<elementu TypeArgument >.** Aby określić kolekcji, wpisz wyrażenie języka Visual Basic w siatce właściwości.|
|*TypeArgument*|True|Określa typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601>. Domyślnie to *elementu TypeArgument* ustawiono typ **Int32**. Aby zmienić typ, zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)