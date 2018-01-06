---
title: "CA2106: Secure potwierdzeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 33e200b06ed9bb0999116ea91a64b06aaa879067
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2106-secure-asserts"></a>CA2106: Potwierdzanie zabezpieczeń
|||  
|-|-|  
|TypeName|SecureAsserts|  
|CheckId|CA2106|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Metoda potwierdza uprawnienia i żadne sprawdzenia zabezpieczeń nie są wykonywane na obiekcie wywołującym.  
  
## <a name="rule-description"></a>Opis reguły  
 Potwierdzanie uprawnienia zabezpieczeń bez sprawdzania zabezpieczeń może pozostawić zdatną do wykorzystania słabość zabezpieczeń w kodzie. Przeszukiwania stosu zabezpieczeń zatrzymywana, gdy jest potwierdzone uprawnienia zabezpieczeń. Jeśli uprawnienie jest assert bez wykonywania jakiejkolwiek kontroli wywołującego, wywołujący pośrednio wykonanie kodu przy użyciu uprawnień. Potwierdza bez sprawdzania zabezpieczeń są dopuszczalne, tylko jeśli masz pewność, że assert nie można użyć w szkodliwy sposób. Assert jest bezpieczne, jeśli kod, który można wywołać jest nieszkodliwy lub użytkownicy nie można przekazać dowolnych informacji do kodu, który można wywołać.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, Dodaj żądania zabezpieczeń do metody lub jej typ deklarujący.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Pomiń ostrzeżenie od tej zasady tylko po dokonaniu przeglądu zabezpieczeń zachować ostrożność.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)