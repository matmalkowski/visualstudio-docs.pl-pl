---
title: 'CA2238: Zaimplementuj poprawnie metody serializacji | Dokumentacja firmy Microsoft'
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
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 772127c7472d9b1204953493188ba405c252dbb5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678690"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238: Należy poprawnie zaimplementować metody serializacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio 2017, zobacz [CA2238: zaimplementuj poprawnie metody serializacji](https://docs.microsoft.com/visualstudio/code-quality/ca2238-implement-serialization-methods-correctly) w witrynie docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|ImplementSerializationMethodsCorrectly|  
|CheckId|CA2238|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Przerywanie — Jeśli metoda jest widoczna spoza zestawu.<br /><br /> Bez podziału — Jeśli metoda nie jest widoczna spoza zestawu.|  
  
## <a name="cause"></a>Przyczyna  
 Metoda, która obsługuje zdarzenie szeregowania, nie ma poprawnej sygnatury zwracanego typu lub widoczności.  
  
## <a name="rule-description"></a>Opis reguły  
 Metoda wyznaczono obsługi zdarzeń serializacji, stosując jedną z następujących atrybutów serializacji, zdarzenia:  
  
-   <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>  
  
 Programy obsługi zdarzeń serializacji przyjmować jeden parametr typu <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, wróć `void`i mieć `private` widoczności.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, popraw podpisu, zwracany typ lub widoczności programu obsługi zdarzeń serializacji.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje poprawnie zadeklarowane serializacji procedury obsługi zdarzeń.  
  
 [!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/cs/FxCop.Usage.SerializationEventHandlers.cs#1)]
 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/vb/FxCop.Usage.SerializationEventHandlers.vb#1)]  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA2236: Wywołuj metody klasy podstawowej w typach ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: Zaimplementuj poprawnie interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Oznacz typy ISerializable za pomocą atrybutu SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Określ metody deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Zabezpiecz konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)

