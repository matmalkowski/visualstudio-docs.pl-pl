---
title: Możliwości Dotfuscator
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
description: Dowiedz się więcej możliwości bezpłatna wersja Community Dotfuscator uwzględnione w programie Visual Studio 2017 r.
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: douge
ms.openlocfilehash: 39ec170858074cb7cb2bc4ab580cb2268164e0ad
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="capabilities-of-dotfuscator"></a>Możliwości Dotfuscator

Ta strona koncentruje się na możliwości Dotfuscator Community Edition (Dotfuscator CE) z niektórych odwołań do zaawansowane opcje dostępne za pośrednictwem [uaktualnień][upgrades].

Jest Dotfuscator *postkompilacyjnego* systemu dla aplikacji .NET.
Z Dotfuscator CE Visual Studio użytkownicy będą mogli [zasłaniają zestawy] [ obfuscation] i wstrzyknąć [obrony active] [ checks] i [analytics śledzenia] [ analytics] do aplikacji — wszystko to bez Dotfuscator wymagające dostęp do oryginalnego kodu źródłowego.
Dotfuscator chroni aplikacji na wiele sposobów tworzenia strategii ochrony warstwowego.

Dotfuscator CE obsługuje szeroki zakres .NET zestawu typu i aplikacja, w tym [Windows platformy Uniwersalnej] [ uwp] i [Xamarin] [ xamarin].

## <a name="intellectual-property-protection"></a>Ochrona praw własności intelektualnej

Projektowanie aplikacji, zachowania i implementacji są formy własności intelektualnej (IP).
Jednak aplikacje utworzone dla programu .NET Framework są zasadniczo Otwórz książek; jest bardzo proste do odtwarzania zestawów platformy .NET, [ponieważ zawierają one wysokiego poziomu metadane i pośredniego kodu][assemblies].

Dotfuscator CE zawiera podstawowe [zaciemnienie .NET] [ obfuscation] w formie [zmiana nazwy][renaming].
Obfuscating kodu za pomocą Dotfuscator zmniejsza ryzyko nieautoryzowanego dostępu do kodu źródłowego za pomocą odtwarzania ważne informacje o nazewnictwie nie będzie już publicznego.
Zaciemnienie przedstawiono również nakładu pracy ze strony użytkownika, aby zabezpieczyć kod badania - cenne krok w ustaleniu, że IP legalnie jest chroniony jako tajemnice handlowe.

Duża liczba [funkcji ochrony integralności aplikacji](#application-integrity-protection) Dotfuscator CE dalsze przeszkodę odtwarzania.
Na przykład aktora zły mogą próbować dołączyć debugera do działającego wystąpienia aplikację, aby zrozumieć logice programu.
Można wstrzyknąć Dotfuscator [zachowanie debugowania przed] [ debug] w aplikacji, aby to utrudniać.

## <a name="application-integrity-protection"></a>Ochrona integralności aplikacji

Oprócz ochrony kodu źródłowego, jest również należy się upewnić, że aplikacja jest używana jako składnik przeznaczony.
Osoby atakujące mogą próbować przejąć aplikację, aby ominąć zasady licencjonowania (tj., piractwo), wykradać lub modyfikowania poufnych danych, które zostały obsłużone przez aplikację, lub do zmiany zachowania aplikacji.

Można wstrzyknąć Dotfuscator CE [kodu walidacji aplikacji] [ checks] do zestawów, w tym [wykrycie przed] [ tamper] i [przed debugowania] [ debug] środków.
Po wykryciu stanu aplikacji nieprawidłowy kod sprawdzania poprawności można [wezwać kod aplikacji, adres do sytuacji, w odpowiedni sposób][check-app].
Lub, jeśli nie chcesz napisać kod nieprawidłowy uchwyt korzysta z aplikacji, Dotfuscator można również wprowadzić [raportowania danych telemetrycznych] [ check-telemetry] i [odpowiedzi] [ check-action] zachowania, bez żadnych modyfikacji kodu źródłowego.

Wiele z tych samych metod również może być używany w celu wymuszenia [terminy z eksploatacji] [ shelflife] oceny lub wersji próbnej oprogramowania.

## <a name="application-monitoring"></a>Monitorowanie aplikacji

Podczas tworzenia aplikacji, bardzo ważne jest zrozumienie wzorców zachowania użytkowników, w tym w wersji beta testerów i użytkownicy wcześniejszych wersji.
Analizy aplikacji służy do śledzenia, jak często aplikacja jest używana i w jaki sposób jest używany w tym jakie błędy klienci mają do czynienia.

Można wstrzyknąć Dotfuscator CE [śledzenia wyjątków][exceptions], [śledzenia sesji][sessions], i [funkcja śledzenia] [ features] kodu do aplikacji.
Po uruchomieniu aplikacji przetworzone dane będą przesyłane analytics do skonfigurowany [punktu końcowego cenią sobie wcześniejsze Analytics][endpoints].

## <a name="see-also"></a>Zobacz też

[W tym temacie w podręczniku użytkownika CE Dotfuscator pełny][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

- [assemblies]: https://docs.microsoft.com/en-us/dotnet/standard/assembly-format
- [uwp]: https://www.preemptive.com/blog/article/856-uwp-applications-in-dotfuscator-ce/91-dotfuscator-ce
- [xamarin]: https://www.preemptive.com/obfuscating-xamarin-with-dotfuscator

- [upgrades]: upgrades.md

- [obfuscation]: https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_overview.html
- [renaming]: https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

- [analytics]: https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_overview.html
- [endpoints]: https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_overview.html#endpoints

- [checks]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
- [check-app]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#app-notification
- [check-action]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#action

- [tamper]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
- [debug]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
- [shelflife]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html
- [exceptions]: https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_exceptions.html
- [sessions]: https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_sessions.html
- [features]: https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_features.html
- [check-telemetry]: https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_checks.html

- [full]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_capabilities.html