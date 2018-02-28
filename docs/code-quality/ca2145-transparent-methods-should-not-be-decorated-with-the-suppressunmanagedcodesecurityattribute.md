---
title: "CA2145: Jawne metody nie powinny być dekorowane za pomocą SuppressUnmanagedCodeSecurityAttribute | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2c6fcfc32dc8ab8a90ea555f43c253a5d93e72a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: Jawne metody nie powinny być dekorowane za pomocą SuppressUnmanagedCodeSecurityAttribute
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|  
|CheckId|CA2145|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Przezroczysty metody, metody, która jest oznaczony atrybutem <xref:System.Security.SecuritySafeCriticalAttribute> metody lub typu, który zawiera metodę jest oznaczony atrybutem <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybutu.  
  
## <a name="rule-description"></a>Opis reguły  
 Metody oznaczone <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybut ma niejawne LinkDemand nałożone na dowolnej metody, która wywołuje go. Ten element LinkDemand wymaga, aby kod wywołujący był krytyczny dla bezpieczeństwa. Metodę, która używa atrybutu SuppressUnmanagedCodeSecurity z <xref:System.Security.SecurityCriticalAttribute> atrybut powoduje, że to wymaganie bardziej oczywistymi dla wywoływania metody.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, oznacz metodę lub typ <xref:System.Security.SecurityCriticalAttribute> atrybutu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
### <a name="code"></a>Kod  
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]  
  
### <a name="comments"></a>Komentarze