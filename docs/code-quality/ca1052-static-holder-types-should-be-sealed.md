---
title: 'CA1052: Typy obsługi statycznej powinny być zapieczętowane'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
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
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bc264b9e47fe9169c0b1ad9d3257323c437620f7
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550430"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: Typy obsługi statycznej powinny być zapieczętowane

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony zawiera tylko statyczne elementy członkowskie i nie jest zadeklarowana za pomocą [zapieczętowanego](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) modyfikator.

## <a name="rule-description"></a>Opis reguły
 Reguła ta zakłada, że typ, który zawiera tylko statyczne elementy członkowskie nie służy do dziedziczone, ponieważ typ nie zapewnia żadnej funkcji, która może zostać zastąpiona w typie pochodnym. Typ, który nie jest przeznaczona do dziedziczone powinien być oznaczony przez `sealed` modyfikator, aby uniemożliwić jego użycie jako typu podstawowego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, oznacz typ jako `sealed`. Jeśli [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 lub nowszej, lepszym rozwiązaniem jest Oznacz typ jako `static`. W ten sposób można uniknąć konieczności zadeklarować Konstruktor prywatny, aby uniemożliwić tworzonych przez klasy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły, tylko wtedy, gdy typ jest przeznaczony do być dziedziczona. Brak `sealed` modyfikator sugeruje, że typ jest przydatne jako typu podstawowego.

## <a name="example-of-a-violation"></a>Przykładem naruszenia

### <a name="description"></a>Opis
 Poniższy przykład pokazuje typ, który narusza regułę.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>Usuń z modyfikator statyczny

### <a name="description"></a>Opis
 Poniższy przykład pokazuje, jak naprawić naruszenie tej zasady, oznaczając typu za pomocą `static` modyfikator.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1053: Statyczne typy przechowujące nie powinny mieć konstruktorów](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
