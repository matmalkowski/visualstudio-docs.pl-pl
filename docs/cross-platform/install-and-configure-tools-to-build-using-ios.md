---
title: "Zainstaluj i skonfiguruj narzędzia do kompilacji przy użyciu systemu iOS | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: d0c311c9-9eb9-42c5-ba07-25604362cd28
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: xplat-cplusplus
ms.openlocfilehash: 734c7b8a8416503e457f964d74e0a3773cbada2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="install-and-configure-tools-to-build-using-ios"></a>Zainstaluj i skonfiguruj narzędzia do kompilacji przy użyciu systemu iOS
Visual C++ for Cross Platform Mobile Development służy do edytowania, debugowania i wdrażania kodu dla systemu iOS w narzędziu iOS Simulator lub urządzenia z systemem iOS, ale z powodu ograniczeń licencji kod musi być skompilowany i zdalnie uruchamiać na komputerach Mac. Aby skompilować i uruchomić aplikacje dla systemu iOS przy użyciu programu Visual Studio, musisz instalowania i konfigurowania zdalnego agenta [vcremote](http://go.microsoft.com/fwlink/p/?LinkId=534988), opartym na systemie Dojścia zdalnego agenta kompilacji żądań w programie Visual Studio i uruchamia aplikację na urządzeniu z systemem iOS podłączone do komputera Mac lub w narzędziu iOS Simulator na komputerach Mac.  
  
> [!NOTE]
>  Uzyskać informacji o usługach hostowanych w chmurze Mac zamiast Mac, zobacz [tworzenie i symulowanie systemu iOS w chmurze](https://taco.visualstudio.com/en-us/docs/build_ios_cloud/). Instrukcje dotyczą tworzenia za pomocą narzędzi Visual Studio Tools for Apache Cordova. Postępuj zgodnie z instrukcjami, aby kompilować przy użyciu programu Visual C++ dla wielu Platform Mobile Development, należy zastąpić vcremote dla wersji programu vs-mda-remote.  
  
 Po zainstalowaniu narzędzia umożliwiające tworzenie za pomocą systemu iOS można znaleźć w tym temacie dla sposobów, aby szybko skonfigurować i zaktualizować zdalnego agenta dla opracowywania aplikacji systemu iOS w programie Visual Studio i opartym na systemie  
  
 [Wymagania wstępne](#Prerequisites)  
  
 [Zainstaluj agenta zdalnego dla systemu iOS](#Install)  
  
 [Uruchom agenta zdalnego](#Start)  
  
 [Konfigurowanie agenta zdalnego w programie Visual Studio](#ConfigureVS)  
  
 [Generowanie nowego zabezpieczającego numeru PIN](#GeneratePIN)  
  
 [Wygeneruj nowy certyfikat serwera](#GenerateCert)  
  
 [Konfigurowanie agenta zdalnego dla komputerów Mac](#ConfigureMac)  
  
##  <a name="Prerequisites"></a>Wymagania wstępne  
 Aby zainstalować i korzystać z agenta zdalnego tworzenie kodu dla systemu iOS, najpierw musi mieć następujące wymagania wstępne:  
  
-   Komputer Mac z systemem OS X Mavericks lub nowszy  
  
-   [Identyfikatora firmy Apple](https://appleid.apple.com/)  
  
-   Aktywny [systemu iOS w programie dla deweloperów](https://developer.apple.com/programs/ios/) konto z firmy Apple  
  
-   [Edytor Xcode 6](https://developer.apple.com/xcode/downloads/)  
  
     Edytor Xcode 6 można pobrać ze sklepu z aplikacjami.  
  
-   Narzędzia wiersza polecenia Xcode  
  
     Aby zainstalować narzędzia wiersza polecenia Xcode, Otwórz aplikację terminalu na komputerze Mac i wprowadź następujące polecenie:  
  
     `xcode-select --install`  
  
-   IOS podpisywania tożsamości skonfigurowanej w środowisku Xcode  
  
     Szczegółowe informacje na temat uzyskiwania tożsamości podpisywania systemu iOS, zobacz [certyfikatów i Obsługa tożsamości podpisywania](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html) w bibliotece deweloperów systemu iOS. Aby wyświetlić lub ustaw tożsamość podpisywania w środowisku Xcode, otwórz **Xcode** menu i wybierz polecenie **preferencje**. Wybierz **kont** i wybierz identyfikator Apple ID, a następnie wybierz **Wyświetl szczegóły** przycisku.  
  
-   Jeśli używasz urządzenia z systemem iOS do tworzenia aplikacji, profilu inicjowania obsługi skonfigurowane w środowisku Xcode dla urządzenia  
  
     Aby uzyskać szczegółowe informacje na temat tworzenia profile aprowizacji, zobacz [tworzenie inicjowania obsługi administracyjnej korzystanie z profilów elementu członkowskiego Centrum](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW24) w bibliotece deweloperów systemu iOS.  
  
-   [Node.js](http://nodejs.org/)  
  
-   Zaktualizowaną wersję programu npm  
  
     Wersja programu npm dołączoną Node.js nie może być wystarczająco aktualna, aby zainstalować vcremote. Aby zaktualizować npm, Otwórz aplikację terminalu na komputerze Mac i wprowadź następujące polecenie:  
  
     `sudo npm install -g npm@latest`  
  
##  <a name="Install"></a>Zainstaluj agenta zdalnego dla systemu iOS  
 Po zainstalowaniu programu Visual C++ dla wielu Platform Mobile Development w Visual Studio może komunikować się z [vcremote](http://go.microsoft.com/fwlink/p/?LinkId=534988), agent zdalnego uruchomiona na komputerze Mac do transferu plików, tworzenie i uruchamianie aplikacji systemu iOS i debugowanie polecenia send.  
  
 Przed zainstalowaniem agenta zdalnego, upewnij się, że zostały spełnione [wymagania wstępne](#Prerequisites) i zainstalowane [Visual C++ for Cross Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md#InstallTheTools).  
  
###  <a name="DownloadInstall"></a>Aby pobrać i zainstalować agenta zdalnego  
  
-   W terminalu aplikacji na komputerze Mac wprowadź:  
  
     `sudo npm install -g --unsafe-perm vcremote`  
  
     Globalne instalacji (**-g**) przełącznik jest zalecane, ale nie są wymagane.  
  
     Podczas instalacji vcremote jest zainstalowany i tryb dewelopera jest uaktywniany opartym na systemie [Homebrew](http://brew.sh/) i dwóch pakietów npm, vcremote-lib i witryny vcremote, są również instalowane.  
  
    > [!NOTE]
    >  Do zainstalowania oprogramowania Homebrew, musi mieć dostęp do operacji sudo (administrator). Jeśli musisz zainstalować vcremote bez sudo, należy ręcznie zainstalować oprogramowania Homebrew w lokalizacji usr/lokalne, a następnie dodaj jego folder bin do ścieżki. Aby uzyskać więcej informacji, zobacz [dokumentacji oprogramowania Homebrew](https://github.com/Homebrew/homebrew/wiki/Installation). Aby ręcznie włączyć tryb dewelopera, wpisz to polecenie w terminalu aplikacji:`DevToolsSecurity -enable`  
  
 Po aktualizacji do nowej wersji programu Visual Studio, należy zaktualizować na bieżącą wersję agenta zdalnego. Aby zaktualizować agenta zdalnego, powtórz kroki, aby pobrać i zainstalować agenta zdalnego.  
  
##  <a name="Start"></a>Uruchom agenta zdalnego  
 Musi być uruchomiona zdalnego agenta dla programu Visual Studio skompilować i uruchomić kod z systemem iOS. Visual Studio musi łączyć się z agentem zdalnym przed może komunikować się. Domyślnie agenta zdalnego działa w trybie bezpiecznego połączenia, który wymaga numeru PIN do sparowania z programem Visual Studio.  
  
###  <a name="RemoteAgentStartServer"></a>Aby uruchomić agenta zdalnego  
  
-   W terminalu aplikacji na komputerze Mac wprowadź:  
  
     `vcremote`  
  
     To agenta zdalnego rozpoczyna się od domyślny katalog kompilacji z ~ / vcremote. Aby uzyskać dodatkowe opcje konfiguracji, zobacz [skonfigurować agenta zdalnego dla komputerów Mac](#ConfigureMac).  
  
 Podczas pierwszego uruchomienia agenta, a w dowolnej chwili możesz utworzyć nowy certyfikat klienta, użytkownicy otrzymywali wymaganych informacji w celu skonfigurowania agenta w programie Visual Studio, w tym nazwę hosta, port i numer PIN.  
  
 ![Umożliwia generowanie bezpieczny kod PIN vcremote](../cross-platform/media/cppmdd_vcremote_generateclientcert.png "CPPMDD_vcremote_generateClientCert")  
  
 Jeśli zamierzasz skonfigurować agenta zdalnego w programie Visual Studio przy użyciu nazwy hosta polecenia ping Mac z systemem Windows przy użyciu nazwy hosta, aby sprawdzić, czy jest dostępny. W przeciwnym razie konieczne może być zamiast tego użyj adresu IP.  
  
 Wygenerowany kod PIN jest przeznaczony dla jednego czasie używana i jest prawidłowy tylko przez ograniczony czas. Visual Studio nie parę z agentem zdalnym przed wygaśnięciem, należy wygenerować nowy numer PIN. Aby uzyskać więcej informacji, zobacz [wygenerować nowy zabezpieczający numer PIN](#GeneratePIN).  
  
 W trybie niezabezpieczona służy agenta zdalnego. W trybie niezabezpieczonym agenta zdalnego mogą łączyć się do programu Visual Studio bez numeru PIN.  
  
#### <a name="to-disable-secured-connection-mode"></a>Aby wyłączyć tryb bezpiecznego połączenia  
  
-   Aby wyłączyć tryb bezpiecznego połączenia w vcremote, wprowadź polecenie w terminalu aplikacji na komputerze Mac:  
  
     `vcremote --secure false`  
  
#### <a name="to-enable-secured-connection-mode"></a>Aby włączyć tryb bezpiecznego połączenia  
  
-   Aby włączyć tryb bezpiecznego połączenia, wpisz to polecenie:  
  
     `vcremote --secure true`  
  
 Po uruchomieniu agenta zdalnego, można użyć go w programie Visual Studio, aż do momentu wyłączenia.  
  
#### <a name="to-stop-the-remote-agent"></a>Aby zatrzymać agenta zdalnego  
  
-   W terminalu vcremote okno działa, wprowadź `Control+C`.  
  
##  <a name="ConfigureVS"></a>Konfigurowanie agenta zdalnego w programie Visual Studio  
 Aby połączyć się z agentem zdalnym z programu Visual Studio, należy określić konfiguracji zdalnej w opcjach programu Visual Studio.  
  
#### <a name="to-configure-the-remote-agent-from-visual-studio"></a>Aby skonfigurować agenta zdalnego w programie Visual Studio  
  
1.  Jeśli agent nie jest już uruchomiona na komputerze Mac, postępuj zgodnie z instrukcjami [uruchomienia agenta zdalnego](#Start). Komputerów Mac musi być uruchomiona vcremote dla programu Visual Studio pomyślnie skojarzyć, łączenie i skompilowanie projektu.  
  
2.  Na komputerze Mac Pobierz nazwę hosta lub adres IP z komputerów Mac.  
  
     Adres IP można uzyskać za pomocą **ifconfig** polecenie w oknie terminalu. Użyj adresu inet interfejsu sieciowego z aktywnego na liście.  
  
3.  Na pasku menu programu Visual Studio wybierz **narzędzia**, **opcje**.  
  
4.  W **opcje** okna dialogowego rozwiń **Cross Platform**, **C++**, **iOS**.  
  
5.  W **nazwy hosta** i **portu** wprowadź wartości określonych przez agenta zdalnego po jej uruchomieniu. Nazwa hosta może być nazwą DNS lub adres IP z komputerów Mac. Domyślny port to 3030.  
  
    > [!NOTE]
    >  Jeśli nie można wywołać Mac przy użyciu nazwy hosta, może być konieczne użycie adresu IP.  
  
6.  Jeśli używasz zdalnego agenta w domyślnym trybie bezpiecznego połączenia, sprawdź **bezpiecznego** pole wyboru, wprowadź numer PIN wartość określoną przez agenta zdalnego w **numeru Pin** pola. Jeśli używasz zdalnego agenta w trybie niezabezpieczone połączenie, wyczyść **bezpiecznego** wyboru i pozostawić **numeru Pin** pole puste.  
  
7.  Wybierz **pary** umożliwia parowanie.  
  
     ![Konfigurowanie połączenia vcremote kompilacji systemu iOS](../cross-platform/media/cppmdd_options_ios.PNG "CPPMDD_Options_iOS")  
  
     Parowanie jest zachowywana do czasu zmiany nazwy hosta lub portu. W przypadku zmiany nazwy hosta lub portu w **opcje** okno dialogowe, aby cofnąć zmianę, wybierz **Przywróć** przycisk, aby powrócić do poprzedniej parowania.  
  
     Jeśli parowanie nie powiedzie się, sprawdź, czy działa agenta zdalnego, wykonując kroki opisane w [uruchomienia agenta zdalnego](#Start). Po zbyt dużo czasu od agenta zdalnego numer PIN został wygenerowany, postępuj zgodnie z instrukcjami [wygenerować nowy zabezpieczający numer PIN](#GeneratePIN) Mac i spróbuj wykonać operację ponownie. Jeśli korzystasz z nazwą hosta komputera Mac, spróbuj użyć adresu IP w **nazwy hosta** zamiast tego pola.  
  
8.  Nazwa folderu w aktualizacji **zdalnym** Aby określić folder używany przez agenta zdalnego w katalogu głównej (~) na komputerach Mac. Domyślnie agenta zdalnego używa /Users/`username`/vcremote jako zdalny katalog główny.  
  
9. Wybierz **OK** można zapisać ustawienia połączenia zdalnego parowania.  
  
 Visual Studio używa tych samych informacji do nawiązania połączenia zdalnego agenta na komputerze Mac każdym jej użyciu. Nie trzeba pary Visual Studio z agentem zdalnym ponownie chyba że generuje nowy certyfikat zabezpieczeń na komputerze Mac lub jego nazwa hosta lub adres IP adresów zmiany.  
  
##  <a name="GeneratePIN"></a>Generowanie nowego zabezpieczającego numeru PIN  
 Podczas uruchamiania agenta zdalnego po raz pierwszy wygenerowany kod PIN jest ważny przez określony czas — domyślnie 10 minut. Visual Studio nie parę z agentem zdalnym przed wygaśnięciem, należy wygenerować nowy numer PIN.  
  
#### <a name="to-generate-a-new-pin"></a>Aby wygenerować nowy kod PIN  
  
1.  Zatrzymaj agenta, lub Otwórz drugie okno terminalu aplikacji na komputerze Mac i użyj jej wprowadź polecenie.  
  
2.  Wprowadź następujące polecenie w terminalu aplikacji:  
  
     `vcremote generateClientCert`  
  
     Agent zdalnego generuje nowy tymczasowy numer PIN. Aby skojarzyć Visual Studio przy użyciu nowego numeru PIN, powtórz kroki w [konfiguracji agenta zdalnego w programie Visual Studio](#ConfigureVS).  
  
##  <a name="GenerateCert"></a>Wygeneruj nowy certyfikat serwera  
 Ze względów bezpieczeństwa serwera certyfikatów tej pary Visual Studio z agentem zdalnym są również powiązane IP adres lub nazwę hosta programu Mac. Zmiana tych wartości musi wygenerować nowy certyfikat serwera, a następnie skonfigurować ponownie program Visual Studio przy użyciu nowych wartości.  
  
#### <a name="to-generate-a-new-server-certificate"></a>Aby wygenerować nowy certyfikat serwera  
  
1.  Zatrzymaj agenta vcremote.  
  
2.  Wprowadź następujące polecenie w terminalu aplikacji:  
  
     `vcremote resetServerCert`  
  
3.  Po wyświetleniu monitu o potwierdzenie, wpisz `Y`.  
  
4.  Wprowadź następujące polecenie w terminalu aplikacji:  
  
     `vcremote generateClientCert`  
  
     Generuje nowy tymczasowy numer PIN.  
  
5.  Aby skojarzyć Visual Studio przy użyciu nowego numeru PIN, powtórz kroki w [konfiguracji agenta zdalnego w programie Visual Studio](#ConfigureVS).  
  
##  <a name="ConfigureMac"></a>Konfigurowanie agenta zdalnego dla komputerów Mac  
 Można skonfigurować agenta zdalnego przy użyciu różnych opcji wiersza polecenia. Na przykład można określić port do nasłuchiwania żądań kompilacji i określ maksymalną liczbę kompilacji do zachowania w systemie plików. Domyślnie limit wynosi 10 kompilacji. Zdalnego agenta spowoduje usunięcie kompilacje, które przekraczają maksymalną podczas zamykania.  
  
#### <a name="to-configure-the-remote-agent"></a>Aby skonfigurować agenta zdalnego  
  
-   Aby wyświetlić pełną listę poleceń agenta zdalnego, w terminalu aplikacji, wpisz:  
  
     `vcremote --help`  
  
-   Aby wyłączyć tryb bezpieczny i włączyć proste połączenia oparty na protokole HTTP, wpisz:  
  
     `vcremote --secure false`  
  
     Usuń zaznaczenie tej opcji **bezpiecznego** wyboru i pozostawić **numeru Pin** puste pole podczas konfigurowania agenta w programie Visual Studio.  
  
-   Aby określić lokalizację dla plików agenta zdalnego, wpisz:  
  
     `vcremote --serverDir directory_path`  
  
     gdzie *directory_path* znajduje się na komputerze Mac, aby umieścić pliki dziennika, kompilacji i certyfikaty serwera. Domyślnie ta lokalizacja jest /Users/*username*/vcremote. Kompilacje są zorganizowane według numeru kompilacji w tej lokalizacji.  
  
-   Na potrzeby przechwytywania przez proces w tle `stdout` i `stderr` w pliku o nazwie server.log, wprowadź:  
  
     `vcremote > server.log 2>&1 &`  
  
     Plik server.log może pomóc w rozwiązywaniu problemów kompilacji.  
  
-   Aby uruchomić agenta przy użyciu pliku konfiguracji zamiast parametry wiersza polecenia, wpisz:  
  
     `vcremote --config config_file_path`  
  
     gdzie *config_file_path* to ścieżka do pliku konfiguracji w formacie JSON. Opcje uruchamiania i ich wartości nie może zawierać kreski.  
  
## <a name="see-also"></a>Zobacz też  
 [Instalowanie języka Visual C++ dla opracowywania aplikacji mobilnych na wiele platform](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)