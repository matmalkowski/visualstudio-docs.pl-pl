---
title: Uruchamianie aplikacji platformy uniwersalnej systemu Windows i Windows 8.1 w symulatorze | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
caps.latest.revision: "42"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: d4a64f9463650941fe8d645a1a6b92376277f0b6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="run-uwp-and-windows-81-apps-in-the-simulator"></a>Uruchamianie aplikacji platformy uniwersalnej systemu Windows i Windows 8.1 w symulatorze
Symulator Visual Studio dla aplikacji platformy uniwersalnej systemu Windows i Windows 8.1 jest aplikacją, która symuluje aplikacji platformy uniwersalnej systemu Windows lub Windows 8.1. Można uruchomić aplikacji wybierz rozmiar ekranu fizycznego i rozwiązania, który ma zostać emulować. Można również Symulowanie zdarzeń obrotu i touch typowe i symulować właściwości połączenia sieciowego.
  
 Symulator udostępnia środowisko, w którym można projektować, rozwijać, debugowania i testowania aplikacji platformy uniwersalnej systemu Windows. Jednak przed opublikowaniem aplikacji Microsoft Store, należy przetestować aplikację na rzeczywistego urządzenia.  
  
 Symulator Visual Studio dla aplikacji platformy uniwersalnej systemu Windows nie działa w izolowanym środowisku na komputerze lokalnym. W związku z tym błędów występujących w symulatorze, takich jak nieodwracalny błąd systemowe, również może mieć wpływ na cały komputer.  
  
 Zobacz [aplikacji Windows Phone uruchamianie w emulatorze](../debugger/run-windows-phone-apps-in-the-emulator.md) informacji Windows Phone.  
  
> [!IMPORTANT]
>  Symulator programu Visual Studio 2015 nie zawiera przycisk używanie funkcji geolokalizacji. Jest to spowodowane symulator systemu Windows 10 nie obejmuje używanie funkcji geolokalizacji symulacji. Jeśli należy wykonać tego rodzaju symulacji, można użyć symulatora programu Visual Studio 2013 na Windows 8.1 lub starszymi systemami operacyjnymi.  
  
##  <a name="BKMK_Set_the_simulator_as_the_target"></a>Ustaw symulator jako element docelowy  
 Uruchamianie aplikacji platformy uniwersalnej systemu Windows w symulatorze, wybierz **symulatora** z listy rozwijanej obok pozycji listy **Rozpocznij debugowanie** przycisk debugera **standardowe** paska narzędzi.  
  
 ![Działających w symulatorze](../debugger/media/vsrun_f5_simulator.png "VSRUN_F5_Simulator")  
  
##  <a name="BKMK_Choose_an_interaction_mode"></a>Wybierz tryb interakcji  
 Można wybrać następujące tryby interakcji  
  
-   ![Tryb myszy](../debugger/media/simulator_mousemodebtn.png "SIMULATOR_MouseModeBtn") tryb myszy: ustawia gesty myszy trybu interakcji. Gesty myszy obejmują kliknięć, dwukrotne kliknięcia i drags.  
  
-   ![Przycisk emulacji dotykowej Start](../debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") uruchamiania emulacji dotykowej: ustawia touch gestów pojedynczego palca trybu interakcji. Palca pojedynczego zdarzenia zawierają naciśnięcie, przeciągając i szybko przesuwając.  
  
     ![Symulator jednym palcem docelowej](../debugger/media/simulator_onefinger.png "SIMULATOR_OneFinger") ikona pojedynczym elementem docelowym wskazuje lokalizację zdarzeń w symulatorze. Umieść wskaźnik za pomocą myszy.  
  
     ![Docelowy touch jednym palcem](../debugger/media/simulator_onefingerengaged.png "SIMULATOR_OneFingerEngaged") naciśnij przycisk lewy przycisk myszy, aby aktywować tryb dotykowy. Na przykład kliknij przycisk, aby symulować tap, lub naciśnij i przytrzymaj klawisz przycisku, przeciągnij lub szybko przesuń.  
  
## <a name="pinch-and-zoom"></a>Ściśnięcie i powiększenia  
 Ustawia tryb interakcji ściśnięcie i gestów dwoma palcami powiększenia.  
  
-   ![Docelowy palca Siimulator dwa](../debugger/media/simulator_twofinger.png "SIMULATOR_TwoFinger")  
  
     Ikona podwójne docelowy wskazuje lokalizację dwoma palcami na ekranie urządzenia.  
  
    -   Przesuń wskaźnik myszy, aby umieścić ikony za pośrednictwem obiektu na ekranie urządzenia.  
  
    -   Obróć kółka myszy wstecz lub do przodu, aby zmienić symulowane odległość między dwoma palcami przed ściśnięcie lub powiększenia.  
  
-   -   ![Ściśnięcie, powiększania i obracania elementów docelowych](../debugger/media/simulator_twofingerengaged.png "SIMULATOR_TwoFingerEngaged")  
  
         Naciśnij przycisk w lewo i Obróć koło z poprzednimi wersjami (w stronę możesz) aby powiększyć (uszczypnięcia).  
  
    -   Naciśnij przycisk po lewej stronie i Obróć kółka myszy do przodu (od siebie), aby pomniejszyć (Powiększenie).  
  
## <a name="object-rotation"></a>Obrót obiektu  
 **Obróć emulacji dotykowej** przycisk ustawia obrotu gesty, przy użyciu dwoma palcami trybu interakcji.  
  
-   -   Przesuń wskaźnik myszy, aby umieścić ikony za pośrednictwem obiektu na ekranie urządzenia.  
  
    -   Obróć kółka myszy wstecz lub do przodu Zmień orientację symulowane dwoma palcami przed obrócić obiekt.  
  
-   -   Naciśnij przycisk po lewej stronie i Obróć koło z poprzednimi wersjami (w stronę możesz) obracania obiektu przeciwnie do ruchu wskazówek zegara. Obróć koło myszy jedną z ikon dwóch docelowy obraca wokół innych względnych rozmiaru obrót.  
  
    -   Naciśnij przycisk po lewej stronie i Obróć kółka myszy do przodu (od siebie) do obracania obiektu do ruchu wskazówek zegara.  
  
##  <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a>Włącz lub wyłącz zawsze w trybie top  
 Możesz ustawić okno symulator, aby być zawsze na wierzchu. **Przełącznika znajdujących się na górze okna** przycisk Włącza lub wyłącza **zawsze na wierzchu** tryb okna symulatora.  
  
##  <a name="BKMK_Change_the_device_orientation"></a>Zmiana orientacji urządzenia  
 Możesz przełączyć orientacji urządzenia pomiędzy pionowy i poziomej przez obrócenie symulatora 90 stopni w dowolnym kierunku.  
  
> [!NOTE]
>  Symulator nie przestrzega [DisplayProperties.AutoRotationPreferences](http://go.microsoft.com/fwlink/?LinkId=249460) właściwości projektu. Na przykład, jeśli projekt Ustawia orientację na `Landscape`i następnie Obróć symulator w orientacji pionowej, symulator wyświetlany obraz zostanie również obracać i zmiany rozmiaru. Przetestuj te ustawienia na rzeczywistego urządzenia.  
  
> [!NOTE]
>  Jeśli tak, aby krawędź symulator jest większy niż jest wyświetlany na ekranie obracania symulatorze, symulator jest automatycznie dopasowane do ekranu. Symulator nie zmieni się rozmiar oryginalny rozmiar obrócenie go ponownie.  
  
##  <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a>Zmiana rozmiaru ekranu symulowane i rozwiązania  
 Aby zmienić rozmiar symulowane ekranu i rozpoznawania, wybierz **zmienić rozpoznawania** znajdującego się na palecie i wybierz z listy nowy rozmiar i rozdzielczość.  
  
 Rozmiar ekranu i rozwiązania, które są wyświetlane jako *cali szerokości ekranu, pikseli szerokość i wysokość pikseli*. Uwaga symulowane zarówno do rozmiaru ekranu i rozdzielczości. Współrzędne lokalizacji w symulatorze są tłumaczone na współrzędne rozmiaru wybranego urządzenia i rozwiązywania.  
  
> [!NOTE]
>  Wersje skalowanie obrazów rastrowych można zapisać w aplikacji i systemu Windows załadowanie prawidłowy obraz dla bieżącej skali. Aby uzyskać więcej informacji, zobacz [wprowadzenie projektu i interfejsu użytkownika](/windows/uwp/layout/design-and-ui-intro). Jednak, że system Windows wybiera inny obraz, aby dopasować rozdzielczość w przypadku zmiany rozpoznawania symulator, należy zatrzymać i uruchomić ponownie sesję debugowania, aby wyświetlić nowy obraz.  
  
##  <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a>Przechwyć zrzut ekranu aplikacji do przesłania do Microsoft Store  
 Podczas przesyłania aplikacji Microsoft Store należy dołączyć zrzuty ekranu aplikacji.  
  
> [!NOTE]
>  Zrzut ekranu jest zapisywany w bieżącym rozdzielczości symulatora. Aby zmienić rozwiązanie, wybierz **zmienić rozpoznawania** przycisku.  
  
-   Aby utworzyć zrzuty ekranu aplikacji w symulatorze, wybierz **Przechwyć zrzut ekranu do Schowka** przycisku.  
  
-   Aby ustawić lokalizacji, gdzie znajdują się zrzuty ekranu, wybierz **ustawienia zrzut ekranu** przycisk i wybierz lokalizację, w menu skrótów.  
  
     ![Menu kontekstowe ustawienia zrzut ekranu](../debugger/media/simulator_screenshotsettingscntxmnu.png "SIMULATOR_ScreenShotSettingsCntxMnu")  
  
##  <a name="BKMK_Simulate_network_connection_properties"></a>Symulowanie właściwości połączenia sieciowego  
 Można ułatwić użytkownikom aplikacji, zarządzania kosztami połączeniach sieci taryfowych utrzymując pogłębianie wiedzy na temat połączenia koszt lub dane planu stanu zmiany w sieci i włączanie aplikacji dzięki tym informacjom można uniknąć ponoszenia dodatkowych kosztów dla mobilnych lub przekroczenie limit transferu określone dane. [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity) interfejsów API pozwala odpowiedzieć [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) i [TriggerType](/uwp/api/windows.applicationmodel.background.systemtrigger) zdarzenia, które logują. Zobacz [Szybki Start: Zarządzanie sieci taryfowej koszt ograniczenia](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
 Debugowanie lub testowanie kodu z uwzględnieniem kosztów sieci, symulator może naśladować właściwości sieci, które są dostępne za pośrednictwem [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) obiektu zwróconego przez [GetInternetConnectionProfile](/uwp/api/windows.networking.connectivity.networkinformation).
  
 Do symulacji sieci: właściwości:  
  
1.  Na pasku narzędzi symulatora wybierz **Zmień właściwości sieci** przycisku.  
  
2.  Na **ustawić właściwości sieci** okno dialogowe, wybierz opcję **Użyj symulowane właściwości sieci**.  
  
     Wyczyść pole wyboru, aby usunąć symulacji i wróć do właściwości sieci aktualnie połączonych interfejsu.  
  
3.  Wprowadź **nazwa profilu** do symulowanej sieci. Firma Microsoft zaleca używanie unikatową nazwę, która służy do identyfikowania symulacji w [ProfileName](/uwp/api/windows.networking.connectivity.connectionprofile) właściwość [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) obiektu.  
  
4.  Wybierz [NetworkCostType](/uwp/api/windows.networking.connectivity.networkcosttype) wartość dla profilu z **typu kosztu sieci** listy.  
  
5.  Z **Flaga statusu limitu danych** listy, możesz ustawić [ApproachingDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) właściwości lub [OverDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) właściwości na wartość true, lub możesz wybrać  **W obszarze danych Limit** można ustawić obie wartości FALSE.  
  
6.  Z **Roaming stanu** listy, ustaw [mobilny](/uwp/api/windows.networking.connectivity.connectioncost) właściwości.  
  
7.  Wybierz **Ustaw właściwości** do symulacji sieci: właściwości wyzwalając planu [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) zdarzeń i tło [SystemTrigger](/uwp/api/windows.applicationmodel.background.systemtrigger) typu  **NetworkStateChange**.  
  
 **Więcej informacji na temat zarządzania połączeniami sieciowymi**  
  
 [Szybki Start: Zarządzanie naliczane ograniczeń koszt sieci](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
 [Przykładowe informacje o sieci](http://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
 [Analiza zużycia energii](../profiling/analyze-energy-use-in-store-apps.md)  
  
 [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity)  
  
 [Odpowiadanie na zdarzenia systemowe z zadaniami w tle](http://msdn.microsoft.com/en-us/f7c86e86-a7ae-4abb-a923-76b03337a80a)  
  
 [Porady: wyzwalanie wstrzymania, wznowienia i zdarzeń w tle w aplikacjach platformy UWP](http://msdn.microsoft.com/library/windows/apps/hh974425.aspx)  
  
##  <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a>Przejdź symulatora za pomocą klawiatury  
 Symulator narzędzi można przechodzić przez naciśnięcie przycisku **klawisze CTRL + ALT + Strzałka w górę** Aby przełączyć fokus w oknie symulatora do narzędzi symulatora. Użyj **Strzałka w górę** i **Strzałka w dół** można przenieść między przyciskami paska narzędzi.  
  
 Symulator można zamknąć, naciskając klawisz **CTRL + ALT + F4**.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchamianie aplikacji w programie Visual Studio](../debugger/run-store-apps-from-visual-studio.md)