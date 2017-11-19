---
title: "CA1410: Metody rejestracji modelu COM powinny być zgodne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 65c6191aff1433d050c1f7b50097c88d1d3cf2a0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: Metody rejestracji COM powinny być dopasowane
|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldBeMatched|  
|CheckId|CA1410|  
|Kategoria|Microsoft.Interoperability|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Typ deklaruje metody, która jest oznaczony atrybutem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atrybutu, ale nie deklaruje metody, która jest oznaczony atrybutem <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atrybutu, albo na odwrót.  
  
## <a name="rule-description"></a>Opis reguły  
 Dla klientów modelu COM (Component Object) można utworzyć [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] typ, typ musi najpierw zostać zarejestrowana. Jeśli jest dostępna, metody, która jest oznaczony atrybutem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> atrybutu jest wywoływana podczas procesu rejestracji do uruchomienia kodu określonego przez użytkownika. Odpowiedniej metody, który jest oznaczony atrybutem <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> atrybutu jest wywoływana podczas procesu wyrejestrowania w celu odwrócenia operacji metoda rejestracji.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, Dodaj odpowiadającej rejestracji lub metody wyrejestrowania.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia typu, który narusza zasady. Komentarze kod przedstawia poprawkę naruszenie.  
  
 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1411: Metody rejestracji modelu COM nie powinny być widoczne](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Rejestrowanie zestawów w modelu COM](/dotnet/framework/interop/registering-assemblies-with-com)   
 [Regasm.exe (narzędzie rejestracji zestawów)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)