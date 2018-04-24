---
title: 'CA1813: Unikaj niezapieczętowanych atrybutów'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db86642cc5b65a93cd2d2bb565ed3ed786362f54
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: Unikaj niezapieczętowanych atrybutów
|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Publiczny typ dziedziczy z <xref:System.Attribute?displayProperty=fullName>, nie jest abstrakcyjna i nie jest zapieczętowany (`NotInheritable` w języku Visual Basic).

## <a name="rule-description"></a>Opis reguły
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Biblioteki klas udostępnia metody do pobierania atrybutów niestandardowych. Domyślnie te metody wyszukiwanie hierarchii dziedziczenia atrybutu; na przykład <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> wyszukiwania dla podanego typu atrybutu lub dowolnego typu atrybutu, rozszerzający podanego typu atrybutu. Atrybut pieczętowania eliminuje wyszukiwanie w hierarchii dziedziczenia i może poprawić wydajność.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać naruszenie tej reguły, typ atrybutów Zapieczętuj lub była abstrakcyjny.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły. Ten krok należy wykonać tylko wtedy, gdy są definiowane hierarchii atrybutów i nie można zapieczętować atrybutu lub była abstrakcyjny.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono niestandardowy atrybut, który spełnia tej reguły.

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA1019: Zdefiniuj metody dostępu dla argumentów atrybutu](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018: Oznacz atrybuty atrybutem AttributeUsage](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>Zobacz też
 [Atrybuty](/dotnet/standard/design-guidelines/attributes)