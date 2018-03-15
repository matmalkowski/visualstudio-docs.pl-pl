---
title: "Obsługiwanie zabezpieczeń aplikacji w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: article
helpviewer_keywords:
- unauthorized access
- Baseline Security Analyzer
- Microsoft Baseline Security Analyzer
- security [.NET Framework], best practices
- MBSA (Microsoft Baseline Security Analyzer)
- security [.NET Framework], maintaining after deployment
ms.assetid: 621d10c1-842b-4902-be60-bb9719591751
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f0594f7c9af507f2c68ac4f0cc80b1d2e38d2a51
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="maintaining-security"></a>Obsługiwanie zabezpieczeń

Często mówi się, że ceną bezpieczeństwa jest nieprzerwana czujność. Pomimo najwyższej uwagi poświęconej bezpieczeństwu podczas projektowania i rozwoju aplikacji, należy przyjąć, że po jej wdrożeniu pojawią się luki w zabezpieczeniach. Dzięki audytom aplikacji i analizie dzienników zdarzeń, możesz odkryć poprzednio ukryte wady.

Ponadto, musisz zachowywać czujność nie tylko, jeśli chodzi o swoją własną aplikację. Musisz też być na bieżąco ze wszystkimi zagrożeniami bezpieczeństwa i błędami dotyczącymi platformy, na której działa aplikacja, i innych produktów, od których zależy aplikacja.

[Zabezpieczeń, prywatności i kont](https://support.microsoft.com/products/microsoft-account?category=privacy#security-privacy-accounts-help=windows-8&v0h=winrttab1&v1h=win8tab1&v2h=win7tab1&v3h=winvistatab1)&mdash;Uzyskaj pomoc dotyczącą bezpieczeństwa, ochrony prywatności i kont użytkownika, w tym informacje o wirusy, hasła, kontroli rodzicielskiej, zapory i szyfrowaniu dysków.

[Biuletyny aktualizacje zabezpieczeń Microsoft](https://technet.microsoft.com/security/bulletins.aspx)&mdash;tej strony można łatwo biuletyny Znajdź wydane wcześniej. Biuletyny bezpieczeństwa, przeznaczone dla specjalistów IT, zawierają szczegółowe informacje dotyczące aktualizacji zabezpieczeń.

[Microsoft Baseline Security Analyzer](https://www.microsoft.com/download/details.aspx?id=7558)&mdash;Microsoft Baseline Security Analyzer (MBSA) jest narzędziem, które umożliwia macierzysty użytkownika, użytkownik firmowy lub administrator skanowania co najmniej jeden komputer z systemem Windows dla wspólnego błędów konfiguracji zabezpieczeń.