---
title: 'CA2241: Dostarcz poprawne argumenty do metod formatowania'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02f01df5ac774a22c5a0b9b22c68650f17d3e8c0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Dostarcz poprawne argumenty do metod formatowania
|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 `format` Argument przekazany do metody, takie jak ciągu <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, lub <xref:System.String.Format%2A?displayProperty=fullName> nie zawiera elementu formatu, który odpowiada każdy argument obiekt, lub na odwrót.

## <a name="rule-description"></a>Opis reguły
 Argumenty do metod, takich jak <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, i <xref:System.String.Format%2A> składają się z ciągu formatu następuje kilka <xref:System.Object?displayProperty=fullName> wystąpień. Ciąg formatu, który składa się z tekstu i elementów osadzonych format w formie {indeksu [, wyrównanie] [: formatString]}. "index" jest liczony od zera liczba całkowita, która wskazuje, które obiekty do formatowania. Jeśli obiekt nie ma odpowiedni indeks w ciągu formatu, obiekt zostanie zignorowany. Jeśli obiekt określony przez "index" nie istnieje, <xref:System.FormatException?displayProperty=fullName> jest zgłaszany w czasie wykonywania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, podaje elementu formatu dla każdego obiektu argumentu i podać argument obiektu dla każdego elementu formatu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia dwa naruszenia reguły.

 [!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
 [!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]