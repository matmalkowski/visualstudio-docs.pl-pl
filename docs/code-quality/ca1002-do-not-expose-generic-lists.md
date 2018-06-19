---
title: 'CA1002: Nie ujawniaj list generycznych'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a2131ef8cb0b8f0ba540d7403d7c5f8dbb8b89df
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31901099"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: Nie ujawniaj list generycznych
|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ zawiera widoczne na zewnątrz elementu członkowskiego, który jest <xref:System.Collections.Generic.List%601?displayProperty=fullName> wpisz zwraca <xref:System.Collections.Generic.List%601?displayProperty=fullName> typu lub którego sygnatura zawiera <xref:System.Collections.Generic.List%601?displayProperty=fullName> parametru.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> jest kolekcją ogólnego, który zaprojektowano pod kątem wydajności i dziedziczenie nie. <xref:System.Collections.Generic.List%601?displayProperty=fullName> nie zawiera wirtualnych elementów członkowskich, które ułatwiają zmianę zachowania dziedziczonej klasie. Następujące kolekcje ogólne są przeznaczone dla dziedziczenia i powinny zostać ujawnione zamiast <xref:System.Collections.Generic.List%601?displayProperty=fullName>.

-   <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

-   <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby usunąć naruszenie tej reguły, zmienić <xref:System.Collections.Generic.List%601?displayProperty=fullName> typu ogólnego kolekcji, które jest przeznaczone do dziedziczenia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżenie od tej reguły, chyba że zestaw, który wywołuje to ostrzeżenie jest nie należy traktować jako biblioteki do ponownego użycia. Na przykład byłoby bezpiecznie pominąć to ostrzeżenie w aplikacji wydajność dostosowana gdzie poprawiać wydajność uzyskane z użycia list ogólnych.

## <a name="related-rules"></a>Powiązanych reguł
 [CA1005: Unikaj nadużywania parametrów w typach ogólnych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Nie deklaruj składowych statycznych w typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Metody ogólne powinny udostępniać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Użyj wystąpień ogólnej procedury obsługi zdarzeń](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Używaj typów ogólnych wszędzie tam, gdzie jest to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Zobacz też
 [Typy ogólne](/dotnet/csharp/programming-guide/generics/index)