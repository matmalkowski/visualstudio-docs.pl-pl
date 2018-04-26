---
title: Obsługa zabezpieczeń aplikacji w programie Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee7a90804c2161fe927bebc2b2f1af45862b8ccd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="maintain-security"></a>Obsługa zabezpieczeń

Często mówi się, że ceną bezpieczeństwa jest nieprzerwana czujność. Pomimo najwyższej uwagi poświęconej bezpieczeństwu podczas projektowania i rozwoju aplikacji, należy przyjąć, że po jej wdrożeniu pojawią się luki w zabezpieczeniach. Dzięki audytom aplikacji i analizie dzienników zdarzeń, możesz odkryć poprzednio ukryte wady.

Ponadto, musisz zachowywać czujność nie tylko, jeśli chodzi o swoją własną aplikację. Musisz też być na bieżąco ze wszystkimi zagrożeniami bezpieczeństwa i błędami dotyczącymi platformy, na której działa aplikacja, i innych produktów, od których zależy aplikacja.

[Zabezpieczeń, prywatności i kont](https://support.microsoft.com/products/microsoft-account?category=privacy#security-privacy-accounts-help=windows-8&v0h=winrttab1&v1h=win8tab1&v2h=win7tab1&v3h=winvistatab1)&mdash;Uzyskaj pomoc dotyczącą bezpieczeństwa, ochrony prywatności i kont użytkownika, w tym informacje o wirusy, hasła, kontroli rodzicielskiej, zapory i szyfrowaniu dysków.

[Aktualizacje zabezpieczeń Microsoft biuletyny](https://technet.microsoft.com/security/bulletins.aspx)&mdash;tej strony można łatwo biuletyny Znajdź wydane wcześniej. Biuletyny bezpieczeństwa, przeznaczone dla specjalistów IT, zawierają szczegółowe informacje dotyczące aktualizacji zabezpieczeń.

[Microsoft Baseline Security Analyzer](https://www.microsoft.com/download/details.aspx?id=7558)&mdash;Microsoft Baseline Security Analyzer (MBSA) jest narzędziem, które umożliwia macierzysty użytkownika, użytkownik firmowy lub administrator skanowania co najmniej jeden komputer z systemem Windows dla wspólnego błędów konfiguracji zabezpieczeń.