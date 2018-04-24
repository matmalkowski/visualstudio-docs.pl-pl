---
title: 'CA2235: Należy oznaczyć wszystkie nieserializowane pola'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 640fd26b7e75b566ccc159d8c41ff8f70d260897
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Należy oznaczyć wszystkie nieserializowane pola
|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Pola wystąpienia typu, który nie może być serializowany, jest zadeklarowany w typie, który jest możliwy do serializacji.

## <a name="rule-description"></a>Opis reguły
 Typ możliwy do serializacji to taki, który jest oznaczony atrybutem <xref:System.SerializableAttribute?displayProperty=fullName> atrybutu. Gdy typem jest serializowana, <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> jest zgłaszany wyjątek, jeśli typ zawiera pole wystąpienia typu, który nie jest możliwy do serializacji.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, zastosuj <xref:System.NonSerializedAttribute?displayProperty=fullName> atrybutu do pola, które nie jest możliwy do serializacji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Tylko pominąć ostrzeżenie od tej reguły, jeśli <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> typ został zadeklarowany, który umożliwia wystąpień pola do serializacji i deserializacji.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono typu, który narusza regułę i typ, który spełnia reguły.

 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA2236: Wywołuj metody klasy podstawowej w typach ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Zaimplementuj poprawnie interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Zaimplementuj poprawnie metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2237: Oznacz typy ISerializable za pomocą atrybutu SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Określ metody deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Zabezpiecz konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)