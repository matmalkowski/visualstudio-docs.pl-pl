---
title: 'CA2236: Wywołuj metody klasy podstawowej w typach ISerializable | Dokumentacja firmy Microsoft'
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
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5cbdd8f2a0df576f20a05a70e9494c340a031e66
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679607"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: Wywołanie metod klasy bazowej typu ISerializable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2236: wywołuj metody klasy podstawowej w typach ISerializable](https://docs.microsoft.com/visualstudio/code-quality/ca2236-call-base-class-methods-on-iserializable-types).  
  
Element TypeName | CallBaseClassMethodsOnISerializableTypes |  
| CheckId | CA2236 |  
| Kategoria | Microsoft.Usage|  
| Zmiana powodująca niezgodność | Inne niż powodująca niezgodność |  
  
## <a name="cause"></a>Przyczyna  
 Typ pochodzi od typu, który implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejsu i jeden z następujących warunków jest spełniony:  
  
-   Typ implementuje konstruktora serializacji, to znaczy konstruktora o <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> podpis parametru, ale nie wywołuje konstruktor serializacji typu podstawowego.  
  
-   Typ implementuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metody, ale nie mogą wywoływać <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody typu podstawowego.  
  
## <a name="rule-description"></a>Opis reguły  
 W procesie serializacji niestandardowej typ implementuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody do wykonywania serializacji jej pola i Konstruktor serializacji, aby deserializować pola. Jeśli typ pochodzi z typu, który implementuje <xref:System.Runtime.Serialization.ISerializable> interfejs, typ podstawowy <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody i serializacja konstruktora powinna być wywoływana do serializacji/cofania-serialize pola typu podstawowego. W przeciwnym razie typu nie można serializować i deserializowany poprawnie. Jeśli typ pochodny nie dodasz nowe pola, typ musi implementować <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metoda ani konstruktora serializacji lub zadzwoń odpowiedniki typu podstawowego.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, należy wywołać typu podstawowego <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metoda lub Konstruktor serializacji z odpowiadającej pochodne typu metoda lub Konstruktor.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia typ pochodny spełniającego reguły przez wywołanie konstruktora serializacji i <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody klasy bazowej.  
  
 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/cs/FxCop.Usage.CallBaseISerializable.cs#1)]
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/vb/FxCop.Usage.CallBaseISerializable.vb#1)]  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA2240: Zaimplementuj poprawnie interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Zaimplementuj poprawnie metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Oznacz typy ISerializable za pomocą atrybutu SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Określ metody deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Zabezpiecz konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)



