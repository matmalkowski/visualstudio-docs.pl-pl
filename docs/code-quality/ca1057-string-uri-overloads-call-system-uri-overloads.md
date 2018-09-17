---
title: 'CA1057: Przeciążenia identyfikatora URI, który jest ciągiem, wywołują przeciążenia System.Uri'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 44130632cb416bf03819ddff13b797ac3b799354
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547179"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Przeciążenia identyfikatora URI, który jest ciągiem, wywołują przeciążenia System.Uri

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Typ deklaruje przeciążenia metody, które różnią się jedynie zastąpienia ciąg parametrem <xref:System.Uri?displayProperty=fullName> parametr i przeciążenia, które przyjmuje parametr typu ciąg, nie wywołuje przeciążenia przyjmującego <xref:System.Uri> parametru.

## <a name="rule-description"></a>Opis reguły
 Ponieważ przeciążenia różnią się tylko ciąg lub <xref:System.Uri> parametr ciągu zakłada się, że reprezentują jednolity identyfikator zasobów (URI). Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. <xref:System.Uri> Klasa udostępnia te usługi w bezpieczny sposób. Aby czerpać korzyści ze <xref:System.Uri> klasy, należy wywołać przeciążenie typu ciąg <xref:System.Uri> przeciążenia, przy użyciu argumentu ciągu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Ponownie metody, która używa reprezentację ciągu identyfikatora URI, tak aby tworzy wystąpienie <xref:System.Uri> przy użyciu argumentu ciągu, a następnie przekazuje <xref:System.Uri> obiekt do przeciążenia, które ma <xref:System.Uri> parametru.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli parametr typu ciąg nie reprezentuje identyfikator URI.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje przeciążenie dla typu string poprawnie zaimplementowana.

 [!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
 [!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2234: Przekaż obiekty System.Uri zamiast ciągów](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: Właściwości identyfikatora URI nie powinny być ciągami](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: Wartości zwracane identyfikatora URI nie powinny być ciągami](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)