---
title: "CA2131: Typy krytyczne dla zabezpieczeń nie może uczestniczyć w równoważnikach typów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2b1ba8aa4584d0d0505c7916d05e7c9bd6f446da
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131: Typy krytyczne dla zabezpieczeń nie mogą brać udziału w równoważnikach typów
|||  
|-|-|  
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|  
|CheckId|CA2131|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Typ uczestniczy w pełnienia roli równoważnika typu, a albo samego typu lub elementu członkowskiego lub pola tego typu, jest oznaczony atrybutem <xref:System.Security.SecurityCriticalAttribute> atrybutu.  
  
## <a name="rule-description"></a>Opis reguły  
 Ta reguła jest uruchamiana na wszystkich typach krytycznych lub typach zawierających metody krytyczne lub pola, które uczestniczą w równoważeniu typu. Wykrycie takiego typu, CLR nie powiedzie się go załadować <xref:System.TypeLoadException> w czasie wykonywania. Zazwyczaj ta reguła uruchamiana jest tylko wtedy, gdy użytkownicy implementują równoważenie typu ręcznie, zamiast wykonać je, opierając się na otokach tlbimp i kompilatorach.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, usuń atrybut SecurityCritical.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano interfejs, metody i pola, które spowodują uruchomienie tej reguły.  
  
 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kod o przezroczystym poziomie bezpieczeństwa, poziom 2](/dotnet/framework/misc/security-transparent-code-level-2)