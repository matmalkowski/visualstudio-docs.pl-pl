---
title: Dowiedz się więcej o programowaniu rozwiązań mobilnych za pomocą platformy Xamarin | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: e970d936-1df4-4c0c-96e3-ef6191295882
ms.prod: xamarin
ms.technology: xamarin-tools
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 98371b648dc7fe18315904d4759b55701a07f7b1
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251682"
---
# <a name="learn-about-mobile-development-with-xamarin"></a>Informacje dotyczące programowania mobilnego za pomocą platformy Xamarin

W tym artykule wymieniono kilka omówienie, które mogą ułatwić zrozumienie, opracowywanie aplikacji mobilnych dla wielu platform za pomocą platformy Xamarin. Jeśli nie zainstalowano jeszcze programu Visual Studio i Xamarin, uruchom [Instalator i instalacja](../cross-platform/setup-and-install.md) procesu po pierwsze, następnie wróć tutaj i pracować za pośrednictwem tych zasobów, gdy instalatory są uruchomione.

> [!NOTE]
> Jeśli nie określono inaczej, początkowo można odczytać tylko tych stron, które są połączone bezpośrednio z tego miejsca i stron nie pomocniczych. Jeśli proces instalacji jest nadal uruchomione po ukończeniu tej listy, możesz przejść wstecz i Poznaj dodatkowe tematy.
>
> Także swobodnie zapoznaj się z tematami, oznaczone jako "Essentials" i wróć do tematów "Bardziej zgłębić temat" później.

## <a name="essentials-introduction-to-xamarin"></a>Podstawy: Wprowadzenie do platformy Xamarin

*10-20 minut*

1.  [Aplikacje mobilne w programie Visual Studio za pomocą platformy Xamarin](https://visualstudio.microsoft.com/xamarin/) (visualstudio.com) zawiera krótkie podsumowania podstawowe właściwości platformy Xamarin.

2.  [Twórz aplikacje mobilne dla wielu platform przy użyciu języka C# i Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2015-Final-Release-Event/Building-cross-platform-mobile-apps-using-C-and-Visual-Studio-2015) (— Channel9, 15m16s) za pomocą platformy Xamarin Propagator, James Montemagno. Pierwsze trzy minuty są z omówieniem platformy Xamarin, następuje pokazów kodu.

## <a name="essentials-overview-of-the-visual-studio-and-xamarin-environment"></a>Podstawy: Omówienie środowiska Visual Studio i Xamarin

*5 – 15 minut*

-   Wykonasz większość swojej pracy na komputerze Windows zainstalowany za pomocą programu Visual Studio i Xamarin. Na tym komputerze bezpośrednio tworzyć aplikacje dla systemu Android i Windows oraz uruchamianie i debugowanie ich na pulpicie, urządzeń lub emulatorów. Również zdalnie kompilowanie, uruchamianie i debugowanie aplikacji dla systemu iOS przy użyciu komputerów Mac. Visual Studio na komputerze Windows też nawiązać połączenie z systemem iOS designer scenorysu i symulatora systemu iOS.

-   Mac za pomocą środowiska Xcode i Visual Studio for Mac zainstalowane służy jako host kompilacji, podpisywania hosta i środowisko uruchomieniowe dla aplikacji systemu iOS. Delegaty Windows komputera z systemem iOS opiera się na tym komputerze Mac. Aplikacja zostanie uruchomiona w symulatorze systemu iOS na komputerze Mac lub bezpośrednio na urządzenia powiązanego połączone na komputerze Mac. Można korzystać z aplikacji na komputerze Mac, ale należy przeprowadzić debugowanie w programie Visual Studio.

Te relacje są przedstawione poniżej.

![Relacja między komputerami deweloperów Windows i Mac w środowisku Xamarin](../cross-platform/media/crossplat-xamarin-learn-1.png "CrossPlat Xamarin informacje 1")

> [!NOTE]
> Windows Phone jest wyświetlany na tym rysunku na potrzeby informacje były kompletne. Korzystając z platformy Xamarin, to zalecana opcja udostępniania kodu jest biblioteki .NET Standard 2.0, który jest niezgodny z urządzeniami Windows Phone lub Windows 10 Mobile.

Możesz dowiedzieć się więcej o pracy z aplikacjami systemu iOS na [wprowadzenie do rozwiązania Xamarin.iOS dla programu Visual Studio](/xamarin/ios/get-started/installation/windows/introduction-to-xamarin-ios-for-visual-studio/).

## <a name="essentials-how-projects-are-structured"></a>Podstawy: Projekty są struktury

*10-30 minut*

1.  [Udostępnianie kodu opcje](/xamarin/cross-platform/app-fundamentals/code-sharing/). W przypadku nowych aplikacji należy używać biblioteki .NET Standard do udostępniania kodu. Większość kodu logiki biznesowej będą znajdować się w bibliotece .NET Standard, w tym dostęp do baz danych, wywołania interfejsów API REST i wywołania przenośne składników platformy Xamarin. (Zobacz [bardziej zgłębić temat: składników platformy Xamarin](#components) na końcu tego artykułu). Wspólny kod interfejsu użytkownika, napisane przy użyciu zestawu narzędzi Xamarin.Forms znajduje się również w biblioteki .NET Standard.

2.  (Opcjonalnie) [Analiza przypadku: Tasky](/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/case-study-tasky/) w tym artykule opisano najlepsze rozwiązania dotyczące projektowania i struktury aplikacji w pełni funkcjonalne, np. tworzenia struktury projektu ze współdzielonym kodem, który oddziela dane, dostęp do danych i warstwy biznesowej.

## <a name="essentials-native-and-xamarinforms-ui-layers"></a>Essentials: natywne i warstwy interfejsu użytkownika zestawu narzędzi Xamarin.Forms

*10-40 minut*

Środowisko Xamarin zapewnia dwa sposoby tworzenia atrakcyjnych aplikacji: Native platformy Xamarin i Xamarin.Forms.

Za pomocą platformy Xamarin Native, pisania osobnego kodu interfejsu użytkownika dla każdej z platform docelowych: iOS, Android i Windows.  W przypadku tej metody masz bezpośredni dostęp do interfejsów API specyficznych dla platformy, aby zaprojektować dostosowane środowisko interfejsu użytkownika dla danej platformy.  Możesz również mieć pełny dostęp do natywnych projektanta i kontrolki dla każdej platformy, pomagające w tworzeniu odpowiedniego interfejsu użytkownika.

Xamarin.Forms zawiera zestaw ogólnych interfejsów API, która umożliwia zapisanie udostępnionej warstwy interfejsu użytkownika dla wszystkich platform z biblioteki .NET Standard.  Renderuje zestaw narzędzi Xamarin.Forms do natywnych kontrolek na każdej z platform docelowych zapewnia natywnego wyglądu i działania.  Zamiast używania projektanta, możesz utworzyć interfejs użytkownika przy użyciu języka C# i XAML.

Większość programistów używa zestawu narzędzi Xamarin.Forms. Jest to zalecane trasy dla nowego środowiska xamarin dla deweloperów. Podejście natywnego platformy Xamarin jest trudniejsze i wymaga, aby uzyskać bardziej szczegółowe wiedzę na temat platform docelowych.

Nie musisz zdecydować, które rozwiązanie do wykonania na początku; aplikacje można zaimplementować przy użyciu kombinacji natywnego środowiska Xamarin i Xamarin.Forms:

-   Do tworzenia ekranów ogólnego przeznaczenia, należy użyć zestawu narzędzi Xamarin.Forms. Te zapewniają podobne interfejsy użytkownika i funkcje na platformach, takich jak nazwy logowania, skontaktuj się z formularzy i wyniki wyszukiwania.

-   Użyj różnych możliwości dostosowywania w interfejsie Xamarin.Forms, aby dopasować interfejsu użytkownika na poszczególnych platform. Obejmuje to najprostsza opcja dostosowywania `OnPlatform` interfejsu API. Możesz również tworzyć widoki niestandardowe, rozszerzyć istniejące programy renderujące i utworzyć niestandardowe programy renderujące.

-   Jeśli to konieczne, należy użyć natywnego platformy Xamarin do tworzenia ekranów, korzystających z unikatowych funkcji poszczególnych platform interfejsu użytkownika. Przykładem jest ekran, który używa natywnego aparatu manipulowania przechwytywania i obrazów.

Zazwyczaj powinien zaczynać rozwiązanie Xamarin.Forms, aby skonfigurować interfejs użytkownika współużytkowanie kodu na wielu platformach. Można następnie dostosować specyficzne dla platformy, należy użyć możliwości dostosowywania. Jeśli potrzebujesz ekrany całkowicie specyficzne dla platformy, można dodać oddzielnie za pomocą natywnego platformy Xamarin.

Aby dowiedzieć się więcej:

1.  [Zestaw narzędzi Xamarin.Forms](/xamarin/xamarin-forms/) zawiera krótkie omówienie i zalet i wad Xamarin.Forms a native warstwy interfejsu użytkownika (czyli Xamarin.iOS i Xamarin.Android).

2.  Pierwsze trzy minuty wideo James Montemagno [Xamarin.Forms: natywnych dla systemów iOS, Android i Windows aplikacje za pomocą języka C# i XAML](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/704) (— Channel9, 13m3s) ogólny innego i będziesz kontynuować, obserwowanie pokazów.

3.  (Opcjonalnie) [Wprowadzenie do zestawu narzędzi Xamarin.Forms](/xamarin/xamarin-forms/get-started/introduction-to-xamarin-forms/)

4.  (Opcjonalnie) Zapoznaj się z przykładami użycia `OnPlatform` do dostosowania w [klasę urządzeń pamięci](/xamarin/xamarin-forms/platform/device/) dokumentacji

5.  (Opcjonalnie) [Dla wielu platform — kodzie udziału interfejsu użytkownika różnych platform urządzeń przenośnych za pomocą zestawu narzędzi Xamarin.Forms](https://msdn.microsoft.com/magazine/dn904669.aspx) przez Jason Smith (MSDN Magazine) przedstawiono opcje dostosowywania różne, w ramach zestawu narzędzi Xamarin.Forms, dla którego szczegółowe informacje znajdują się na [ Niestandardowe programy renderujące](/xamarin/xamarin-forms/app-fundamentals/custom-renderer/).

## <a name="deeper-dive-debugging-with-emulators"></a>Bardziej zgłębić temat: debugowanie przy użyciu emulatorów

*10 – 15 minut*

Aby debugować aplikacje dla wielu platform bez konieczności używania fizycznego urządzenia, należy użyć emulatorów omówionych w tym miejscu:

### <a name="microsofts-android-emulator"></a>Emulator systemu Android firmy Microsoft

Zaleca się, że używasz firmy Microsoft [narzędzie Visual Studio emulator for Android](visual-studio-emulator-for-android.md), która jest instalowana z programem Visual Studio.  [Narzędzie Visual Studio emulator for Android](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/711) wideo (Channel9, 5m55s) zapewnia przegląd i prezentacja.

### <a name="apples-ios-simulator"></a>Symulator systemu iOS firmy Apple

Aby dowiedzieć się więcej, przeczytaj [wprowadzenie w narzędziu iOS Simulator](https://developer.apple.com/library/prerelease/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html#//apple_ref/doc/uid/TP40012848-CH5-SW1) (apple.com).

### <a name="microsofts-windows-phone-emulator"></a>Emulator Windows Phone firmy Microsoft

Aby dowiedzieć się więcej, przeczytaj [testu za pomocą emulatora firmy Microsoft dla systemu Windows 10 Mobile](/windows/uwp/debug-test-perf/test-with-the-emulator).

<a name="components" />

## <a name="deeper-dive-xamarin-components"></a>Bardziej zgłębić temat: składników platformy Xamarin

*10 minut*

Wiele rozszerzone możliwości są dostępne dla aplikacji platformy Xamarin przy użyciu składników platformy Xamarin. Możesz znaleźć pełne wykazu, dostępna do pobrania na [ http://components.xamarin.com/ ](http://components.xamarin.com/), która obejmuje składniki dodatkowe formanty interfejsu użytkownika, uwierzytelnianie, szereg usług cloud services, takich jak Microsoft Azure i wiele więcej.