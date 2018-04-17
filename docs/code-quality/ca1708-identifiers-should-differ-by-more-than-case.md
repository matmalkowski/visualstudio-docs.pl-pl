---
title: 'CA1708: Identyfikatory powinny różnić się tylko wielkością liter | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 35626f9e59aa1138c6d1756953ed5fdd72906deb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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