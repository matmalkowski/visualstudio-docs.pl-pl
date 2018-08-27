---
title: 'CA2239: Dostarcz metody deserializacji dla pól opcjonalnych | Dokumentacja firmy Microsoft'
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
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 235880285ce80d74fec67e5bcd497f046f3aa842
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902486"
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239: Dostarcz metody deserializacji pól opcjonalnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2239: Podaj metody deserializacji dla pól opcjonalnych](https://docs.microsoft.com/visualstudio/code-quality/ca2239-provide-deserialization-methods-for-optional-fields).

|||
|-|-|
|TypeName|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ ma pole oznaczone jako <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> atrybut i typ nie zawiera metod obsługi zdarzeń deserializacji.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Runtime.Serialization.OptionalFieldAttribute> Atrybut nie ma wpływu na serializacji; pola oznaczone atrybutem jest serializowana. Jednakże pole jest ignorowana na deserializacji i zachowuje domyślnej wartości skojarzonej z typem. Programy obsługi zdarzeń deserializacji powinien być zadeklarowany można ustawić pola podczas deserializacji.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy dodać metod z typem obsługi zdarzeń deserializacji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli pola mają być ignorowane podczas deserializacji.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ pole opcjonalne i zdarzeń deserializacji metody obsługi.

 [!code-csharp[FxCop.Usage.OptionalFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OptionalFields/cs/FxCop.Usage.OptionalFields.cs#1)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OptionalFields/vb/FxCop.Usage.OptionalFields.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2236: Wywołuj metody klasy podstawowej w typach ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Zaimplementuj poprawnie interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Zaimplementuj poprawnie metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Oznacz typy ISerializable za pomocą atrybutu SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2120: Zabezpiecz konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)



