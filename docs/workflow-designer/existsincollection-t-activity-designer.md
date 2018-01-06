---
title: "ExistsInCollection&lt;T&gt; Projektant działań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: bcd3028335ed48f4eba8c647f124d0d537deaf3c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="existsincollectionlttgt-activity-designer"></a>ExistsInCollection&lt;T&gt; Projektant działań
**ExistsInCollection\<T >** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.ExistsInCollection%601> działania.  
  
## <a name="the-existsincollectiont-activity"></a>ExistsInCollection < T\> działania  
 <xref:System.Activities.Statements.ExistsInCollection%601> Działania określa, czy określony element istnieje w określonej kolekcji.  
  
### <a name="using-the-existsincollectiont-activity-designer"></a>Przy użyciu ExistsInCollection\<T > Projektant działań  
 **ExistsInCollection\<T >** Projektant działań można znaleźć w **kolekcji** kategorii **przybornika**, które jest dostępne po kliknięciu  **Przybornik** karcie [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)  
  
 **ExistsInCollection\<T >** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań są zwykle umieszczane, takich jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.ExistsInCollection%601> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z ExistsInCollection < Int32\>. (Domyślnie *elementu TypeArgument* jest **Int32**. Go można zmienić w siatce właściwości.)  <xref:System.Activities.Activity.DisplayName%2A> Wartość można edytować w nagłówku **ExistsInCollection < T\>**  Projektant działań lub **DisplayName** pola siatki właściwości. Inne właściwości, należy edytować na siatce właściwości.  
  
### <a name="the-existsincollectiont-properties"></a>ExistsInCollection < T\> właściwości  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.ExistsInCollection%601> właściwości oraz opis korzystania z nich w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.ExistsInCollection%601> działania. Wartość domyślna to ExistsInCollection < Int32\>. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagane, jest najlepszym rozwiązaniem jej użyć.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Wartość true|Element do dodania do kolekcji\<T >. Ten element jest typu *T* jest typu *elementu TypeArgument*. Aby określić elementu, wpisz wyrażenie języka Visual Basic w siatce właściwości.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Wartość true|Kolekcja, do której można dodać elementu. Ta kolekcja jest typu **implementację interfejsu ICollection < elementu TypeArgument\>.** Aby określić kolekcji, wpisz wyrażenie języka Visual Basic w siatce właściwości.|  
|*Elementu TypeArgument*|Wartość true|Typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601>. Domyślnie to *elementu TypeArgument* ustawiono typ **Int32**. Aby zmienić typ, zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Wartość, która wskazuje, czy określony element istnieje w kolekcji. Aby określić zmienną, aby powiązać wynik, typu zmienną języka Visual Basic w siatce właściwości.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcja](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)   
 [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)