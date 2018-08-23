---
title: 'CA2135: Zestawy poziomu 2 nie powinny zawierać LinkDemands | Dokumentacja firmy Microsoft'
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
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3222004e07ddcef6eb40e5894a566ad12f1b0b68
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42632933"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: Zestawy poziomu 2 nie powinny zawierać LinkDemands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2135: zestawy poziomu 2 nie powinny zawierać LinkDemands](https://docs.microsoft.com/visualstudio/code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands).  
  
Element TypeName | SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands |  
| CheckId | CA2135 |  
| Kategoria | Microsoft.Security|  
| Zmiana powodująca niezgodność | Przerwanie |  
  
## <a name="cause"></a>Przyczyna  
 Używa klasy ani składowej klasy <xref:System.Security.Permissions.SecurityAction> w aplikacji, która używa zabezpieczenia na poziomie 2.  
  
## <a name="rule-description"></a>Opis reguły  
 LinkDemands są przestarzałe w zestawie reguł zabezpieczeń poziomu 2. Zamiast używania LinkDemands do wymuszenia zabezpieczeń w czasie kompilacji programu just-in-time (JIT), należy oznaczyć metody, typy i pola za pomocą <xref:System.Security.SecurityCriticalAttribute> atrybutu.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, Usuń <xref:System.Security.Permissions.SecurityAction> i oznacz typ lub element członkowski o <xref:System.Security.SecurityCriticalAttribute> atrybutu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Security.Permissions.SecurityAction> powinny zostać usunięte, a metoda oznaczona atrybutem <xref:System.Security.SecurityCriticalAttribute> atrybutu.  
  
 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2135.securityrulesetlevel2methodsshouldnotbeprotectedwithlinkdemands/cs/ca2135 - securityrulesetlevel2methodsshouldnotbeprotectedwithlinkdemands.cs#1)]



