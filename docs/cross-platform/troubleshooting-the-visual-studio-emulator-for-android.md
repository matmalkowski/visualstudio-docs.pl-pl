---
title: Rozwiązywanie problemów z programu Visual Studio Emulator for Android | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3fb5df4-3aae-40e4-9450-bbe15b0c5af5
caps.latest.revision: ''
author: mgmclemore
ms.author: mamcle
manager: crdun
ms.workload:
- multiple
ms.openlocfilehash: 7d333295461617eb8a85f0970bc82e33f5a2ec68
ms.sourcegitcommit: fb1fede41d8c5e459dd222755b0497b9d361bc51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="troubleshooting-the-visual-studio-emulator-for-android"></a>Rozwiązywanie problemów z emulatorem programu Visual Studio dla systemu Android
Ten temat zawiera informacje ułatwiające rozwiązywanie problemów, które mogą wystąpić podczas korzystania z programu Visual Studio Emulator for Android.  
  
> [!WARNING]
>  Po zainstalowaniu emulatora, program instalacyjny sprawdza wymagania wstępne dotyczące uruchamiania oprogramowania. Wyświetla ostrzeżenia, jeśli wymagania wstępne nie są dostępne, ale nie jest wymagane ich instalacji.  
  
 Ten temat zawiera następujące sekcje.  
  
-   [Przed rozpoczęciem](#BeforeYouStart)  
  
-   [Emulator niepowodzeniu instalacji](#NoInstall)  
  
-   [Nie można nawiązać połączenia z miejsc docelowych sieci w domenie lub sieci firmowej](#DomainNetwork)  
  
-   [Nie można połączyć się sieci miejsc docelowych, jeśli ustawienia sieciowe wymagają ręcznej konfiguracji](#ManualNetworkConfig)  
  
-   [Emulator uruchamia się powoli, kończy się niepowodzeniem, aby uruchomić ze względu na przekroczenie limitu czasu lub wdrożenia aplikacji nie powiedzie się.](#SlowStart)  
  
-   [Emulator nie powiedzie się](#NoStart2)  
  
-   [Emulator nie powiedzie się (pierwszym użyciu)](#NoStart)  
  
-   [Komputerowi nie uda się uruchomić po zainstalowaniu emulatora](#NoBoot)  
  
-   [Visual Studio zablokowała próba wdrożenia aplikacji na emulatorze lub emulatora nie jest wyświetlany jako cel debugowania w innych IDEs](#ADB)  
  
-   [Emulator zawiesza się, ponieważ nie można skonfigurować UDP port](#XamarinPlayer)  
  
-   [Nie można dołączyć debugera do projektu Xamarin](#Skylake)  
  
-   [Emulator nie powiedzie się uruchomić aplikację, która używa usług Google Play](#GooglePlay)  
  
-   [Przeciąganie i upuszczanie plików, APK lub pliku zip oprogramowanie nie działa](#DragAndDrop)  
  
-   [Rozdzielczość zrzut ekranu jest nieprawidłowa](#Resolution)  
  
-   [Emulator nie powiedzie się do renderowania zawartości OpenGL](#OpenGL)  
  
-   [Emulator nie odpowiada na gestów dotykowych wielu](#Multitouch)  
  
-   [Zasoby pomocy technicznej](#Support)  
  
##  <a name="BeforeYouStart"></a> Przed rozpoczęciem  
 Przed rozpoczęciem rozwiązywania problemów, warto przejrzeć następujące tematy:  
  
-   [Wymagania systemowe dotyczące emulatora programu Visual Studio dla systemu Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
##  <a name="NoInstall"></a> Emulator niepowodzeniu instalacji  
 Jeśli nie masz zainstalowanych funkcji Hyper-V, następujący komunikat zostanie wyświetlony, gdy użytkownik próbuje zainstalować emulator. Na komputerze, który obsługuje funkcji Hyper-v musi mieć i musi być włączona.  
  
 ![Android&#95;Emu&#95;zainstalować&#95;problem](../cross-platform/media/android_emu_install_issue.png "Android_Emu_Install_Issue")  
  
> [!NOTE]
>  Ten komunikat ma zastosowanie zarówno do programu Visual Studio Emulator for Android i Windows Phone Emulator. Windows 8.1 i Windows 10 obsługuje emulatora.  
  
 Jeśli ten komunikat zostanie wyświetlony, sprawdź [wymagania systemowe dla programu Visual Studio Emulator for Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) aby zobaczyć, czy można uruchomić emulatora.  
  
##  <a name="DomainNetwork"></a> Nie można nawiązać połączenia z miejsc docelowych sieci w domenie lub sieci firmowej  
 Visual Studio Emulator for Android pojawia się w sieci jako osobne urządzenia z adresu IP. Nie jest przyłączony do domeny systemu Windows i nie udostępnia poświadczenia domeny lub grupy roboczej na komputerze hosta.  
  
 Jeśli sieć wymaga autoryzacji domeny lub grupy roboczej do sieci podstawowej i łączności z Internetem, skontaktuj się z administratorem IT Wystąpił wyjątek. Ten wyjątek umożliwia programowanie jako maszynę granic i do akceptowania połączeń z urządzeniami sieciowymi przyłączone do domeny, takich jak emulator.  
  
 Visual Studio Emulator for Android używa również własny zestaw adresów MAC. Jeśli nie masz dostępu do sieci lub zasobów internetowych z emulatora, skontaktuj się z administratorem IT, aby upewnić się, że adresy MAC to emulator zostały zatwierdzone w sieci.  
  
#### <a name="to-view-the-emulators-mac-addresses"></a>Aby wyświetlić MAC to emulator adresów  
  
1.  Uruchom emulator.  
  
2.  Na pasku narzędzi emulatora, kliknij przycisk (>>) można otworzyć okna dodatkowych narzędzi.  
  
3.  W oknie dodatkowe narzędzia kliknij kartę sieci.  
  
4.  Na stronie sieci Znajdź wpisy adresów fizycznych.  
  
##  <a name="ManualNetworkConfig"></a> Nie można połączyć się sieci miejsc docelowych, jeśli ustawienia sieciowe wymagają ręcznej konfiguracji  
 Do nawiązania miejsc docelowych sieci z emulatora, sieć musi spełniać następujące wymagania:  
  
-   DHCP. Emulator wymaga protokołu DHCP, ponieważ konfiguruje się jako osobne urządzenia w sieci za pomocą adresu IP.  
  
-   Automatycznie skonfigurowana DNS i ustawień bramy. Nie jest możliwe do skonfigurowania ustawień DNS i bramy ręcznie dla emulatora.  
  
 Jeśli sieć wymaga ręcznie skonfigurowane ustawienia, skontaktuj się z administratorem IT, aby ustalić, jak można włączyć łączności sieciowej dla emulatora.  
  
##  <a name="SlowStart"></a> Emulator uruchamia się powoli, kończy się niepowodzeniem, aby uruchomić ze względu na przekroczenie limitu czasu lub wdrożenia aplikacji nie powiedzie się.  
 W niektórych warunkach emulatora może zająć kilka minut, aby uruchomić lub nie została uruchomiona z powodu przekroczenia limitu czasu. Gdy emulator nie powiedzie się, zostanie wyświetlony następujący komunikat: `App deployment failed. Please try again`. Ten błąd może spowodować następujące warunki.  
  
-   Uruchomiona programu Visual Studio Emulator for Android z rozruchowego dysku VHD. Ta konfiguracja nie jest obsługiwana.  
  
-   Uszkodzony dysk twardy. Należy rozważyć uruchomienie programu chkdsk.  
  
-   Dysk twardy, który wymaga defragmentacji. Należy rozważyć defragmentacji dysku.  
  
-   Dysk twardy, który jest prawie pełna. Sprawdź ilość miejsca dostępnego miejsca na dysku.  
  
-   Za mało pamięci jest dostępne ze względu na inne uruchomione aplikacje. Zmniejsz liczbę aplikacji, które wykorzystują pamięci lub zwiększ ilość pamięci.  
  
-   Ogólnie rzecz biorąc współczynnik która wnosi wkład na pogorszenie wydajności w systemie. Rozpocznij rozwiązywanie problemów ze składnikiem ma najniższą częściowy w indeksie wydajności systemu Windows, który można znaleźć na stronie informacje o wydajności i narzędzia w Panelu sterowania.  
  
##  <a name="NoStart2"></a> Emulator nie powiedzie się  
 Jeśli emulator działał wcześniej, ale nie obsługuje teraz, przejść przez następujące zadania. Jeśli używasz emulatora po raz pierwszy, zobacz [emulatora nie powiedzie się (pierwszym użyciu)](#NoStart) przed podjęciem próby następujące kroki.  
  
-   Usuń wszystkie wystąpienia funkcji Hyper-V emulatora.  
  
    1.  Zamknij program Visual Studio.  
  
    2.  Otwórz Menedżera funkcji Hyper-V i Zatrzymaj wszystkie wystąpienia funkcji Hyper-V emulatora (maszyn wirtualnych), który jest już zainstalowany i prawdopodobnie w stanie uszkodzenia.  
  
    3.  W Menedżerze funkcji Hyper-V należy usunąć wszystkie inne emulatora maszyn wirtualnych.  
  
    4.  Ponownego rozruchu komputera.  
  
-   Upewnij się, że masz co najmniej 4 GB pamięci oraz że jego jest nie są używane przez inne programy zasobów i procesów (np. Spróbuj zamknąć wszystkie okna przeglądarki).  
  
-   W Menedżerze funkcji Hyper-V Otwórz Menedżera przełącznika wirtualnego i sprawdź, czy masz dwie przełączników sieciowych; Sprawdź, czy pierwsza z nich to przełącznik wewnętrzny i drugi jest zewnętrzny.  
  
     ![Android&#95;Emu&#95;V&#95;Switch&#95;Man](../cross-platform/media/android_emu_v_switch_man.png "Android_Emu_V_Switch_Man")  
  
     Jeśli używasz systemu Windows 10 Instalatora jest nieprawidłowa, może podjąć próbę [ponownie urządzeń sieciowych przy użyciu polecenia -d netcfg](http://windows.microsoft.com/en-us/windows-10/fix-network-connection-issues) (sekcja 6).  
  
-   Jeśli te czynności nie rozwiąże problemu, zobacz [emulatora nie powiedzie się (pierwszym użyciu)](#NoStart) uzyskać informacji o 3 oprogramowanie firm, które może zakłócać emulator.  
  
##  <a name="NoStart"></a> Emulator nie powiedzie się (pierwszym użyciu)  
 Nie można uruchomić emulatora, należy przejść przez następujące zadania, aby zidentyfikować i rozwiązać problem.  
  
-   Upewnij się, że zostały spełnione minimalne wymagania dotyczące sprzętu oraz czy ustawienia systemu BIOS są prawidłowe.  
  
     Emulator i Windows 8 funkcji Hyper-V wymaga 64-bitowego procesora z adresów drugiego poziomu tłumaczenia (SLAT). Firmy Intel potrzebne są zasadniczo i3 Core, i5 lub i7 procesora (lub jeden z wielu Xeons). Lista mikroukłady AMD jest dostępna [tutaj](http://support.amd.com/en-us).  
  
    1.  Upewnij się, że Twoje komputer spełnia [wymagania systemowe](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md).  
  
    2.  Sprawdź, czy [narzędzie SLAT](https://slatstatuscheck.codeplex.com/) zgłasza, że komputer jest w stanie SLAT.  
  
    3.  W ustawieniach systemu BIOS komputera upewnij się, czy włączono wszystkie technologii wirtualizacji. Dokładne opisy systemu BIOS mogą być różne dla każdego producenta sprzętu. Ogólnie rzecz biorąc Włącz funkcje związane z programem:  
  
        -   SLAT (drugi poziom translacji adresów)  
  
        -   Typ projektu w Przedsiębiorstwie (rozszerzone tabele stron) (Intel)  
  
        -   NPT (strona zagnieżdżone tabele) (AMD)  
  
        -   RVI (szybkie wirtualizacji indeksowania) (AMD)  
  
        -   VMX (Intel akronim wskazujący Obsługa wirtualizacji sprzętowej)  
  
        -   SVM (akronim AMD wskazujący Obsługa wirtualizacji sprzętowej)  
  
        -   XD (Wyłącz wykonywania) (Intel); musi być włączona  
  
        -   NX (nie Execute)(AMD); musi być włączony.  
  
    4.  Jeśli poniższe opcje są obecne w systemie BIOS, należy je wyłączyć.  
  
        -   Wyłącz Intel VT-d  
  
        -   Wyłącz zaufane wykonywanie  
  
         Aby uzyskać więcej informacji, zobacz ten artykuł: Technet: funkcja Hyper-V: jak do napraw BIOS błędy włączenie funkcji Hyper-V  
  
    5.  Upewnij się, że masz co najmniej 4 GB pamięci oraz że jego jest nie są używane przez inne procesy i programów zasobów.  
  
    6.  Upewnij się, systemem Windows 8 Professional lub lepszą (Windows Server 2008 nie jest obsługiwane). Windows Server 2012 jest obsługiwane, ale należy włączyć środowisko pulpitu.  
  
     Możesz sprawdzić Podgląd zdarzeń, aby zobaczyć, czy wystąpiły żadne błędy funkcji Hypervisor. Aby to zrobić, otwórz Podgląd zdarzeń (klucz Start + R, wpisz `eventvwr`), a następnie wybierz **dzienniki systemu Windows**, **systemu**. Następnie przeprowadź filtrowanie dziennika przez źródło zdarzenia ustawienie źródło **funkcji Hyper-V-funkcji Hypervisor**. Sprawdź błędy, aby zidentyfikować przyczynę.  
  
     Jeśli użytkownika spełnia procesora minimalne wymagania, ale funkcja hypervisor nadal nie działa prawidłowo, należy wziąć pod uwagę sprawdzanie, jeśli istnieje uaktualnienie systemu BIOS dla danego komputera. Jeśli istnieje, i wybierz opcję uaktualniania, należy koniecznie sprawdzić wszelkie środki ostrożności od producenta podczas uaktualniania systemu BIOS (na przykład upewnić się, uaktualnienie oprogramowania układowego BIOS nie zostało przerwane na skutek utraty zasilania, które trwale może spowodować uszkodzenie systemu BIOS).  
  
-   Upewnij się, że masz co najmniej 4 GB pamięci oraz że jego jest nie są używane przez inne procesy i programów zasobów.  
  
-   Usuń/wyłączanie sterowników firm trzecich lub oprogramowania, które może zakłócać sieci wirtualnej.  
  
     Brak niektórych znanych problemów z niektórych 3 produktów strona zainstalowane w systemie Windows 8, takie jak sterowniki/protokołów sieciowych, które nie są w pełni zgodny z stosu sieciowego funkcji Hyper-V.  
  
     Ogólnie rzecz biorąc będzie ona do tych produktów deweloperom aktualizacji oprogramowania, aby był zgodny z systemem Windows 8 i funkcji Hyper-V.  
  
     Następujące produkty mogą wymagać uaktualnienia zgodności systemu Windows 8: VirtualBox, Virtual PC 7, VMWare, niektórzy klienci sieci VPN zapór programowych niektóre wersje klientów sieci VPN firmy Cisco i innych systemów wirtualizacji. Współpraca z deweloperów oprogramowania wirtualizacji wątpliwa zachęcić ich do uaktualnienia oprogramowania, aby był zgodny z systemem Windows 8 i funkcji Hyper-V.  
  
     Jako **obejście**, możesz wyłączyć wszystkie sterowniki innych firm i aplikacji, które może zakłócać sieci wirtualnej, używany przez Emulator do komunikowania się z programem Visual Studio. Te aplikacje mogą obejmować:  
  
    -   Aplikacje antywirusowe (które przyłączanie się do stosu sieciowego)  
  
    -   Narzędzia do monitorowania sieci  
  
    -   Narzędzia rejestrowania sieci  
  
    -   Inne oprogramowanie do monitorowania systemu  
  
     Innym możliwym obejściem jest zbyt mała odinstalowaniu produktów pytanie (i żąda developer produktu do wersji zaktualizowanej wersji), ma wykonać następujące czynności.  
  
    1.  Uruchom Menedżera połączeń sieciowych (na ekranie startowym wpisz `View Network Connections` i wybrać tę opcję, aby wyświetlić połączenia sieciowe.)  
  
    2.  Dla karty vEthernet (Ethernet portu Windows Phone Emulator wewnętrznego przełącznika wewnętrznego) wybierz **właściwości** z menu kontekstowego.  
  
         ![Karta wirtualna używana w funkcji Hyper&#45;V](../cross-platform/media/android_emu_virtual_adapter.png "Android_Emu_Virtual_Adapter")  
  
         Właściwości karty są wyświetlane tutaj.  
  
         ![Właściwości karty wirtualnego](../cross-platform/media/android_emu_virtual_adapter_properties.png "Android_Emu_Virtual_Adapter_Properties")  
  
    3.  Dla tej karty tylko elementy, które należy wybrać w obszarze **to połączenie wykorzystuje następujące składniki** powinny być następujące:  
  
        -   Klient sieci Microsoft Networks  
  
        -   Harmonogram pakietów QoS  
  
        -   Udostępnianie plików i drukarek w sieciach Microsoft Networks  
  
        -   Sterownik protokołu LLDP firmy Microsoft  
  
        -   Sterownik mapowania odnajdowania topologii warstwy łącza  
  
        -   Obiekt odpowiadający odnajdywania topologii warstwy łącza  
  
        -   Protokół internetowy w wersji 6 (TCP/IPv6)  
  
        -   Protokół internetowy w wersji 4 (TCP/IPv4)  
  
    4.  Usuń zaznaczenie wszystkich innych elementów.  
  
     Wadą stosowania tej metody interfejsu jest czy kiedykolwiek nowy 3 firmy instaluje sterowniki nieobsługiwany lub zainstalowaniu emulatora za każdym razem te kroki należy powtórzyć.  
  
     Po odinstalowaniu produkty innych firm może być konieczne przywrócić przełącznika wewnętrznego Emulator Windows Phone. W tym:  
  
    -   Otwórz funkcji Hyper-V i przejdź do Menedżera przełącznika wirtualnego. Utwórz przełącznik wirtualny o nazwie "Windows Phone Emulator wewnętrznego przełącznika" i ustaw jej typ połączenia **sieci wewnętrznej**.  
  
         ![Menedżer przełącznika wirtualnego](../cross-platform/media/android_emu_virtual_switch_manager.png "Android_Emu_Virtual_Switch_Manager")  
  
     Teraz uruchom emulator. Powinien działać.  
  
##  <a name="NoBoot"></a> Komputerowi nie uda się uruchomić po zainstalowaniu emulatora  
 Ten problem może wystąpić, gdy są spełnione następujące warunki:  
  
-   Komputer ma gigabajt płyty głównej.  
  
-   USB3 jest włączona na płycie głównej.  
  
 Aby rozwiązać ten problem, wyłącz USB3 w ustawieniach systemu BIOS płyty głównej i uruchom ponownie komputer. Następnie sprawdź, czy gigabajt wydała aktualizacji systemu BIOS z płyty głównej.  
  
 Aby uzyskać więcej informacji, zobacz następujący artykuł bazy wiedzy Knowledge Base: [rozruch awarii po zakończeniu instalacji roli funkcji Hyper-V w systemach gigabajt](https://support.microsoft.com/en-us/kb/2693144).  
  
##  <a name="ADB"></a> Visual Studio zablokowała próba wdrożenia aplikacji na emulatorze lub emulatora nie jest wyświetlany jako cel debugowania w innych IDEs  
 Jeśli emulator działa, ale nie ma zostać połączona z ADB (mostka debugowania systemu Android) lub pojawia się narzędzia korzystające z ADB (na przykład Android Studio lub Eclipse) dla systemu Android, może być konieczne dostosowanie, gdy emulator szuka ADB. Emulator używa klucza rejestru do zidentyfikowania lokalizacji podstawowego zestawu SDK systemu Android i wyszukuje plik \platform-tools\adb.exe w tym katalogu. Aby zmodyfikować tę ścieżkę zestawu SDK systemu Android emulatora:  
  
-   Otwórz Edytor rejestru, wybierając **Uruchom** z menu kontekstowego przyciski Start, wpisując `regedit` w oknie dialogowym i wybierając polecenie **OK**.  
  
-   Przejdź do narzędzia zestawu SDK HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Android w drzewie folderów po lewej stronie.  
  
-   Modyfikowanie **ścieżki** zmiennej rejestru odpowiadające ścieżka do zestawu SDK systemu Android.  
  
 Ponowne uruchomienie emulatora i powinno być teraz możliwe emulator połączony ADB i skojarzone narzędzia dla systemu Android.  
  
##  <a name="XamarinPlayer"></a> Emulator zawiesza się, ponieważ nie można skonfigurować UDP port  
 Może występować ten problem z powodu niezgodności z Xamarin Player. Emulator zawieszenie lub jeśli zostanie wyświetlony ten komunikat o błędzie "nie można nawiązać połączenia z programem system operacyjny urządzenia jest to emulator: nie można skonfigurować UDP port.  Niektóre funkcje mogą być wyłączone", może występować ten problem. Wykonaj następujące kroki.  
  
1.  Odinstaluj program Xamarin Player.  
  
2.  Sprawdź, czy pole danej wirtualnej został usunięty (Xamarin Player działa na polu wirtualnego).  
  
3.  Przejdź do Menedżera urządzeń, wybierz opcję Pokaż ukryte urządzenia, a następnie usuń wszystkie elementy oprócz karty sieci fizycznej.  
  
4.  Możesz spróbować odinstalowanie/ponowne instalowanie funkcji Hyper-V po usunięciu żadnych kart sieciowych z systemem innym niż fizycznych.  
  
##  <a name="Skylake"></a> Nie można dołączyć debugera do projektu Xamarin  
 Jeśli korzystasz z systemu Windows 10 z procesorów Intel Skylake, aplikacje platformy Xamarin może zakończyć się niepowodzeniem do uruchomienia w emulatorze lub debuger programu Visual Studio nie może dołączyć do nich. Jest to spowodowane problemem z funkcją Hyper-V i Skylake procesorów. Aby uniknąć tego problemu, należy wykonać następujące kroki.  
  
1.  Otwórz Menedżera funkcji Hyper-V, a następnie wybierz maszynę Wirtualną, dla emulatora profil, który czy przy użyciu.  
  
2.  Wybierz **Usuń zapisany stan** (prawym dolnym rogu).  
  
3.  Wybierz **ustawień...**  
  
4.  Rozwiń węzeł procesora, a następnie wybierz **zgodności**.  
  
5.  Włącz **Migruj do komputera fizycznego z inną wersją procesora**.  
  
6.  Uruchom ponownie usługę (w obszarze **akcje**), a następnie spróbuj ponownie.  
  
##  <a name="GooglePlay"></a> Emulator nie powiedzie się uruchomić aplikację, która używa usług Google Play  
 Emulator nie jest dostarczany z biblioteki dla usług Google Play. Przeciągnij i upuść instalacji plików zip oprogramowanie obsługuje jednak emulator.  
  
##  <a name="DragAndDrop"></a> Przeciąganie i upuszczanie plików, APK lub pliku zip oprogramowanie nie działa  
 Emulator używa ADB.exe ułatwiające transfer plików podczas przeciągania i upuszczania pliku na ekranie. Jeśli podczas próby przeciąganie i upuszczanie plików w przypadku wystąpienia błędu, prawdopodobnie oznacza to emulatora nie jest podłączony do ADB.exe. Aby rozwiązać, wykonaj kroki opisane w [programu Visual Studio zablokowała próba wdrożenia aplikacji na emulatorze lub emulatora nie jest wyświetlany jako cel debugowania w innych IDEs](#ADB).  
  
##  <a name="Resolution"></a> Rozdzielczość zrzut ekranu jest nieprawidłowa  
 Jeśli musisz wykonać zrzut ekranu przy użyciu karty zrzut ekranu w **dodatkowych narzędzi** okno i obraz wynikowy jest nieoczekiwany rozmiar, może być konieczne dostosowanie poziom powiększenia ekranu przed wybraniem **przechwytywania**. Emulator ma zrzuty ekranu w rozdzielczości ekranu na monitorze komputera hosta.  
  
##  <a name="OpenGL"></a> Emulator nie powiedzie się do renderowania zawartości OpenGL  
 Emulator renderuje zawartość OpenGL przy użyciu komputera hosta procesora GPU i używa projektu kąt na konwertowanie tych wywołań programu DirectX. Jeśli aplikacja renderuje poprawnie na urządzeniu, ale niepoprawne w emulatorze, jest prawdopodobne, że urządzenie jest zmniejszenia nieprawidłowe wywołanie OpenGL (na przykład przy użyciu programu do cieniowania zmiennych, które nie są zgodne).  
  
##  <a name="Multitouch"></a> Emulator nie odpowiada na gestów dotykowych wielu  
 W niektórych przypadkach emulator uruchomi i nie odpowiadają wielodotyku albo za pomocą bezpośredniej interakcji z obsługą dotyku ekranu lub za pomocą narzędzia Obsługa wielodotyku na pasku narzędzi emulatora. Jeśli jest to możliwe, wybierz **Obróć** znajdującego się na pasku narzędzi emulator i spróbuj ponownie użyć wielodotyku. Jeśli problem będzie się powtarzać, przeczytaj [emulatora nie powiedzie się do renderowania zawartości OpenGL](#OpenGL) problem.  
  
##  <a name="Support"></a> Zasoby pomocy technicznej  
 Jeśli komputer-host spełnia wymagania systemowe i nie wystąpi problem omówione w tym przewodniku rozwiązywania problemów:  
  
-   Zadaj pytanie na temat używania StackOverflow [emulatora systemu android](http://stackoverflow.com/questions/tagged/android-emulator) i tagi visual studio.  
  
-   Zgłoś problem za pomocą Wyślij uśmiech narzędzia programu Visual Studio lub w Menedżerze emulatora.