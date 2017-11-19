---
title: "CA1003: Użyj wystąpień obsługi zdarzeń generycznych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cf4f11f3f8fae1130c2cc99468a40ed269c77481
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Użyj wystąpień obsługi zdarzeń generycznych
|||  
|-|-|  
|TypeName|UseGenericEventHandlerInstances|  
|CheckId|CA1003|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Typ zawiera delegata zwracającego typ void, którego sygnatura zawiera dwa parametry (pierwszy obiekt i drugi typ, który można przypisać do EventArgs) i celów zestawu zawierającego [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  
  
## <a name="rule-description"></a>Opis reguły  
 Przed [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], aby przekazać niestandardowe informacje do obsługi zdarzeń nowe delegowanie musiały zadeklarowana, który określa klasę, który został utworzony na podstawie <xref:System.EventArgs?displayProperty=fullName> klasy. Nie jest to już PRAWDA w [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], który wprowadzono <xref:System.EventHandler%601?displayProperty=fullName> delegowanie. Ten delegat ogólny umożliwia każdej klasy, która jest pochodną <xref:System.EventArgs> do można używać razem z obsługi zdarzeń.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, Usuń delegata i zastąp jego użycie przy użyciu <xref:System.EventHandler%601?displayProperty=fullName> delegowanie. Jeśli delegat zostanie wygenerowana automatycznie przez [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kompilatora, zmiany składni deklaracji zdarzenia do użycia <xref:System.EventHandler%601?displayProperty=fullName> delegowanie.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono delegata, który narusza zasady. W [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] przykład komentarze opisują sposób modyfikowania przykład spełniają reguły. Na przykład C# przykład następuje pokazujący modyfikacji kodu.  
  
 [!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
 [!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład usuwa poprzedni przykład, który spełnia reguły i zastępuje jego użycia w deklaracji obiektu delegowanego `ClassThatRaisesEvent` i `ClassThatHandlesEvent` metody przy użyciu <xref:System.EventHandler%601?displayProperty=fullName> delegowanie.  
  
 [!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1005: Unikaj nadużywania parametrów na typach ogólnych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: Nie deklaruj statycznych elementów członkowskich na typach generycznych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: Nie zagnieżdżaj typów generycznych w podpisach elementu członkowskiego](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Generyczne metody powinny dostarczyć parametry typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1007: Używaj danych generycznych wszędzie gdzie jest to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Typy ogólne](/dotnet/csharp/programming-guide/generics/index)