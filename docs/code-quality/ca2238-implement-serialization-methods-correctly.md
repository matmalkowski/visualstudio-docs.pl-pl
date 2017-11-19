---
title: 'CA2238: Poprawnie Implementuj metody serializacji | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9ca904e9259855127825b594db80cdc3524d53ec
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
 [CA2236: Wywołanie metod klasy podstawowej typu ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: Zaimplementować ISerializable poprawnie](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Zaimplementować konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2235: Należy oznaczyć wszystkie nieserializowane pola](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Dostarcz metody deserializacji pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Zabezpieczaj konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)