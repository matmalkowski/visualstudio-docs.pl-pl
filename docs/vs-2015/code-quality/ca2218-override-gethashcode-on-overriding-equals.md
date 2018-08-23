---
title: 'CA2218: Zastąp GetHashCode przy przesłanianiu Equals | Dokumentacja firmy Microsoft'
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
- CA2218
- OverrideGetHashCodeOnOverridingEquals
helpviewer_keywords:
- OverrideGetHashCodeOnOverridingEquals
- CA2218
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cf8fb22f5cfd6b5a9752077f11c47076b504b46c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679875"
---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218: Zastąp GetHashCode przy przesłanianiu Equals
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2218: Zastąp GetHashCode przy przesłanianiu Equals](https://docs.microsoft.com/visualstudio/code-quality/ca2218-override-gethashcode-on-overriding-equals).

Element TypeName | OverrideGetHashCodeOnOverridingEquals | | CheckId | CA2218 | | Kategoria | Microsoft.Usage| | Zmiana powodująca niezgodność | Inne niż powodująca niezgodność |

## <a name="cause"></a>Przyczyna
 Typ publiczny zastępuje <xref:System.Object.Equals%2A?displayProperty=fullName> , ale nie przesłania <xref:System.Object.GetHashCode%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Object.GetHashCode%2A> Zwraca wartość, w oparciu o bieżące wystąpienie, które jest odpowiednie dla algorytmów wyznaczania wartości skrótu i struktur danych, takich jak Tabela skrótów. Dwa obiekty są tego samego typu, które są takie same musi zwracać taki sam skrót, aby zapewnić prawidłowe działanie wystąpień z następujących typów:

-   <xref:System.Collections.Hashtable?displayProperty=fullName>

-   <xref:System.Collections.SortedList?displayProperty=fullName>

-   <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>

-   <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>

-   <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>

-   <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>

-   <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>

-   <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>

-   Typy, które implementują <xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy udostępnić implementację klasy <xref:System.Object.GetHashCode%2A>. Pary obiektów tego samego typu, należy upewnić się, że implementacja zwraca tę samą wartość, jeśli implementacja <xref:System.Object.Equals%2A> zwraca `true` dla pary.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="class-example"></a>Przykład klasy

### <a name="description"></a>Opis
 Poniższy przykład przedstawia klasę (typ odwołania), która narusza tę regułę.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeErrorClass/cs/FxCop.Usage.GetHashCodeErrorClass.cs#1)]

### <a name="comments"></a>Komentarze
 Poniższy przykład naprawia naruszenia przez zastąpienie <xref:System.Object.GetHashCode>.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeFixedClass/cs/FxCop.Usage.GetHashCodeFixedClass.cs#1)]

## <a name="structure-example"></a>Przykład struktury

### <a name="description"></a>Opis
 Poniższy przykład pokazuje strukturę (typ wartości), która narusza tę regułę.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeErrorStruct/cs/FxCop.Usage.GetHashCodeErrorStruct.cs#1)]

### <a name="comments"></a>Komentarze
 Poniższy przykład naprawia naruszenia przez zastąpienie <xref:System.Object.GetHashCode>.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeFixedStruct/cs/FxCop.Usage.GetHashCodeFixedStruct.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1046: Nie przeciążaj operatora równości w typach referencyjnych](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Przeciążenia operatora mają nazwane alternatywy](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: Operatory powinny mieć symetryczne przeciążenia](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Przesłaniaj metodę Equals w przypadku przeciążania operacji równości operatorów](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- <xref:System.Object.GetHashCode%2A?displayProperty=fullName>
- <xref:System.Collections.Hashtable?displayProperty=fullName>
- [Operatory równości](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)