---
title: Konfigurowanie i instalowanie | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 04/13/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
caps.latest.revision: "16"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 4f525157e9e34838be4379f8df0845b294880f11
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
---
# <a name="setup-and-install"></a>Instalator i instalacja
Tworzenie natywnych iOS, Android i Windows aplikacji ze wspólnego C# / kodu .NET podstawowej za pomocą platformy Xamarin, należy spełnić następujące warunki:  
  
-   Do pracy z systemem Windows i aplikacje dla systemu Android: komputera systemu Windows z programu Visual Studio 2017 lub 2015 za pomocą platformy Xamarin zainstalowane. Można również użyć programu Visual Studio 2013 zgodnie z instrukcjami dla [bezpośredniej instalacji Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com). 
  
-   Do pracy z aplikacjami systemu iOS: Mac z macOS Sierra 10.12 lub powyżej, z Xcode i Xamarin zainstalowane.  
  
 Można skonfigurować komputery z systemem Windows i Mac, w tym samym czasie, a podczas wykonywania tych instalatorów można przejść przez [Dowiedz się więcej o programowanie przenośnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) do odczytywania i obejrzyj materiałów niezbędne tła.  
 
Jeśli masz problemy po wykonaniu tego Instalatora i zainstaluj za pomocą platformy Xamarin, zgłoś zapytanie na [forums.xamarin.com](http://forums.xamarin.com/).
  
> [!NOTE]
>  31 marca 2016 r. wszystkie Xamarin jest dołączony do wszystkich wersji programu Visual Studio bez dodatkowych kosztów i nie wymaga oddzielnej licencji. Program Xamarin Studio Community dla komputerów Mac również jest bezpłatna dla uczniów lub studentów, OSS deweloperów i niewielkich zespołów. Należy pamiętać, że dla istniejącej instalacji programu Visual Studio, które są skonfigurowane przy użyciu wcześniejszych licencji Xamarin, musisz zaktualizować Xamarin do wersji 4.0.3.214 lub nowszej. Aby to zrobić, przejdź do **Narzędzia > Opcje > Xamarin > innych**, kliknij przycisk **Sprawdź** łącze i 4.0.3.214 pobierania aktualizacji. Po ponownym uruchomieniu programu Visual Studio, przejdź do **Narzędzia > Konto Xamarin...**  i powinna zostać wyświetlona zaktualizowany stan.  
  
##  <a name="prereq"></a>Wymagania wstępne  
  
###  <a name="for-targeting-windows-and-android"></a>Przeznaczony do systemu Windows i Android 
  
1.  Zalecane: fizycznych komputerem z systemem Windows (nie maszyn wirtualnych) systemem Windows 8 lub nowszym, aby uzyskać najlepszą wydajność emulatora systemu Android. (Czy możemy wymienić należy komputera fizycznego, a nie maszyna wirtualna?)  
  
2.  Można użyć komputera z systemem Windows 7 lub starszym, w którym to przypadku użyjesz Xamarin Player dla systemu Android jako emulator. 
    
3. Dla obu konfiguracji będzie można uruchamiać aplikacje bezpośrednio na podłączone urządzenia fizycznego.  
  
### <a name="for-targeting-ios"></a>Przeznaczony dla systemu iOS  
  
1.  Mac lub Mac w sieci A mini macOS Sierra uruchomiony system macOS 10.12 lub nowszy (wymagane dla Xcode 8.3).  
  
2.  Korzystając z programu Visual Studio na komputerze z systemem Windows (7 +) jako środowiska deweloperskiego podstawowego, sieciowych Mac jest tylko do kompilowania i debugowania aplikacji systemu iOS, dołączyć do symulatora systemu iOS lub powiązanego urządzeń oraz za pomocą projektanta scenorysu w programie Visual Studio dla Projektowanie interfejsu użytkownika. Starsze modele Mac są całkowicie wystarczający dla tej roli dodatkowej.  
  
##  <a name="windows"></a>Instalator systemu Windows (Visual Studio i Xamarin)  
  
> [!TIP]
>  Te instrukcje dotyczą programu Visual Studio 2017 r. Dla programu Visual Studio 2015 [MSDN](setup-and-install.md). Aby Xamarin za pomocą programu Visual Studio 2013 (wymagana jest aktualizacja 2), postępuj zgodnie z instrukcjami dotyczącymi [bezpośredniej instalacji Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com).  
  
1.  [Pobierz i uruchom Instalatora programu dowolnej wersji programu Visual Studio 2017](https://www.visualstudio.com/downloads/) (Community, Professional lub Enterprise). Visual Studio 2017 Community jest bezpłatna wersja; wersje Professional i Enterprise może służyć wypróbowania przez 30 dni, po których musisz kupić licencję.  
  
    1.  Jeśli masz już Visual Studio 2017 r zainstalowane, uruchom **Instalator programu Visual Studio** z **Start** menu.
  
2.  W ramach Instalatora, kliknij przycisk **dodatkowymi opcjami** przycisk (trzy paski ikona) _obok pozycji_ **uruchamianie** wybierz **Modyfikuj**.:  
  
     ![Wybranie opcji Modyfikuj w instalacji programu Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1a.png "na wiele różnych Xamarin konfiguracji 1")  
  
3.  Sprawdź następujące pola:  
  
    1.  **Mobile i gier > Mobile Development z platformą .NET**. Automatycznie wybierze różnych narzędzi dla systemu Android w obszarze popularne narzędzia i zestawy Software Development Kit. Tej opcji należy również zaktualizować ewentualne istniejące instalacje Xamarin.  
  
         ![Wybierz opcję programowania aplikacji mobilnych, gier i aplikacji mobilnych](../cross-platform/media/cross-plat-xamarin-setup-2a.png "na wiele różnych Xamarin Instalatora 2")  
  
    2. (Opcjonalnie) **Windows > rozwoju platformy uniwersalnej systemu Windows**. Te opcje include dla instalowanie obrazów emulatory, które będą miały dłużej; Możesz zawsze wrócić do Instalatora programu Visual Studio, aby je dodać później. 
  
4.  Kliknij przycisk **Modyfikuj** przycisk i umożliwić uruchamianie procesu. Ponownie, potrwa to trochę czasu, w tym czasie można kontynuować Mac instrukcje instalacji i przejść przez [Dowiedz się więcej o programowanie przenośnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).  
  
5.  Po zakończeniu instalacji uruchom Visual Studio i zaloguj się przy użyciu konta Microsoft w przypadku wyświetlenia monitu (jest to samo konto używane w systemie Windows).  
      
6.  Do testowania aplikacji systemu Android, użyj [emulatora Android SDK](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/android-sdk-emulator/) Jeśli nie masz urządzenia fizycznego. Zobacz uwagi poniżej.  
  
 **Uwaga dotycząca emulatory na komputerach z systemem Windows:** procesorów obsługuje tylko jeden technologii wirtualizacji w czasie, jest najlepszym rozwiązaniem jest tylko jeden używany na komputerze dewelopera. Istnieją trzy główne wirtualizacji komputerów PC, technologie są funkcji Hyper-V (wykorzystywane przez Visual Studio Emulator dla systemów Android i Windows Phone emulator), pole wirtualne (używane przez Genymotion) i HAXM firmy Intel (wykorzystywane przez emulatora Android SDK). Ze względu na różne problemy między funkcją Hyper-V i wirtualnych pole najlepiej używać emulatory tylko jednego typu na dowolnym danym komputerze, dlatego zalecenia powyżej, aby użyć funkcji Hyper-V w systemie Windows 8 lub nowszym komputerów i emulatory Intel HAXM w systemie Windows 7 i wcześniejszych oraz kiedy systemem Windows na komputerach Mac.  
  
##  <a name="mac"></a>Instalator Mac (Apple ID, Xcode i Xamarin)  
  
1.  Utwórz bezpłatne identyfikator firmy Apple w [https://appleid.apple.com](https://appleid.apple.com/) Jeśli nie masz już. Jest to niezbędne do instalowania i rejestrowania się w środowisku Xcode.  
  
2.  Pobierz i zainstaluj program Xcode z [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/), i Dodaj identyfikator Apple ID, zgodnie z opisem na [Dodawanie Twoje konto xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).  
  
3.  Pobierz i zainstaluj program Xamarin, postępując zgodnie z instrukcjami [Instalowanie i konfigurowanie Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (xamarin.com).  
  
4.  Po zakończeniu instalowania Xamarin na komputerach z systemem Windows i Mac, postępuj zgodnie z instrukcjami [połączenie z komputerem Mac](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) (xamarin.com), dzięki czemu można pracować z systemem iOS i Mac w programie Visual Studio na komputerze z systemem Windows.  
  
     Należy pamiętać, że oba komputery muszą być w tej samej sieci lokalnej.