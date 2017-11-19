---
title: "CA2239: Dostarcz metody deserializacji pól opcjonalnych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6992dc561fb9ef018de02b0192528621d2e069fb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239: Dostarcz metody deserializacji pól opcjonalnych
|||  
|-|-|  
|TypeName|ProvideDeserializationMethodsForOptionalFields|  
|CheckId|CA2239|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Typ ma pole oznaczone jako <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> atrybutu i typ nie zapewnia obsługi metody deserializacji zdarzeń.  
  
## <a name="rule-description"></a>Opis reguły  
 <xref:System.Runtime.Serialization.OptionalFieldAttribute> Atrybut nie ma wpływu na serializacji; pole oznaczone atrybutem jest serializowany. Jednak to pole jest ignorowany w deserializacji i zachowuje domyślną wartość skojarzoną z typem. Programy obsługi zdarzeń deserializacji powinny zostać zadeklarowane można ustawić pola podczas deserializacji.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, Dodaj obsługi metody na typ zdarzeń deserializacji.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli pole powinno być zignorowane podczas deserializacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono typu pole opcjonalne i zdarzenia deserializacji metody obsługi.  
  
 [!code-csharp[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA2236: Wywołanie metod klasy podstawowej typu ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: Zaimplementować ISerializable poprawnie](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Zaimplementować konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Poprawnie Implementuj metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: Należy oznaczyć wszystkie nieserializowane pola](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2120: Zabezpieczaj konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)