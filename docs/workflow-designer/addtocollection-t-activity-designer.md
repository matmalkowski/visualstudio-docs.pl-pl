---
title: "AddToCollection&lt;T&gt; Projektant działań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: aa1579629e68931ca0841117e07e227e879f331c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="addtocollectionlttgt-activity-designer"></a>AddToCollection&lt;T&gt; Projektant działań
**AddToCollection\<T >** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.AddToCollection%601> działania.  
  
## <a name="the-addtocollectiont-activity"></a>AddToCollection < T\> działania  
 <xref:System.Activities.Statements.AddToCollection%601> Działania dodaje element do kolekcji.  
  
### <a name="using-the-addtocollectiont-activity-designer"></a>Przy użyciu AddToCollection\<T > Projektant działań  
 **AddToCollection\<T >** Projektant działań można znaleźć w **kolekcji** kategorii **przybornika**, które jest dostępne po kliknięciu  **Przybornik** karcie [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)  
  
 **AddToCollection\<T >** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań zwykle są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.AddToCollection%601> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z AddToCollection < Int32\>. (Domyślnie *elementu TypeArgument* jest **Int32**. Można to zmienić w siatce właściwości.) <xref:System.Activities.Activity.DisplayName%2A> Wartość można edytować w nagłówku **AddToCollection < T\>**  Projektant działań lub **DisplayName** pola siatki właściwości. Inne właściwości, należy edytować na siatce właściwości.  
  
### <a name="the-addtocollectiont-properties"></a>AddToCollection < T\> właściwości  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.AddToCollection%601> właściwości oraz opis korzystania z nich w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.AddToCollection%601> działania. Wartość domyślna to AddToCollection < Int32\>. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagane, jest najlepszym rozwiązaniem jej użyć.|  
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Wartość true|Element do dodania do kolekcji\<T >. Ten element jest typu *T*, która jest typu *elementu TypeArgument*. Aby określić elementu, wpisz w wyrażeniu języka Visual Basic w siatce właściwości.|  
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Wartość true|Kolekcja, do której można dodać elementu. Ta kolekcja jest typu **implementację interfejsu ICollection < elementu TypeArgument\>**. Aby określić kolekcji, wpisz wyrażenie języka Visual Basic w siatce właściwości.|  
|*Elementu TypeArgument*|Wartość true|Typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601>. Domyślnie to *elementu TypeArgument* ustawiono typ **Int32**. Aby zmienić typ, zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcja](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T > Projektant działań](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)