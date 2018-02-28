---
title: "CA2134: Metody muszą przechowywać spójną jawność podczas nadpisywania metod bazowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 62438b49d91f680ae360f1d32f7cfe3b0efa2b75
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: Metody muszą przechowywać spójną jawność podczas nadpisywania metod bazowych
|||  
|-|-|  
|TypeName|MethodsMustOverrideWithConsistentTransparency|  
|CheckId|CA2134|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Ta zasada generowane, gdy metoda oznaczona z <xref:System.Security.SecurityCriticalAttribute> zastępuje metodę, która jest przezroczysty lub oznaczone przy <xref:System.Security.SecuritySafeCriticalAttribute>. Reguła także generowane, gdy metodę, która jest przezroczysty lub oznaczone przy <xref:System.Security.SecuritySafeCriticalAttribute> zastępuje metodę, która jest oznaczony atrybutem <xref:System.Security.SecurityCriticalAttribute>.  
  
 Reguła jest stosowana podczas zastępowania metody wirtualnej lub implementującej interfejs.  
  
## <a name="rule-description"></a>Opis reguły  
 Ta zasada wyzwala na próby zmiany dostępność zabezpieczeń metody dalsze zapasowej łańcuch dziedziczenia. Na przykład w przypadku przezroczysty lub bezpieczne krytyczne wirtualnej metody w klasie podstawowej następnie Klasa pochodna musi zastępować go za pomocą metody przezroczystego lub bezpieczne krytyczne. Z drugiej strony w przypadku wirtualnej zabezpieczeń, krytyczne, klasy pochodnej muszą przesłaniać za pomocą metody krytyczne zabezpieczeń. Ta zasada ma zastosowanie do implementacji metod interfejsu.  
  
 Przezroczystość zasady są wymuszane kod jest skompilowana zamiast w czasie wykonywania w trybie JIT, dzięki czemu obliczania przezroczystość nie ma typu dynamicznego informacji. W związku z tym wynikiem obliczenia przezroczystość musi mieć możliwość można określić wyłącznie z typów statycznych trwa JIT kompilacji, niezależnie od typu dynamicznego.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby usunąć naruszenie tej reguły, zmienić przezroczystość metody, która jest przesłanianie metody wirtualnej lub implementacji interfejsów odpowiadające przezroczystość wirtualnej lub metody interfejsu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżenia od tej reguły. Naruszeń tej reguły spowoduje w środowisku uruchomieniowym <xref:System.TypeLoadException> dla zestawów, które używają przezroczystość poziomu 2.  
  
## <a name="examples"></a>Przykłady  
  
### <a name="code"></a>Kod  
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kod o przezroczystym poziomie bezpieczeństwa, poziom 2](/dotnet/framework/misc/security-transparent-code-level-2)