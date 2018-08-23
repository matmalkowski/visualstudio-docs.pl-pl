---
title: 'CA1007: Używaj typów ogólnych wszędzie, gdzie jest to odpowiednie | Dokumentacja firmy Microsoft'
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
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b0fecf0c8221e9e83a42c131e5b77de7beef0c4b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677988"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: Używaj danych generycznych wszędzie, gdzie jest to odpowiednie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1007: Używaj typów ogólnych wszędzie, gdzie jest to odpowiednie](https://docs.microsoft.com/visualstudio/code-quality/ca1007-use-generics-where-appropriate).  
  
Element TypeName | UseGenericsWhereAppropriate |  
| CheckId | CA1007 |  
| Kategoria | Microsoft.Design|  
| Zmiana powodująca niezgodność | Przerwanie |  
  
## <a name="cause"></a>Przyczyna  
 Metoda widoczna na zewnątrz zawiera parametr przekazany przez odwołanie typu <xref:System.Object?displayProperty=fullName>, zawierające cele zestawu i [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)].  
  
## <a name="rule-description"></a>Opis reguły  
 Parametr przekazany przez odwołanie jest parametr, który jest modyfikowana przy użyciu `ref` (`ByRef` w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) — słowo kluczowe. Typ argumentu, który jest dostarczany dla parametru odwołania musi dokładnie odpowiadać typ parametru odwołania. Aby użyć typu, który pochodzi od typu parametru odwołania, typ najpierw należy przypisać do zmiennej typu parametru odwołania i rzutowania. Użyj metody ogólnej umożliwia wszystkich typów podlegających ograniczeniom, które zostaną przekazane do metody bez uprzedniego rzutowania typu do typu parametru odwołania.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, wprowadzić metody rodzajowe i Zastąp <xref:System.Object> parametru za pomocą parametru typu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje procedury wymiany ogólnego przeznaczenia, który jest implementowany jako metody zarówno nierodzajowych, jak i ogólnych. Należy pamiętać o tym, jak wydajnie ciągi są zamienione przy użyciu metody rodzajowej, w porównaniu do nierodzajowymi metody.  
  
 [!code-csharp[FxCop.Design.UseGenerics#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/cs/FxCop.Design.UseGenerics.cs#1)]
 [!code-vb[FxCop.Design.UseGenerics#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/vb/FxCop.Design.UseGenerics.vb#1)]  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA1005: Unikaj nadużywania parametrów w typach ogólnych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: Nie deklaruj składowych statycznych w typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Metody ogólne powinny udostępniać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Użyj wystąpień ogólnej procedury obsługi zdarzeń](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Typy ogólne](http://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)



