---
title: 'CA1013: Przeciąż operator equals przeciążając operatory add i subtract'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11841248192bc9b726076641e1219f54ab526447
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31897434"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: Przeciąż operator equals przeciążając operatory add i subtract
|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony implementuje operatory dodawania lub odejmowania bez implementowania operatora porównania.

## <a name="rule-description"></a>Opis reguły
 Wystąpienie typu można łączyć przy użyciu operacji, takich jak dodawanie i odejmowanie, powinien prawie zawsze definiować, równości do zwrócenia `true` dla dwa wystąpienia, które mają takie same wartości składników.

 Nie można użyć domyślnego operatora równości w implementacji przeciążenia operatora równości. W ten sposób spowoduje przepełnienie stosu. Aby zaimplementować operator równości, należy użyć metody Object.Equals implementacji. Zobacz poniższy przykład.

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
 Aby naprawić naruszenie tej reguły, należy zaimplementować operator równości tak, aby były zgodne ze sobą matematycznie przy użyciu operatorów dodawania i odejmowania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest to bezpieczne Pomiń ostrzeżenie od tej reguły, gdy domyślna implementacja operator równości zapewnia prawidłowe działanie dla typu.

## <a name="example"></a>Przykład
 W poniższym przykładzie zdefiniowano typ (`BadAddableType`), co narusza tę regułę. Tego typu należy zaimplementować operator równości, aby dwa wystąpienia, które mają takie same wartości pola test `true` pod kątem równości. Typ `GoodAddableType` przedstawia poprawiony implementację. Należy pamiętać, że ten typ również implementuje operator nierówności i zastępuje <xref:System.Object.Equals%2A> do zaspokojenia inne zasady. Pełna implementacja może także implementować <xref:System.Object.GetHashCode%2A>.

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]

## <a name="example"></a>Przykład
 Poniższy przykład badań równości przy użyciu wystąpienia typów, które zostały uprzednio zdefiniowane w tym temacie, aby zilustrować domyślnym i poprawne zachowanie dla operatora równości.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]

 W tym przykładzie tworzy następujące dane wyjściowe.

 **Zły typ: {2,2} {2,2} są takie same? Nie**
**typu dobrej: {3,3} {3,3} są takie same? Tak**
**typu dobrej: {3,3} {3,3} są ==?   Tak**
**zły typ: {2,2} {9,9} są takie same? Nie**
**typu dobrej: {3,3} {9,9} są ==?   Brak**
## <a name="see-also"></a>Zobacz też
 [Operatory równości](/dotnet/standard/design-guidelines/equality-operators)