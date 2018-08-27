---
title: 'CA2226: Operatory powinny mieć symetryczne przeciążenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6df4a36dae04dadf61790e7be16834dc0d59bdc0
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42900556"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: Operatory powinny być przeciążane symetrycznie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2226: operatory powinny mieć symetryczne przeciążenia](https://docs.microsoft.com/visualstudio/code-quality/ca2226-operators-should-have-symmetrical-overloads).

|||
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ implementuje operator równości lub nierówności, ale nie implementuje operatora przeciwnego.

## <a name="rule-description"></a>Opis reguły
 Nie ma żadnych okoliczności gdzie równości i nierówności ma zastosowanie do wystąpień typu i operatora przeciwnego jest niezdefiniowana. Typy zwykle implementuje operator nierówności, zwracając zanegowaną wartość operatora równości.

 Kompilator języka C# generuje błąd dla naruszenie tej zasady.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, implementują równości i nierówności operatorów lub Usuń ten, który jest obecny.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Danego typu nie będą działać w taki sposób, który jest zgodny z [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

## <a name="related-rules"></a>Powiązane reguły
 [CA1046: Nie przeciążaj operatora równości w typach referencyjnych](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Przeciążenia operatora mają nazwane alternatywy](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2224: Przesłaniaj metodę Equals w przypadku przeciążania operacji równości operatorów](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Przesłoń metodę GetHashCode przy przesłanianiu metody Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)



