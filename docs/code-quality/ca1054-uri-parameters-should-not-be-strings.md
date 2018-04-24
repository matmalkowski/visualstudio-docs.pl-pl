---
title: 'CA1054: Parametry identyfikatora URI nie powinny być ciągami'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 98e042d65e0c7530c35134f79357565e1b88f4de
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054: Parametry identyfikatora URI nie powinny być ciągami
|||
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ deklaruje metody z parametru ciągu, których nazwa zawiera "uri", "Identyfikator Uri", "urn", "Urn", "url" lub "Url" i typ nie deklaruje odpowiedniego przeciążenia, które przyjmuje <xref:System.Uri?displayProperty=fullName> parametru.

## <a name="rule-description"></a>Opis reguły
 Ta zasada dzieli nazwę parametru na tokeny na podstawie Konwencji mieszanej wielkości liter i sprawdza, czy każdy token jest równa "uri", "Identyfikator Uri", "urn", "Urn", "url" lub "Url". Jeśli istnieje dopasowanie, reguła przyjęto założenie, że parametr reprezentuje identyfikator uniform resource identifier (URI). Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. Jeśli metoda pobiera reprezentację ciągu identyfikatora URI, odpowiednie przeciążenie należy przyznać pobierającej wystąpienia <xref:System.Uri> klasy, która dostarcza tych usług w sposób bezpieczny i bezpieczne.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby usunąć naruszenie tej reguły, zmienić parametru <xref:System.Uri> wpisz; jest to istotne zmiany. Alternatywnie Udostępnij przeciążenie metody, która przyjmuje <xref:System.Uri> parametru; jest to zmiana nierozdzielający.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli parametr nie reprezentuje identyfikator URI.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono typu `ErrorProne`, który narusza tę regułę, a typem, `SaferWay`, odpowiadającej reguły.

 [!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA1056: Właściwości identyfikatora URI nie powinny być ciągami](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1055: Wartości zwracane identyfikatora URI nie powinny być ciągami](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: Przekaż obiekty System.Uri zamiast ciągów](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: Przeciążenia identyfikatora URI w postaci ciągu wywołują przeciążenia metody System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)