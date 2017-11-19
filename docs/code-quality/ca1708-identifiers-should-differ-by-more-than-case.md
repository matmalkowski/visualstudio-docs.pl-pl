---
title: "CA1708: Identyfikatory powinny różnić się tylko wielkością liter | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cda7936a1a701b1b51957a7038db496f70ddd9c0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: Identyfikatory powinny różnić się czymś więcej niż wielkością liter
|||  
|-|-|  
|TypeName|IdentifiersShouldDifferByMoreThanCase|  
|CheckId|CA1708|  
|Kategoria|Microsoft.Naming|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Nazwy dwa typy, elementy członkowskie, parametry lub przestrzeni nazw FQDN są identyczne, przekonwertowany na małe litery.  
  
## <a name="rule-description"></a>Opis reguły  
 Identyfikatory przestrzeni nazw, typów, elementów członkowskich i parametry nie mogą się różnić jedynie wielkością liter, ponieważ języki dla środowiska uruchomieniowego języka wspólnego nie muszą rozróżniać wielkości liter. Na przykład [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] jest powszechnie używany język bez uwzględniania wielkości liter.  
  
 Ta zasada wyzwala na tylko publicznie widocznych elementów członkowskich.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Wybierz nazwę, która jest unikatowa, gdy jest porównywany do innych identyfikatorów, w sposób, bez uwzględniania wielkości liter.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły. Biblioteka może nie można używać we wszystkich językach dostępne w [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## <a name="example-of-a-violation"></a>Przykładem naruszenia  
 W poniższym przykładzie pokazano naruszenie tej reguły.  
  
 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)