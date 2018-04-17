---
title: Uaktualnij Dotfuscator Community Edition (CE) | Dokumentacja firmy Microsoft
ms.date: 2017-02-08
ms.devlang: dotnet
ms.technology:
- vs-ide-general
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, Wywłaszczaniem, cenią sobie wcześniejsze rozwiązania w zakresie ochrony cenią sobie wcześniejsze, ochrona, community edition, Zaciemnienie, .NET wolny, uaktualniania, wiersza polecenia programu Visual Studio 2017 r,
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: Dowiedz się, jak uaktualnić bezpłatna wersja Community Dotfuscator uwzględnione w programie Visual Studio 2017 r.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: Joe-Sewell-PreEmptive
manager: douge
ms.openlocfilehash: 03fdaae7a152db2af4ca042d14748e6508185b78
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="upgrade-dotfuscator-community-edition-ce"></a>Uaktualnij Dotfuscator Community Edition (CE)

Dotfuscator Community Edition (Dotfuscator CE) oferuje wiele ochrona aplikacji i funkcje ograniczania funkcjonalności natychmiast dla wszystkich deweloperów przy użyciu programu Microsoft Visual Studio.
Istnieją więcej funkcji dostępne dla użytkowników, którzy ich wersji Dotfuscator uaktualnienia.

## <a name="registering-dotfuscator-ce"></a>Rejestrowanie Dotfuscator CE

Zarejestrowani użytkownicy Dotfuscator CE uzyskać dostęp do dodatkowych funkcji, takich jak [obsługę wiersza polecenia][cli], który ułatwia integrowanie Dotfuscator CE w procesie budowy automatycznych.
Ponadto rejestrowanie będzie zezwalał na dostęp do Lucidator, wbudowane narzędzie służące do [dekodowania śladów stosu zaciemnionego][decode-obfuscated].

Rejestracja jest szybkie, proste i bezpłatnie.
Aby zarejestrować Dotfuscator CE, zobacz [sekcji rejestrowanie CE Dotfuscator na stronie wprowadzenie pełnej Podręcznik użytkownika CE Dotfuscator][register-ce].

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

Dotfuscator Community Edition zawiera podstawowe poziomu ochrony, natomiast  **_cenią sobie wcześniejsze ochrony - Dotfuscator_ Professional Edition** zawiera transformacje zaciemnienie rozszerzone i ochrony możliwości.
Należą do nich następujące elementy:

* *Ochrona praw własności intelektualnej*
  * Zmiana nazwy opcji, w tym Enhanced Overload Induction™ i identyfikator losowe wybieranie dodatkowych.
  * Narzędzia do zdekodowania zaciemniona śladów stosu.
  * Dostęp do przekształcenia zaciemnienie na poziomie przedsiębiorstwa, w tym [transformacje celem defeating automatycznego dekompilacji kodu][control-flow].
  * Możliwość [przesłaniać poufnych ciągów][string-encryption], co proste wyszukiwanie decompiled kodu jest niemożliwe.
  * Możliwość [dyskretne osadzanie ciągów własności i dystrybucji w ponownie zestawy] [ watermarking] (oprogramowania znaku wodnego), umożliwiając ustalenia źródła nieautoryzowany przecieki oprogramowania.
  * Możliwość [połączyć wiele zestawów w jednym][linking], co nawet utrudnia osobom atakującym Określanie ról elementy kodu, ponieważ separacji został wyeliminowany.
  * Możliwość [automatycznie Usuń nieużywane kod z aplikacji][pruning], skracając poufnych kodu, który jest dostarczany.
* *Ochrona integralności aplikacji*
  * Dodatkowe [zachowania obrony aplikacji][check-actions].
  * Możliwość zapewnienia okresie ostrzeżenia, przed upływem ostatecznego terminu z eksploatacji aplikacji.
  * Możliwość powiadomić kod aplikacji w okresie ostrzeżenia z eksploatacji lub po upływie ostatecznego terminu.
  * Szyfrowanie danych telemetrycznych.
* *Monitorowanie aplikacji*
  * Możliwość zbierania i zapisywanie zebranych informacji podczas awarii sieci tymczasowego.
  * Możliwość zbierać dane osobowe.
  * Użycie nieograniczone [funkcja śledzenia][features].
  * Możliwość śledzenia wyjątków przechwycony i generowany przez kod, oprócz nieobsługiwanych wyjątków.
  * Możliwość śledzenia wyjątków w `.dll` zestawów.
  * Szyfrowanie danych telemetrycznych.

Dotfuscator Professional to branżowy standard [faktem .NET] [ net-obfuscator] i jest odpowiedni dla deweloperów w przedsiębiorstwach wymagających trwającą pomocy technicznej, obsługi i aktualizacje produktów.
Ponadto Dotfuscator Professional oferuje zwiększenie poziomu integracji z programem Visual Studio i jest licencjonowany do użytku komercyjnego.

Aby uzyskać więcej informacji na funkcje ochrony zaawansowanych aplikacji Dotfuscator Professional, odwiedź stronę cenią sobie wcześniejsze rozwiązań [strony Przegląd Dotfuscator] [ product-about] i [go do porównania Wersja Community][product-compare].
[Pełni obsługiwane wersje próbne są dostępne na żądanie w preemptive.com][eval].

## <a name="see-also"></a>Zobacz też

[W tym temacie w podręczniku użytkownika CE Dotfuscator pełny][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[control-flow]: https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]: https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]: https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]: https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]: https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]: https://www.preemptive.com/dotfuscator/pro/userguide/en/protection_checks_overview.html#actions
[features]: https://www.preemptive.com/dotfuscator/pro/userguide/en/instrumentation_features.html

[net-obfuscator]: https://www.preemptive.com/products/dotfuscator/overview
[eval]: https://www.preemptive.com/eval-request

[product-about]: https://www.preemptive.com/products/dotfuscator/overview
[product-compare]: https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]: https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[decode-obfuscated]: https://www.preemptive.com/dotfuscator/ce/docs/help/gui_decode_stack_trace.html