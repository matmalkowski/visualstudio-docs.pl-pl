---
title: Projektant przepływu pracy — RemoveFromCollection&lt;T&gt; Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b6aedee945ab19201406ce26183db4e2f3519263
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31977962"
---
# <a name="removefromcollectiont-activity-designer"></a>RemoveFromCollection\<T > Projektant działań

**RemoveFromCollection\<T >** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.RemoveFromCollection%601> działania.

## <a name="the-removefromcollectiontactivity"></a>RemoveFromCollection\<T > działania
 <xref:System.Activities.Statements.RemoveFromCollection%601> Działania usuwa określony element z danej kolekcji.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Przy użyciu RemoveFromCollection\<T > Projektant działań
 **RemoveFromCollection\<T >** Projektant działań można znaleźć w **kolekcji** kategorii **przybornika**, które jest dostępne po kliknięciu **Przybornika** karty w Projektancie przepływów pracy (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)

 **RemoveFromCollection\<T >** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie działań zwykle są umieszczane, takich jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.RemoveFromCollection%601> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z RemoveFromCollection < Int32\>. <xref:System.Activities.Activity.DisplayName%2A> Wartość można edytować w nagłówku **RemoveFromCollection < T\>**  Projektant działań lub **DisplayName** pola siatki właściwości. Inne właściwości, należy edytować na siatce właściwości.

### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection < T\> właściwości
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.RemoveFromCollection%601> właściwości oraz opis korzystania z nich w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalne przyjazna nazwa <xref:System.Activities.Statements.RemoveFromCollection%601> działania. Wartość domyślna to RemoveFromCollection < Int32\>.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem jej użyć.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|Element do dodania do **kolekcji\<T >**. Ten element jest typu *T*, która jest typu *elementu TypeArgument*. Aby określić elementu, wpisz w wyrażeniu języka Visual Basic w siatce właściwości.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|Kolekcja, do której można dodać elementu. Ta kolekcja jest typu **implementację interfejsu ICollection < elementu TypeArgument\>.** Aby określić kolekcji, wpisz w wyrażeniu języka Visual Basic w siatce właściwości.|
|*TypeArgument*|True|Typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601>. Domyślnie to *elementu TypeArgument* ustawiono typ **Int32**. Aby zmienić typ, zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Wartość, która wskazuje, czy określony element został usunięty z kolekcji. Aby określić zmienną, aby powiązać wynik, wpisz w zmiennej w siatce właściwości|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)