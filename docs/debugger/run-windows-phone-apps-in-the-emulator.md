---
title: Uruchamianie aplikacji Windows Phone 8.1 w emulatorze | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 07/18/2017
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
ms.assetid: c7590788-beb3-403c-a7dd-18472a9e585e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fc458bddfe354f43afd15176d0283cad4875234d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="run-windows-phone-81-apps-in-the-emulator"></a>Uruchamianie aplikacji Windows Phone 8.1 w emulatorze
Emulator Windows Phone zawiera środowisku wirtualnym, w którym można debugowania i testowania aplikacji Windows Phone na komputerze bez urządzenia fizycznego. Można Symulowanie zdarzeń obrotu i touch typowe i wybierz rozmiar ekranu fizycznego i rozwiązania, który ma zostać emulować. Może także przetestować wiele często używane funkcje, takie jak lokalizacja, sieci, powiadomienia, czujników, przyspieszeniomierza i opcjonalne karty SD.  

Aby uzyskać informacje dotyczące uruchamiania systemu Windows 10 Mobile w emulatorze, zobacz [testu w emulatorze Microsoft](/windows/uwp/debug-test-perf/test-with-the-emulator).
  
Aby uzyskać więcej informacji o funkcjach, które można sprawdzić w emulatorze systemu Windows Phone 8.1, zobacz [przetestować funkcje aplikacji w emulatorze Windows Phone](http://msdn.microsoft.com/en-us/c1b2b0ec-b8cc-4a98-84c1-701428e45cb1).  
  
Wraz z programu Visual Studio emulator zapewnia pełne środowisko, w którym można projektować, rozwijać, debugowania i testowania aplikacji Windows Phone.  
  
##  <a name="BKMK_run"></a>Uruchamianie aplikacji Windows Phone w emulatorze  
 Gdy tworzony jest aplikacji Windows Phone, możesz użyć emulatora Windows Phone do wdrożenia i przetestowania aplikacji szybko. Zaleca się przetestowanie aplikacji na rzeczywistego urządzenia Windows Phone, jednak przed opublikowaniem aplikacji w Sklepie Windows Phone. Dzięki temu można mają aplikacji, ponieważ użytkownicy mogą mieć go.  
  
 Po uruchomieniu aplikacji Windows Phone po raz pierwszy w Emulator Windows Phone, wykonywane są następujące zdarzenia:  
  
1.  Zostanie uruchomiony emulator.  
  
2.  Emulator ładuje system operacyjny Windows Phone.  
  
3.  Emulator Wyświetla ekranie Start systemu Windows Phone.  
  
4.  Aplikacja jest wdrażana na emulator.  
  
5.  Uruchamia aplikację w emulatorze.  
  
 Jeśli wybrany emulatora jest już uruchomiona, aplikacji jest wdrożony i uruchomić w działającego emulatora. W momencie można uruchomić tylko jedno wystąpienie każdego emulatora.  
  
> [!TIP]
>  Podczas testowania aplikacji na emulatorze, pozostaw emulator otwarte między debugowania sesji, więc można szybko ponownie uruchom aplikację.  
  
###  <a name="BKMK_vs"></a>Uruchamianie aplikacji w programie Visual Studio  
  
##### <a name="to-deploy-and-run-an-app-from-visual-studio"></a>Wdrażanie i uruchamianie aplikacji w programie Visual Studio  
  
1.  W programie Visual Studio Otwórz projekt Windows Phone.  
  
2.  Na **standardowe** narzędzi, wybierz jedną z opcji emulatora.  
  
     ![Listy obrazów systemu Windows Phone Emulator](../debugger/media/wp_emulator_list.png "WP_Emulator_list")  
  
3.  Wdrażanie i uruchamianie aplikacji z debugowaniem, na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**, lub naciśnij klawisz F5.  
  
     Wdrażanie i uruchamianie aplikacji bez debugowania, na **debugowania** menu, kliknij przycisk **uruchomić bez debugowania**, lub naciśnij klawisze Ctrl + F5.  
  
     Aplikacja jest wdrożona i uruchomić.  
  
     Do wdrożenia aplikacji bez konieczności uruchamiania, na **kompilacji** menu, kliknij przycisk **wdrożyć rozwiązanie**.  
  
##### <a name="to-stop-a-running-app"></a>Aby zatrzymać uruchomionej aplikacji  
  
-   Aby zatrzymać uruchomionej aplikacji, wykonaj jedną z następujących czynności:  
  
    -   W programie Visual Studio na **debugowania** menu, kliknij przycisk **Zatrzymaj debugowanie**, lub naciśnij klawisze Shift + F5.  
  
    -   W emulatorze, naciśnij klawisz **ponownie** przycisk, aby zakończyć działanie aplikacji. Jeśli aktywnej strony aplikacji nie było strony początkowej aplikacji, może być konieczne naciśnięcie **ponownie** przycisk więcej niż raz.  
  
     Umożliwia zamknięcie aplikacji i uruchomienia, pojawi się ekran. To kończy się w bieżącej sesji debugowania.  
  
##### <a name="to-restart-an-app-without-debugging"></a>Aby ponownie uruchomić aplikację bez debugowania  
  
1.  W emulatorze na ekranie startowym przejdź od lewej do wyświetlenia na liście aplikacji.  
  
2.  Na liście aplikacji naciśnij ikonę aplikacji. Aplikacja ponowne uruchomienie bez debugowania.  
  
##### <a name="to-deactivate-a-running-app"></a>Aby zdezaktywować uruchomionej aplikacji  
  
1.  Przed uruchomieniem aplikacji w programie Visual Studio, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, a następnie wybierz **właściwości** otworzyć **projektanta projektu**.  
  
2.  W **projektanta projektu**na **debugowania** zostaw **reliktu po dezaktywacji podczas debugowania** zaznacz pole niezaznaczone aplikacji, aby przejść do nieaktywni Jeśli dezaktywowane. Zaznacz pole wyboru, jeśli ma być replikacji, gdy dezaktywowana aplikacji.  
  
3.  Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**, lub naciśnij klawisz F5, aby uruchomić aplikację.  
  
4.  W emulatorze, naciśnij klawisz **Start** przycisku. Zostanie wyświetlony ekran Start i aplikacja jest dezaktywowana. Aplikacja albo przechodzi w stan nieaktywni lub jest ona replikacji, w zależności od ustawienia **reliktu po dezaktywacji podczas debugowania** pole wyboru.  
  
##### <a name="to-reactivate-a-dormant-or-tombstoned-app"></a>Aby ponownie uaktywnić nieaktywni lub replikacji aplikacji  
  
-   W emulatorze, naciśnij klawisz **ponownie** przycisk, aby powrócić do aplikacji. Jeśli przejście do innych stron lub otworzyć innej aplikacji, może być konieczne naciśnięcie **ponownie** przycisk więcej niż raz, aby ponownie uaktywnić aplikacji.  
  
     Wznawia sesję debugowania. Jeśli debuger został odłączony od aplikacji, może być konieczne naciśnij klawisz F5, aby wznowić sesji debugowania.  
  
###  <a name="BKMK_depltool"></a>Uruchom aplikację za pomocą narzędzia wdrażania aplikacji  
 Można także użyć narzędzia wdrażania aplikacji Windows Phone (**AppDeploy.exe**) do uruchamiania aplikacji w emulatorze. Narzędzie to jest autonomicznym aplikacji, który jest instalowany podczas instalowania narzędzi do tworzenia Windows Phone.  
  
 Aby uzyskać więcej informacji, zobacz [wdrażanie Windows Phone 8.1 aplikacji za pomocą narzędzia Application Deployment](http://msdn.microsoft.com/Library/23700f82-1399-44d9-bc0c-714be4a48ee6).  
  
##  <a name="BKMK_toolbar"></a>Konfigurowanie emulator Windows Phone przy użyciu narzędzi emulatora  
 W poniższej tabeli zamieszczono konfiguracji przycisków dostępnych na pasku narzędzi emulatora.  
  
|Przyciski paska narzędzi|Opcje konfiguracji|  
|---------------------|---------------------------|  
|![Wprowadź opcje na pasku narzędzi systemu Windows Phone Emulator](../debugger/media/wp_emulator_.png "WP_Emulator_")|**Skonfiguruj punkt jednego lub wielu danych wejściowych**<br /><br /> Po włączeniu punktu wielu danych wejściowych, kliknąć prawym przyciskiem myszy, aby przenieść punktów touch bez dotykania ekranu. Następnie można lewym do przeniesienia oba punkty touch jednocześnie.|  
|![Orientacja na pasku narzędzi systemu Windows Phone Emulator](../debugger/media/wp_emulator_rotation.png "WP_Emulator_rotation")|**Skonfiguruj orientację emulatora**<br /><br /> Orientacja w Emulator Windows Phone można zmienić do jednej z trzech orientacje: pionowa, pozioma po lewej lub prawej pozioma. Rozmiar emulatora nie ulega zmianie, gdy zmiana orientacji.<br /><br /> Aby zmienić orientację, kliknij przycisk **Obróć w lewo** przycisk lub **Obróć w prawo** przycisku.|  
|![Rozmiar opcji paska narzędzi systemu Windows Phone Emulator](../debugger/media/wp_emulator_size.png "WP_Emulator_size")|**Skonfiguruj rozmiar emulatora**<br /><br /> Można zmienić rozmiar emulatora na ekranie komputera hosta. Punkty na cal (DPI) dla emulatora jest oparta na monitor hosta DPI, niezależnie od wartości powiększenia.<br /><br /> -Aby dopasować emulatora do ekranu, kliknij przycisk **Dopasuj do ekranu** przycisku.<br />— Aby zmienić ustawienie powiększenia, kliknij przycisk **powiększenie** przycisku. **Powiększenie** zostanie otwarte okno dialogowe. W **powiększenie** okna dialogowego wprowadź wartość powiększenia między 33 i 100.|  
  
##  <a name="BKMK_buttons"></a>Użyj przycisków symulowane sprzętu w emulatorze  
 Symulowanie przyciski regulacji sprzętu phone za pomocą przycisków symulowane sprzętu po prawej stronie ekranu emulatora.  
  
-   Kliknij przycisk **zasilania** przycisk, aby symulować i Włącz Włączanie wyświetlania. Kliknij i przytrzymaj, aby symulować wyłączenie przez telefon.  
  
-   Kliknij przycisk **woluminu się** lub **woluminu w dół** przycisk, aby symulować zmiana wielkości prelegenta telefonu do połączeń telefonicznych i powiadomień.  
  
-   **Aparatu** przycisk uruchamia aplikację aparatu. Można symulować, biorąc zdjęcie lub wideo za pomocą formantów w aplikacji aparatu.  
  
 Poniższy zrzut ekranu przedstawia przycisków symulowane sprzętu.  
  
1.  Obraz po lewej stronie wyświetla ekranu startowego w emulatorze.  
  
2.  Obraz środkowy przedstawia emulator po naciśnięcie **zasilania** przycisk, aby wyłączyć wyświetlania.  
  
3.  Prawy obraz wyświetla ekran emulatora po naciśnięcie **woluminu się** przycisk, aby zwiększyć wolumin.  
  
 ![Przyciski emulatora Windows Phone](../debugger/media/wp_emulator_buttons.png "WP_Emulator_buttons")  
  
##  <a name="BKMK_tasks_kbd"></a>Używanie klawiatury komputera w emulatorze  
 Emulator obsługuje mapowania klawiatury sprzętu na komputerze deweloperskim do klawiatury na Windows Phone. Zachowanie kluczy jest taki sam jak na urządzeniu Windows Phone.  
  
 Domyślnie klawiatury sprzętu nie jest włączona. Ta implementacja jest odpowiednikiem przesuwanego klawiatury, należy wdrożyć przed jego użyciem. Przed włączeniem klawiatury sprzętu emulator przyjmuje klucza tylko z kluczami kontroli.  
  
 Znaki specjalne na klawiaturze zlokalizowanej wersji komputerze dewelopera systemu Windows nie są obsługiwane przez emulator. Aby wprowadzić znaki specjalne, które znajdują się na zlokalizowanej klawiatury, użyj panelu wprowadzania oprogramowania (SIP).  
  
 Aby używać klawiatury komputera w emulatorze, naciśnij klawisz PAGE UP klucz lub klucz PAUSE/BREAK (emulatora systemu Windows 8/8.1) lub F4 (emulatora systemu Windows 10).  
  
 Aby zatrzymać przy użyciu klawiatury komputera w emulatorze, naciśnij klawisz PAGE DOWN klucz lub klucz PAUSE/BREAK (emulatora systemu Windows 8/8.1) lub F4 (emulatora systemu Windows 10).  
  
 W poniższej tabeli wymieniono klucze na klawiaturze sprzętu służącego do emulacji przycisków i innych kontrolek na Windows Phone.  
  
|Klucz sprzętu komputera|Przycisk sprzętu Windows Phone|Uwagi|  
|---------------------------|-----------------------------------|-----------|  
|F1|WSTECZ|Długie naciśnięcie działać zgodnie z oczekiwaniami.|  
|F2|POCZĄTEK|Długie naciśnięcie działać zgodnie z oczekiwaniami.|  
|F3|WYSZUKIWANIE||  
|F4|Przełączanie się między przy użyciu klawiatury komputera lokalnego, a nie przy użyciu klawiatury komputera lokalnego w emulatorze systemu Windows 10.|Nie dotyczy w emulatorze systemu Windows 8/8.1.|  
|F5|Nie dotyczy.||  
|F6|APARAT FOTOGRAFICZNY POŁOWA|Przycisk dedykowanego aparatu, który zostanie naciśnięty połowie.|  
|F7|PEŁNY APARAT FOTOGRAFICZNY|Przycisk dedykowanego aparatu.|  
|F8|Nie dotyczy.||  
|F9|WOLUMIN W GÓRĘ||  
|F10|WOLUMIN W DÓŁ||  
|F11|Nie dotyczy.||  
|F12|ZASILANIA|Naciśnij klawisz F12 dwa razy, aby włączyć ekranu blokady.<br /><br /> Długie naciśnięcie działać zgodnie z oczekiwaniami.|  
|ESC|WSTECZ|Długie naciśnięcie działać zgodnie z oczekiwaniami.|  
|WSTRZYMAJ/PODZIAŁU|Przełącz klawiaturę (tylko w emulatorze systemu windows 8/8.1).|Nie dotyczy emulatora systemu Windows 10.|  
|STRONA W GÓRĘ|Umożliwia klawiaturze sprzętu (tylko w emulatorze systemu Windows 8/8.1).|Nie dotyczy emulatora systemu Windows 10.|  
|PAGE DOWN|Wyłącza klawiatury sprzętu (tylko w emulatorze systemu Windows 8/8.1).|Nie dotyczy emulatora systemu Windows 10.|  
  
##  <a name="BKMK_checkpoints"></a>Zapisz i załadować niestandardowe punkty kontrolne  
 Zapisz migawkę stanu emulatora przy użyciu **punktów kontrolnych** kartę emulatora **dodatkowe narzędzia**. Ta funkcja jest przydatna, jeśli często testowanie aplikacji za pomocą tych samych danych i ustawień.  
  
 Na przykład jeśli aplikacja wymaga kilku kontaktów, można utworzyć rekordy kontaktów jeden raz i Zapisz migawkę emulatora. W przeciwnym razie należy ponownie utworzyć rekordy kontaktów podczas uruchamiania emulatora.  
  
-   Kliknij przycisk **nowego punktu kontrolnego** do przechwytywania nową migawkę stanu emulatora przy użyciu danych i ustawień wymaganych do testowania aplikacji ponownie później. Nowy punkt kontrolny jest dodawany do **punktów kontrolnych** listy.  
  
     Nie można przechwycić punkt kontrolny, gdy debuger jest dołączony do emulatora.  
  
-   Wybierz punkt kontrolny w **punktów kontrolnych** listy, aby wyświetlić informacje dotyczące punktu kontrolnego.  
  
-   Zaznacz przycisk radiowy w **domyślne** kolumnę, aby wyświetlić zapisane punktu kontrolnego domyślnego punktu kontrolnego dla active emulatora.  
  
-   Kliknij przycisk **przywrócić** Aby ponownie uruchomić system operacyjny Windows Phone emulator i załadować zaznaczona migawka.  
  
-   Kliknij przycisk **usunąć** usunąć migawki, które nie są już potrzebne.  
  
 Oryginalny obraz emulatora zawsze jest wyświetlany jako pierwszy element **punktów kontrolnych** listy i nie można zmienić ani usunąć. Jednak można wybrać innej migawki jako domyślny obraz emulatora.  
  
 ![Karta punktów kontrolnych emulatora Windows Phone](../debugger/media/wp_emulator_checkpoints.png "WP_Emulator_checkpoints")  
  
##  <a name="BKMK_tasks_shot"></a>Przechwyć zrzuty ekranu w emulatorze  
 Zrzuty ekranu aplikacji Windows Phone można utworzyć za pomocą narzędzia zrzut ekranu z dodatkowych narzędzi okna. Narzędzie tworzy pliki PNG, zgodne rozpoznanie działającego emulatora.  
  
 ![Zrzuty ekranu z Windows Phone Emulator](../debugger/media/wp_emulator_screenshots.png "WP_Emulator_screenshots")  
  
#### <a name="to-create-an-app-screenshot-by-using-the-built-in-emulator-screenshot-tool"></a>Aby utworzyć zrzut ekranu aplikacji przy użyciu emulatora wbudowane narzędzie zrzut ekranu  
  
1.  Aby zoptymalizować jakość Twojej zrzuty ekranu, ustawić poziom powiększenia emulatora do 100 procent. Im większa możesz ustawić poziom powiększenia, tym lepiej jakość zrzut ekranu.  
  
2.  Uruchom aplikację w emulatorze.  
  
3.  Na pasku narzędzi emulatora, kliknij przycisk Rozwiń, aby otworzyć **dodatkowe narzędzia** okna.  
  
4.  Kliknij przycisk **zrzut ekranu** kartę.  
  
5.  Gdy aplikacja jest gotowa, kliknij przycisk **przechwytywania** przycisku.  
  
     Zrzut ekranu zostanie wyświetlony w obszarze roboczym.  
  
6.  Kliknij przycisk **zapisać** przycisk, aby otworzyć **Zapisz jako** okno dialogowe.  
  
7.  Wybierz lokalizację i **nazwę pliku** , a następnie kliknij przycisk **zapisać**.  
  
8.  Opcjonalnie przejdź do innych stron w aplikacji i przechwycenia dodatkowych zrzuty ekranu.  
  
9. Uruchom emulator z różnych rozdzielczości do przechwytywania tego samego zrzuty ekranu w różnych rozdzielczości. W przypadku uruchomienia aplikacji z debugowaniem, musisz zatrzymać debugowanie, aby uruchomić ją ponownie na innym emulatora.  
  
 Wyłącz liczniki szybkości klatek na ekranie emulatora, przed przechwyceniem zrzuty ekranu, które zostaną przesłane do Sklepu Windows Phone.  
  
#### <a name="to-disable-frame-rate-counters-in-the-emulator-before-capturing-screenshots"></a>Aby wyłączyć liczniki szybkości klatek w emulatorze przed przechwyceniem zrzuty ekranu  
  
-   Określ kompilacji wydania programu Visual Studio. Po określeniu kompilacji wydania, uruchom aplikację wybierając **Wdróż *[Nazwa aplikacji]***  łącze **kompilacji** menu.  
  
-   Alternatywnie komentarz wiersz kodu w pliku app.xaml.cs lub app.xaml.vb i ustawia wartość `EnableFrameRateCounter` do `true`.