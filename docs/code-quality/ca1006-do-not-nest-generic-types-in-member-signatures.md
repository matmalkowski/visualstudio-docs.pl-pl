---
title: 'CA1006: Nie zagnieżdżaj typów generycznych w podpisach elementu członkowskiego'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotNestGenericTypesInMemberSignatures
- CA1006
helpviewer_keywords:
- CA1006
- DoNotNestGenericTypesInMemberSignatures
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 120acca8486d65962a5d8e3cd26a05ae8cc5ac78
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1006-do-not-nest-generic-types-in-member-signatures"></a>CA1006: Nie zagnieżdżaj typów generycznych w podpisach elementu członkowskiego
|||
|-|-|
|TypeName|DoNotNestGenericTypesInMemberSignatures|
|CheckId|CA1006|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Widoczne na zewnątrz element członkowski ma podpis zawierający argumentu typu zagnieżdżonego.

## <a name="rule-description"></a>Opis reguły
 Argument typu zagnieżdżonego jest argumentem typu, który jest również typem ogólnym. Aby wywołać element członkowski, którego podpis zawiera argument typu zagnieżdżonego, użytkownik musi zainicjować wystąpienie pierwszego typu ogólnego i przekazać go do konstruktora drugiego typu ogólnego. Wymagana procedura oraz składnia są złożone i należy ich unikać.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby usunąć naruszenie tej reguły, zmienić projekt, aby usunąć argumentu typu zagnieżdżonego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Udostępnia typy ogólne w składni, które jest łatwe do zrozumienia i użycia zmniejsza czas, który jest wymagany, aby dowiedzieć się więcej i zwiększa szybkość przyjęcia nowych bibliotek.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono metodę, która narusza regułę i składnię, która jest wymagana, aby wywołać metodę naruszających zasady.

 [!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
 [!code-csharp[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA1005: Unikaj nadużywania parametrów w typach ogólnych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Nie deklaruj składowych statycznych w typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1004: Metody ogólne powinny udostępniać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Użyj wystąpień ogólnej procedury obsługi zdarzeń](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Używaj typów ogólnych wszędzie tam, gdzie jest to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Zobacz też
 [Typy ogólne](/dotnet/csharp/programming-guide/generics/index)