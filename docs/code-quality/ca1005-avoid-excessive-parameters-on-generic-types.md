---
title: "CA1005: Unikaj nadużywania parametrów na typach ogólnych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b5fad132dfdda0ef12e6d74c503c5d27024a8382
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: Unikaj nadużywania parametrów na typach generycznych
|||  
|-|-|  
|TypeName|AvoidExcessiveParametersOnGenericTypes|  
|CheckId|CA1005|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Widoczne na zewnątrz typu ogólnego ma więcej niż dwóch parametrów typu.  
  
## <a name="rule-description"></a>Opis reguły  
 Im więcej parametrów typu zawiera typ ogólny, tym trudniej poznać i zapamiętać, co reprezentuje każdy z nich. Jest zwykle oczywiste z parametrem typu, jak w `List<T>`, a w niektórych przypadkach z dwoma parametrami typu, jak w `Dictionary<TKey, TValue>`. Jeśli istnieje więcej niż dwoma parametrami typu, trudności staje się zbyt duży dla większości użytkowników (na przykład `TooManyTypeParameters<T, K, V>` w języku C# lub `TooManyTypeParameters(Of T, K, V)` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby usunąć naruszenie tej reguły, zmienić projekt, aby używać nie więcej niż dwóch parametrów typu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżenie od tej reguły, chyba że projektu absolutnie wymaga więcej niż dwóch parametrów typu. Udostępnia typy ogólne w składni, które jest łatwe do zrozumienia i użycia zmniejsza czas, który jest wymagany, aby dowiedzieć się więcej i zwiększa szybkość przyjęcia nowych bibliotek.  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: Nie deklaruj statycznych elementów członkowskich na typach generycznych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: Nie zagnieżdżaj typów generycznych w podpisach elementu członkowskiego](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Generyczne metody powinny dostarczyć parametry typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Użyj wystąpień obsługi zdarzeń generycznych](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Używaj danych generycznych wszędzie gdzie jest to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Typy ogólne](/dotnet/csharp/programming-guide/generics/index)