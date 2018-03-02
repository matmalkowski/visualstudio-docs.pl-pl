---
title: "Instalator, instalacja i weryfikacja dla użytkowników komputerów Mac | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 04/13/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22725520-59ba-4f6f-80e4-097b1287a34b
ms.technology: vs-ide-mobile
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- xamarin
ms.openlocfilehash: 366dd699555cd3eed637687668fc194ba00d5be4
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="setup-install-and-verifications-for-mac-users"></a>Instalator, instalacja i weryfikacja dla użytkowników komputerów Mac
W tym temacie jest przeznaczona dla deweloperów pracujących przede wszystkim na komputerze Mac, które opcjonalnie Visual Studio umożliwia maszynie wirtualnej systemu Windows na komputerach Mac. Jeśli jesteś deweloperem pracy przede wszystkim na komputerze z systemem Windows i należy skonfigurować dodatkowej Mac przeznaczony dla systemu iOS, znajduje się w [Instalatora i zainstaluj](../cross-platform/setup-and-install.md) tematu.

 Aby pracować z platformą Xamarin na komputerze Mac, będą potrzebne następujące czynności:

-   Mac z macOS Sierra 10.12 lub powyżej, z Xcode i Xamarin zainstalowane.

-   Jeden z następujących konfiguracji:

    -   **Do uruchamiania Xamarin Studio bezpośrednio na Mac:** Xamarin Studio jest środowisko programistyczne na platformie Xamarin obsługuje tworzenie aplikacji systemu Android, iOS i Windows za pomocą języka C#.  Aby uzyskać szybki przegląd Xamarin Studio, zobacz [Przegląd Xamarin Studio](https://xamarin.com/studio) (xamarin.com).

    -   **Jeśli masz już równoleżników lub VMWare skonfigurowany na komputerze Mac:** systemem Windows za pomocą programu Visual Studio 2017 i Xamarin wewnątrz równoleżników lub VMWare.  W tej konfiguracji Xamarin to rozszerzenie, które jest zainstalowany program Visual Studio, która zapewnia możliwość używania programu Visual Studio jako swoje Środowisko deweloperskie do tworzenia aplikacji systemu Android, iOS i Windows za pomocą języka C#.  Należy zwrócić uwagę, czy można uzyskać bezpłatną subskrypcję równoleżników 3-miesięczna jako część programu Visual Studio Developer Essentials. Zobacz [dostępu równoleżników i Microsoft Visual Studio Dev Essentials będzie zawierać równoleżników Desktop Pro](http://blog.parallels.com/blog/2015/11/18/visual-studio-dev-essentials/) (blog równoleżników).

 Ten temat zawiera instrukcje dotyczące tych wymagań.  Podczas procesu instalacji, należy przejrzeć temat [Dowiedz się więcej o programowanie przenośnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) do odczytywania i obejrzyj materiałów niezbędne tła.

##  <a name="mac"></a> Instalator Mac (Apple ID, Xcode i Xamarin)

1.  Utwórz bezpłatne identyfikator firmy Apple w [mój identyfikator Apple ID](https://appleid.apple.com/) Jeśli nie masz już. Jest to niezbędne do instalowania i rejestrowania się w środowisku Xcode.

2.  Pobierz i zainstaluj program Xcode z [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/).

3.  Pobierz i zainstaluj program Xamarin, postępując zgodnie z instrukcjami [Instalowanie i konfigurowanie Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (xamarin.com).

4.  Po zakończeniu instalowania Xamarin na komputerach z systemem Windows i Mac, postępuj zgodnie z instrukcjami [połączenie z komputerem Mac przy użyciu XMA](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (xamarin.com), dzięki czemu można pracować z systemem iOS i Mac w programie Visual Studio w systemie Windows komputer.

##  <a name="windows"></a> Instalator systemu Windows wewnątrz równoleżników (Visual Studio i Xamarin)

1.  Korzystanie z pulpitu systemu Windows, skonfigurowanego wewnątrz równoleżników/VMWare [Pobierz i uruchom Instalatora programu dowolnej wersji programu Visual Studio 2017](https://www.visualstudio.com/downloads/) (Community, Professional lub Enterprise). Visual Studio 2017 Community jest bezpłatna wersja; wersje Professional i Enterprise może służyć próbny o 30 dni.

2.  W ramach Instalatora, kliknij przycisk **dodatkowymi opcjami** przycisk (trzy paski ikona) _obok pozycji_ **uruchamianie** wybierz **Modyfikuj**.:  
  
     ![Wybranie opcji Modyfikuj w instalacji programu Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1a.png "na wiele różnych Xamarin konfiguracji 1")  
  
3.  Sprawdź następujące pola:

    1.  **Mobile i gier > Mobile Development z platformą .NET**. Automatycznie wybierze różnych narzędzi dla systemu Android w obszarze popularne narzędzia i zestawy Software Development Kit. Tej opcji należy również zaktualizować ewentualne istniejące instalacje Xamarin.  
  
         ![Wybierz opcję programowania aplikacji mobilnych, gier i aplikacji mobilnych](../cross-platform/media/cross-plat-xamarin-setup-2a.png "na wiele różnych Xamarin Instalatora 2")  
  
    2. (Opcjonalnie) **Windows > rozwoju platformy uniwersalnej systemu Windows**. Obejmuje to opcje instalowanie obrazów emulatory, które będą miały dłużej; Możesz zawsze wrócić do Instalatora programu Visual Studio, aby je dodać później.  

4.  Kliknij przycisk **Modyfikuj** przycisk i umożliwić uruchamianie procesu. Ponownie, potrwa to trochę czasu, w tym czasie można kontynuować Mac instrukcje instalacji i przejść przez [Dowiedz się więcej o programowanie przenośnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

5.  Po zakończeniu instalacji uruchom Visual Studio i zaloguj się przy użyciu konta Microsoft w przypadku wyświetlenia monitu (jest to samo konto używane w systemie Windows).

6.  Po zakończeniu instalowania Xamarin na komputerach z systemem Windows i Mac, postępuj zgodnie z instrukcjami [połączenie z komputerem Mac przy użyciu XMA](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (xamarin.com), dzięki czemu można pracować z systemem iOS w programie Visual Studio.

##  <a name="verify"></a> Sprawdź środowiska
 Po ukończeniu ma instalatorów spędzają na kilka minut, sprawdź, czy wszystko jest gotowe do środowisko rozwoju Xamarin.

### <a name="xamarin-studio"></a>Xamarin Studio
 Najpierw upewnij się, że po przejściu do podanego łącza, czy masz **Xamarin Studio** wybrane w prawym górnym rogu, aby zobaczyć poprawna wersja dokumentacji Xamarin:

 ![Wybieranie platformy Xamarin Studio można znaleźć w dokumentacji poprawne na Xamarin.com](../cross-platform/media/crossplat-xamarin-mac-1.png "CrossPlat Xamarin Mac 1")

**Android**

1.  Sprawdź poprawność Tworzenie projektu dla systemu Android zgodnie z instrukcjami [utworzyć projekt Android](http://developer.xamarin.com/recipes/android/general/projects/create_an_android_project/) (xamarin.com).

2.  Sprawdź poprawność debugowania w emulatorze systemu Android za pośrednictwem [Android Player > integracji z dokumentacją Xamarin Studio](https://developer.xamarin.com/guides/android/getting_started/installation/android-player/#Integration_with_Xamarin_Studio) (xamarin.com).

**iOS**

1.  Sprawdź poprawność tworzenia projektu iOS zgodnie z instrukcjami [tworzenie systemu iOS](http://developer.xamarin.com/recipes/ios/general/projects/create_an_ios_project/) (xamarin.com).

2.  Sprawdź poprawność debugowania w symulatorze systemu iOS za pośrednictwem [debugowania w dokumentacji symulatora](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) (xamarin.com).

### <a name="visual-studio"></a>Visual Studio
 Najpierw upewnij się, że po przejściu do podanego łącza, czy masz **programu Visual Studio** wybrane w prawym górnym rogu, aby zobaczyć poprawna wersja dokumentacji Xamarin:

 ![Wybieranie programu Visual Studio można znaleźć w dokumentacji poprawne na Xamarin.com](../cross-platform/media/crossplat-xamarin-mac-2.png "CrossPlat Xamarin Mac 2")

**Android**

1.  Sprawdź poprawność Tworzenie projektu dla systemu Android zgodnie z instrukcjami [utworzyć projekt Android](http://developer.xamarin.com/recipes/android/general/projects/create_an_android_project/) (xamarin.com).

2.  Sprawdź poprawność projektanta dla systemu Android: w projekcie systemu Android w Eksploratorze rozwiązań Otwórz **zasobów > Układ > Main.axml** pliku.

    -   Jeśli zostanie wyświetlony błąd informujący o tym "Zainstalowany zestaw SDK systemu Android jest zbyt stary", kliknij przycisk **Otwórz zestaw SDK systemu Android** tego komunikatu, a następnie wybierz dostępne najnowsza wersja zestawu SDK. Należy pamiętać, że użytkownik musi być uruchomiony program Visual Studio jako administrator, aby zaktualizować zestaw SDK.

3.  Zweryfikuj, czy można nawiązać z programu Visual Studio emulator zainstalowanego opartym na systemie  Wynik jest zobaczą Xamarin Player na liście emulatory, które można wybrać z poziomu programu Visual Studio do debugowania.  Aby to zrobić, postępuj zgodnie z instrukcjami [łączenie programu Visual Studio dla platformy Xamarin Android odtwarzacza](http://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/android-player-with-visual-studio-in-vm/) (xamarin.com).

**iOS**

1.  Upewnij się, że komputera Mac jest dostępny w sieci i sparowanego z programem Visual Studio, zgodnie z opisem w [połączenie z komputerem Mac](https://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac) (xamarin.com).

2.  Sprawdź poprawność tworzenia projektu iOS zgodnie z instrukcjami [tworzenie systemu iOS](http://developer.xamarin.com/recipes/ios/general/projects/create_an_ios_project/) (xamarin.com).

3.  Sprawdź poprawność projektanta scenorysu: w projekcie systemu iOS w Eksploratorze rozwiązań Otwórz **MainStoryboard.storyboard** pliku. W tym miejscu Visual Studio jest hostem tego projektanta, który jest uruchamiany zdalnie na komputerów Mac.

4.  Sprawdź poprawność kompilowanie i debugowanie:

    1.  Kliknij prawym przyciskiem myszy projekt iOS w Eksploratorze rozwiązań i wybierz **Ustaw jako projekt startowy**.

    2.  Wybierz **iPhoneSimulator** z rozwijanej kompilacji programu Visual Studio docelową, jak pokazano poniżej. Jeśli nie są wyświetlane nie symulatorów, uruchom Xcode na komputerze Mac, wybierz **Xcode -> Preferencje**i kliknij przycisk **Pobierz**. W obszarze **składniki** powinna zostać wyświetlona wersji symulator, które są dostępne do pobrania. Dodatkowe instrukcje dotyczące debugowania można znaleźć w Xamarin [debugowanie](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) strony (xamarin.com).

         ![Wybieranie iPhoneSimulator kompilacji docelowej](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin Sprawdź 5")

    3.  Wybierz obiekt docelowy iPhone z rozwijanej debugowania programu Visual Studio, jak pokazano poniżej, a następnie uruchomienia debugera, naciskając klawisz F5. Spowoduje to uruchomienie symulatora dla komputerów Mac, w którym interakcji z aplikacją, a debugowanie odbywa się w programie Visual Studio.

         ![Wybieranie obiektu docelowego debugowania iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin Sprawdź 6")