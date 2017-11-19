---
title: "CA2236: Wywołanie metod klasy podstawowej typu ISerializable | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a5379defde7ace66f43cad0983c9b14b554fb232
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: Wywołanie metod klasy podstawowej typu ISerializable
|||  
|-|-|  
|TypeName|CallBaseClassMethodsOnISerializableTypes|  
|CheckId|CA2236|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Typ pochodzi z typu, który implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> dotyczy interfejsu i jeden z następujących warunków:  
  
-   Typ implementuje konstruktora serializacji, czyli konstruktora z <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> Sygnatura parametru, ale nie wywołuje konstruktor serializacji typu podstawowego.  
  
-   Typ implementuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metody, ale nie wywołuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody typu podstawowego.  
  
## <a name="rule-description"></a>Opis reguły  
 W procesie niestandardowej serializacji, typ implementuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody do serializacji swoich pól i Konstruktor serializacji można zdeserializować pola. Jeśli typ pochodzi z typu, który implementuje <xref:System.Runtime.Serialization.ISerializable> interfejsu, typ podstawowy <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> — metoda i serializacja konstruktora powinna być wywoływana do serializacji/dezaktywuje-serialize pola typu podstawowego. W przeciwnym razie wartość typu nie można serializować i deserializowany poprawnie. Jeśli typ pochodny nie dodaje żadnych nowych pól, typ musi implementować <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody ani Konstruktor serializacji lub zadzwoń typ podstawowy równoważnych.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, wywołanie typu podstawowego <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> pochodnych metody lub serializacji konstruktora z odpowiedniej metody typu lub konstruktora.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono spełniająca reguły przez wywołanie konstruktora serializacji typu pochodnego i <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody klasy podstawowej.  
  
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA2240: Zaimplementować ISerializable poprawnie](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Zaimplementować konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Poprawnie Implementuj metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: Należy oznaczyć wszystkie nieserializowane pola](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Dostarcz metody deserializacji pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Zabezpieczaj konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)