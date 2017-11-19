---
title: "CA1002: Nie ujawniaj list ogólnych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 08092243699e58bd6bc4d737d31c60e5b3c3dd0b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: Nie ujawniaj list generycznych
|||  
|-|-|  
|TypeName|DoNotExposeGenericLists|  
|CheckId|CA1002|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Typ zawiera widoczne na zewnątrz elementu członkowskiego, który jest <xref:System.Collections.Generic.List%601?displayProperty=fullName> wpisz zwraca <xref:System.Collections.Generic.List%601?displayProperty=fullName> typu lub którego sygnatura zawiera <xref:System.Collections.Generic.List%601?displayProperty=fullName> parametru.  
  
## <a name="rule-description"></a>Opis reguły  
 <xref:System.Collections.Generic.List%601?displayProperty=fullName>jest kolekcją ogólnego, który zaprojektowano pod kątem wydajności i dziedziczenie nie. <xref:System.Collections.Generic.List%601?displayProperty=fullName>nie zawiera wirtualnych elementów członkowskich, które ułatwiają zmianę zachowania dziedziczonej klasie. Następujące kolekcje ogólne są przeznaczone dla dziedziczenia i powinny zostać ujawnione zamiast <xref:System.Collections.Generic.List%601?displayProperty=fullName>.  
  
-   <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby usunąć naruszenie tej reguły, zmienić <xref:System.Collections.Generic.List%601?displayProperty=fullName> typu ogólnego kolekcji, które jest przeznaczone do dziedziczenia.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżenie od tej reguły, chyba że zestaw, który wywołuje to ostrzeżenie jest nie należy traktować jako biblioteki do ponownego użycia. Na przykład byłoby bezpiecznie pominąć to ostrzeżenie w aplikacji wydajność dostosowana gdzie poprawiać wydajność uzyskane z użycia list ogólnych.  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1005: Unikaj nadużywania parametrów na typach ogólnych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: Nie deklaruj statycznych elementów członkowskich na typach generycznych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1006: Nie zagnieżdżaj typów generycznych w podpisach elementu członkowskiego](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Generyczne metody powinny dostarczyć parametry typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Użyj wystąpień obsługi zdarzeń generycznych](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Używaj danych generycznych wszędzie gdzie jest to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Typy ogólne](/dotnet/csharp/programming-guide/generics/index)