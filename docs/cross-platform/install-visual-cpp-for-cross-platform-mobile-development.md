---
title: Zainstaluj Visual C++ for Cross Platform Mobile Development | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/21/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 5013f1ce5ed9c20ba51feef7dd73d80adc152103
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
ms.locfileid: "34454704"
---
# <a name="install-cross-platform-mobile-development-with-c"></a>Instalowanie i platform Mobile development przy użyciu języka C++

C++ w programie Visual Studio umożliwia tworzenie aplikacji pulpitu systemu Windows, aplikacje systemu Windows platformy Uniwersalnej aplikacji dla systemu Linux i teraz, aplikacje dla systemów Android i iOS. **Mobile development z C++** obciążenie jest zestaw instalowalnych składników w Visual Studio, która obejmuje i platform systemu iOS, Android i platformy uniwersalnej systemu Windows programu Visual Studio szablonów. Instaluje narzędzia wieloplatformowe i zestawy SDK, należy rozpocząć się szybko, bez konieczności zlokalizować, pobieranie i skonfigurować je samodzielnie. Można użyć tych narzędzi w programie Visual Studio do łatwego tworzenia, edytowania, debugowania i testowania projektów i platform. W tym temacie opisano sposób instalowania narzędzi i oprogramowanie innych firm wymagane do opracowywania i platform aplikacji w języku C++ za pomocą programu Visual Studio. Aby uzyskać ogólne informacje, zobacz [Visual C++ i Platform przenośnych](https://go.microsoft.com/fwlink/p/?LinkId=536383)

## <a name="requirements"></a>Wymagania

- Wymagania instalacji można znaleźć [wymagania systemowe rodziny produktów Visual Studio](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs).

   > [!IMPORTANT]
   > Jeśli korzystasz z systemu Windows 7 lub Windows Server 2008 R2, można opracować kodu dla aplikacji pulpitu systemu Windows, Android Native działanie aplikacji i bibliotek i aplikacje i bibliotek kodu dla systemu iOS, ale aplikacje nie Windows Phone lub platformy uniwersalnej systemu Windows.

Aby tworzyć aplikacje dla konkretnych platform sprzętowych, istnieją pewne dodatkowe wymagania:

- Emulatory Windows Phone i programu Microsoft Visual Studio Emulator for Android wymagają komputera, który można uruchomić funkcji Hyper-V. Funkcja Hyper-V w systemie Windows musi być włączony, zanim można zainstalować i uruchomić emulatorów. Aby uzyskać więcej informacji, zobacz emulatora [wymagania systemowe](system-requirements-for-the-visual-studio-emulator-for-android.md).

- X86 Android emulatorów, które pochodzą z zestawu SDK systemu Android działa najlepiej na komputerach z systemem sterownika Intel HAXM. Ten sterownik wymaga z procesorem Intel x64 VT-x i Obsługa wykonania bitowego wyłączyć. Aby uzyskać więcej informacji, zobacz [® sprzętu przyspieszony wykonywania Menedżer Intel (Intel® HAXM)](https://go.microsoft.com/fwlink/p/?LinkId=536385).

- Kompilowanie kodu dla systemu iOS wymaga Identyfikatora firmy Apple, konto dewelopera programu z systemem iOS i komputera Mac, który można uruchomić [Xcode](https://go.microsoft.com/fwlink/p/?LinkId=536387) w wersji 6 lub nowszego systemu operacyjnego Mavericks X (w wersji 10.9) lub nowszy. Łącze do kroków instalacji, zobacz [Zainstaluj narzędzia dla systemu iOS](#install-tools-for-ios).

## <a name="get-the-tools"></a>Pobierz narzędzia

Tworzenie przenośnych za pomocą języka C++ jest dostępna w wersji Visual Studio Community, Professional i Enterprise. Aby uzyskać Visual Studio, przejdź do [programu Visual Studio pobiera](https://go.microsoft.com/fwlink/p/?linkid=517106) strony. Wiele platform przenośnych dostępnych narzędzi uruchamianie w programie Visual Studio 2015 Update 2 lub nowszym.

## <a name="install-the-tools"></a>Instalowanie narzędzi

Instalator programu Visual Studio dla programu Visual Studio 2017 obejmuje **Mobile development z C++** obciążenia, który instaluje narzędzia języka C++, szablony i składniki wymagane do tworzenia aplikacji systemu Android i iOS w programie Visual Studio. Instaluje ją procesami GCC i Clang, potrzebne dla systemu Android kompilacji debugowania i składniki do komunikowania się z komputerów Mac na potrzeby opracowywania aplikacji systemu iOS. Instaluje również narzędzia innych firm i zestawy SDK, które są wymagane do obsługi systemu iOS i tworzenia aplikacji systemu Android. Większość tych narzędzi innych firm są wymagane do obsługi platformy Android oprogramowania typu open source.

- Native Development Kit (zestawu NDK systemu android) jest wymagany do kompilowania kodu C++, przeznaczonego dla platformy systemu Android.

- Android SDK, Java SE Development Kit i Apache Ant są wymagane przez proces kompilacji systemu Android.

- Emulator systemu Google Android i przyspieszony menedżera wykonywania programu Intel sprzętu są opcjonalne, ale zalecane składniki. Mogą tworzyć i debugować bezpośrednio na urządzeniu z systemem Android, ale często jest łatwiejsze w emulatorze na pulpicie do debugowania. Microsoft udostępnia również Visual Studio Emulator for Android, którą można zainstalować oddzielnie.

#### <a name="to-install-the-mobile-development-with-c-workload-in-visual-studio-2017"></a>Aby zainstalować Mobile development przy użyciu obciążenia C++ w programie Visual Studio 2017 r.

1. Uruchom **Instalator programu Visual Studio** z **Start** menu.

1. Jeśli po zainstalowaniu programu Visual Studio, wybierz **Modyfikuj** przycisk dla zainstalowanej wersji programu Visual Studio, które chcesz zmodyfikować. W przeciwnym razie wybierz **zainstalować** do zainstalowania programu Visual Studio.

1. Z **obciążeń** karta zaznaczone, przewiń w dół i wybierz **Mobile development z C++** obciążenia w Instalatorze programu Visual Studio. Po wybraniu to obciążenie wybrane zostaną także inne składniki wymagane w przypadku programowania w języku C++. Możesz również innych obciążeń i poszczególne składniki do zainstalowania na tym samym czasie. Aby skompilować kod i platform, który również jest przeznaczony dla platformy uniwersalnej systemu Windows, zaznacz **rozwoju platformy uniwersalnej systemu Windows** obciążenia.

1. W **szczegółowe informacje dotyczące instalacji** okienku rozwiń **Mobile development z C++**. W **opcjonalnie** sekcji, można wybrać dodatkowe wersje zestawu NDK, Emulator systemu Google Android sprzętu Intel przyspieszony menedżera wykonywania i IncrediBuild narzędzie przyspieszenia kompilacji.

1. Domyślnie co najmniej jeden składnik instalacji zestawu SDK systemu Android znajdują się przez obciążenie. Dostępne są dodatkowe wersje zestawu SDK systemu Android. Aby dodać je do instalacji, wybierz **pojedynczych składników** , a następnie przewiń w dół do **zestawów SDK, bibliotek i platform** sekcji, aby dokonać wyboru.

1. Wybierz **Modyfikuj** lub **zainstalować** przycisk, aby zainstalować **Mobile development z C++** obciążenia oraz inne wybrane obciążeń i opcjonalnych składników.

   Po zakończeniu instalacji zamknij Instalatora i uruchom ponownie komputer. Niektóre działania Instalatora dla składników innych firm nie będą obowiązywać do czasu ponownego uruchomienia komputera.

   > [!IMPORTANT]
   > Należy ponownie uruchomić upewnij się, że wszystko jest poprawnie zainstalowane.

1. Otwórz program Visual Studio. Jeśli po raz pierwszy, uruchomienia programu Visual Studio, może upłynąć trochę czasu na konfigurowanie i zaloguj się. Gdy program Visual Studio jest gotowy, sprawdź, czy wszystkie aktualizacje i zainstaluj je.

#### <a name="to-install-the-mobile-development-component-and-third-party-tools-in-visual-studio-2015"></a>Aby zainstalować składnik programowania aplikacji mobilnych i narzędzi innych firm w programie Visual Studio 2015

Jeśli używasz programu Visual Studio 2015, jego Instalator zawiera opcję instalowania programu Visual C++ dla programowania aplikacji mobilnych i Platform, która instaluje narzędzia języka C++ wymagane, szablony i składniki programu Visual Studio 2015.

1. Uruchom Instalatora programu Visual Studio 2015. Aby zainstalować składniki opcjonalne, wybierz **niestandardowy** jako typ instalacji. Wybierz **dalej** zaznacz opcjonalne składniki do zainstalowania.

1. W **wybierz funkcje**, rozwiń węzeł **Cross Platform Mobile Development** i sprawdź **Visual C++ Mobile Development**.

   ![Wybierz program Visual C&#43; &#43; Mobile Development](../cross-platform/media/cppmdd_install_vcmdd.png "CPPMDD_Install_VCMDD")

   Domyślnie po wybraniu **Visual C++ Mobile Development**, **języki programowania** opcja jest ustawiona do zainstalowania **Visual C++** i **typowe narzędzia i zestawy SDK** opcje są ustawione na zainstalowanie wymaganych składników innych firm. Jeśli potrzebne są dostępne dodatkowe składniki. Domyślnie **Microsoft Visual Studio Emulator for Android** jest zaznaczony. Składniki, które są już zainstalowane są wyświetlane jako nieaktywne na liście.

   Do tworzenia aplikacji uniwersalnych systemu Windows i udostępniaj kod między nimi i projektów dla systemu Android i iOS, w **wybierz funkcje**, rozwiń węzeł **systemu Windows i aplikacji sieci Web** i sprawdź **uniwersalnej aplikacji systemu Windows Narzędzia deweloperskie**. Jeśli nie planujesz do tworzenia aplikacji uniwersalnych systemu Windows, można pominąć tej opcji.

   Wybierz **dalej** aby kontynuować.

1. Składników innych firm mają własne postanowienia licencyjne. Postanowienia licencyjne można wyświetlić, wybierając **postanowień licencyjnych** link obok każdego składnika. Wybierz **zainstalować** dodać składniki i zainstalować program Visual Studio i języka Visual C++ dla aplikacji mobilnych dla wielu Platform.

1. Po zakończeniu instalacji zamknij Instalatora i uruchom ponownie komputer. Niektóre działania Instalatora dla składników innych firm nie będą obowiązywać do czasu ponownego uruchomienia komputera.

   > [!IMPORTANT]
   > Należy ponownie uruchomić upewnij się, że wszystko jest poprawnie zainstalowane.

   Jeśli nie można zainstalować programu Microsoft Visual Studio Emulator systemu Android składnika, komputer może nie ma funkcji Hyper-V jest włączona. Użyj **Włącz lub wyłącz funkcje systemu Windows** aplikacji Panelu sterowania, aby włączyć funkcji Hyper-V, a następnie ponownie uruchom Instalatora programu Visual Studio.

   > [!NOTE]
   > Jeśli komputer lub używanej wersji systemu Windows nie obsługuje funkcji Hyper-V, nie można użyć programu Microsoft Visual Studio Emulator systemu Android składnika. Home Edition z systemu Windows nie obsługują funkcji Hyper-V.

1. Otwórz program Visual Studio. Jeśli po raz pierwszy, uruchomienia programu Visual Studio, może upłynąć trochę czasu na konfigurowanie i zaloguj się. Po wykonaniu tych czynności w Visual Studio **narzędzia** menu, wybierz opcję **rozszerzenia i aktualizacje**, **aktualizacje**. Jeśli istnieje, że Visual Studio aktualizacje dostępne dla programu Visual C++ dla wielu Platform Mobile Development lub programu Microsoft Visual Studio Emulator for Android, zainstaluj je.

## <a name="install-tools-for-ios"></a>Zainstaluj narzędzia dla systemu iOS

Visual C++ for Cross Platform Mobile Development służy do edytowania, debugowania i wdrażania kodu dla systemu iOS w narzędziu iOS Simulator lub urządzenia z systemem iOS, ale z powodu ograniczeń licencji kod muszą zostać skompilowane na zdalnie na komputerach Mac. Aby skompilować i uruchomić aplikacje dla systemu iOS przy użyciu programu Visual Studio, należy skonfigurować i skonfigurować agenta zdalnego opartym na systemie Aby uzyskać szczegółowe instrukcje dotyczące instalacji i wymagania wstępne opcje konfiguracji, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](install-and-configure-tools-to-build-using-ios.md). Jeśli tworzysz nie dla systemu iOS, możesz pominąć ten krok.

## <a name="install-or-update-dependencies-manually"></a>Zainstaluj lub zaktualizuj ręcznie zależności

Jeśli nie chcesz zainstalować jedną lub więcej zależności innych firm za pomocą Instalatora programu Visual Studio po zainstalowaniu **Mobile development z C++** obciążenia (lub programu Visual Studio 2015, Visual C++ Mobile Development opcja), możesz można zainstalować je później za pomocą kroków w [zainstalować narzędzia](#install-the-tools). Instalator programu Visual Studio jest regularnie aktualizowana w celu zainstaluj najnowsze składniki innych firm. Można ją zainstalować zaktualizowaną zestawy SDK i NDKs. Można również zainstalować lub zaktualizować je niezależnie od programu Visual Studio.

> [!CAUTION]
> Zależności można zainstalować w dowolnej kolejności, z wyjątkiem Java. Należy zainstalować i skonfigurować zestaw JDK, przed zainstalowaniem zestawu SDK systemu Android.

Przeczytaj następujące informacje, a następnie użyj poniższych linków, aby ręcznie zainstalować zależności.

- [Zestaw Java SE Development Kit](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

   Domyślnie Instalator umieszcza narzędzia Java w \Java C:\Program Files (x86).

- [Zestaw SDK systemu android](https://developer.android.com/sdk/index.html#command-tools)

   Podczas instalacji należy zaktualizować interfejsy API jako zalecana. Upewnij się, że co najmniej jest zainstalowany zestaw SDK dla systemu Android 5.0 interfejs typu lizak (poziom interfejsu API 21). Domyślnie Instalator umieszcza zestawu SDK systemu Android w C:\Program Files (x86) \Android\android-sdk.

   Można uruchomić aplikacji SDK Manager w katalogu zestawu SDK systemu Android ponownie, aby zaktualizować zestaw SDK i instalowania opcjonalnych narzędzi i dodatkowe poziomy interfejsu API. Aktualizacje mogą się zainstalować tylko w przypadku **Uruchom jako administrator** do uruchomienia aplikacji SDK Manager. Jeśli masz problemy z kompilacją aplikacji systemu Android, sprawdź w Menedżerze SDK aktualizacje do programu zainstalowanych zestawów SDK.

   Aby korzystać z niektórych Android emulatorów, które pochodzą z zestawu SDK systemu Android, należy zainstalować opcjonalne sterowniki Intel HAXM. Może być konieczne usunięcie funkcji Hyper-V z systemu Windows do pomyślnego zainstalowania sterowników Intel HAXM. Należy przywrócić funkcji Hyper-V, aby użyć emulatory Windows Phone i Microsoft Visual Studio Emulator for Android. Aby uzyskać więcej informacji, zobacz [przyspieszanie sprzętowe emulatora systemu Android](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin).

- [Zestawu NDK systemu android](https://developer.android.com/tools/sdk/ndk/index.html)

   Domyślnie Instalator umieszcza zestawu NDK systemu Android w C:\ProgramData\Microsoft\AndroidNDK. Można pobrać i zainstalować zestaw Android NDK ponownie, aby zaktualizować instalacji zestawu NDK.

- [Apache Ant](https://ant.apache.org/bindownload.cgi)

   Domyślnie Instalator umieszcza Apache Ant w \Microsoft C:\Program Files (x86) 14.0\Apps programu Visual Studio.

- [Microsoft Visual Studio Emulator for Android](https://aka.ms/vscomemudownload)

   Microsoft Visual Studio Emulator for Android jest opcjonalny emulator przydatne w przypadku testowania i debugowania kodu. Po wydaniu programu Visual Studio Emulator for Android, Google zaktualizować ich emulatora systemu Android do używania sprzętowego przyspieszania za pośrednictwem Intel obiektu HAXM. Firma Microsoft zaleca się, że używasz emulatora przyspieszonego firmy Google gdy to możliwe, ponieważ zapewnia dostęp do najnowszych obrazów systemu operacyjnego Android i sklepu Google Play usług.

W większości przypadków Visual Studio może wykryć konfiguracji oprogramowania innych firm zostały zainstalowane i obsługuje ścieżek instalacji w zmiennych środowiskowych wewnętrznego. Można zastąpić domyślne ścieżki tych narzędzi aplikacji dla wielu platform w programie Visual Studio IDE.

#### <a name="to-set-the-paths-for-third-party-tools"></a>Można ustawić ścieżki do narzędzi innych firm

1. Na pasku menu programu Visual Studio wybierz **narzędzia** > **opcje**.

1. W **opcje** okno dialogowe, wybierz opcję **Cross Platform** > **C++** > **Android**.

   ![Opcje ścieżki narzędzia android](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")

1. Aby zmienić ścieżkę używaną przez narzędzie, zaznacz pole wyboru obok ścieżkę i edytować ścieżkę folderu w polu tekstowym. Można także użyć przycisku Przeglądaj (**...** ) można otworzyć **wybierz lokalizację** okna dialogowego, aby wybrać folder.

1. Wybierz **OK** zapisać narzędzie niestandardowe lokalizacje folderów.

## <a name="see-also"></a>Zobacz też

- [Instalowanie i konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](install-and-configure-tools-to-build-using-ios.md)
- [Visual C++ i Platform przenośnych](https://go.microsoft.com/fwlink/p/?LinkId=536383)
