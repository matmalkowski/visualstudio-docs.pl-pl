---
title: "CA1004: Generyczne metody powinny dostarczyć parametry typu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1004
- GenericMethodsShouldProvideTypeParameter
helpviewer_keywords:
- GenericMethodsShouldProvideTypeParameter
- CA1004
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 01e795c4505b71f337212f85c3946f8800fbc05d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1004-generic-methods-should-provide-type-parameter"></a>CA1004: Generyczne metody powinny dostarczyć parametry typu
|||  
|-|-|  
|TypeName|GenericMethodsShouldProvideTypeParameter|  
|CheckId|CA1004|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Sygnatura parametru widoczne na zewnątrz metody ogólnej nie zawiera typy, które odpowiadają wszystkie parametry typu metody.  
  
## <a name="rule-description"></a>Opis reguły  
 Wnioskowanie to ustalenie argumentu typu metody ogólnej przez typ argumentu przekazanego do metody, zamiast użycia jawnej specyfikacji argumentu typu. Aby włączyć wnioskowanie, podpis parametru metody ogólnej musi zawierać parametr, który jest tego samego typu co parametr typu dla metody. W tym przypadku argument typu nie musi zostać określony. Użycie wnioskowania dla wszystkich parametrów typu, składnia wywołania metody wystąpienia ogólnych i nierodzajowe jest identyczne. Upraszcza to użyteczność metody ogólne.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby usunąć naruszenie tej reguły, należy zmienić projekt tak, aby parametr podpis zawiera ten sam typ, dla każdego parametru typu metody.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły. Udostępnia typy ogólne w składni, które jest łatwe do zrozumienia i użycia zmniejsza czas, który jest wymagany, aby dowiedzieć się więcej i zwiększa szybkość przyjęcia nowych bibliotek.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia składnię wywołania dwóch metod ogólnych. Typ argumentu dla `InferredTypeArgument` jest wywnioskowany, a typ argumentu dla `NotInferredTypeArgument` musi być jawnie określona.  
  
 [!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
 [!code-csharp[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1005: Unikaj nadużywania parametrów na typach ogólnych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: Nie deklaruj statycznych elementów członkowskich na typach generycznych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: Nie zagnieżdżaj typów generycznych w podpisach elementu członkowskiego](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1003: Użyj wystąpień obsługi zdarzeń generycznych](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Używaj danych generycznych wszędzie gdzie jest to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Typy ogólne](/dotnet/csharp/programming-guide/generics/index)