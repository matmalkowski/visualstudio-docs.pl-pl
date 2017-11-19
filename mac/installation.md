---
title: Zainstaluj program Visual Studio for Mac | Dokumentacja firmy Microsoft
description: "Instrukcje dotyczące instalowania programu Visual Studio for Mac i dodatkowe składniki wymagane dla aplikacji dla wielu platform."
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.openlocfilehash: 25d3227bcf8a18a2fc6ba68c194e9cac75b2e919
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="setup-and-install-visual-studio-for-mac"></a>Konfigurowanie i instalowanie oprogramowania Visual Studio dla komputerów Mac

## <a name="setup"></a>Konfiguracja

Do rozpoczęcia tworzenia natywnych, wieloplatformowych aplikacji po pobraniu programu Visual Studio dla komputerów Mac jest kilka rzeczy, które należy zainstalować i skonfigurować w ramach przygotowania.

Do pracy z systemem iOS w programie Visual Studio potrzebne są następujące elementy:

* Mac z macOS Sierra 10.12 lub nowszy
* Xcode 8.3
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

## <a name="manual-installation"></a>Instalacja ręczna

Jeśli instalacja nie powiedzie się lub dowolnego pojedynczego składnika Instalacja nie powiedzie się, można rozwiązać ten problem za pomocą ręcznej instalacji. Aby wyświetlić wymagane składniki i pobrać każdego z nich, wykonaj następujące czynności:

1. Na ekranie drugi na Instalator programu Visual Studio, przejdź do paska menu, a następnie wybierz **instrukcje dotyczące instalacji ręcznego widoku**:

    ![Opcja przedstawiający ręczne zainstalowanie elementu menu](media/installer-image12.png)

2. Postępuj zgodnie z instrukcjami, aby pobrać i zainstalować składniki ręcznie:

  ![Okno dialogowe Instalacja ręczna](media/installer-image13.png)

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Zainstaluj program Visual Studio dla komputerów Mac za serwerem zapory lub serwera proxy

Aby zainstalować program Visual Studio dla komputerów Mac za zaporą, niektórych punktów końcowych musi być dostępne w celu pobrania aktualizacji oprogramowania i wymaganych narzędzi.

Skonfiguruj sieci, aby umożliwić dostęp do następujących lokalizacji:

* [Visual Studio punkty końcowe](https://docs.microsoft.com/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)