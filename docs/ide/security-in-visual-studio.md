---
title: Zabezpieczenia w Visual Studio
ms.date: 02/17/2017
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 74e557fd0e92742f33c25d68862ae15254104963
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="security-in-visual-studio"></a>Zabezpieczenia w Visual Studio

Należy rozważyć bezpieczeństwo we wszystkich aspektach programowania aplikacji, od projektowania do wdrożenia. Rozpocznij od działanie programu Visual Studio w bezpieczny sposób. Zobacz [uprawnienia użytkownika](../ide/user-permissions-and-visual-studio.md).

 Aby efektywnie rozwijać bezpieczne aplikacje, powinieneś rozumieć podstawy pojęć związanych z bezpieczeństwem i funkcji zabezpieczeń platform, dla których tworzysz. Należy również mieć świadomość bezpiecznych technik kodowania.

## <a name="understand-security"></a>Zrozumienie zabezpieczeń
 [Zabezpieczenia](/dotnet/standard/security/index) zabezpieczenia dostępu kodu w tym artykule opisano .NET Framework, na podstawie ról zabezpieczeń, zasady zabezpieczeń i narzędzia zabezpieczeń.

 [Obrony kodu za pomocą wskazówki dotyczące bezpieczeństwa pierwszych dziesięciu Każdy deweloper musi znać](http://go.microsoft.com/fwlink/?LinkId=72877) opisano problemy, które należy uważać się na tak, aby nie naruszyć bezpieczeństwo danych lub systemu.

## <a name="code-for-security"></a>Kod zabezpieczeń
 Większość błędów kodowania, które powodują powstanie luk w zabezpieczeniach, występuje, ponieważ deweloperzy mogą stosować błędne założenia podczas pracy z danymi wejściowymi użytkownika lub ponieważ nie w pełni rozumieją platformę, dla której tworzą.

 [Bezpieczne wytyczne dotyczące kodowania](/dotnet/standard/security/secure-coding-guidelines) zawiera wskazówki dotyczące klasyfikacji składniki do rozwiązywania problemów zabezpieczeń.

 [Najlepsze rozwiązania](/cpp/top/security-best-practices-for-cpp) funkcji dostarczanej przez flagę kompilacji/GS kontroli przepełnienia buforu Discusses i pełnego obrazu zabezpieczeń Microsoft Visual C++.

## <a name="build-for-security"></a>Tworzenie dla zabezpieczeń
 Zabezpieczenia są też ważną kwestią w procesie kompilacji.  Kilka dodatkowych kroków można poprawić bezpieczeństwo wdrożonej aplikacji i zapobiec nieautoryzowanym odtwarzania, fałszowania lub inne ataki.

 [Dotfuscator Community Edition (CE)](dotfuscator/index.md) wyjaśniono, jak skonfigurować i rozpocząć korzystanie z bezpłatnej ochrony cenią sobie wcześniejsze - Dotfuscator Community Edition do ochrony zestawów platformy .NET z odtwarzania i nieautoryzowanego użycia (na przykład nieautoryzowanego debugowanie).

 [Zarządzanie zestawu i manifestu podpisywania](managing-assembly-and-manifest-signing.md) Discusses silnej nazwy podpisywania, która może służyć do unikatowego identyfikowania składników oprogramowania, uniemożliwia fałszowania nazwy.