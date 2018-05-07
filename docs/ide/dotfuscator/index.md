---
title: Dotfuscator Community Edition (CE)
ms.date: 10/10/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, Wywłaszczaniem, cenią sobie wcześniejsze rozwiązań cenią sobie wcześniejsze ochrony, ochronie, community edition, Zaciemnienie, .NET wolny, Visual Studio 2017 r.
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Dowiedz się, jak możesz chronić aplikacje .NET z bezpłatna wersja Community Dotfuscator uwzględnione w programie Visual Studio 2017 r.
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: douge
ms.openlocfilehash: a81d640e2ecebe46a20f7a3661584cb5c7423691
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dotfuscator-community-edition-ce"></a>Dotfuscator Community Edition (CE)

*Ochrona cenią sobie wcześniejsze — Dotfuscator* zapewnia kompleksową ochronę aplikacji .NET łatwo mieści się w cyklu programistycznym z bezpiecznego oprogramowania.
Użycie ograniczenia funkcjonalności, ochronę i Oczyść pulpitu, mobile serwera i aplikacji embedded ułatwia bezpiecznego tajemnice handlowe i inne prawa własności intelektualnej (IP), ograniczyć piractwo i fałszowania oraz ochronę przed naruszeniem i nieautoryzowanym debugowania.
Dotfuscator działa na skompilowane zestawy bez konieczności dodatkowego programowania lub nawet dostępu do kodu źródłowego.

![Ochrona cenią sobie wcześniejsze — Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>Dlaczego ma znaczenie ochrony

Ważne jest, aby **ochrony własności intelektualnej** (IP).
Kod aplikacji zawiera szczegóły projekt i implementację, które mogą być uważane za IP.
Jednak aplikacje utworzone w programie .NET Framework [obejmują znaczących metadanych i wysokiego poziomu pośredniego kod][assemblies], udostępnia je łatwo odtworzyć, używając jednego z wielu wolny, automatycznego narzędzia.
Zakłócania i zatrzymywanie odtwarzania możesz można zapobiec nieuprawnionym ujawnieniem adresu IP, a także pokazują, że kod zawiera tajemnice handlowe.
Można Dotfuscator [zasłaniają] [ obfuscation] Twojego zestawów platformy .NET utrudnić odtwarzania, przy zachowaniu oryginalnej zachowanie aplikacji.

Ważna jest również **ochronę integralności aplikacji**.
Oprócz odtwarzania nieupoważnione osoby mogą próbować pirate aplikacji, zmiany zachowania aplikacji w czasie wykonywania lub manipulować danymi.
Dotfuscator można wstrzyknąć aplikacji przy użyciu możliwości [wykrywanie, raport i odpowiadać na nieautoryzowany używa][checks], w tym o naruszeniu i debugowanie innych firm.

Aby uzyskać więcej informacji na jak Dotfuscator dopasowuje się do cyklu programistycznym bezpiecznego oprogramowania, zobacz cenią sobie wcześniejsze rozwiązania [strona ochrony aplikacji SDL][sdl-protection].

## <a name="about-dotfuscator-ce"></a>O Dotfuscator CE

Twoja kopia programu Microsoft Visual Studio 2017 zawiera kopię  ***cenią sobie wcześniejsze ochrony - Dotfuscator* Community Edition**, znanej również jako CE Dotfuscator bezpłatnie do użytku osobistego.
Aby uzyskać instrukcje na temat instalowania wersji uwzględnionych w programie Visual Studio 2017 CE Dotfuscator, zobacz [strona instalacji][install].

Dotfuscator CE oferuje szeroką gamę [ochrony oprogramowania i ograniczania funkcjonalności] [ software-protection] usług dla deweloperów, architektów i testerów.
Przykłady [zaciemnienie .NET] [ obfuscation] i innych [ochrona aplikacji] [ app-protection] funkcje zawarte w Dotfuscator CE są:

* *[Zmiana nazwy] [ renaming]*  identyfikatorów utrudnić odtwarzania skompilowane zestawy.
* *[Wykrycie przed] [ tamper]*  do wykrywania wykonywania aplikacji zmodyfikowany, przesłać alerty incydentu, a następnie Zakończ zmodyfikowany sesji.
* *[Układ debugowania] [ debug]*  do wykrywania dołączanie debugera do uruchomienia aplikacji, przesłać alerty incydentu, a następnie Zakończ debugowanym sesji.
* *[Zachowania wygaśnięcia aplikacji] [ shelflife]*  który kodowania daty "z wycofanych", wysyłać alerty, kiedy są wykonywane po ich Data wygaśnięcia aplikacji, a następnie Zakończ aplikacji wygasłych sesji.
* *[Śledzenie wyjątków] [ exceptions]*  do monitorowania nieobsługiwanych wyjątków występujących w aplikacji.
* *[Sesja] [ sessions] i [funkcji] [ features] śledzenie użycia* do określenia, jakie aplikacje były wykonywane, jakie wersje tych aplikacje i jakie funkcje są używane w tych aplikacjach.

Szczegółowe informacje o tych funkcjach, w tym sposób dopasowania do strategii ochrony aplikacji można znaleźć [strony możliwości][capabilities].

Dotfuscator CE udostępnia podstawowe ochrony out-of--box.
Jeszcze więcej środków ochronnych aplikacji dostępnych w zarejestrowani użytkownicy Dotfuscator CE i użytkowników *cenią sobie wcześniejsze ochrony - Dotfuscator* Professional Edition początkowe na świecie [faktem .NET] [net-obfuscator].
Aby dowiedzieć się, jak udoskonalanie Dotfuscator, zobacz [strony uaktualnienia][upgrades].

## <a name="getting-started"></a>Wprowadzenie

Aby rozpocząć korzystanie z CE Dotfuscator z programu Visual Studio, wpisz `dotfuscator` do **Szybkie uruchamianie** pasek wyszukiwania (Ctrl + Q).

* Jeśli zainstalowano Dotfuscator CE **Szybkie uruchamianie** wywołuje *Menu* opcję, aby uruchomić interfejs użytkownika Dotfuscator CE. Aby uzyskać więcej informacji, zobacz [na stronie wprowadzenie pełnej Podręcznik użytkownika CE Dotfuscator][get-started].
* Jeśli nie zainstalowano jeszcze Dotfuscator CE, **Szybkie uruchamianie** wyświetlenie odpowiedniego *zainstalować* opcji. Zobacz [strona instalacji] [ install] szczegółowe informacje.

Można także uzyskać **najnowszej wersji** CE Dotfuscator z [strony Dotfuscator pliki do pobrania na preemptive.com][download].

## <a name="full-documentation"></a>Pełną dokumentację

Tę stronę i jego podstrony stanowią ogólne omówienie funkcji Dotfuscator CE, jak również [instrukcje dotyczące instalowania narzędzia][install].

Zobacz [pełny przewodnik użytkownika CE Dotfuscator w preemptive.com] [ full] szczegółowe instrukcje dotyczące obsługi, w tym [sposobu uruchamiania przy użyciu interfejsu użytkownika Dotfuscator CE] [ get-started].

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

- [assemblies]: https://docs.microsoft.com/en-us/dotnet/standard/assembly-format
- [software-protection]: https://www.preemptive.com/software-protection
- [obfuscation]: https://www.preemptive.com/obfuscation
- [app-protection]: https://www.preemptive.com/application-protection
- [sdl-protection]: https://www.preemptive.com/solutions/SDL-App-Protection
- [net-obfuscator]: https://www.preemptive.com/products/dotfuscator/overview
- [download]: https://www.preemptive.com/products/dotfuscator/downloads

- [install]: install.md
- [capabilities]: capabilities.md
- [upgrades]: upgrades.md

- [get-started]: https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

- [renaming]: https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

- [checks]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
- [tamper]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
- [debug]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
- [shelflife]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

- [exceptions]: https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_exceptions.html
- [sessions]: https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_sessions.html
- [features]: https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_features.html

- [full]: https://www.preemptive.com/dotfuscator/ce/docs/help/index.html