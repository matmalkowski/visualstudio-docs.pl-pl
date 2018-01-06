---
title: "CA1411: Metody rejestracji modelu COM nie powinny być widoczne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 43b1f340b62726edc33b3e7e05d52634c2a2595b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: Metody rejestracji modelu COM nie powinny być widoczne
|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldNotBeVisible|  
|CheckId|CA1411|  
|Kategoria|Microsoft.Interoperability|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Metody, która jest oznaczony atrybutem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> lub <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atrybutu jest widoczna zewnętrznie.  
  
## <a name="rule-description"></a>Opis reguły  
 Po zarejestrowaniu zestawu z składnik modelu COM. wpisy są dodawane do rejestru dla każdego typu widoczny dla modelu COM w zestawie. Metody, które są oznaczone ikoną z <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> i <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> atrybuty wywoływane podczas procesu rejestrowania i wyrejestrowania odpowiednio do uruchomienia kodu użytkownika, specyficzne dla rejestracji/wyrejestrowanie tych typów. Ten kod nie powinna być wywoływana poza tych procesów.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, zmień dostępność metody `private` lub `internal` (`Friend` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono dwie metody, które naruszają zasady.  
  
 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1410: Metody rejestracji modelu COM powinny być dopasowane](../code-quality/ca1410-com-registration-methods-should-be-matched.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Rejestrowanie zestawów w modelu COM](/dotnet/framework/interop/registering-assemblies-with-com)   
 [Regasm.exe (narzędzie rejestracji zestawów)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)