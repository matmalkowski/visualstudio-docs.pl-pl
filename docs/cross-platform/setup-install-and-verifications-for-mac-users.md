---
title: Instalator, instalacja i weryfikacja dla użytkowników komputerów Mac | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/13/2017
ms.topic: conceptual
ms.assetid: 22725520-59ba-4f6f-80e4-097b1287a34b
ms.prod: visual-studio-dev15
ms.technology: vs-ide-mobile
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: fb9c926d1c51278263b84ab617a0d00b088a77e1
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495508"
---
# <a name="setup-install-and-verifications-for-mac-users"></a>Instalator, instalacja i weryfikacja dla użytkowników komputerów Mac

W tym temacie jest przeznaczona dla deweloperów pracy przede wszystkim na komputerze Mac, którzy opcjonalnie będą korzystać z programu Visual Studio na maszynie wirtualnej Windows na komputerze Mac. Jeśli jesteś deweloperem pracy przede wszystkim na komputerze Windows i konieczne skonfigurowanie dodatkowych komputerów Mac dla przeznaczonych dla systemu iOS, zobacz główny [Instalator i instalacja](../cross-platform/setup-and-install.md) tematu.

Aby pracować za pomocą platformy Xamarin na komputerze Mac, będą potrzebne następujące czynności:

-   Komputer Mac z systemem macOS Sierra 10.12 lub powyżej, za pomocą środowiska Xcode i Xamarin zainstalowane.

-   Jeden z następujących konfiguracji:

    -   **Do uruchamiania programu Xamarin Studio bezpośrednio na komputerze Mac:** Xamarin Studio to środowisko programistyczne dla platformy Xamarin, które obsługuje tworzenie aplikacji systemu Android, iOS i Windows przy użyciu języka C#.  Aby uzyskać szybki przegląd programu Xamarin Studio, zobacz [Omówienie programu Xamarin Studio](https://xamarin.com/studio) (strony xamarin.com).

    -   **Jeśli masz już Parallels lub VMWare skonfigurowane na komputerze Mac:** uruchamianie Windows za pomocą programu Visual Studio 2017 i platformy Xamarin wewnątrz Parallels lub VMWare.  W przypadku tej konfiguracji platformy Xamarin to rozszerzenie, które jest instalowane z Visual Studio, który zapewnia możliwość używania programu Visual Studio jako środowiska programowania do tworzenia aplikacji systemu Android, iOS i Windows przy użyciu języka C#.  Należy zwrócić uwagę na to, czy można uzyskać bezpłatną subskrypcję równoleżników 3-miesięczna jako część programu Visual Studio Developer Essentials. Zobacz [programu Microsoft Visual Studio Dev Essentials będzie zawierać rozwiązanie Parallels Desktop Pro i dostęp do oprogramowania Parallels](http://blog.parallels.com/blog/2015/11/18/visual-studio-dev-essentials/) (blog oprogramowania Parallels).

Ten temat zawiera instrukcje dotyczące tych wymagań.  Proces instalacji jest uruchomiona, można przejrzeć temat [Dowiedz się więcej o programowaniu rozwiązań mobilnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) do odczytywania i obejrzyj materiał niezbędne tła.

##  <a name="mac"></a> Instalator Mac (identyfikator Apple ID, Xcode i Xamarin)

1.  Utwórz bezpłatne identyfikator Apple ID w [mój identyfikator Apple ID](https://appleid.apple.com/) Jeśli nie masz jeszcze takiego. Jest to niezbędne do instalowania i rejestrowania się w środowisku Xcode.

2.  Pobierz i zainstaluj środowisko Xcode ze [ https://developer.apple.com/xcode/ ](https://developer.apple.com/xcode/).

3.  Pobierz i zainstaluj platformę Xamarin, postępując zgodnie z instrukcjami wyświetlanymi [zainstalować i skonfigurować rozszerzenia Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (strony xamarin.com).

4.  Po zakończeniu instalacji Xamarin na komputerach Mac i Windows, postępuj zgodnie z instrukcjami [nawiązywanie połączenia z komputerem Mac przy użyciu XMA](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (strony xamarin.com), dzięki czemu można pracować z systemami iOS i Mac w programie Visual Studio na komputerze Windows.

##  <a name="windows"></a> Instalator Windows wewnątrz równoleżników (Visual Studio i Xamarin)

1.  Przy użyciu programu Windows desktop, skonfigurowanego wewnątrz Parallels/VMWare, [Pobierz i uruchom Instalatora programu Visual Studio 2017 w każdej wersji](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) (Community, Professional lub Enterprise). Visual Studio 2017 Community jest bezpłatną; wersje Professional i Enterprise może służyć do wypróbowania przez 30 dni.

2.  W ramach Instalatora, kliknij przycisk **dodatkowe opcje** przycisku (ikona trzy słupki) _obok_ **Uruchom** wybierz **Modyfikuj**.:

     ![Wybranie opcji Modyfikuj w instalacji programu Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1a.png "1 instalacji Xamarin Cross-Plat")

3.  Sprawdź następujące pola:

    1.  **Urządzenia przenośne i gry > Tworzenie aplikacji mobilnych przy użyciu platformy .NET**. To będzie również automatycznie wybierać różne narzędzia dla systemu Android, w obszarze wspólne narzędzia i zestawy Software Development Kit. Tej opcji należy również zaktualizować wszelkich istniejących instalacji Xamarin.

         ![Wybierz opcję programowanie aplikacji mobilnych, gier i opracowywania aplikacji mobilnych](../cross-platform/media/cross-plat-xamarin-setup-2a.png "2 instalacji Xamarin Cross-Plat")

    2. (Opcjonalnie) **Windows > programowania na platformę uniwersalną Windows**. Obejmuje to opcje instalacji obrazów emulatorów, które będzie trwać dłużej, aby pobrać; zawsze możesz wrócić do Instalatora programu Visual Studio, aby je dodać później.

4.  Kliknij przycisk **Modyfikuj** przycisk i pozwól procesu, uruchom. Ponownie zajmie trochę czasu, w tym czasie możesz kontynuować instrukcje dotyczące konfigurowania komputerów Mac i przechodzą przez [Dowiedz się więcej o programowaniu rozwiązań mobilnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

5.  Po zakończeniu instalacji uruchom program Visual Studio i zaloguj się przy użyciu swojego konta Microsoft, jeśli zostanie wyświetlony monit (jest to to samo konto, możesz za pomocą Windows).

6.  Po zakończeniu instalacji Xamarin na komputerach Mac i Windows, postępuj zgodnie z instrukcjami [nawiązywania połączenia z komputerem Mac przy użyciu XMA](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (strony xamarin.com), dzięki czemu można pracować z systemem iOS w programie Visual Studio.

##  <a name="verify"></a> Sprawdź środowisko

Po zakończeniu instalatory Poświęć kilka minut, sprawdź, czy wszystko jest gotowe do środowisko programowania Xamarin.

### <a name="xamarin-studio"></a>Xamarin Studio

Najpierw upewnij się, że po przejściu do podanych łączy, że masz **Xamarin Studio** zaznaczona w prawym górnym rogu, aby wyświetlić poprawną wersję dokumentacji platformy Xamarin:

![Wybierz program Xamarin Studio znajdują się w dokumentacji poprawne na strony Xamarin.com](../cross-platform/media/crossplat-xamarin-mac-1.png "CrossPlat Xamarin Mac 1")

**Android**

1.  Weryfikowanie, tworząc projekt systemu Android, postępując zgodnie z instrukcjami [utworzyć projekt systemu Android](http://developer.xamarin.com/recipes/android/general/projects/create_an_android_project/) (strony xamarin.com).

2.  Sprawdzanie poprawności, debugowanie w emulatorze systemu Android za pośrednictwem [odtwarzacza systemu Android > integracji z dokumentacją programu Xamarin Studio](https://developer.xamarin.com/guides/android/getting_started/installation/android-player/#Integration_with_Xamarin_Studio) (strony xamarin.com).

**iOS**

1.  Sprawdź poprawność Tworzenie projektu dla systemu iOS zgodnie z instrukcjami [tworzenie systemu iOS](http://developer.xamarin.com/recipes/ios/general/projects/create_an_ios_project/) (strony xamarin.com).

2.  Sprawdzanie poprawności, debugowanie w symulatorze systemu iOS za pośrednictwem [debugowania w dokumentacji symulator](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) (strony xamarin.com).

### <a name="visual-studio"></a>Visual Studio

Najpierw upewnij się, że po przejściu do podanych łączy, że masz **programu Visual Studio** zaznaczona w prawym górnym rogu, aby wyświetlić poprawną wersję dokumentacji platformy Xamarin:

![Wybranie programu Visual Studio można znaleźć w dokumentacji poprawne na strony Xamarin.com](../cross-platform/media/crossplat-xamarin-mac-2.png "CrossPlat Xamarin Mac 2")

**Android**

1.  Weryfikowanie, tworząc projekt systemu Android, postępując zgodnie z instrukcjami [utworzyć projekt systemu Android](http://developer.xamarin.com/recipes/android/general/projects/create_an_android_project/) (strony xamarin.com).

2.  Sprawdź poprawność narzędzia Android designer: w projekcie dla systemu Android w Eksploratorze rozwiązań Otwórz **zasobów > Układ > Main.axml** pliku.

    -   Jeśli zostanie wyświetlony błąd informujący o "Zainstalowanego zestawu SDK systemu Android jest zbyt stara", kliknij przycisk **Otwórz zestawu Android SDK** tego komunikatu, a następnie wybierz najnowszą wersję zestawu SDK dostępne. Należy pamiętać, że użytkownik musi być uruchomiony program Visual Studio jako administrator, aby zaktualizować zestaw SDK.

3.  Zweryfikuj, że można połączyć z programu Visual Studio w emulatorze, który jest zainstalowany na komputerze Mac.  Z tego powodu jest zobaczą programu Xamarin Player na liście emulatorów, które można wybrać z poziomu programu Visual Studio do debugowania.  Aby to zrobić, postępuj zgodnie z instrukcjami [łączenia z Visual Studio, aby program Xamarin Android Player](http://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/android-player-with-visual-studio-in-vm/) (strony xamarin.com).

**iOS**

1.  Upewnij się, że komputer Mac jest dostępny w sieci oraz sparowany z programem Visual Studio, zgodnie z opisem w [nawiązywanie połączenia z komputerem Mac](https://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac) (strony xamarin.com).

2.  Sprawdź poprawność Tworzenie projektu dla systemu iOS zgodnie z instrukcjami [tworzenie systemu iOS](http://developer.xamarin.com/recipes/ios/general/projects/create_an_ios_project/) (strony xamarin.com).

3.  Sprawdzanie poprawności projektanta scenorysu: w projekcie dla systemu iOS w Eksploratorze rozwiązań Otwórz **MainStoryboard.storyboard** pliku. W tym miejscu Visual Studio jest hostem tego projektanta, który jest zdalnie uruchomiony na komputerze Mac.

4.  Sprawdzanie poprawności, kompilowania i debugowania:

    1.  Kliknij prawym przyciskiem myszy projekt iOS, w Eksploratorze rozwiązań i wybierz **Ustaw jako projekt startowy**.

    2.  Wybierz **iPhoneSimulator** element docelowy z rozwijanej kompilacji programu Visual Studio, jak pokazano poniżej. Jeśli nie są wyświetlane nie symulatorów, uruchom program Xcode na komputerze Mac, wybierz **Xcode -> Preferencje**i kliknij przycisk **Pobierz**. W obszarze **składniki** powinien zostać wyświetlony wersji symulator, które są dostępne do pobrania. Dodatkowe instrukcje dotyczące debugowania można znaleźć na środowisku Xamarin [debugowanie](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) strony (strony xamarin.com).

         ![Wybieranie iPhoneSimulator tworzenia pod kątem](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin Sprawdź 5")

    3.  Wybierz obiekt docelowy dla telefonu iPhone z rozwijanej debugowania programu Visual Studio, jak pokazano poniżej, a następnie uruchom debuger, naciskając klawisz F5. Spowoduje to uruchomienie symulator na komputerze Mac, w którym interakcji z aplikacją, podczas gdy profilowanie odbywa się w programie Visual Studio.

         ![Wybieranie obiektu docelowego debugowania dla telefonu iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin Sprawdź 6")