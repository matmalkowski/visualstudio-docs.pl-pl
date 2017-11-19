---
title: "CA2240: Zaimplementować ISerializable poprawnie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c8e3f9ba0e3cb182ec08dd802dc87728a0fb9dc0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: Należy poprawnie zaimplementować ISerializable
|||  
|-|-|  
|TypeName|ImplementISerializableCorrectly|  
|CheckId|CA2240|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Można przypisać do jest widoczne na zewnątrz typu <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> dotyczy interfejsu i jeden z następujących warunków:  
  
-   Typ dziedziczy, ale nie przesłania <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> — metoda i typ deklaruje pól wystąpień, które nie są oznaczone ikoną z <xref:System.NonSerializedAttribute?displayProperty=fullName> atrybutu.  
  
-   Typ nie jest zapieczętowany i typ implementuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodę, która jest zewnętrznie niewidoczny i możliwym do zastąpienia.  
  
## <a name="rule-description"></a>Opis reguły  
 Wystąpienie pola, które są zadeklarowane w typie, który dziedziczy <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejsu nie są automatycznie uwzględnione w procesie serializacji. Aby dołączyć pola, typ musi implementować <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> — metoda i Konstruktor serializacji. Jeśli pola nie powinny być serializowane, zastosuj <xref:System.NonSerializedAttribute> atrybutu do pól, aby jawnie wskazać decyzji.  
  
 Typy, które nie są zapieczętowane, implementacje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody powinny być widoczne na zewnątrz. W związku z tym metoda może być wywoływany przez typy pochodne i jest możliwym do zastąpienia.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody widoczne i którą można przesłonić i upewnij się, że wszystkie pola wystąpienia są uwzględnione w procesie serializacji lub jawnie oznaczone <xref:System.NonSerializedAttribute> atrybutu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia dwa typy serializacji, które naruszają zasady.  
  
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rozwiązuje dwa poprzednie naruszeń, dostarczając implementację zastępowalnych <xref:System.Runtime.Serialization.ISerializable.GetObjectData> w klasie książki oraz dostarczając implementację `GetObjectData` klasy biblioteki.  
  
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA2236: Wywołanie metod klasy podstawowej typu ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
 [CA2229: Zaimplementować konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)  
 [CA2238: Poprawnie Implementuj metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
 [CA2235: Należy oznaczyć wszystkie nieserializowane pola](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
 [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
 [CA2239: Dostarcz metody deserializacji pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
 [CA2120: Zabezpieczaj konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)  
