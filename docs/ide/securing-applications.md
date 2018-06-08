---
title: Zabezpieczenia
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio], applications
- application design, securability
ms.assetid: 7d32c4cf-8bec-4307-a2a8-42f0ceddf3eb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87e9cb7e9400253713caab17da04c44eb11f5ed1
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843913"
---
# <a name="secure-applications"></a>Zabezpieczanie aplikacji

Należy rozważyć bezpieczeństwo we wszystkich aspektach programowania aplikacji, od projektowania do wdrożenia. Rozpocznij od działanie programu Visual Studio w bezpieczny sposób. Zobacz [uprawnienia użytkownika](../ide/user-permissions-and-visual-studio.md).

Aby efektywnie rozwijać bezpieczne aplikacje, powinieneś rozumieć podstawy pojęć związanych z bezpieczeństwem i funkcji zabezpieczeń platform, dla których tworzysz. Należy również mieć świadomość bezpiecznych technik kodowania.

## <a name="code-for-security"></a>Kod zabezpieczeń

Większość błędów kodowania, które powodują powstanie luk w zabezpieczeniach występują, ponieważ deweloperzy tworzą nieprawidłowe wartości domyślne, podczas pracy z danych wejściowych użytkownika lub nie w pełni rozumieją platformy, dla którego jest tworzenie.

- [Bezpieczne wytyczne dotyczące kodowania](/dotnet/standard/security/secure-coding-guidelines) opisano różne sposoby kodu platformy .NET mogą służyć do pracy w systemie zabezpieczeń.
- [Najlepsze rozwiązania dotyczące C++](/cpp/top/security-best-practices-for-cpp) zawiera informacje dotyczące narzędzi zabezpieczeń i wskazówki dla deweloperów języka C++.

## <a name="build-for-security"></a>Tworzenie dla zabezpieczeń

Zabezpieczenia są też ważną kwestią w procesie kompilacji. Kilka dodatkowych kroków można poprawić bezpieczeństwo wdrożonej aplikacji i pomaga w zapobieganiu nieautoryzowanego odtwarzania, fałszowania lub inne ataki:

- [Dotfuscator](dotfuscator/index.md) jest wolny i ułatwia ochronę odtwarzania i nieautoryzowanego wykorzystania, takich jak debugowanie nieautoryzowanego zestawów platformy .NET.
- [Podpisu silnej nazwy](managing-assembly-and-manifest-signing.md) można jednoznacznie zidentyfikować składników oprogramowania i zapobiec fałszowania nazwy.

## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia w programie .NET Framework](/dotnet/standard/security/index)
- [Zabezpieczeń platformy Azure](/azure/security/)
- [Przewodnik po zabezpieczeniach systemu Windows 10 Mobile](/windows/security/threat-protection/windows-10-mobile-security-guide)
- [Funkcje zabezpieczeń platformy Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/security/best-practices?view=toolsforcordova-2017)
- [Zabezpieczenia platformy ASP.NET Core](/aspnet/core/security/?view=aspnetcore-2.1)
- [Formularze systemu Windows](/dotnet/framework/winforms/windows-forms-security)