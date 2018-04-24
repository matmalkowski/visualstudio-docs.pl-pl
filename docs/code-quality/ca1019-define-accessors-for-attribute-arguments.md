---
title: 'CA1019: Zdefiniuj metody dostępu do argumentów atrybutu'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 56354e4d0d6bf3ed381cb077cc0ed9c9a41d4843
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: Zdefiniuj metody dostępu do argumentów atrybutu
|||
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 W jego konstruktora atrybutu określa argumenty, które nie mają odpowiednich właściwości.

## <a name="rule-description"></a>Opis reguły
 Atrybuty mogą definiować obowiązkowe argumenty, które trzeba określić, aby móc zastosować atrybut do obiektu docelowego. Znane są również jako argumenty pozycyjne, ponieważ są one dostarczane do konstruktorów atrybutu jako parametry pozycyjne. Dla każdego obowiązkowego argumentu atrybut powinien również dostarczyć odpowiadającą właściwość tylko do odczytu, dzięki której można pobrać wartość argumentu w czasie wykonywania. Ta reguła sprawdza, czy dla każdego parametru konstruktora zdefiniowano odpowiadających im właściwości.

 Atrybuty mogą też definiować argumenty opcjonalne, które są znane również jako argumenty nazwane. Argumenty te są dostarczane do konstruktorów atrybutu poprzez nazwę i powinny mieć odpowiadającą właściwość umożliwiającą odczyt i zapis.

 Należy użyć obowiązkowe i opcjonalne argumenty, właściwościami i parametrami konstruktora takie same nazwy ale o innej wielkości liter. Właściwości użyj Pascal wielkości liter i wielkości liter camel Użyj parametrów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Dodaj dla każdego parametru konstruktora, który nie ma właściwości tylko do odczytu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie od tej reguły, jeśli nie chcesz, aby wartość argument obowiązkowy za pobieranie.

## <a name="custom-attributes-example"></a>Przykład atrybuty niestandardowe

### <a name="description"></a>Opis
 Poniższy przykład przedstawia dwa atrybuty definiujące obowiązkowy parametr (pozycyjny). Implementacja pierwszego atrybutu nieprawidłowo jest zdefiniowany. Drugi implementacja jest prawidłowa.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]

## <a name="positional-and-named-arguments"></a>Argumenty nazwane i pozycyjnych

### <a name="description"></a>Opis
 Argumenty nazwane i pozycyjnych należy wyczyścić konsumentom biblioteki argumenty, które są obowiązkowe dla atrybutu i argumentów, które są opcjonalne.

 Poniższy przykład przedstawia implementację atrybut, który ma argumenty nazwane i pozycyjnych.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]

### <a name="comments"></a>Komentarze
 Poniższy przykład pokazuje, jak do zastosowania atrybutu niestandardowego do dwie właściwości.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA1813: Unikaj niezapieczętowanych atrybutów](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Zobacz też
 [Atrybuty](/dotnet/standard/design-guidelines/attributes)