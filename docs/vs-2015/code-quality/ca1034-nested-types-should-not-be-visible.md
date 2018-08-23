---
title: 'CA1034: Zagnieżdżone typy nie powinny być widoczne | Dokumentacja firmy Microsoft'
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
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8c4e3af21672c77ba982b98f3d672149be76faa5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682721"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: Zagnieżdżone typy nie powinny być widoczne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1034: zagnieżdżone typy nie powinny być widoczne](https://docs.microsoft.com/visualstudio/code-quality/ca1034-nested-types-should-not-be-visible).  
  
Element TypeName | NestedTypesShouldNotBeVisible |  
| CheckId | CA1034 |  
| Kategoria | Microsoft.Design|  
| Zmiana powodująca niezgodność | Przerwanie |  
  
## <a name="cause"></a>Przyczyna  
 Typ widoczny na zewnątrz zawiera deklarację typu widocznego na zewnątrz. Wyliczenia zagnieżdżonych i chronionych typów są wykluczone z tej reguły.  
  
## <a name="rule-description"></a>Opis reguły  
 Typ zagnieżdżony to typ zadeklarowany wewnątrz zakresu innego typu. Zagnieżdżone typy są przydatne do enkapsulacji szczegółów implementacji prywatnej typu zawierającego. Używane w tym celu typy zagnieżdżone nie powinny być widoczne na zewnątrz.  
  
 Nie używaj widocznego na zewnątrz typy zagnieżdżone powodują ustawienie logicznego grupowania lub aby uniknąć konfliktów nazw; Zamiast tego należy użyć przestrzeni nazw.  
  
 Zagnieżdżone typy obejmują pojęcie dostępność składowej, która niektórych programistów niezrozumiały wyraźnie.  
  
 Typy chronionych może służyć w podklasy i zagnieżdżone typy w scenariuszach Dostosowywanie zaawansowane.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Jeśli nie ma typu zagnieżdżonego, aby być widoczne na zewnątrz, zmień dostępność typu. W przeciwnym razie Usuń typu zagnieżdżonego od jego elementu nadrzędnego. Jeśli zagnieżdżania ma na celu kategoryzowania typu zagnieżdżonego, należy użyć przestrzeni nazw w zamian tworzenie hierarchii.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje typ, który narusza regułę.  
  
 [!code-cpp[FxCop.Design.NestedTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cpp/FxCop.Design.NestedTypes.cpp#1)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cs/FxCop.Design.NestedTypes.cs#1)]
 [!code-vb[FxCop.Design.NestedTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/vb/FxCop.Design.NestedTypes.vb#1)]



