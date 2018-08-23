---
title: RemoveFromCollection&lt;T&gt; projektanta działań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 9cb791c64909cf8c494b5c5b3dc481f106dc8cf1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678064"
---
# <a name="removefromcollectionlttgt-activity-designer"></a>RemoveFromCollection&lt;T&gt; Projektant działań
**RemoveFromCollection\<T >** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.RemoveFromCollection%601> działania.  
  
## <a name="the-removefromcollectiont-activity"></a>RemoveFromCollection\<T > działania  
 <xref:System.Activities.Statements.RemoveFromCollection%601> Działanie usuwa określony element z określonej kolekcji.  
  
### <a name="using-the-removefromcollectiont-activity-designer"></a>Za pomocą RemoveFromCollection\<T > Projektant działań  
 **RemoveFromCollection\<T >** projektanta działań można znaleźć w **kolekcji** kategorii **przybornika**, które jest dostępne po kliknięciu **Przybornika** karcie [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać **narzędzi** z **widoku** menu lub klawiszy CTRL + ALT + X.)  
  
 **RemoveFromCollection\<T >** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działań są zazwyczaj umieszczane, takich jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.RemoveFromCollection%601> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> z RemoveFromCollection\<Int32 >. <xref:System.Activities.Activity.DisplayName%2A> Wartość może być edytowana w nagłówku **RemoveFromCollection\<T >** projektanta działań lub **DisplayName** pola siatki właściwości. W siatce właściwości, należy edytować inne właściwości.  
  
### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection\<T > Właściwości  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.RemoveFromCollection%601> właściwości i w tym artykule opisano, jak są używane w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalna nazwa przyjazna <xref:System.Activities.Statements.RemoveFromCollection%601> działania. Wartość domyślna to RemoveFromCollection\<Int32 >.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest bezwzględnie konieczne jest najlepszym rozwiązaniem, aby użyć jednego.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|Element do dodania do **kolekcji\<T >**. Ten element jest typu *T*, która jest typu *elementu typeargument w języku*. Aby określić element, wpisz wyrażenie języka Visual Basic w siatce właściwości.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|Kolekcja, do którego ma zostać dodany element. Ta kolekcja jest typu **ICollection\<elementu typeargument w języku >.** Aby określić kolekcję, wpisz wyrażenie języka Visual Basic w siatce właściwości.|  
|*TypeArgument*|True|Typu T z elementów znajdujących się w <xref:System.Collections.Generic.ICollection%601>. Domyślnie to *elementu typeargument w języku* ustawiono typ **Int32**. Aby zmienić typ, zmień wartość *elementu typeargument w języku* w polu kombi w siatce właściwości.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Wartość, która wskazuje, czy określony element został usunięty z kolekcji. Aby określić zmienną, aby powiązać wynik, wpisz w zmiennej w siatce właściwości|  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcja](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)