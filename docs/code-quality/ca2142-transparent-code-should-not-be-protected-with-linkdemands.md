---
title: 'CA2142: Jawny kod nie powinien być chroniony za pomocą LinkDemands | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8c598a6aff671f0ce3ce489a203805e77eda7183
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: Jawny kod nie powinien być chroniony za pomocą LinkDemands
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2142|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Metoda przezroczysty wymaga <xref:System.Security.Permissions.SecurityAction> lub inne żądanie zabezpieczeń.  
  
## <a name="rule-description"></a>Opis reguły  
 Ta reguła jest uruchamiana na przezroczystych metodach wymagających żądania LinkDemands, aby uzyskać do nich dostęp. Przezroczysty kod zabezpieczeń nie powinien być odpowiedzialny za weryfikację zabezpieczeń operacji, a zatem nie powinien wymagać uprawnień. Ponieważ metody przezroczysty powinna być neutralne zabezpieczeń, ich powinien nie można podejmowania żadnych zabezpieczeń decyzji. Ponadto bezpieczne krytyczne kod, który oznacza, że decyzje dotyczące zabezpieczeń, nie powinien chroniony przez kod o przezroczystym do wcześniej zostały wykonane takiej decyzji.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, Usuń łącze zapotrzebowanie na metody przezroczysty lub Oznacz metodę z <xref:System.Security.SecuritySafeCriticalAttribute> sprawdza atrybut, jeśli jest wykonywana zabezpieczeń, takich jak żądania kontroli zabezpieczeń.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie reguła generowane w metodzie ponieważ metoda działa w sposób niewidoczny i jest oznaczony atrybutem LinkDemand <xref:System.Security.PermissionSet> zawierający <xref:System.Security.Permissions.SecurityAction>.  
  
 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]  
  
 Nie pomijaj ostrzeżeń dla tej reguły.