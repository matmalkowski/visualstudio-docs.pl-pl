---
title: "CA2138: Jawne metody nie mogą wywoływać metod z atrybutem suppressunmanagedcodesecurity | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0cef17ce232582cd23f961850bd52c048479e849
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: Jawne metody nie mogą wywoływać metod z atrybutem SuppressUnmanagedCodeSecurity
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|  
|CheckId|CA2138|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Metoda przezroczysty zabezpieczeń wywołuje metodę, która jest oznaczony atrybutem <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybutu.  
  
## <a name="rule-description"></a>Opis reguły  
 Ta zasada wyzwala na przezroczysty — metoda, która wywołuje bezpośrednio do kodu macierzystego, na przykład za pomocą przy użyciu elementu P/Invoke (Wywołanie platformy) wywołań. P/Invoke i COM interop metody, które są oznaczone ikoną z <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybutu spowodować LinkDemand wykonywana względem metody wywołującej. Ponieważ kod o przezroczystym zabezpieczeń nie mogą spełniać LinkDemands, kod także nie można wywołać metody, które są oznaczone atrybutem atrybutu SuppressUnmanagedCodeSecurity lub metody klasy, który jest oznaczony atrybutem atrybutu SuppressUnmanagedCodeSecurity. Metoda zakończy się niepowodzeniem lub żądanie zostanie przekonwertowany na pełne żądanie.  
  
 Naruszeń tej reguły prowadzić do <xref:System.MethodAccessException> w modelu przezroczystości zabezpieczeń poziomu 2 i pełne żądanie dla <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> w modelu przezroczystość poziomu 1.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, Usuń <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybutu i oznacz metodę z <xref:System.Security.SecurityCriticalAttribute> lub <xref:System.Security.SecuritySafeCriticalAttribute> atrybutu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]