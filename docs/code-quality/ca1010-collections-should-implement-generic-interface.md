---
title: 'CA1010: Kolekcje powinny implementować interfejs generyczny'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb43481b80726171414fab6b6a65fee8a5e29cb0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Kolekcje powinny implementować interfejs generyczny
|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Widoczne na zewnątrz typ implementuje <xref:System.Collections.IEnumerable?displayProperty=fullName> interfejsu, ale nie implementuje <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interfejsu i celów zestawu zawierającego [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]. Ta zasada powoduje ignorowanie typów, które implementują <xref:System.Collections.IDictionary?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 Aby poszerzyć użyteczność kolekcji, zaimplementuj jeden z interfejsów kolekcji generycznej. Następnie Kolekcja może być używana do wypełniania typy kolekcji ogólnych, takie jak następujące:

-   <xref:System.Collections.Generic.List%601?displayProperty=fullName>

-   <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>

-   <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, implementować jeden z następujących interfejsów kolekcji ogólnych:

-   <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>

-   <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

-   <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie od tej reguły; Kolekcja będzie jednak bardziej ograniczone użycie.

## <a name="example-violation"></a>Przykład naruszenie

### <a name="description"></a>Opis
 W poniższym przykładzie przedstawiono klasy (typ odwołania), która pochodzi z nieogólnego `CollectionBase` klasy, która narusza tę regułę.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

### <a name="comments"></a>Komentarze
 Aby naprawić naruszenie to naruszenie, powinien implementować interfejsów ogólnych lub zmień klasy podstawowej typu, który już implementuje zarówno ogólne i inny niż ogólny interfejsów, takich jak `Collection<T>` klasy.

## <a name="fix-by-base-class-change"></a>Rozwiązać przez zmianę w klasie podstawowej

### <a name="description"></a>Opis
 Poniższy przykład poprawia naruszenie, zmieniając klasy podstawowej kolekcji z nieogólnego `CollectionBase` klasy ogólnej `Collection<T>` (`Collection(Of T)` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) klasy.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

### <a name="comments"></a>Komentarze
 Zmiana klasy podstawowej klasy już zwolnione jest uznawane za istotną zmianę dla istniejących konsumentów.

## <a name="fix-by-interface-implementation"></a>Usuń przez implementację interfejsu

### <a name="description"></a>Opis
 Poniższy przykład poprawia naruszenie zaimplementowanie te interfejsy ogólne: `IEnumerable<T>`, `ICollection<T>`, i `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)`, i `IList(Of T)` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA1005: Unikaj nadużywania parametrów w typach ogólnych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1000: Nie deklaruj składowych statycznych w typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Metody ogólne powinny udostępniać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Użyj wystąpień ogólnej procedury obsługi zdarzeń](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Używaj typów ogólnych wszędzie tam, gdzie jest to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Zobacz też
 [Typy ogólne](/dotnet/csharp/programming-guide/generics/index)