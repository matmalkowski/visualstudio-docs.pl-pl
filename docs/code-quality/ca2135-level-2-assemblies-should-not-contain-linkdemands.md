---
title: "CA2135: Zestawy poziomu 2 nie powinny zawierać LinkDemands | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2374b8de7e3d4f915f836f718b32dee028bee9ff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: Zestawy poziomu 2 nie powinny zawierać LinkDemands
|||  
|-|-|  
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2135|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Klasa lub element członkowski klasy jest używana <xref:System.Security.Permissions.SecurityAction> w aplikacji, która używa zabezpieczeń poziomu 2.  
  
## <a name="rule-description"></a>Opis reguły  
 LinkDemands są przestarzałe w zestawie reguł zabezpieczeń poziomu 2. Zamiast Wymuszanie zabezpieczeń na czas kompilacji just in time (JIT) za pomocą LinkDemands oznaczyć metody, typy i pól z <xref:System.Security.SecurityCriticalAttribute> atrybutu.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, Usuń <xref:System.Security.Permissions.SecurityAction> i oznacz typ lub element członkowski z <xref:System.Security.SecurityCriticalAttribute> atrybutu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Security.Permissions.SecurityAction> powinna zostać usunięta, a metoda oznaczona atrybutem <xref:System.Security.SecurityCriticalAttribute> atrybutu.  
  
 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]