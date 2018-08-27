---
title: 'CA1002: Nie ujawniaj list ogólnych | Dokumentacja firmy Microsoft'
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
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 03435b59381f5127aeb7662df16c11e1e085824d
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902722"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: Nie ujawniaj list generycznych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1002: nie ujawniaj list ogólnych](https://docs.microsoft.com/visualstudio/code-quality/ca1002-do-not-expose-generic-lists).

|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ zawiera widoczne na zewnątrz elementu członkowskiego, który jest <xref:System.Collections.Generic.List%601?displayProperty=fullName> wpisz zwraca <xref:System.Collections.Generic.List%601?displayProperty=fullName> typu lub którego podpis zawiera <xref:System.Collections.Generic.List%601?displayProperty=fullName> parametru.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> jest kolekcją ogólną, zapewniające wydajność i nie o dziedziczeniu. <xref:System.Collections.Generic.List%601?displayProperty=fullName> nie zawiera wirtualnych elementów członkowskich, które ułatwiają zmiany zachowania odziedziczoną klasę. Następujące kolekcje ogólne są zaprojektowane do obsługi dziedziczenia i powinny zostać ujawnione zamiast <xref:System.Collections.Generic.List%601?displayProperty=fullName>.

-   <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

-   <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmienić <xref:System.Collections.Generic.List%601?displayProperty=fullName> typu do jednej z kolekcji ogólnych, które jest przeznaczone do obsługi dziedziczenia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły, chyba, że zestaw, który generuje to ostrzeżenie jest nie należy traktować jako biblioteki do ponownego użycia. Na przykład będzie bezpiecznie pominąć to ostrzeżenie w aplikacji wydajność dostosowana gdzie uzyskane korzyści wydajności z użycia list ogólnych.

## <a name="related-rules"></a>Powiązane reguły
 [CA1005: Unikaj nadużywania parametrów w typach ogólnych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Nie deklaruj składowych statycznych w typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Metody ogólne powinny udostępniać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Użyj wystąpień ogólnej procedury obsługi zdarzeń](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Używaj typów ogólnych wszędzie tam, gdzie jest to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Zobacz też
 [Typy ogólne](http://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)



