---
title: 'CA1819: Właściwości nie powinny zwracać tablic'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 68f64d37a7616f095a86452353edc498d2d27f28
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549420"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: Właściwości nie powinny zwracać tablic

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Właściwość publiczna lub chroniona w typie publicznym zwraca tablicę.

## <a name="rule-description"></a>Opis reguły
 Tablice zwracane przez właściwości nie są zabezpieczony przed zapisem, nawet jeśli właściwość jest tylko do odczytu. Aby zachować tablicę odporną na manipulacje, właściwość musi zwracać kopię tablicy. Zwykle użytkownicy nie rozumieją, jakie niekorzystne następstwa dla wydajności ma wywołanie takiej właściwości. W szczególności mogą użyć właściwości jako indeksowana właściwość.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, ustawić właściwość jako metodę lub zmień wartość właściwości do zwrócenia kolekcji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Atrybuty mogą zawierać właściwości, które zwracają tablice, ale nie może zawierać właściwości, które zwracają kolekcje. Można pominąć ostrzeżenia, które jest wywoływane dla właściwości atrybutu, która jest pochodną <xref:System.Attribute> klasy. W przeciwnym razie nie Pomijaj ostrzeżeń dla tej reguły.

## <a name="example-violation"></a>Przykład naruszenia

### <a name="description"></a>Opis
 Poniższy przykład pokazuje właściwości, która narusza tę regułę.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]

### <a name="comments"></a>Komentarze
 Aby naprawić naruszenie tej zasady, ustawić właściwość jako metodę lub zmień wartość właściwości do zwrócenia kolekcji zamiast tablicy.

## <a name="change-the-property-to-a-method-example"></a>Zmień właściwości, na przykład metody

### <a name="description"></a>Opis
 Poniższy przykład naprawia naruszenia, zmieniając właściwość do metody.

### <a name="code"></a>Kod
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]

## <a name="return-a-collection-example"></a>Zwraca przykład kolekcji

### <a name="description"></a>Opis
 Poniższy przykład naprawia naruszenia, zmieniając właściwość do zwrócenia

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]

## <a name="allowing-users-to-modify-a-property"></a>Zezwalanie użytkownikom na modyfikowanie właściwości

### <a name="description"></a>Opis
 Możesz chcieć umożliwia konsumentowi klasy zmodyfikować właściwości. Poniższy przykład pokazuje właściwości odczytu/zapisu, która narusza tę regułę.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]

### <a name="comments"></a>Komentarze
 Poniższy przykład naprawia naruszenia, zmieniając właściwość do zwrócenia <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>.

### <a name="code"></a>Kod
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1024: Używaj właściwości wszędzie tam, gdzie jest to odpowiednie](../code-quality/ca1024-use-properties-where-appropriate.md)