---
title: "CA1007: Używaj danych generycznych odpowiednim | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 47ee7caafdadd94f7d4ffaaca68a412e406c7c87
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: Używaj danych generycznych wszędzie, gdzie jest to odpowiednie
|||  
|-|-|  
|TypeName|UseGenericsWhereAppropriate|  
|CheckId|CA1007|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Widocznej zewnętrznie metodzie zawiera odwołanie do parametru typu <xref:System.Object?displayProperty=fullName>i celów zestawu zawierającego [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  
  
## <a name="rule-description"></a>Opis reguły  
 Parametr odwołania jest zmodyfikowany za pomocą parametru `ref` (`ByRef` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) — słowo kluczowe. Typ argumentu jest dostarczona dla parametru odwołania musi dokładnie odpowiadać z typem parametru odwołania. Aby użyć typu, który pochodzi od typu parametru odwołania, typu najpierw musisz przypisaną do zmiennej typu parametru odwołania i rzutowania. Metoda ogólna umożliwiają wszystkich typów, pod warunkiem ograniczenia mają być przekazane do metody bez uprzedniego rzutowania typu na typ parametru odwołania.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, wprowadzić ogólne metodę i Zastąp <xref:System.Object> parametru za pomocą parametru typu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono procedury wymiany ogólnego przeznaczenia, implementowany jako metody zarówno nierodzajowe i rodzajowy. Należy zwrócić uwagę, jak skutecznie ciągi są zamienione za pomocą metody rodzajowe w porównaniu do metody nierodzajowe.  
  
 [!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1005: Unikaj nadużywania parametrów na typach ogólnych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: Nie deklaruj statycznych elementów członkowskich na typach generycznych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: Nie zagnieżdżaj typów generycznych w podpisach elementu członkowskiego](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Generyczne metody powinny dostarczyć parametry typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Użyj wystąpień obsługi zdarzeń generycznych](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Typy ogólne](/dotnet/csharp/programming-guide/generics/index)