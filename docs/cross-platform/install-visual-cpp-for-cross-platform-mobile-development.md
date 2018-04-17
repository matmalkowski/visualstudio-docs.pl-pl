---
title: Zainstaluj Visual C++ for Cross Platform Mobile Development | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 64bdc654bc1bcd6721cc29052a9409e00f6afd07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="install-visual-c-for-cross-platform-mobile-development"></a>Zainstaluj Visual C++ for Cross Platform Mobile Development
[Visual C++ dla wielu Platform Mobile Development](http://go.microsoft.com/fwlink/p/?LinkId=536383) jest instalowalnych składników programu Visual Studio 2015. Zawiera szablony programu Visual Studio i platform, a instaluje narzędzia wieloplatformowe i zestawy SDK, aby rozpocząć się szybko, bez konieczności zlokalizować, pobieranie i skonfigurować je samodzielnie. Te narzędzia Visual Studio umożliwia łatwe tworzenie, edytowanie, debugowania i testowania projektów i platform. W tym temacie opisano sposób instalowania narzędzi i oprogramowanie innych firm wymagane umożliwiające tworzenie wieloplatformowych aplikacji za pomocą programu Visual Studio. Omówienie składnika, zobacz [Visual C++ i Platform przenośnych](http://go.microsoft.com/fwlink/p/?LinkId=536387)  
  
 [Wymagania](#Requirements)   
 [Pobierz narzędzia](#GetTheTools)   
 [Instalowanie narzędzi](#InstallTheTools)   
 [Zainstaluj narzędzia dla systemu iOS](#InstallForiOS)   
 [Zainstaluj lub zaktualizuj ręcznie zależności](#ThirdParty)  
  
##  <a name="Requirements"></a> Wymagania  
  
-   Wymagania instalacji można znaleźć [wymagania dotyczące programu Visual Studio 2015 System](https://www.visualstudio.com/visual-studio-2015-system-requirements-vs).  
  
    > [!IMPORTANT]
    >  Jeśli korzystasz z systemu Windows 7 lub Windows Server 2008 R2, można opracować kodu dla aplikacji systemu Windows, aplikacje systemu Android działania natywnego i bibliotek oraz aplikacji i bibliotek kodu dla systemu iOS, ale nie aplikacje ze Sklepu Windows lub uniwersalnych systemu Windows.  
  
 Aby tworzyć aplikacje dla konkretnych platform sprzętowych, istnieją pewne dodatkowe wymagania:  
  
-   Emulatory Windows Phone i programu Microsoft Visual Studio Emulator for Android wymagają komputera, który można uruchomić funkcji Hyper-V. Funkcja Hyper-V w systemie Windows musi być włączony, zanim można zainstalować i uruchomić emulatorów. Aby uzyskać więcej informacji, zobacz emulatora [wymagania systemowe](http://msdn.microsoft.com/en-us/4d5bb438-231a-4cd2-84b7-e9660b0e3baf).  
  
-   X86 Android emulatorów, które pochodzą z zestawu SDK systemu Android działa najlepiej na komputerach z systemem sterownika Intel HAXM. Ten sterownik wymaga z procesorem Intel x64 VT-x i Obsługa wykonania bitowego wyłączyć. Aby uzyskać więcej informacji, zobacz [instrukcje dotyczące instalacji Intel® sprzętu przyspieszyć wykonywanie Manager - Microsoft Windows](http://go.microsoft.com/fwlink/p/?LinkId=536385).  
  
-   Kompilowanie kodu dla systemu iOS wymaga Identyfikatora firmy Apple, konto dewelopera programu z systemem iOS i komputera Mac, który można uruchomić [Xcode 6](http://go.microsoft.com/fwlink/p/?LinkId=536387) lub nowszego systemu operacyjnego X Mavericks lub nowszy. Instalacja proste kroki opisane w artykule [Zainstaluj narzędzia dla systemu iOS](#InstallForiOS).  
  
##  <a name="GetTheTools"></a> Pobierz narzędzia  
 Visual C++ dla wielu Platform Mobile Development jest dostępna w wersjach programu Visual Studio Community, Professional i Enterprise składnik do zainstalowania. Aby uzyskać Visual Studio, przejdź do [Visual Studio 2015 pliki do pobrania](http://go.microsoft.com/fwlink/p/?linkid=517106) strony i pobierania programu Visual Studio 2015 Update 2 lub nowszym.  
  
##  <a name="InstallTheTools"></a> Instalowanie narzędzi  
 Instalator programu Visual Studio 2015 obejmuje możliwość zainstalowania Visual C++ dla aplikacji mobilnych dla wielu Platform. Spowoduje to zainstalowanie wymaganych narzędzi języka C++, szablonów i składników dla programu Visual Studio, GCC i Clang procesami potrzebne dla systemu Android kompilacji debugowania i składniki do komunikowania się z komputerów Mac na potrzeby opracowywania aplikacji systemu iOS. Instaluje również narzędzia innych firm i zestawy SDK, które są wymagane do obsługi systemu iOS i tworzenia aplikacji systemu Android. Większość tych narzędzi innych firm są wymagane do obsługi platformy Android oprogramowania typu open source.  
  
-   Native Development Kit (zestawu NDK systemu android) jest wymagany do kompilowania kodu C++, przeznaczonego dla platformy systemu Android.  
  
-   Android SDK, Java SE Development Kit i Apache Ant są wymagane przez proces kompilacji systemu Android.  
  
-   Microsoft Visual Studio Emulator for Android jest opcjonalny emulatora wysokiej wydajności przydatne w przypadku testowania i debugowania kodu.  
  
#### <a name="to-install-visual-c-for-cross-platform-mobile-development-and-the-third-party-tools"></a>Aby zainstalować Visual C++ dla wielu Platform Mobile Development i narzędzi innych firm  
  
1.  Uruchom Instalatora programu Visual Studio 2015 pobranego następujące łącze w [narzędzia](#GetTheTools). Aby zainstalować składniki opcjonalne, wybierz **niestandardowy** jako typ instalacji. Wybierz **dalej** zaznacz opcjonalne składniki do zainstalowania.  
  
2.  W wybrane funkcje, rozwiń węzeł **Cross Platform Mobile Development** i sprawdź **Visual C++ Mobile Development**.  
  
     ![Wybierz program Visual C&#43; &#43; Mobile Development](../cross-platform/media/cppmdd_install_vcmdd.png "CPPMDD_Install_VCMDD")  
  
     Domyślnie po wybraniu **Visual C++ Mobile Development**, **języki programowania** opcja jest ustawiona do zainstalowania **Visual C++**i **typowe narzędzia i zestawy SDK** opcje są ustawione na zainstalowanie wymaganych składników innych firm. Jeśli potrzebne są dostępne dodatkowe składniki. Domyślnie **Microsoft Visual Studio Emulator for Android** jest zaznaczony. Składniki, które są już zainstalowane są wyświetlane jako nieaktywne na liście.  
  
     Do tworzenia aplikacji uniwersalnych systemu Windows i udostępniaj kod między nimi i projektów dla systemu Android i iOS, w **wybierz funkcje**, rozwiń węzeł **systemu Windows i aplikacji sieci Web** i sprawdź **uniwersalnej aplikacji systemu Windows Narzędzia deweloperskie**. Jeśli nie planujesz do tworzenia aplikacji uniwersalnych systemu Windows, można pominąć tej opcji.  
  
     Wybierz **dalej** aby kontynuować.  
  
3.  Składników innych firm mają własne postanowienia licencyjne. Postanowienia licencyjne można wyświetlić, wybierając **postanowień licencyjnych** link obok każdego składnika. Wybierz **zainstalować** dodać składniki i zainstalować program Visual Studio i języka Visual C++ dla aplikacji mobilnych dla wielu Platform.  
  
4.  Po zakończeniu instalacji zamknij Instalatora i uruchom ponownie komputer. Niektóre działania Instalatora dla składników innych firm nie będą obowiązywać do czasu ponownego uruchomienia komputera.  
  
    > [!IMPORTANT]
    >  Należy ponownie uruchomić upewnij się, że wszystko jest poprawnie zainstalowane.  
  
     Jeśli nie można zainstalować programu Microsoft Visual Studio Emulator systemu Android składnika, komputer może nie ma funkcji Hyper-V jest włączona. Użyj **Włącz lub wyłącz funkcje systemu Windows** aplikacji Panelu sterowania, aby włączyć funkcji Hyper-V, a następnie ponownie uruchom Instalatora programu Visual Studio.  
  
    > [!NOTE]
    >  Jeśli komputer lub używanej wersji systemu Windows nie obsługuje funkcji Hyper-V, nie można użyć programu Microsoft Visual Studio Emulator systemu Android składnika. Home Edition z systemu Windows nie obsługują funkcji Hyper-V.  
  
5.  Otwórz program Visual Studio. Jeśli po raz pierwszy, uruchomienia programu Visual Studio, może upłynąć trochę czasu na konfigurowanie i zaloguj się. Po wykonaniu tych czynności w Visual Studio **narzędzia** menu, wybierz opcję **rozszerzenia i aktualizacje**, **aktualizacje**. Jeśli istnieje, że Visual Studio aktualizacje dostępne dla programu Visual C++ dla wielu Platform Mobile Development lub programu Microsoft Visual Studio Emulator for Android, zainstaluj je.  
  
##  <a name="InstallForiOS"></a> Zainstaluj narzędzia dla systemu iOS  
 Visual C++ for Cross Platform Mobile Development służy do edytowania, debugowania i wdrażania kodu dla systemu iOS w narzędziu iOS Simulator lub urządzenia z systemem iOS, ale z powodu ograniczeń licencji kod muszą zostać skompilowane na zdalnie na komputerach Mac. Aby skompilować i uruchomić aplikacje dla systemu iOS przy użyciu programu Visual Studio, należy skonfigurować i skonfigurować agenta zdalnego opartym na systemie Aby uzyskać szczegółowe instrukcje dotyczące instalacji i wymagania wstępne opcje konfiguracji, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Jeśli tworzysz nie dla systemu iOS, możesz pominąć ten krok.  
  
##  <a name="ThirdParty"></a> Zainstaluj lub zaktualizuj ręcznie zależności  
 Jeśli nie chcesz zainstalować jedną lub więcej zależności innych firm za pomocą Instalatora programu Visual Studio podczas instalowania opcja Visual C++ programowania aplikacji mobilnych, można zainstalować je później za pomocą kroków w [zainstalować narzędzia](#InstallTheTools). Można również zainstalować lub zaktualizować je niezależnie od programu Visual Studio.  
  
> [!CAUTION]
>  Zależności można zainstalować w dowolnej kolejności, z wyjątkiem Java. Należy zainstalować i skonfigurować zestaw JDK, przed zainstalowaniem zestawu SDK systemu Android.  
  
 Przeczytaj następujące informacje, a następnie użyj poniższych linków, aby ręcznie zainstalować zależności.  
  
-   [Zestaw Java SE Development Kit](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  
  
     Domyślnie Instalator umieszcza narzędzia Java w \Java C:\Program Files (x86).  
  
-   [Zestaw SDK systemu android](https://developer.android.com/sdk/index.html#Other)  
  
     Podczas instalacji należy zaktualizować interfejsy API jako zalecana. Upewnij się, że co najmniej jest zainstalowany zestaw SDK dla systemu Android 5.0 interfejs typu lizak (poziom interfejsu API 21). Domyślnie Instalator umieszcza zestawu SDK systemu Android w C:\Program Files (x86) \Android\android-sdk.  
  
     Można uruchomić aplikacji SDK Manager w katalogu zestawu SDK systemu Android ponownie, aby zaktualizować zestaw SDK i instalowania opcjonalnych narzędzi i dodatkowe poziomy interfejsu API. Aktualizacje mogą się zainstalować tylko w przypadku **Uruchom jako administrator** do uruchomienia aplikacji SDK Manager. Jeśli masz problemy z kompilacją aplikacji systemu Android, sprawdź w Menedżerze SDK aktualizacje do programu zainstalowanych zestawów SDK.  
  
     Aby korzystać z niektórych Android emulatorów, które pochodzą z zestawu SDK systemu Android, należy zainstalować opcjonalne sterowniki Intel HAXM. Może być konieczne usunięcie funkcji Hyper-V z systemu Windows do pomyślnego zainstalowania sterowników Intel HAXM. Należy przywrócić funkcji Hyper-V, aby użyć emulatory Windows Phone i Microsoft Visual Studio Emulator for Android.  
  
-   [Zestawu NDK systemu android](https://developer.android.com/tools/sdk/ndk/index.html)  
  
     Domyślnie Instalator umieszcza zestawu NDK systemu Android w C:\ProgramData\Microsoft\AndroidNDK. Można pobrać i zainstalować zestaw Android NDK ponownie, aby zaktualizować instalacji zestawu NDK.  
  
-   [Apache Ant](http://ant.apache.org/bindownload.cgi)  
  
     Domyślnie Instalator umieszcza Apache Ant w \Microsoft C:\Program Files (x86) 14.0\Apps programu Visual Studio.  
  
-   [Microsoft Visual Studio Emulator for Android](http://go.microsoft.com/fwlink/p/?LinkId=536390)  
  
     Można zainstalować i aktualizacja programu Microsoft Visual Studio Emulator for Android z galerii programu Visual Studio.  
  
 W większości przypadków Visual Studio może wykryć konfiguracji oprogramowania innych firm zostały zainstalowane i obsługuje ścieżek instalacji w zmiennych środowiskowych wewnętrznego. Można zastąpić domyślne ścieżki tych narzędzi aplikacji dla wielu platform w programie Visual Studio IDE.  
  
#### <a name="to-set-the-paths-for-third-party-tools"></a>Można ustawić ścieżki do narzędzi innych firm  
  
1.  Na pasku menu programu Visual Studio wybierz **narzędzia**, **opcje**.  
  
2.  W **opcje** okna dialogowego rozwiń **Cross Platform**, **C++**i wybierz **Android**.  
  
     ![Opcje ścieżki narzędzia android](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")  
  
3.  Aby zmienić ścieżkę używaną przez narzędzie, zaznacz pole wyboru obok ścieżkę i edytować ścieżkę folderu w polu tekstowym. Można także użyć przycisku Przeglądaj (**...** ) można otworzyć **wybierz lokalizację** okna dialogowego, aby wybrać folder.  
  
4.  Wybierz **OK** zapisać narzędzie niestandardowe lokalizacje folderów.  
  
## <a name="see-also"></a>Zobacz też  
 [Zainstaluj i skonfiguruj narzędzia do kompilacji przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)   
 [Visual C++ i Platform przenośnych](https://www.visualstudio.com/explore/cplusplus-mdd-vs.aspx)