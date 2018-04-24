---
title: 'CA2231: Przeciąż operator equals przy zastępowaniu ValueType.Equals'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
- OverrideOperatorEqualsOnOverridingValueTypeEquals
helpviewer_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81d4a0d571a1692748453d64aa5d4cc3dced87ec
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca2231-overload-operator-equals-on-overriding-valuetypeequals"></a>CA2231: Przeciąż operator equals przy zastępowaniu ValueType.Equals
|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|
|CheckId|CA2231|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ wartości zastępuje <xref:System.Object.Equals%2A?displayProperty=fullName> , ale nie implementuje operatora równości.

## <a name="rule-description"></a>Opis reguły
 W większości języków programowania nie ma żadnej implementacji domyślnego operatora równości (==) dla typów wartości. Jeśli język programowania obsługuje przeciążenia operatorów, należy rozważyć wdrożenie operatora równości. Jego zachowanie powinny być identyczne z <xref:System.Object.Equals%2A>.

 Nie można użyć domyślnego operatora równości w implementacji przeciążenia operatora równości. W ten sposób spowoduje przepełnienie stosu. Aby zaimplementować operator równości, należy użyć metody Object.Equals implementacji. Na przykład:

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać naruszenie tej reguły, zaimplementuj operatora równości.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie od tej reguły; jednak zalecane, jeśli to możliwe zapewnienie operator równości.

## <a name="example"></a>Przykład
 W poniższym przykładzie zdefiniowano typ, który narusza tę regułę.

 [!code-csharp[FxCop.Usage.EqualsGetHashCode#1](../code-quality/codesnippet/CSharp/ca2231-overload-operator-equals-on-overriding-valuetype-equals_1.cs)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA1046: Nie przeciążaj operatora równości w typach referencyjnych](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Przeciążenia operatora mają nazwane alternatywy](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: Operatory powinny mieć symetryczne przeciążenia](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Przesłaniaj metodę Equals w przypadku przeciążania operacji równości operatorów](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Przesłoń metodę GetHashCode przy przesłanianiu metody Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Object.Equals%2A?displayProperty=fullName>