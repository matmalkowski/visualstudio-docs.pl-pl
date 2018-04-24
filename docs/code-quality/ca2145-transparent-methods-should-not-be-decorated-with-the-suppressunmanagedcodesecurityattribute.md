---
title: 'CA2145: Jawne metody nie powinny być dekorowane za pomocą SuppressUnmanagedCodeSecurityAttribute'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 072aa9a7b77441fbd2d742209e6221cd74fd6bf1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
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