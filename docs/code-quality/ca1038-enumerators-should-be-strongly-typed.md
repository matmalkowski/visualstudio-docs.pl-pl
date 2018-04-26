---
title: 'CA1038: Wyliczenia powinny być silnie typizowane'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b15295b0af35c927e56c37f56a48c86ac4c705af
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Wyliczenia powinny być silnie typizowane
|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Implementuje typu publiczne lub chronione <xref:System.Collections.IEnumerator?displayProperty=fullName> , ale nie zapewnia silnie typizowaną wersję <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> właściwości. Typy pochodzące z następujących typów są wyjątkiem od tej reguły:

-   <xref:System.Collections.CollectionBase?displayProperty=fullName>

-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>

-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Opis reguły
 Ta zasada wymaga <xref:System.Collections.IEnumerator> implementacji, aby zapewnić silnie typizowaną wersję <xref:System.Collections.IEnumerator.Current%2A> właściwości, dzięki czemu użytkownicy nie są wymagane do rzutowania wartości zwracanej typu silne przy korzystaniu z funkcji dostępnych za pośrednictwem interfejsu. Ta zasada przyjęto założenie, że typ, który zawiera <xref:System.Collections.IEnumerator> zawiera kolekcję wystąpień typu, który jest mocniejszy niż element <xref:System.Object>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać naruszenie tej reguły, zaimplementuj właściwości interfejsu jawnie (Zadeklaruj ją jako `IEnumerator.Current`). Dodaj publiczny silnie typizowaną wersję właściwości zadeklarowane jako `Current`, i zwraca obiekt jednoznacznie.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Po zaimplementowaniu opartej na obiektach modułu wyliczającego do użytku z kolekcją opartej na obiektach, takich jak drzewo binarne, Pomiń ostrzeżenie od tej reguły. Typy, które rozszerzają Nowa kolekcja będzie zdefiniować jednoznacznie modułu wyliczającego i ujawniać silnie typizowane właściwości.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano poprawne sposób implementowania silnie typizowaną <xref:System.Collections.IEnumerator> typu.

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA1035: Implementacje interfejsu ICollection mają silnie typizowane składowe](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039: Listy są silnie typizowane](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Collections.IEnumerator?displayProperty=fullName> <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.DictionaryBase?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>