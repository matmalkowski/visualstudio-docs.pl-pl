---
title: 'CA2237: Należy oznaczyć typ ISerializable atrybutem SerializableAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8629262da35b9897b789b2fae853bff4eea1aa8f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551738"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: Należy oznaczyć typ ISerializable atrybutem SerializableAttribute

|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ widoczny na zewnątrz implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejsu i typ nie jest oznaczony atrybutem <xref:System.SerializableAttribute?displayProperty=fullName> atrybutu. Reguły są ignorowane typy pochodne, którego typ podstawowy nie jest możliwy do serializacji.

## <a name="rule-description"></a>Opis reguły
 Aby zostały rozpoznane przez środowisko uruchomieniowe języka wspólnego jako możliwe do serializacji, muszą być oznaczone typy <xref:System.SerializableAttribute> atrybutu nawet, jeśli typ używa niestandardowych procedur serializacji przez implementację <xref:System.Runtime.Serialization.ISerializable> interfejsu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zastosować <xref:System.SerializableAttribute> atrybutu typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły dla klasy wyjątków, ponieważ musi być możliwy do serializacji, aby działać poprawnie w różnych domenach aplikacji.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę. Usuń znaczniki komentarza <xref:System.SerializableAttribute> atrybutu wiersz, aby spełniać reguły.

 [!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
 [!code-csharp[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2236: Wywołuj metody klasy podstawowej w typach ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Zaimplementuj poprawnie interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Zaimplementuj poprawnie metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2239: Określ metody deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Zabezpiecz konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)