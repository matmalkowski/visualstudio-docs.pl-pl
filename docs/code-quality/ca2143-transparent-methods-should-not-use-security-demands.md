---
title: 'CA2143: Jawne metody nie powinny używać żądania kontroli zabezpieczeń | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c94cf356a90b98c279071c0c68e6e853d1550517
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: Jawne metody nie powinny używać żądań zabezpieczeń
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotDemand|  
|CheckId|CA2143|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Tranparent typ lub metoda deklaratywnie jest oznaczony atrybutem <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` żądanie lub wywołania metody <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> metody.  
  
## <a name="rule-description"></a>Opis reguły  
 Przezroczysty kod zabezpieczeń nie powinien być odpowiedzialny za weryfikację zabezpieczeń operacji, a zatem nie powinien wymagać uprawnień. Przejrzysty pod względem bezpieczeństwa kod powinien używać pełnych żądań do podejmowania decyzji związanych z zabezpieczeniami, a kod krytyczny pod względem zabezpieczeń nie powinien opierać się na kodzie przezroczystym do wykonywania pełnego żądania. Zamiast tego powinna być bezpieczne krytyczne kodu, który przeprowadza kontrole zabezpieczeń, takich jak w przypadku żądania kontroli zabezpieczeń.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Ogólnie rzecz biorąc, aby naprawić naruszenie tej reguły, oznacz metodę z <xref:System.Security.SecuritySafeCriticalAttribute> atrybutu. Można również usunąć żądanie.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 Reguła plików na następujący kod, ponieważ metoda przezroczystego sprawia, że żądanie zabezpieczenia deklaratywne.  
  
 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [CA2142: Kod przezroczysty nie powinien być chroniony za pomocą żądań LinkDemand](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)