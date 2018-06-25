---
title: Projektant przepływu pracy — ExistsInCollection&lt;T&gt; Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83ae11cad7e132bd13bb930607abd40011e0392a
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756470"
---
# <a name="existsincollectiont-activity-designer"></a>ExistsInCollection\<T > Projektant działań

**ExistsInCollection\<T >** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.ExistsInCollection%601> działania.

## <a name="the-existsincollectiont-activity"></a>ExistsInCollection\<T > działania
 <xref:System.Activities.Statements.ExistsInCollection%601> Działania określa, czy określony element istnieje w określonej kolekcji.

### <a name="using-the-existsincollectiont-activity-designer"></a>Przy użyciu ExistsInCollection\<T > Projektant działań
 **ExistsInCollection\<T >** Projektant działań można znaleźć w **kolekcji** kategorii **przybornika**, które jest dostępne po kliknięciu  **Przybornik** karcie projektanta przepływów pracy. Można także wybrać **przybornika** z **widoku** menu lub naciśnij klawisz **Ctrl**+**Alt** + **X**.

 **ExistsInCollection\<T >** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie działania są zwykle umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.ExistsInCollection%601> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z ExistsInCollection < Int32\>. (Domyślnie *elementu TypeArgument* jest **Int32**. Go można zmienić w siatce właściwości.)  <xref:System.Activities.Activity.DisplayName%2A> Wartość można edytować w nagłówku **ExistsInCollection < T\>**  Projektant działań lub **DisplayName** pola siatki właściwości. Inne właściwości, należy edytować na siatce właściwości.

### <a name="the-existsincollectiont-properties"></a>ExistsInCollection\<T > Właściwości
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.ExistsInCollection%601> właściwości oraz opis korzystania z nich w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.ExistsInCollection%601> działania. Wartość domyślna to ExistsInCollection < Int32\>. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagane, jest najlepszym rozwiązaniem jej użyć.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|Element do dodania do kolekcji\<T >. Ten element jest typu *T* jest typu *elementu TypeArgument*. Aby określić elementu, wpisz wyrażenie języka Visual Basic w siatce właściwości.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|Kolekcja, do której można dodać elementu. Ta kolekcja jest typu **implementację interfejsu ICollection < elementu TypeArgument\>.** Aby określić kolekcji, wpisz wyrażenie języka Visual Basic w siatce właściwości.|
|*TypeArgument*|True|Typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601>. Domyślnie to *elementu TypeArgument* ustawiono typ **Int32**. Aby zmienić typ, zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Wartość, która wskazuje, czy określony element istnieje w kolekcji. Aby określić zmienną, aby powiązać wynik, typu zmienną języka Visual Basic w siatce właściwości.|

## <a name="see-also"></a>Zobacz także

- [Kolekcja](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)