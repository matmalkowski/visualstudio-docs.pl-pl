---
title: 'CA1813: Unikaj niezapieczętowanych atrybutów | Dokumentacja firmy Microsoft'
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
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c422e4e261374d591acd0630f428f139b29cfcca
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42903010"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: Unikaj niezapieczętowanych atrybutów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1813: Unikaj niezapieczętowanych atrybutów](https://docs.microsoft.com/visualstudio/code-quality/ca1813-avoid-unsealed-attributes).

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Publiczny typ dziedziczy z <xref:System.Attribute?displayProperty=fullName>, nie jest abstrakcyjna i nie jest zapieczętowany (`NotInheritable` w języku Visual Basic).

## <a name="rule-description"></a>Opis reguły
 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Biblioteka klas zawiera metody do pobierania atrybutów niestandardowych. Domyślnie te metody wyszukują hierarchie dziedziczenia atrybutu; na przykład <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> wyszukiwania dla podanego typu atrybutu lub dowolny typ atrybutu, który rozszerza podanego typu atrybutu. Plombowanie atrybutu eliminuje wyszukiwanie przez hierarchię dziedziczenia i może zwiększyć wydajność.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Zapieczętuj typ atrybutu lub ułatwiają abstrakcyjne.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły. Należy to zrobić tylko w przypadku definiowania hierarchii atrybutów i nie można zapieczętować ten atrybut lub ułatwiają abstrakcyjne.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje niestandardowy atrybut, który spełnia tę regułę.

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/cs/FxCop.Performance.AttributesSealed.cs#1)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/vb/FxCop.Performance.AttributesSealed.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1019: Zdefiniuj metody dostępu dla argumentów atrybutu](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018: Oznacz atrybuty atrybutem AttributeUsage](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>Zobacz też
 [Atrybuty](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)



