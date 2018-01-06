---
title: Zabezpieczenia w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: "20"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 995ac17cd99c395dcf1c69f0d05e1b273ac72f1d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="security-in-visual-studio"></a>Zabezpieczenia w Visual Studio
Należy rozważyć bezpieczeństwo we wszystkich aspektach programowania aplikacji, od projektowania do wdrożenia. Rozpocznij od działanie programu Visual Studio w bezpieczny sposób. Zobacz [uprawnienia użytkownika](../ide/user-permissions-and-visual-studio.md).  
  
 Aby efektywnie rozwijać bezpieczne aplikacje, powinieneś rozumieć podstawy pojęć związanych z bezpieczeństwem i funkcji zabezpieczeń platform, dla których tworzysz. Należy również mieć świadomość bezpiecznych technik kodowania.  
  
## <a name="understanding-security"></a>Opis zabezpieczeń  
 [Zabezpieczenia](/dotnet/standard/security/index)  
 Opisuje zabezpieczenia dostępu do kodu .NET Framework, zabezpieczenia oparte na rolach, zasady zabezpieczeń i narzędzia zabezpieczeń.  
  
 [Obrony kodu za pomocą pierwszych dziesięciu porady dotyczące zabezpieczeń, których każdy deweloper musi wiedzieć](http://go.microsoft.com/fwlink/?LinkId=72877)  
 W tym artykule opisano problemy, na które należy zwrócić uwagę, aby nie naruszyć danych lub systemu.  
  
## <a name="coding-for-security"></a>Bezpieczne kodowanie  
 Większość błędów kodowania, które powodują powstanie luk w zabezpieczeniach, występuje, ponieważ deweloperzy mogą stosować błędne założenia podczas pracy z danymi wejściowymi użytkownika lub ponieważ nie w pełni rozumieją platformę, dla której tworzą.  
  
 [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)  
 Zawiera wskazówki dotyczące klasyfikacji składników, aby rozwiązywać problemy z bezpieczeństwem.  
  
 [Najlepsze rozwiązania](/cpp/top/security-best-practices-for-cpp)  
 W tym artykule omówiono przepełnienia bufora oraz pełny obraz funkcji kontroli zabezpieczeń Microsoft Visual C++, dostarczanej przez flagę czasu kompilacji /GS.

## <a name="building-for-security"></a>Tworzenie dla zabezpieczeń  
 Zabezpieczenia są też ważną kwestią w procesie kompilacji.  Kilka dodatkowych kroków można poprawić bezpieczeństwo wdrożonej aplikacji i zapobiec nieautoryzowanym odtwarzania, fałszowania lub inne ataki.

 [Dotfuscator Community Edition (CE)](dotfuscator/index.md)  
 Wyjaśniono, jak skonfigurować i rozpocząć korzystanie z bezpłatnej ochrony cenią sobie wcześniejsze - Dotfuscator Community Edition do ochrony zestawów platformy .NET z odtwarzania i nieautoryzowanego użycia (na przykład nieautoryzowanego debugowanie).
  
 [Zarządzanie podpisywaniem zestawu i manifestu](managing-assembly-and-manifest-signing.md)  
 W tym artykule omówiono silnej nazwy podpisywania, która może służyć do unikatowego identyfikowania składników oprogramowania, uniemożliwia fałszowania nazwy.