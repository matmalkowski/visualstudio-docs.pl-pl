---
title: Zabezpieczenia w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/17/2017
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d7862f5f7b3eeb46d28e5cc25c38865c7a208c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="security-in-visual-studio"></a>Zabezpieczenia w programie Visual Studio

Należy rozważyć zabezpieczeń we wszystkich aspektach programowania aplikacji, z projektu do wdrożenia. Rozpocznij od działanie programu Visual Studio w bezpieczny sposób. Zobacz [uprawnienia użytkownika](../ide/user-permissions-and-visual-studio.md).  
  
 Aby skutecznie tworzyć aplikacje bezpieczne, powinien mieć podstawową wiedzę na temat pojęć związanych z zabezpieczeniami i funkcje zabezpieczeń platformy, dla których tworzenie. Należy również poznać bezpiecznego technik programowania.  
  
## <a name="understanding-security"></a>Opis zabezpieczeń  
 [Zabezpieczeń](/dotnet/standard/security/index)  
 W tym artykule opisano zabezpieczenia dostępu kodu .NET Framework, na podstawie ról zabezpieczeń, zasady zabezpieczeń i narzędzia zabezpieczeń.  
  
 [Obrony kodu za pomocą pierwszych dziesięciu porady dotyczące zabezpieczeń, których każdy deweloper musi wiedzieć](http://go.microsoft.com/fwlink/?LinkId=72877)  
 W tym artykule opisano problemy, które należy uważać się na tak, aby nie naruszyć bezpieczeństwo danych lub systemu.  
  
## <a name="coding-for-security"></a>Kodowanie dla zabezpieczeń  
 Większość błędów kodowania, które powodują powstanie luk w zabezpieczeniach wynikać deweloperzy tworzą nieprawidłowe wartości domyślne, podczas pracy z danych wejściowych użytkownika lub nie w pełni rozumieją platformy, dla którego jest tworzenie.  
  
 [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)  
 Zawiera wskazówki dotyczące klasyfikacji składniki do rozwiązywania problemów zabezpieczeń.  
  
 [Najlepsze rozwiązania](/cpp/top/security-best-practices-for-cpp)  
 W tym artykule omówiono przepełnienia buforu i pełnego obrazu udostępniane przez flagę kompilacji/GS funkcji kontroli zabezpieczeń Microsoft Visual C++.

## <a name="building-for-security"></a>Tworzenie dla zabezpieczeń  
 Zabezpieczenia są też ważną kwestią w procesie kompilacji.  Kilka dodatkowych kroków można poprawić bezpieczeństwo wdrożonej aplikacji i zapobiec nieautoryzowanym odtwarzania, fałszowania lub inne ataki.

 [Dotfuscator Community Edition (CE)](dotfuscator/index.md)  
 Wyjaśniono, jak skonfigurować i rozpocząć korzystanie z bezpłatnej ochrony cenią sobie wcześniejsze - Dotfuscator Community Edition do ochrony zestawów platformy .NET z odtwarzania i nieautoryzowanego użycia (na przykład nieautoryzowanego debugowanie).
  
 [Zarządzanie zestawem i podpisywanie manifestu](managing-assembly-and-manifest-signing.md)  
 W tym artykule omówiono silnej nazwy podpisywania, która może służyć do unikatowego identyfikowania składników oprogramowania, uniemożliwia fałszowania nazwy.