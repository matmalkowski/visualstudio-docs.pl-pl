---
title: 'CA1309: Użyj porządkowego StringComparison'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 964dfee8b8ed78de76ead4ee5eda63fe0a49a72c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Użyj porządkowego StringComparison
|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Operacja porównywania ciągów, która jest nonlinguistic nie ustawia <xref:System.StringComparison> albo parametr **numer** lub **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Opis reguły
 Ciąg wielu operacji najważniejszych <xref:System.String.Compare%2A?displayProperty=fullName> i <xref:System.String.Equals%2A?displayProperty=fullName> metod, zapewnia teraz przeciążenia, które akceptuje <xref:System.StringComparison?displayProperty=fullName> wartość wyliczenia jako parametr.

 Po określeniu albo **wartości StringComparison.Ordinal** lub **StringComparison.OrdinalIgnoreCase**, porównania ciągów będzie nonlinguistic. Oznacza to funkcje, które są specyficzne dla języka naturalnego są ignorowane, podczas porównywania decyzji. Oznacza to decyzje są oparte na jednobajtowych porównania i Ignoruj wielkość liter lub równoważność tabel, które mają zdefiniowane przez kultury. W związku z tym przez jawne ustawienie dla parametru albo **wartości StringComparison.Ordinal** lub **StringComparison.OrdinalIgnoreCase**, kodzie często uzyskuje szybkości, zwiększa prawidłowości i staje się bardziej niezawodne.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać naruszenie tej reguły, zmień metodę porównywania ciągów na przeciążenia, które akceptuje <xref:System.StringComparison?displayProperty=fullName> wyliczenie jako parametru i określ **numer** lub **OrdinalIgnoreCase**. Na przykład zmienić `String.Compare(str1, str2)` do `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest to bezpieczne Pomiń ostrzeżenie od tej reguły, gdy biblioteki lub aplikacji ma ograniczone odbiorców lokalnym lub gdy semantykę bieżącej kultury powinny być używane.

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia globalizacji](../code-quality/globalization-warnings.md) [CA1307: Określ StringComparison](../code-quality/ca1307-specify-stringcomparison.md)