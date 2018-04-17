---
title: 'CA2141: jawne metody nie mogą spełniać LinkDemands | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 90b1873a13f6e60863a99492c353d2270fdea5e4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>Metody CA2141:Transparent nie mogą spełniać LinkDemands
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|  
|CheckId|CA2141|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Metoda przezroczysty zabezpieczeń wywołuje metodę w zestawie, który nie jest oznaczony atrybutem <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu (APTCA) lub metody przezroczysty zabezpieczeń spełnia <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` dla typu lub metody.  
  
## <a name="rule-description"></a>Opis reguły  
 Spełniające LinkDemand jest poufnych operacji zabezpieczeń, co może spowodować niezamierzoną podniesienie uprawnień. Kod o przezroczystym zabezpieczeń nie mogą spełniać LinkDemands, ponieważ nie podlega ona te same wymagania inspekcji zabezpieczeń jako kod krytyczny dla zabezpieczeń. Jawne metody w zestawach poziom 1 zestaw reguł zabezpieczeń spowoduje, że wszystkie LinkDemands spełniają ma zostać przekonwertowane na pełne wymagania w czasie wykonywania, co może spowodować problemy z wydajnością. W zestawy poziomu 2 zestaw reguł zabezpieczeń jawne metody zakończy się niepowodzeniem do skompilowania kompilatora just in time (JIT) przy próbie spełniają LinkDemand.  
  
 W zestawach zgłasza tego usee zabezpieczeń poziomu 2, prób przez metodę przezroczysty zabezpieczeń spełniają LinkDemand lub wywołanie metody w zestawie-APTCA <xref:System.MethodAccessException>; w zestawach poziomu 1 LinkDemand staje się pełne żądanie.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, oznacz podczas uzyskiwania dostępu do metody z <xref:System.Security.SecurityCriticalAttribute> lub <xref:System.Security.SecuritySafeCriticalAttribute> atrybut lub usunąć LinkDemand z metody dostępu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przezroczysty — metoda podejmuje próbę wywołania metody, która ma LinkDemand. Ta reguła zostanie zastosowana dla tego kodu.  
  
 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]