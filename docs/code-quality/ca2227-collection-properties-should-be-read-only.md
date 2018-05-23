---
title: 'CA2227: Właściwości kolekcji powinny być tylko do odczytu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: aa1d8644049f78eccfda7402360bdbc930b61601
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Właściwości kolekcji powinny być tylko do odczytu

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Właściwość widoczne na zewnątrz, zapisywalny, jest typu, który implementuje <xref:System.Collections.ICollection?displayProperty=fullName>. Ta zasada powoduje ignorowanie tablic, indeksatory (właściwości o nazwie "Item") i zestawów uprawnień.

## <a name="rule-description"></a>Opis reguły

Właściwości kolekcji zapisywalny umożliwia użytkownikowi Zamień kolekcji całkowicie innej kolekcji. Właściwości tylko do odczytu zatrzymanie kolekcji z figury geometrycznej, ale nadal umożliwia poszczególne elementy członkowskie, które można ustawić. Jeśli celem jest zastąpienie kolekcji, wzorzec projektowy preferowany jest uwzględnienie metodę, aby usunąć wszystkie elementy z kolekcji, a metoda ponownie wypełnić kolekcji. Zobacz <xref:System.Collections.ArrayList.Clear%2A> i <xref:System.Collections.ArrayList.AddRange%2A> metody <xref:System.Collections.ArrayList?displayProperty=fullName> klasy przykład tego wzorca.

Zarówno pliku binarnego, jak i serializacji XML obsługuje właściwości tylko do odczytu, które są kolekcjami. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> Klasa ma określonych wymagań dotyczących typów, które implementują <xref:System.Collections.ICollection> i <xref:System.Collections.IEnumerable?displayProperty=fullName> aby podlegać serializacji.

## <a name="how-to-fix-violations"></a>Jak rozwiązać naruszeń

Napraw naruszenie tej reguły, aby właściwość tylko do odczytu. Jeśli projekt wymaga, Dodaj metody, aby usunąć i ponownie wypełnić kolekcji.

## <a name="when-to-suppress-warnings"></a>Kiedy pomijanie ostrzeżeń

Nie pomijaj ostrzeżenia od tej reguły.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje typ z właściwością zapisywalny kolekcji i pokazuje, jak kolekcji można zastąpić bezpośrednio. Ponadto preferowany sposób zastępowanie właściwości kolekcji tylko do odczytu za pomocą `Clear` i `AddRange` metody jest wyświetlany.

[!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
[!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
[!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>Powiązanych reguł

[CA1819: Właściwości nie powinny zwracać tablic](../code-quality/ca1819-properties-should-not-return-arrays.md)