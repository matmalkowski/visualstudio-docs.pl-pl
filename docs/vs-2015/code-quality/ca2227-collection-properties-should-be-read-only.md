---
title: 'CA2227: Właściwości kolekcji powinny być tylko do odczytu | Dokumentacja firmy Microsoft'
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
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 95085c8b79e49d38bc55aea65b4f9867ce6dfb2a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42631042"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Właściwości kolekcji powinny być tylko do odczytu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2227: właściwości kolekcji powinny być tylko do odczytu](https://docs.microsoft.com/visualstudio/code-quality/ca2227-collection-properties-should-be-read-only).  
  
Element TypeName | CollectionPropertiesShouldBeReadOnly |  
| CheckId | CA2227 |  
| Kategoria | Microsoft.Usage|  
| Zmiana powodująca niezgodność | Przerwanie |  
  
## <a name="cause"></a>Przyczyna  
 Widoczne na zewnątrz zapisywalną właściwość jest typu, który implementuje <xref:System.Collections.ICollection?displayProperty=fullName>. Tablice, indeksatory (właściwości o nazwie "Item") i zestawy uprawnień są ignorowane przez regułę.  
  
## <a name="rule-description"></a>Opis reguły  
 Właściwość zapisywalnej kolekcji pozwala użytkownikowi zastąpić kolekcję całkowicie inną kolekcję. Właściwość tylko do odczytu uniemożliwia zastępowanie kolekcji, ale nadal umożliwia ustawienie poszczególnych członków. Zastępowanie kolekcji celem jest wzorzec projektowy preferowanych czy metodę, aby usunąć wszystkie elementy z kolekcji i metodę, aby ponownie wypełnić kolekcji. Zobacz <xref:System.Collections.ArrayList.Clear%2A> i <xref:System.Collections.ArrayList.AddRange%2A> metody <xref:System.Collections.ArrayList?displayProperty=fullName> klasy, na przykład tego wzorca.  
  
 Plik binarny i serializacji XML obsługuje właściwości tylko do odczytu, które są kolekcjami. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> Klasa ma określonych wymagań dotyczących typów, które implementują <xref:System.Collections.ICollection> i <xref:System.Collections.IEnumerable?displayProperty=fullName> aby podlegać serializacji.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, należy ustawić właściwość jako tylko do odczytu i jeśli projekt wymaga, Dodaj metody, aby usunąć i ponownie wypełnić kolekcji.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono typ z właściwość zapisywalnej kolekcji i pokazuje, jak kolekcji można zastąpić bezpośrednio. Ponadto preferowany sposób zastąpienia właściwość kolekcji tylko do odczytu za pomocą `Clear` i `AddRange` metody jest wyświetlana.  
  
 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA1819: Właściwości nie powinny zwracać tablic](../code-quality/ca1819-properties-should-not-return-arrays.md)



