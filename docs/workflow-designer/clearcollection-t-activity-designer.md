---
title: "ClearCollection&lt;T&gt; Projektant działań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 54cac37194a3b96d464b886c14bfbbbde4a1f861
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="clearcollectionlttgt-activity-designer"></a>ClearCollection&lt;T&gt; Projektant działań
**ClearCollection\<T >** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.ClearCollection%601> działania.  
  
## <a name="the-clearcollectiont-activity"></a>ClearCollection < T\> działania  
 <xref:System.Activities.Statements.ClearCollection%601> Działania usuwa wszystkie elementy dla określonej kolekcji.  
  
### <a name="using-the-clearcollectiont-activity-designer"></a>Przy użyciu ClearCollection\<T > Projektant działań  
 **ClearCollection\<T >** Projektant działań można znaleźć w **kolekcji** kategorii **przybornika**, które jest dostępne po kliknięciu  **Przybornik** karcie [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)  
  
 **ClearCollection\<T >** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań zwykle są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.ClearCollection%601> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z ClearCollection < Int32\>. (Domyślnie *elementu TypeArgument* jest **Int32**. Można to zmienić w siatce właściwości.) <xref:System.Activities.Activity.DisplayName%2A> Wartość można edytować w nagłówku **ClearCollection < T\>**  Projektant działań lub **DisplayName** pola siatki właściwości. Inne właściwości, należy edytować na siatce właściwości.  
  
### <a name="the-clearcollectiont-properties"></a>ClearCollection < T\> właściwości  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.ClearCollection%601> właściwości oraz opis korzystania z nich w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalne przyjazna nazwa <xref:System.Activities.Statements.ClearCollection%601> działania. Wartość domyślna to ClearCollection < Int32\>. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagane, jest najlepszym rozwiązaniem jej użyć.|  
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|Wartość true|Określa kolekcję można wyczyścić elementów. Ta kolekcja jest typu **ICollection\<elementu TypeArgument >.** Aby określić kolekcji, wpisz wyrażenie języka Visual Basic w siatce właściwości.|  
|*Elementu TypeArgument*|Wartość true|Określa typ T elementów zawartych w <xref:System.Collections.Generic.ICollection%601>. Domyślnie to *elementu TypeArgument* ustawiono typ **Int32**. Aby zmienić typ, zmień wartość *elementu TypeArgument* w polu kombi w siatce właściwości.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcja](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)