---
title: 'CA1057: Ciąg przeciążenia identyfikatora URI wywołują przeciążenia System.Uri | Dokumentacja firmy Microsoft'
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
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7cb8f559e4290c27c7b241bc15daf6ff79298372
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42900921"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Przeciążenia identyfikatora URI, który jest ciągiem, wywołują przeciążenia System.Uri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1057: przeciążenia identyfikatora URI z ciągu wywołują przeciążenia System.Uri](https://docs.microsoft.com/visualstudio/code-quality/ca1057-string-uri-overloads-call-system-uri-overloads).

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ deklaruje przeciążenia metody, które różnią się jedynie zastąpienia ciąg parametrem <xref:System.Uri?displayProperty=fullName> parametr i przeciążenia, które przyjmuje parametr typu ciąg, nie wywołuje przeciążenia przyjmującego <xref:System.Uri> parametru.

## <a name="rule-description"></a>Opis reguły
 Ponieważ przeciążenia różnią się tylko ciąg /<xref:System.Uri> parametr ciągu zakłada się, że reprezentują jednolity identyfikator zasobów (URI). Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. <xref:System.Uri> Klasa udostępnia te usługi w bezpieczny sposób. Aby czerpać korzyści ze <xref:System.Uri> klasy, należy wywołać przeciążenie typu ciąg <xref:System.Uri> przeciążenia, przy użyciu argumentu ciągu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Ponownej implementacji metody, która używa reprezentację ciągu identyfikatora URI, tak aby tworzy wystąpienie <xref:System.Uri> przy użyciu argumentu ciągu, a następnie przekazuje <xref:System.Uri> obiekt do przeciążenia, które ma <xref:System.Uri> parametru.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli parametr typu ciąg nie reprezentuje identyfikator URI.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje przeciążenie dla typu string poprawnie zaimplementowana.

 [!code-cpp[FxCop.Design.CallUriOverload#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cpp/FxCop.Design.CallUriOverload.cpp#1)]
 [!code-csharp[FxCop.Design.CallUriOverload#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cs/FxCop.Design.CallUriOverload.cs#1)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/vb/FxCop.Design.CallUriOverload.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2234: Przekaż obiekty System.Uri zamiast ciągów](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: Właściwości identyfikatora URI nie powinny być ciągami](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: Wartości zwracane identyfikatora URI nie powinny być ciągami](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)



