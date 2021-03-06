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
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e8f0f3d40ea24828430983efd2cf39f4fa399238
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547727"
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
 W przypadku wystąpień typu mogą być połączone za pomocą operacji, takich jak dodawanie i odejmowanie, prawie zawsze należy zdefiniować równości, aby zwrócić `true` dla dwóch wystąpień, które mają takie same wartości składowych.

 Nie można używać operatora równości Domyślna implementacja Przeciążony operator równości. Ten sposób spowoduje przepełnienie stosu. Aby zaimplementować operator równości, użyj metody metody Object.Equals w danej implementacji. Zobacz poniższy przykład.

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
 Aby naprawić naruszenie tej zasady, implementuje operator równości, aby były ze sobą matematycznie zgodne z operatorów dodawania i odejmowania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, gdy domyślna implementacja operatora równości udostępnia poprawne zachowanie dla typu.

## <a name="example"></a>Przykład
 W poniższym przykładzie zdefiniowano typ (`BadAddableType`) który narusza tę regułę. Ten typ należy zaimplementować operator równości, który ma być sprawia, że dwa wystąpienia, mających takie same wartości pola, testowanie `true` pod kątem równości. Typ `GoodAddableType` przedstawia implementację poprawiony. Zwróć uwagę, że ten typ także implementuje operator nierówności i zastępuje <xref:System.Object.Equals%2A> spełniać inne zasady. Pełne wdrożenie będzie także implementować <xref:System.Object.GetHashCode%2A>.

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]

## <a name="example"></a>Przykład
 Poniższy przykład sprawdza pod kątem równości, za pomocą wystąpień typów, które zostały wcześniej zdefiniowane w tym temacie, aby zilustrować domyślne i poprawnego zachowania dla operatora równości.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]

Ten przykład generuje następujące wyniki:

```txt
Bad type:  {2,2} {2,2} are equal? No
Good type: {3,3} {3,3} are equal? Yes
Good type: {3,3} {3,3} are == ?   Yes
Bad type:  {2,2} {9,9} are equal? No
Good type: {3,3} {9,9} are == ?   No
```

## <a name="see-also"></a>Zobacz także

- [Operatory równości](/dotnet/standard/design-guidelines/equality-operators)