---
title: Zainstaluj platformę Xamarin dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
ms.prod: visual-studio-dev15
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 8bbb27ad3368b53fc3e333d3260f2f30551c4177
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251195"
---
# <a name="setup-and-install"></a>Instalator i instalacja

Do tworzenia natywnych dla systemów iOS, Android i Windows aplikacje z poziomu wspólnego języka C# / kodu platformy .NET przy użyciu platformy Xamarin, potrzebny następujący sprzęt i oprogramowanie:

-   Do pracy z Windows i aplikacje dla systemu Android: Windows komputerze deweloperskim (nie maszyna wirtualna) przy użyciu programu Visual Studio 2017 (w tym funkcji programowania Xamarin) zainstalowane.

-   Do pracy z aplikacjami systemu iOS: Mac z systemem macOS Sierra 10.12 lub powyżej, za pomocą środowiska Xcode jest zainstalowany i programu Visual Studio dla komputerów Mac jest zainstalowany.

Nie osobnych licencji są wymagane do używania platformy Xamarin.

Można skonfigurować komputery Windows i Mac, w tym samym czasie, a podczas wykonywania tych instalatorów można przejść przez [Dowiedz się więcej o programowaniu rozwiązań mobilnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) do odczytywania i obejrzyj materiał niezbędne tła.

Jeśli masz problemy po wykonaniu tego Instalator i instalacja przy użyciu platformy Xamarin, opublikuj swoje pytanie na [forums.xamarin.com](http://forums.xamarin.com/).

<a name="prereq" />

## <a name="pre-requisites"></a>Wymagania wstępne

###  <a name="for-targeting-windows-and-android"></a>Aby uzyskać przeznaczone dla Windows i Android

Zobacz [wymagania systemowe rodziny produktów 2017 r. w usłudze Visual Studio](/visualstudio/productinfo/vs2017-system-requirements-vs) dla szczegółowe wymagania wstępne dotyczące instalowania programu Visual Studio 2017.

Zainstaluj program Visual 2017 na komputerze fizycznym Windows (nie maszyna wirtualna) z systemu Windows 10 z zainstalowanymi aktualizacjami wszystkich.

### <a name="for-targeting-ios"></a>Aby uzyskać przeznaczonych dla systemu iOS

Docelowy z systemem iOS emulatorów i urządzeń z komputera Windows potrzebna będzie również sieciowym Mac lub komputerów Mac mini z systemem macOS 10.12 lub nowszej i Xcode 8.3. Zobacz [Instalator i instalacja programu Visual Studio dla komputerów Mac](/visualstudio/mac/installation) bardziej szczegółowe wymagania.

<a name="windows" />

##  <a name="windows-setup-visual-studio-and-xamarin"></a>Instalator Windows (Visual Studio i Xamarin)

Jeśli nie masz jeszcze zainstalowanego programu Visual Studio 2017, wykonaj następujące czynności:

1.  [Pobierz i uruchom Instalatora programu Visual Studio 2017 w każdej wersji](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) (Community, Professional lub Enterprise). Visual Studio 2017 Community jest bezpłatną. Wersje Professional i Enterprise są dostępne do wypróbowania przez 30 dni, po upływie których licencja jest to konieczne.

2.  Gdy **instalowanie** zostanie wyświetlone okno dialogowe, sprawdź następujące pola:

    - **Urządzenia przenośne i gry > Tworzenie aplikacji mobilnych przy użyciu platformy .NET**. Ta opcja również automatycznie wybiera różne Android narzędzia i zestawy Software Development Kit.

        ![Wybierz opcję programowanie aplikacji mobilnych, gier i opracowywania aplikacji mobilnych](../cross-platform/media/cross-plat-xamarin-setup-2a.png "2 instalacji Xamarin Cross-Plat")

    - (Opcjonalnie) **Windows > programowania na platformę uniwersalną Windows**.

Jeśli masz już program Visual Studio 2017, ale jeszcze nie zainstalowano platformy Xamarin, wykonaj następujące czynności:

1. Uruchom **Instalatora programu Visual Studio** z **Start** menu.

2.  W oknie Instalatora kliknij **więcej** przycisk, a następnie wybierz **Modyfikuj**:

    ![Wybranie opcji Modyfikuj w instalacji programu Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1a.png "1 instalacji Xamarin Cross-Plat")

3.  Gdy **instalowanie** zostanie wyświetlone okno dialogowe, sprawdź **urządzenia przenośne i gry > opracowywanie aplikacji mobilnych przy użyciu platformy .NET** i (opcjonalnie) **Windows > programowania na platformę Windows uniwersalną**. **Programowanie aplikacji mobilnych przy użyciu platformy .NET** opcji należy również zaktualizować żadnej istniejącej instalacji Xamarin.

Po uruchomieniu instalacji można kontynuować instrukcje dotyczące konfigurowania komputerów Mac i przechodzą przez [Dowiedz się więcej o programowaniu rozwiązań mobilnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

5.  Po zakończeniu instalacji uruchom program Visual Studio i zaloguj się przy użyciu konta Microsoft, jeśli zostanie wyświetlony monit. To konto jest tego samego konta, którego używasz z Windows.

6.  W przypadku testowania aplikacji dla systemu Android, użyj [emulatora Android SDK](/xamarin/android/get-started/installation/android-emulator/) Jeśli nie masz urządzenia fizycznego systemu Android.

<a name="mac" />

##  <a name="mac-setup-apple-id-xcode-and-xamarin"></a>Instalator Mac (identyfikator Apple ID, Xcode i Xamarin)

1.  Utwórz bezpłatne identyfikator Apple ID w [ https://appleid.apple.com ](https://appleid.apple.com/) Jeśli nie masz jeszcze takiego. Ten identyfikator Apple ID jest niezbędne do instalowania i rejestrowania się w środowisku Xcode.

2.  Pobierz i zainstaluj środowisko Xcode ze [ https://developer.apple.com/xcode/ ](https://developer.apple.com/xcode/), i Dodaj swój identyfikator firmy Apple, zgodnie z opisem na [Dodaj swoje konto w narzędziu Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).

3.  Pobieranie i instalowanie programu Visual Studio dla komputerów Mac, postępując zgodnie z instrukcjami wyświetlanymi [Instalator i instalacja programu Visual Studio dla komputerów Mac](/visualstudio/mac/installation).

4.  Po zakończeniu instalacji Xamarin na komputerach Mac i Windows, postępuj zgodnie z instrukcjami [nawiązywania połączenia z komputerem Mac](/xamarin/ios/get-started/installation/windows/connecting-to-mac/) , dzięki czemu można pracować z systemami iOS i Mac w programie Visual Studio na komputerze Windows.

Oba komputery muszą być w tej samej sieci lokalnej.
