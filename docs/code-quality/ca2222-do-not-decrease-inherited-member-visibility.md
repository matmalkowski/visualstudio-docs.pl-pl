---
title: "CA2222: Nie Zmniejszaj widoczności dziedziczonego elementu członkowskiego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ac62bc901629e65d5104bede66046711dd879930
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: Nie zmniejszaj widoczności dziedziczonego elementu członkowskiego
|||  
|-|-|  
|TypeName|DoNotDecreaseInheritedMemberVisibility|  
|CheckId|CA2222|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Metoda prywatna w niezamknięty typ ma podpis, który jest taki sam jak publiczny metody zadeklarowanej w typie podstawowym. Metoda prywatna nie jest ostateczny.  
  
## <a name="rule-description"></a>Opis reguły  
 Nie należy zmieniać modyfikatora dostępu dla dziedziczonych elementów członkowskich. Zmiana dziedziczonej składowej na prywatną nie uniemożliwia wywołującym uzyskania dostępu do implementacji metody klasy podstawowej. Jeśli element członkowski ma zostać prywatnych i typ jest otwarty, dziedziczenie typów mogą wywoływać ostatniego wykonania publicznej metody w hierarchii dziedziczenia. Jeśli musisz zmienić modyfikator dostępu, metoda powinna być oznaczona jako ostatecznego lub jego typu powinny być zapieczętowane aby zapobiec zastąpieniu metody.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby usunąć naruszenie tej reguły, zmienić dostępu za prywatne. Alternatywnie Jeśli język programowania obsługuje tę funkcję, możesz wprowadzić metody końcowego.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia typu, który narusza tę regułę.  
  
 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]