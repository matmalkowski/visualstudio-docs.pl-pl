---
title: 'CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ecb9934ddefe0458f2974af0d73560532a17cc07
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: Należy oznaczyć typ ISerializable atrybutem SerializableAttribute
|||  
|-|-|  
|TypeName|MarkISerializableTypesWithSerializable|  
|CheckId|CA2237|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Widoczne na zewnątrz typ implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejsu i typ nie jest oznaczony atrybutem <xref:System.SerializableAttribute?displayProperty=fullName> atrybutu. Reguła ignoruje typów pochodnych, którego typ podstawowy nie jest możliwy do serializacji.  
  
## <a name="rule-description"></a>Opis reguły  
 Rozpoznane przez środowisko uruchomieniowe języka wspólnego jako możliwy do serializacji, muszą być oznaczone typy <xref:System.SerializableAttribute> atrybutu nawet, jeśli typ używa niestandardowej serializacji procedury przez wdrożenie <xref:System.Runtime.Serialization.ISerializable> interfejsu.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, zastosuj <xref:System.SerializableAttribute> atrybutu typu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżenia od tej reguły dla klasy wyjątków, ponieważ musi być możliwy do serializacji działał prawidłowo między domenami aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia typu, który narusza zasady. Usuń znaczniki komentarza <xref:System.SerializableAttribute> atrybutu wiersza, aby spełniać regułę.  
  
 [!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
 [!code-csharp[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA2236: Wywołanie metod klasy podstawowej typu ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: Zaimplementować ISerializable poprawnie](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Zaimplementować konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Poprawnie Implementuj metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: Należy oznaczyć wszystkie nieserializowane pola](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2239: Dostarcz metody deserializacji pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Zabezpieczaj konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)