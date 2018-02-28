---
title: "CA2146: Typy muszą być co najmniej tak ważne, jak ich typy podstawowe i interfejsy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6e2ed089ee94a6d88e51c9c69e93b515db7e7fa4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: Typy muszą być co najmniej tak ważne, jak ich typy podstawowe i interfejsy
|||  
|-|-|  
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|  
|CheckId|CA2146|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Przezroczysty typ pochodzi z typu, który jest oznaczony atrybutem <xref:System.Security.SecuritySafeCriticalAttribute> lub <xref:System.Security.SecurityCriticalAttribute>, lub typu, który jest oznaczony atrybutem <xref:System.Security.SecuritySafeCriticalAttribute> atrybut pochodzi z typu, który jest oznaczony atrybutem <xref:System.Security.SecurityCriticalAttribute> atrybutu.  
  
## <a name="rule-description"></a>Opis reguły  
 Ta reguła jest uruchamiana, gdy typ pochodny ma atrybut przezroczystości pod względem zabezpieczeń, który nie jest tak krytyczny, jak jego typ podstawowy lub zaimplementowany interfejs. Tylko typy krytyczne pod względem zabezpieczeń mogą pochodzić od podstawowych typów krytycznych lub implementować interfejsy krytyczne, a tylko typy krytyczne lub krytyczne dla bezpieczeństwa mogą pochodzić od podstawowych typów krytycznych dla bezpieczeństwa lub implementować interfejsy krytyczne dla bezpieczeństwa. Naruszeń tej reguły w przezroczystość poziomu 2 powoduje <xref:System.TypeLoadException> dla typu pochodnego.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Ustalenie to naruszenie, oznacz typ pochodne lub wykonawczych z atrybutem przezroczystość co najmniej tak krytyczne jako typu podstawowego lub interfejs.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../code-quality/codesnippet/CSharp/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces_1.cs)]