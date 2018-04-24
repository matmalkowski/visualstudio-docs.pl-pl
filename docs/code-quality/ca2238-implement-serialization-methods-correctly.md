---
title: 'CA2238: Należy poprawnie zaimplementować metody serializacji'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3aaed1be0ba5f44f3d426e9c9e825d063688a865
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238: Należy poprawnie zaimplementować metody serializacji
|||
|-|-|
|TypeName|ImplementSerializationMethodsCorrectly|
|CheckId|CA2238|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Dzielenie — metoda jest widoczna poza zestaw.<br /><br /> Bez podziału — Jeśli metoda nie jest widoczna poza zestaw.|

## <a name="cause"></a>Przyczyna
 Metoda, która obsługuje zdarzenie szeregowania, nie ma poprawnej sygnatury zwracanego typu lub widoczności.

## <a name="rule-description"></a>Opis reguły
 Metoda wyznaczono obsługi zdarzeń serializacji, stosując jedną z następujących atrybutów serializacji zdarzeń:

-   <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>

-   <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>

-   <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>

-   <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>

 Programy obsługi zdarzeń serializacji przyjmować jeden parametr typu <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, zwróć `void`i mieć `private` widoczności.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, popraw podpisu, zwracany typ lub widoczność serializacji obsługi zdarzeń.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono poprawnie zadeklarowane serializacji procedury obsługi zdarzeń.

 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/VisualBasic/ca2238-implement-serialization-methods-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/CSharp/ca2238-implement-serialization-methods-correctly_1.cs)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA2236: Wywołuj metody klasy podstawowej w typach ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Zaimplementuj poprawnie interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Oznacz typy ISerializable za pomocą atrybutu SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Określ metody deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Zabezpiecz konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)