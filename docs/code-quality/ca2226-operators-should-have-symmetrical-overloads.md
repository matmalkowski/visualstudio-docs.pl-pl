---
title: 'CA2226: Operatory powinny być przeciążane symetrycznie'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 98f5653d326c257e46becd2d7f8ad1091dfcf0c7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: Operatory powinny być przeciążane symetrycznie
|||
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ implementuje operator równości lub nierówności, ale nie implementuje operatora przeciwnego.

## <a name="rule-description"></a>Opis reguły
 Nie ma w żadnym gdzie równości i nierówności jest stosowana do wystąpień typu i przeciwną operator jest niezdefiniowany. Typy zwykle implementować operator nierówności zwracając o zanegowaną wartość operatora równości.

 Kompilator języka C# generuje błąd dla naruszeń tej reguły.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać naruszenie tej reguły, implementują równości i nierówności operatorów lub Usuń ten, który jest obecny.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Danego typu nie będą działać w sposób zgodny z [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

## <a name="related-rules"></a>Powiązanych reguł
 [CA1046: Nie przeciążaj operatora równości w typach referencyjnych](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Przeciążenia operatora mają nazwane alternatywy](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2224: Przesłaniaj metodę Equals w przypadku przeciążania operacji równości operatorów](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Przesłoń metodę GetHashCode przy przesłanianiu metody Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)