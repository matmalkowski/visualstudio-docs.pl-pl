---
title: "CA1034: Zagnieżdżone typy nie powinny być widoczne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dc35514eab2344c086305ec88435ff8a32285e4f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: Zagnieżdżone typy nie powinny być widoczne
|||  
|-|-|  
|TypeName|NestedTypesShouldNotBeVisible|  
|CheckId|CA1034|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Widoczne na zewnątrz typu zawiera deklarację typu widoczne na zewnątrz. Zagnieżdżone wyliczeń i typy chronione są wyjątkiem od tej reguły.  
  
## <a name="rule-description"></a>Opis reguły  
 Zagnieżdżony typ jest typem zadeklarowanym w zakresie innego typu. Zagnieżdżone typy są przydatne do zawierający szczegóły prywatna implementacja typu zawierającego. Używane w tym celu typy zagnieżdżone nie powinny być widoczne na zewnątrz.  
  
 Nie używaj widoczne na zewnątrz typy zagnieżdżone grupowania logicznego lub w celu uniknięcia konfliktów nazw; Zamiast tego należy użyć przestrzeni nazw.  
  
 Zagnieżdżone typy podstawowe pojęcie w zakresie dostępność elementu członkowskiego, który niektórych programistów nie rozumie wyraźnie.  
  
 Typy chronione można używać w podklasy i typy zagnieżdżone w scenariuszach dostosowywania wyprzedzeniem.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Jeśli nie będą widoczne na zewnątrz zagnieżdżony typ, Zmień typ dostępność. W przeciwnym razie Usuń typu zagnieżdżonego po swoim obiekcie nadrzędnym. Jeśli zagnieżdżanie ma na celu skategoryzowania typu zagnieżdżonego, umożliwiają utworzenie hierarchii zamiast tego obszaru nazw.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia typu, który narusza zasady.  
  
 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]