---
title: 'CA1052: Statyczne typy przechowujące powinny być zapieczętowane | Dokumentacja firmy Microsoft'
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
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a912276f2f4008d1bea95027a5f2a1b67ff83e55
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42901929"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: Typy obsługi statycznej powinny być zapieczętowane
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1052: statyczne typy przechowujące powinny być zapieczętowane](https://docs.microsoft.com/visualstudio/code-quality/ca1052-static-holder-types-should-be-sealed).

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony zawiera tylko statyczne elementy członkowskie i nie jest zadeklarowana za pomocą [zapieczętowanego](http://msdn.microsoft.com/library/8e4ed5d3-10be-47db-9488-0da2008e6f3f) ([NotInheritable](http://msdn.microsoft.com/library/5c4da7c9-9562-4653-a947-1972e992f9f9)) modyfikator.

## <a name="rule-description"></a>Opis reguły
 Reguła ta zakłada, że typ, który zawiera tylko statyczne elementy członkowskie nie służy do dziedziczone, ponieważ typ nie zapewnia żadnej funkcji, która może zostać zastąpiona w typie pochodnym. Typ, który nie jest przeznaczona do dziedziczone powinien być oznaczony przez `sealed` modyfikator, aby uniemożliwić jego użycie jako typu podstawowego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, oznacz typ jako `sealed`. Jeśli [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 lub starszym, lepszym rozwiązaniem jest Oznacz typ jako `static`. W ten sposób można uniknąć konieczności zadeklarować Konstruktor prywatny, aby uniemożliwić tworzonych przez klasy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły, tylko wtedy, gdy typ jest przeznaczony do być dziedziczona. Brak `sealed` modyfikator sugeruje, że typ jest przydatne jako typu podstawowego.

## <a name="example-of-a-violation"></a>Przykładem naruszenia

### <a name="description"></a>Opis
 Poniższy przykład pokazuje typ, który narusza regułę.

### <a name="code"></a>Kod
 [!code-cpp[FxCop.Design.StaticMembers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cpp/FxCop.Design.StaticMembers.cpp#1)]
 [!code-csharp[FxCop.Design.StaticMembers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cs/FxCop.Design.StaticMembers.cs#1)]
 [!code-vb[FxCop.Design.StaticMembers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/vb/FxCop.Design.StaticMembers.vb#1)]

## <a name="fix-with-the-static-modifier"></a>Usuń z modyfikator statyczny

### <a name="description"></a>Opis
 Poniższy przykład pokazuje, jak naprawić naruszenie tej zasady, oznaczając typu za pomocą `static` modyfikator.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembersFixed/cs/FxCop.Design.StaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1053: Statyczne typy przechowujące nie powinny mieć konstruktorów](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)



