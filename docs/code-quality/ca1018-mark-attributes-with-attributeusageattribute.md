---
title: 'CA1018: Oznacz atrybuty atrybutem Attributeusage | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e9218d3908872871ff5dab13529e8b1cbcec0c8d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Oznacz atrybuty AttributeUsageAttribute
|||  
|-|-|  
|TypeName|MarkAttributesWithAttributeUsage|  
|CheckId|CA1018|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 <xref:System.AttributeUsageAttribute?displayProperty=fullName> Atrybut nie jest obecny na atrybutu niestandardowego.  
  
## <a name="rule-description"></a>Opis reguły  
 Podczas definiowania atrybutu niestandardowego, oznacz go za pomocą <xref:System.AttributeUsageAttribute> wskaż, gdzie w kodzie źródłowym atrybutu niestandardowego można zastosować. Znaczenie i zamierzone użycie atrybutu określi jego prawidłowe lokalizacje w kodzie. Na przykład można zdefiniować atrybut, który identyfikuje osoby, kto jest odpowiedzialny za utrzymanie i poprawa każdego typu w bibliotece, a odpowiedzialność są zawsze przypisane na poziomie typu. W takim przypadku kompilatory należy włączyć atrybutu do klas, wyliczeń i interfejsów, ale nie należy włączać na zdarzeń, metody lub właściwości. Zasady organizacyjne i procedur czy określają, czy ten atrybut powinien być włączony zestawów.  
  
 <xref:System.AttributeTargets?displayProperty=fullName> Wyliczenie definiuje obiekty docelowe, które można określić dla atrybutu niestandardowego. W przypadku pominięcia <xref:System.AttributeUsageAttribute>, niestandardowy atrybut będzie obowiązywał dla wszystkich celów, zgodnie z definicją w `All` wartość <xref:System.AttributeTargets> wyliczenia.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Napraw naruszenie tej reguły, należy określić przy użyciu elementów docelowych dla atrybutu <xref:System.AttributeUsageAttribute>. Zobacz poniższy przykład.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Należy naprawić naruszenie tej reguły, zamiast z wyłączeniem wiadomości. Nawet wtedy, gdy atrybut inherits <xref:System.AttributeUsageAttribute>, ten atrybut powinien być obecny, aby uprościć zarządzanie kodu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano dwa atrybuty. `BadCodeMaintainerAttribute`niepoprawnie pomija <xref:System.AttributeUsageAttribute> instrukcji i `GoodCodeMaintainerAttribute` poprawnie implementuje atrybut, który jest opisany w tej sekcji. Należy pamiętać, że właściwość `DeveloperName` jest wymagana przez tę zasadę projektowania [CA1019: zdefiniuj metody dostępu do argumentów atrybutu](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) i został uwzględniony, aby informacje były kompletne.  
  
 [!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1019: Zdefiniuj metody dostępu do argumentów atrybutu](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1813: Unikaj niezapieczętowanych atrybutów](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty](/dotnet/standard/design-guidelines/attributes)