---
title: 'CA2120: Konstruktory serializacji Secure | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e28d76315b3ef5844bd9b525764e6f5a5111ef56
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: Zabezpieczaj konstruktory serializacji
|||  
|-|-|  
|TypeName|SecureSerializationConstructors|  
|CheckId|CA2120|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Typ implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejsu, nie jest interfejs lub delegat i jest zadeklarowany w zestawie, który umożliwia częściowo zaufanych wywołań. Typ ma konstruktora przyjmującego <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> obiektu i <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> obiektu (sygnatura konstruktora serializacji). Ten konstruktor nie jest zabezpieczone kontrola zabezpieczeń, ale co najmniej jednego z konstruktorów regularne w typie jest zabezpieczony.  
  
## <a name="rule-description"></a>Opis reguły  
 Ta zasada ma zastosowanie w przypadku typów, które obsługują niestandardowej serializacji. Typem obsługuje niestandardowej serializacji, jeśli implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejsu. Konstruktor serializacji jest wymagany i służy do zdeserializować lub ponownie utworzyć obiekty, które zostały zserializowanym przy użyciu <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metody. Konstruktor serializacji przydziela i inicjuje obiekty, dlatego kontroli zabezpieczeń, które znajdują się na regularne konstruktorów musi również znajdować się na Konstruktor serializacji. Jeśli naruszają tę regułę, wywołań, które w przeciwnym razie nie można utworzyć wystąpienia można użyć w tym celu Konstruktor serializacji.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, chronić Konstruktor serializacji z żądania kontroli zabezpieczeń, które są identyczne jak ochrona innych konstruktorów.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj naruszenia reguły.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia typu, który narusza zasady.  
  
 [!code-csharp[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2237: Oznacz typy ISerializable za pomocą atrybutu SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>