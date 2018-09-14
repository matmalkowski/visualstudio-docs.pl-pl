---
title: 'CA2234: Przekaż obiekty System.Uri zamiast ciągów'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: fcc7994e67e268aff21af925632d2ee9cf102ff4
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547165"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: Przekaż obiekty System.Uri zamiast ciągów

|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Wykonano wywołanie do metody, która ma parametr typu ciąg, którego nazwa zawiera "uri", "Uri", "urn", "Urn", "url" lub "Url"; deklarujący typ metody zawiera odpowiadające przeciążenie metody, która ma <xref:System.Uri?displayProperty=fullName> parametru.

## <a name="rule-description"></a>Opis reguły
 Nazwa parametru jest podzielony na tokeny oparte na Konwencji camelcase, a następnie każdy token jest sprawdzane w celu sprawdzenia, czy jest ona równa "uri", "Uri", "urn", "Urn", "url" lub "Url". W przypadku dopasowania parametru zakłada, że do reprezentowania identyfikatora uniform resource identifier (URI). Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. <xref:System.Uri> Klasa udostępnia te usługi w bezpieczny sposób. Gdy istnieje możliwość wyboru między dwa przeciążenia, które różnią się tylko do reprezentacji identyfikatora URI, użytkownik powinien wybrać przeciążenia, które przyjmuje <xref:System.Uri> argumentu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy wywołać przeciążenia, które przyjmuje <xref:System.Uri> argumentu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli parametr typu ciąg nie reprezentuje identyfikator URI.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano metodę `ErrorProne`, który narusza regułę i metody `SaferWay`, który prawidłowo wywołuje <xref:System.Uri> przeciążenia.

 [!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
 [!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
 [!code-csharp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1057: Przeciążenia identyfikatora URI w postaci ciągu wywołują przeciążenia metody System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056: Właściwości identyfikatora URI nie powinny być ciągami](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: Wartości zwracane identyfikatora URI nie powinny być ciągami](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)