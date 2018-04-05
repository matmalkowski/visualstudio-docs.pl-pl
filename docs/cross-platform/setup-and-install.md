---
title: Zainstaluj program Xamarin dla Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 4dcd83ffb1076211f8d23aa4491f853d2b7d316f
ms.sourcegitcommit: a0a49cceb0fdc1465ddf76d131c6575018b628b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2018
---
# <a name="setup-and-install"></a>Instalator i instalacja

Tworzenie natywnych iOS, Android i Windows aplikacji ze wspólnego C# / kodu .NET podstawowej za pomocą platformy Xamarin, potrzebny następujący sprzęt i oprogramowanie:

-   Do pracy z systemem Windows i aplikacje dla systemu Android: Programowanie komputerem z systemem Windows (nie maszynę wirtualną) z programu Visual Studio 2017 r (w tym funkcje tworzenia Xamarin) zainstalowany.  

-   Do pracy z aplikacjami systemu iOS: Mac z macOS Sierra 10.12 lub powyżej, z Xcode zainstalowany i programu Visual Studio for Mac zainstalowane.

Brak licencji oddzielne muszą korzystać z platformy Xamarin.
 
Można skonfigurować komputery z systemem Windows i Mac, w tym samym czasie, a podczas wykonywania tych instalatorów można przejść przez [Dowiedz się więcej o programowanie przenośnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) do odczytywania i obejrzyj materiałów niezbędne tła.

Jeśli masz problemy po wykonaniu tego Instalatora i zainstaluj za pomocą platformy Xamarin, zgłoś zapytanie na [forums.xamarin.com](http://forums.xamarin.com/).

<a name="prereq" /> 

## <a name="pre-requisites"></a>Wymagania wstępne

###  <a name="for-targeting-windows-and-android"></a>Przeznaczony do systemu Windows i Android

Zobacz [Visual Studio 2017 produktu z rodziny System wymagania](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs) dla szczegółowe wymagania wstępne dotyczące instalowania programu Visual Studio 2017 r.

Visual 2017 należy zainstalować na komputerze fizycznym z systemem Windows (nie maszyny wirtualnej) systemem Windows 10 z wszystkie zainstalowane aktualizacje. 

### <a name="for-targeting-ios"></a>Przeznaczony dla systemu iOS

Emulatory dla systemu iOS docelowych i urządzeń z komputera z systemem Windows musisz również sieciowych Mac lub Mac mini system macOS, 10.12 lub nowszy i Xcode 8.3. Zobacz [Instalatora i zainstaluj pakiet Visual Studio for Mac](/visualstudio/mac/installation.md) bardziej szczegółowe wymagania.

<a name="windows" /> 

##  <a name="windows-setup-visual-studio-and-xamarin"></a>Instalator systemu Windows (Visual Studio i Xamarin)

Jeśli jeszcze nie został zainstalowany program Visual Studio 2017 r, wykonaj następujące czynności:

1.  [Pobierz i uruchom Instalatora programu dowolnej wersji programu Visual Studio 2017](https://www.visualstudio.com/downloads/) (Community, Professional lub Enterprise). Visual Studio 2017 Community jest bezpłatna wersja. Wersje Professional i Enterprise są dostępne na podstawie wersji próbnej przez 30 dni, po których konieczne jest licencja.

2.  Gdy **instalowanie** zostanie wyświetlone okno dialogowe, sprawdź następujące pola:    

    - **Mobile i gier > Mobile Development z platformą .NET**. Ta opcja będzie również automatycznie wybierać różnych narzędzi dla systemu Android i Software Development Kit. 

        ![Wybierz opcję programowania aplikacji mobilnych, gier i aplikacji mobilnych](../cross-platform/media/cross-plat-xamarin-setup-2a.png "na wiele różnych Xamarin Instalatora 2")

    - (Opcjonalnie) **Windows > rozwoju platformy uniwersalnej systemu Windows**. 

Jeśli już masz Visual Studio 2017 r zainstalowany, ale nie został jeszcze zainstalowany platformy Xamarin, wykonaj następujące czynności:

1. Uruchom **Instalator programu Visual Studio** z **Start** menu.

2.  W ramach Instalatora, kliknij przycisk **więcej** przycisk, a następnie wybierz pozycję **Modyfikuj**:

    ![Wybranie opcji Modyfikuj w instalacji programu Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1a.png "na wiele różnych Xamarin konfiguracji 1")

3.  Gdy **instalowanie** zostanie wyświetlone okno dialogowe, sprawdź **Mobile i gier > programowania aplikacji mobilnych z platformą .NET** i (opcjonalnie) **Windows > rozwoju platformy uniwersalnej systemu Windows**. **Programowania aplikacji mobilnych z platformą .NET** opcji należy również zaktualizować ewentualne istniejące instalacje Xamarin.

Podczas instalacji, możesz kontynuować Mac instrukcje dotyczące instalacji i przejść przez [Dowiedz się więcej o programowanie przenośnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

5.  Po zakończeniu instalacji uruchom program Visual Studio i zaloguj się przy użyciu konta Microsoft, jeśli zostanie wyświetlony monit. To konto jest to samo konto, które są używane w systemie Windows.

6.  Do testowania aplikacji systemu Android, użyj [emulatora Android SDK](/xamarin/android/get-started/installation/android-emulator/) Jeśli nie masz urządzenia fizycznego systemu Android. 

<a name="mac" />

##  <a name="mac-setup-apple-id-xcode-and-xamarin"></a>Instalator Mac (Apple ID, Xcode i Xamarin)

1.  Utwórz bezpłatne identyfikator firmy Apple w [ https://appleid.apple.com ](https://appleid.apple.com/) Jeśli nie masz już. Ten identyfikator Apple ID jest niezbędne do instalowania i rejestrowania się w środowisku Xcode.

2.  Pobierz i zainstaluj program Xcode z [ https://developer.apple.com/xcode/ ](https://developer.apple.com/xcode/), i Dodaj identyfikator Apple ID, zgodnie z opisem na [Dodawanie Twoje konto xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).

3.  Pobierz i zainstaluj program Visual Studio for Mac zgodnie z instrukcjami [Instalatora i zainstaluj pakiet Visual Studio for Mac](/visualstudio/mac/installation.md).

4.  Po zakończeniu instalowania Xamarin na komputerach z systemem Windows i Mac, postępuj zgodnie z instrukcjami [połączenie z komputerem Mac](/xamarin/ios/get-started/installation/windows/connecting-to-mac/) , dzięki czemu można pracować z systemem iOS i Mac w programie Visual Studio na komputerze z systemem Windows.

Oba komputery muszą być w tej samej sieci lokalnej.