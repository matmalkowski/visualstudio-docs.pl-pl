---
title: "CA1719: Nazwy parametrów nie powinny odpowiadać nazwom elementu członkowskiego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 03c6459a4f879dce0f03e3516601e64c53d44b33
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: Nazwy parametrów nie powinny odpowiadać nazwom elementów członkowskich
|||  
|-|-|  
|TypeName|ParameterNamesShouldNotMatchMemberNames|  
|CheckId|CA1719|  
|Kategoria|Microsoft.Naming|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Nazwa elementu członkowskiego widoczne na zewnątrz odpowiada porównania bez uwzględniania wielkości liter nazwę jednego z jego parametrów.  
  
## <a name="rule-description"></a>Opis reguły  
 Nazwa parametru powinna przekazywać znaczenie parametru, a nazwa elementu członkowskiego — znaczenie elementu członkowskiego. W projekcie rzadko są one takie same. Nazywanie parametru tak samo jak nazwa jego elementu członkowskiego jest nieintuicyjne i utrudnia korzystanie z biblioteki.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Wybierz nazwę parametru, który nie jest zgodna z nazwą elementu członkowskiego.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 W nowych wdrożeniach, Brak znanego scenariusze wystąpić, gdy należy pominąć ostrzeżenie od tej reguły. Dla wysyłania bibliotek, może być konieczne pominąć ostrzeżenie od tej reguły.  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Identyfikatory powinny różnić się tylko wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: Identyfikatory nie powinny zawierać podkreśleń](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)