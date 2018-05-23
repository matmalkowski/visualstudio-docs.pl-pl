---
title: Zainstaluj program Visual Studio dla komputerów Mac
description: Instrukcje dotyczące instalowania programu Visual Studio for Mac i dodatkowe składniki wymagane dla aplikacji dla wielu platform.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.openlocfilehash: 0523c418c5361bfdda6f56bc7845989ed0fdaa8c
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="setup-and-install-visual-studio-for-mac"></a>Konfigurowanie i instalowanie oprogramowania Visual Studio dla komputerów Mac

## <a name="setup"></a>Konfiguracja

Do rozpoczęcia tworzenia natywnych, wieloplatformowych aplikacji po pobraniu programu Visual Studio dla komputerów Mac jest kilka rzeczy, które należy zainstalować i skonfigurować w ramach przygotowania.

Do pracy z systemem iOS w programie Visual Studio potrzebne są następujące elementy:

* Mac z macOS Sierra 10.12 lub nowszy
* Xcode 8.3 lub nowszej. Najnowsza stabilna wersja zazwyczaj jest zalecane.
* Identyfikator firmy Apple. Jeśli nie masz już identyfikator Apple ID można utworzyć nową na https://appleid.apple.com. Należy mieć identyfikator firmy Apple do instalowania i rejestrowania się w środowisku Xcode.

## <a name="install"></a>Zainstaluj

1. Pobierz program Visual Studio for Mac z [https://www.visualstudio.com/](https://www.visualstudio.com/)

2. Pobrany pakiet Instalatora kliknij **VisualStudioInstaller.dmg** plik, aby zainstalować Instalatora i uruchomić go przez dwukrotne kliknięcie logo, jak pokazano na poniższej ilustracji:

  ![Okno dialogowe Instalator](media/installer-image1.png)

3. Może zostać wyświetlony monit z okna dialogowego alertu podobnie do poniższej ilustracji. W takim przypadku kliknij **Otwórz**:

  ![okna dialogowego alertu](media/installer-image2.png)

4. Instalator sprawdza systemu, aby sprawdzić składniki, które muszą być zainstalowane lub zaktualizowane:

  ![Oceny systemu](media/installer-image3.png)

5. Następnie zostaną wyświetlone z prośbą o potwierdzenie postanowienia licencyjne i poufności informacji okna dialogowego alertu. Naciśnij klawisz **Kontynuuj** przycisk, aby potwierdzić warunki:

  ![Okno dialogowe licencji](media/installer-image4.png)

6. Instalator wyświetla listę wymaganych składników brakujące i które mają zostać pobrana i zainstalowana. Wybierz produkty, które chcesz pobrać tutaj:

  ![Wybierz elementy](media/installer-image5.png)

  Jeśli nie chcesz, aby zainstalować wszystkie platformy, pomocne w podejmowaniu decyzji, które platformy, aby zainstalować za pomocą przewodnika poniżej:

  * **Aplikacje za pomocą platformy Xamarin**:
      - Platformy Xamarin.Forms — wybierz **Android** i **iOS** platform.
      - Wybierz tylko — iOS **iOS** platformy (należy pamiętać, że będą musieli zainstalować [ **Xcode**](https://developer.apple.com/xcode/)).
      - Wybierz tylko — android **Android** platformy (Zwróć uwagę, należy również wybrać odpowiednie zależności).
      - Wybierz tylko — Mac **macOS** platformy (należy pamiętać, że będą musieli zainstalować [ **Xcode**](https://developer.apple.com/xcode/)).
      - Wybierz pełni wieloplatformowych aplikacji platformy Xamarin — **Android**, **iOS**, i **macOS** platform.
  * **Aplikacje .NET core** — wybierz **.NET Core** platformy.
  * **Aplikacje sieci Web platformy ASP.NET Core** — wybierz **.NET Core** platformy.
  * **Aplikacji gry dla wielu platform Unity** — nie dodatkowych platform muszą być zainstalowane poza Visual Studio dla komputerów Mac. Zapoznaj się [przewodnik konfiguracji środowiska Unity](setup-vsmac-tools-unity.md) Aby uzyskać więcej informacji na temat instalowania rozszerzenia Unity.

  Na tym ekranie instalacji Wyświetla wersji i rozmiaru poszczególnych składników. Kliknij przycisk każdego składnika, aby wyświetlić listę zależności dla tego składnika (dla systemu Android), zobacz dodatkowe pakiety, które pobiera (dla platformy .NET Core) lub wyświetlić dodatkowe aplikacje wymagane (dla systemów iOS i macOS):

  ![Dodatkowe zależności dla systemu android](media/installer-image6.png)

7. Po przejściu wszystkiego wybór wybierz **instalacji i aktualizacji** przycisk, aby rozpocząć proces instalacji.

8. Instalator uruchamia pobieranie i zainstaluj proces zaznaczonych elementów:

  ![Rozpoczynanie instalacji](media/installer-image7.png)

  ![Pobieranie Xamarin.Mac](media/installer-image8.png)

  ![Kończenie instalacji](media/installer-image9.png)

9. Użytkownik może zostać poproszony o podniesienie uprawnień niezbędnych do pojedynczych składników, które są niezbędne do ukończenia instalacji. Wprowadź poświadczenia administratora tutaj, aby kontynuować proces instalacji:

  ![Wprowadź uprawnień, aby kontynuować przy użyciu Instalatora](media/installer-image10.png)

10. Po zakończeniu instalacji możesz rozpocząć tworzenie aplikacji w programie Visual Studio, naciskając klawisz **Start**:

  ![Otwórz program Visual Studio](media/installer-image11.png)

> [!NOTE]
Jeśli została wybrana opcja Instaluj platformy lub narzędzia podczas oryginalnej instalacji (przez unselecting go w kroku #6), należy uruchomić [Instalator](https://www.visualstudio.com/vs/) ponownie, jeśli chcesz później dodać składniki.


## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Zainstaluj program Visual Studio dla komputerów Mac za serwerem zapory lub serwera proxy

Aby zainstalować program Visual Studio dla komputerów Mac za zaporą, niektórych punktów końcowych musi być dostępne w celu pobrania aktualizacji oprogramowania i wymaganych narzędzi.

Skonfiguruj sieci, aby umożliwić dostęp do następujących lokalizacji:

* [Visual Studio punkty końcowe](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Następne kroki

Instalacja programu Visual Studio for Mac pozwala rozpocząć pisanie kodu dla aplikacji. Poniższe przewodniki są dostarczane do przeprowadzenia w następnych krokach zapisywania i wdrażania projektów.

### <a name="ios"></a>iOS

1. [Witaj, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Inicjowania obsługi administracyjnej urządzeniu](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning)(do uruchamiania aplikacji na urządzeniu).


### <a name="android"></a>Android

1. [Za pomocą platformy Xamarin Android SDK Manager](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Emulator zestawu SDK systemu Android](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Konfigurowanie urządzenia na potrzeby programowania](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>Aplikacje .NET core, aplikacje sieci web platformy ASP.NET Core, tworzenie gier środowiska Unity

Inne obciążenia można znaleźć w temacie [obciążeń](workloads.md) strony.
