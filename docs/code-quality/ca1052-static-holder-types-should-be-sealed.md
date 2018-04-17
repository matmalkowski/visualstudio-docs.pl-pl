---
title: 'CA1052: Statyczne typy przechowujące powinny być zapieczętowane | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fc3954c4c446ff578790e92bc60dd97e42a0d8c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: Typy obsługi statycznej powinny być zapieczętowane
|||  
|-|-|  
|TypeName|StaticHolderTypesShouldBeSealed|  
|CheckId|CA1052|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Zawiera tylko statyczne elementy członkowskie typu publiczne lub chronione, a nie jest zadeklarowany z [zapieczętowanego](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) modyfikator.  
  
## <a name="rule-description"></a>Opis reguły  
 Ta zasada przyjęto założenie, że typ, który zawiera tylko statyczne elementy członkowskie nie jest przeznaczony do dziedziczone, ponieważ typ nie ma żadnej funkcji, która może zostać zastąpiona w typie pochodnym. Typ, który nie ma być dziedziczona powinien być oznaczony przez `sealed` modyfikator zabrania jego użycia jako typu podstawowego.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, oznacz typ jako `sealed`. Jeśli aplikacja jest przeznaczona dla [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 lub nowszej, lepszym rozwiązaniem jest oznaczenie typu jako `static`. W ten sposób można uniknąć Zadeklaruj Konstruktor prywatny, aby uniemożliwić tworzona klasy.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Pomiń ostrzeżenie od tej zasady tylko wtedy, gdy typ ma być dziedziczona. Brak `sealed` modyfikator sugeruje, że typ jest użyteczne jako typu podstawowego.  
  
## <a name="example-of-a-violation"></a>Przykładem naruszenia  
  
### <a name="description"></a>Opis  
 Poniższy przykład przedstawia typu, który narusza zasady.  
  
### <a name="code"></a>Kod  
 [!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]  
  
## <a name="fix-with-the-static-modifier"></a>Usuń z modyfikator statyczny  
  
### <a name="description"></a>Opis  
 Poniższy przykład pokazuje, jak rozwiązać naruszenie tej reguły oznaczenia typu za `static` modyfikator.  
  
### <a name="code"></a>Kod  
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1053: Statyczne typy przechowujące nie powinny mieć konstruktorów](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
