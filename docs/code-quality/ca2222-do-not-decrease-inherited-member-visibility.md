---
title: 'CA2222: Nie zmniejszaj widoczności dziedziczonego elementu członkowskiego'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa8730789ef9f905def64c17081eb44113241282
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: Nie zmniejszaj widoczności dziedziczonego elementu członkowskiego
|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Metoda prywatna w niezamknięty typ ma podpis, który jest taki sam jak publiczny metody zadeklarowanej w typie podstawowym. Metoda prywatna nie jest ostateczny.

## <a name="rule-description"></a>Opis reguły
 Nie należy zmieniać modyfikatora dostępu dla dziedziczonych elementów członkowskich. Zmiana dziedziczonej składowej na prywatną nie uniemożliwia wywołującym uzyskania dostępu do implementacji metody klasy podstawowej. Jeśli element członkowski ma zostać prywatnych i typ jest otwarty, dziedziczenie typów mogą wywoływać ostatniego wykonania publicznej metody w hierarchii dziedziczenia. Jeśli musisz zmienić modyfikator dostępu, metoda powinna być oznaczona jako ostatecznego lub jego typu powinny być zapieczętowane aby zapobiec zastąpieniu metody.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby usunąć naruszenie tej reguły, zmienić dostępu za prywatne. Alternatywnie Jeśli język programowania obsługuje tę funkcję, możesz wprowadzić metody końcowego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typu, który narusza tę regułę.

 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]