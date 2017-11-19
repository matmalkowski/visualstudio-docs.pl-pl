---
title: "Sprawdź środowisku Xamarin | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd39882e-06d1-4b39-80d2-4d07b6e4f8f5
caps.latest.revision: "13"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: a770fdeae316e6ee79e919df9c9cc1b4551b90b6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="verify-your-xamarin-environment"></a>Sprawdź środowisku Xamarin
Po ukończeniu ma instalatorów (zobacz [Instalatora i zainstaluj](../cross-platform/setup-and-install.md)), spędzają na kilka minut, sprawdź, czy wszystko jest gotowe do środowisko rozwoju Xamarin.  
  
 Po wykonaniu tych weryfikacji, można wykonać jedną lub obie następujące wskazówki:  
  
-   [Dowiedz się podstawowe informacje dotyczące tworzenia aplikacji z platformy Xamarin.Forms w programie Visual Studio](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md)  
  
-   [Tworzenie aplikacji za pomocą natywnego interfejsu użytkownika za pomocą platformy Xamarin w programie Visual Studio](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)  
  
## <a name="all-platforms"></a>Wszystkie platformy  
 Najpierw wybierz **Narzędzia > Opcje**, rozwiń węzeł **Xamarin > innych**i kliknij przycisk **Sprawdź** łącza dla aktualizacji. Należy z Xamarin 4.0.3.214 lub nowszej, aby uniknąć problemów z poprzednich licencjonowania.  
  
 Następnie utwórz nowe rozwiązanie platformy Xamarin w programie Visual Studio przy użyciu **Plik > Nowy projekt**, następnie w oknie dialogowym Rozwiń **Szablony > inne języki > Visual C# > wieloplatformowych**, wybierz pozycję  **Pusta aplikacja (Native przenośne)**i kliknij przycisk OK. Spowoduje to utworzenie rozwiązania z projektu biblioteki klas przenośnych udostępnionego i poszczególnych projektów dla systemu Android, iOS i Windows:  
  
 ![Wyniki tworzenia nowego projektu z pustą aplikację &#40; Przenośna natywnego &#41; Szablon](../cross-platform/media/crossplat-xamarin-verify-1.png "CrossPlat Xamarin Sprawdź 1")  
  
> [!NOTE]
>  Jeśli szablony nie są widoczne, [szablonów projektu Xamarin Brak? Spróbuj to](#missing) u dołu tej strony.  
  
## <a name="android"></a>Android  
  
1. Sprawdź, czy masz najnowsze narzędzia zestawu SDK systemu Android zainstalowane, przechodząc do **Narzędzia > Android > Android SDK Manager** i zainstalowanie najnowszej wersji narzędzia zestawu SDK systemu Android, narzędzi platformy zestawu SDK systemu Android i narzędzi kompilacji zestawu SDK systemu Android składniki. Należy pamiętać, że nie jest konieczne Zawsze instaluj najnowsze poziom interfejsu API systemu Android; na poziomie platformy, które ma być docelowa zależy od interfejsu API, które są potrzebne. Ogólnie rzecz biorąc instalowanie Xamarin zainstaluje poziom platformy, które wymaga.  

2.  Sprawdź poprawność projektanta dla systemu Android: w projekcie systemu Android w Eksploratorze rozwiązań Otwórz **zasobów > Układ > Main.axml** pliku. (Jeśli nie widzisz ten plik bezpośrednio, spróbuj wykonać wyszukiwanie w Eksploratorze rozwiązań; istnieje w projekcie systemu Android tylko, a nie w projekt dla systemu iOS.)  
  
    - Jeśli zostanie wyświetlony błąd informujący o tym "Zainstalowany zestaw SDK systemu Android jest zbyt stary", kliknij przycisk **Otwórz zestaw SDK systemu Android** w tej wiadomości do wybierz i zainstaluj najnowsze zestawu SDK w wersji narzędzi dostępnych jako w kroku 1 powyżej. 
  
3.  Sprawdź poprawność kompilowanie i debugowanie w emulatora (lub urządzenie):  
  
    -   Kliknij prawym przyciskiem myszy projekt systemu Android w Eksploratorze rozwiązań i wybierz **Ustaw jako projekt startowy**.  
  
         ![Visual Studio Ustaw jako opcję uruchamiania projektu](../cross-platform/media/crossplat-xamarin-verify-2.png "CrossPlat Xamarin Sprawdź 2")  
  
    -   Wybierz odpowiednie emulatora, zależnie od wersji Android docelowym; Jeśli masz urządzenia z systemem Android development podłączone do komputera, pojawi się także w tym miejscu liście obok emulatorów:  
  
        -   System Windows 8: Wybierz **emulatora VS** docelowego w rozwijanej debugowania programu Visual Studio, jak pokazano poniżej, a następnie uruchomienia debugera, naciskając klawisz **F5**. Aby uzyskać więcej informacji, zobacz [wprowadzenie do programu Visual Studio Emulator for Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx) (blog Visual Studio ALM). Jeśli wystąpią problemy z uzyskiwaniem emulatora do pracy, zobacz [Rozwiązywanie problemów z programu Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md). Można również utworzyć nowe urządzenie profile dla emulatora, wybierając **Narzędzia > Visual Studio Emulator for Android...** .  
  
             ![Wybieranie programu Visual Studio Emulator for Android jako cel debugowania](../cross-platform/media/crossplat-xamarin-verify-3.png "CrossPlat Xamarin Sprawdź 3")  
  
             Uwaga: Jeśli nie widzisz **Narzędzia > Visual Studio Emulator for Android...**  opcji menu, możesz nie mieć się zainstalować emulator. Przejdź do **Panel sterowania > programy i funkcje**, wybierz pozycję **programu Microsoft Visual Studio**i kliknij przycisk **zmiany** Aby ponownie uruchomić Instalatora. Kliknij przycisk **Modyfikuj** w Instalatorze, zaznacz pole wyboru, aby uzyskać **Cross Platform Mobile Development > Microsoft Visual Studio Emulator for Android**i kliknij przycisk **aktualizacji**.  
  
        -   W systemie Windows 7 i starszych wersji: Wybierz Xamarin Player dla systemu Android w listy rozwijanej zamiast i naciśnij klawisz F5, aby uruchomić. Szczegółowe informacje dotyczące Xamarin Player, jego Menedżera urządzeń i wskazówki, przeczytaj [Xamarin Android Player](http://developer.xamarin.com/guides/android/getting_started/installation/android-player/) (xamarin.com).  
  
> [!NOTE]
>  W programie Visual Studio mogą pojawić się obecności przycisk Menedżera emulatora systemu Android (AVD) na pasku narzędzi (wyświetlane poniżej), które umożliwia otwarcie Menedżera urządzeń, w szczególności służący do konfigurowania emulator systemu Google Android.  To nie ma wpływu na albo emulatora programu Visual Studio dla systemu Android lub Xamarin Player, z których każda ma własne Menedżera urządzeń dotyczące konfigurowania profilów.  Zobacz [wprowadzenie do programu Visual Studio Emulator for Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx) (blog Visual Studio ALM) i [Xamarin Android Player](http://developer.xamarin.com/guides/android/getting_started/installation/android-player/) (xamarin.com) Aby uzyskać szczegółowe informacje.  
> ![CrossPlat Xamarin Sprawdź 7](../cross-platform/media/crossplat-xamarin-verify-7.png "CrossPlat Xamarin Sprawdź 7")  
  
## <a name="windows-phone"></a>Windows Phone  
  
1.  Sprawdź poprawność projektancie Windows Phone: w projekcie Windows Phone w Eksploratorze rozwiązań Otwórz **MainPage.xaml** pliku.  
  
2.  Sprawdź poprawność kompilowanie i debugowanie w emulatorze lub na urządzeniu (Uwaga: musisz mieć zainstalowane w ramach instalacji programu Visual Studio dla tego kroku lub urządzenia powiązanego emulator Windows Phone):  
  
    -   Kliknij prawym przyciskiem myszy projekt Windows Phone w Eksploratorze rozwiązań i wybierz **Ustaw jako projekt startowy**.  
  
    -   Wybierz **Emulator 8.1** docelowej lub dołączonego urządzenia w programie Visual Studio debugowania listy rozwijanej, jak pokazano poniżej i uruchomienia debugera, naciskając klawisz F5.  
  
         ![Wybranie emulatora Windows Phone jako cel debugowania](../cross-platform/media/crossplat-xamarin-verify-4.png "CrossPlat Xamarin Sprawdź 4")  
  
    -   Jeśli wystąpią problemy z uzyskiwaniem emulatora do pracy, przeczytaj [Rozwiązywanie problemów z Emulator Windows Phone 8](https://msdn.microsoft.com/library/windows/apps/jj681694.aspx).  
  
## <a name="ios"></a>iOS  
  
1.  Upewnij się, że komputera Mac jest dostępny w sieci i sparowanego z programem Visual Studio, zgodnie z opisem na [połączenie z komputerem Mac](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) (xamarin.com).  
  
2.  Sprawdź poprawność projektanta scenorysu: w projekcie systemu iOS w Eksploratorze rozwiązań Otwórz **Main.storyboard** pliku. W tym miejscu Visual Studio jest hostem tego projektanta, który jest uruchamiany zdalnie na komputerów Mac.  
  
3.  Sprawdź poprawność kompilowanie i debugowanie:  
  
    1.  Kliknij prawym przyciskiem myszy projekt iOS w Eksploratorze rozwiązań i wybierz **Ustaw jako projekt startowy**.  
  
    2.  Wybierz **iPhoneSimulator** z rozwijanej kompilacji programu Visual Studio docelową, jak pokazano poniżej, lub **iPhone** docelowych, jeśli masz urządzenia powiązanego. Jeśli nie są wyświetlane nie symulatorów, uruchom Xcode na komputerze Mac, wybierz **Xcode -> Preferencje**i kliknij przycisk **Pobierz**. W obszarze **składniki** powinna zostać wyświetlona wersji symulator, które są dostępne do pobrania. Dodatkowe instrukcje dotyczące debugowania można znaleźć w Xamarin [debugowanie](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) strony (xamarin.com).  
  
         ![Wybieranie iPhoneSimulator kompilacji docelowej](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin Sprawdź 5")  
  
    3.  Wybierz obiekt docelowy iPhone z rozwijanej debugowania programu Visual Studio, jak pokazano poniżej, a następnie uruchomienia debugera, naciskając klawisz F5. Spowoduje to uruchomienie symulatora dla komputerów Mac, w którym interakcji z aplikacją, a debugowanie odbywa się w programie Visual Studio. Jeśli fizyczne urządzenia iPhone lub iPad podłączone do komputera Mac, pojawi się w tym miejscu i można ją wybrać w zamian. Jeśli nie ma żadnych urządzeń ani symulatorów na liście, sprawdź, czy połączenie z komputerem Mac, przeglądając tematu w kroku 1 lub przechodząc do **narzędzia** >**iOS**  > **Xamarin Mac Agent**  
  
         ![Wybieranie obiektu docelowego debugowania iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin Sprawdź 6")  
  
    4.  Jeśli wystąpią problemy z połączeniem z adresem MAC odczytu [Rozwiązywanie problemów z połączenia](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/xma-troubleshooting/) (xamarin.com).  
  
    5.  Jeśli zostanie wyświetlony błąd zawierający komunikat "nie zainstalowanych profilów aprowizacji zainstalowanych z systemem iOS kluczy podpisywania są zgodne, wykonaj następujące czynności:  
  
        -   Sprawdź, że Twoje konto Apple Id został dodany w programie Xcode na komputerze Mac, zgodnie z opisem na [Dodawanie Twoje konto xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).  Po dodaniu konta, należy ponownie uruchom Visual Studio i Xcode.  
  
             ![Sprawdź 8, CrossPlat Xamarin](../cross-platform/media/crossplat-xamarin-verify-8.png "CrossPlat Xamarin Sprawdź 8")  
  
        -   Upewnij się, w dla systemu iOS właściwości projektu w sklepie iOS pakietu podpisywania karcie, czy pole niestandardowe uprawnienie jest pusta dla konfiguracji debugowania aktywnego.  Uwaga: należy tylko spróbować usuwanie to ustawienie, jeśli zostały napotkane powyżej komunikat o błędzie.  
  
##  <a name="missing"></a>Brak szablonów projektu Xamarin? Spróbuj to  
 Szablony mogą być brakujące, w przypadku zainstaluj program Xamarin bezpośrednio z witryny sieci Web platformy Xamarin i Visual Studio 2013 i Visual Studio 2015 zainstalowane obok siebie. To proste rozwiązać problem, ale: po prostu włącz **Xamarin dla Visual Studio 2015** funkcji w Instalatorze programu Xamarin.  
  
1.  W Panelu sterowania otwórz **programy i funkcje**, wybierz **Xamarin** elementu, a następnie kliknij przycisk **zmiany**.  
  
2.  W Kreatorze instalacji xamarin, która jest wyświetlana, kliknij przycisk **dalej** , a następnie **zmiany**.  
  
3.  Na liście funkcji opcjonalnych, aby zainstalować, rozwiń węzeł **Xamarin dla Visual Studio 2015**, wybierz **zostanie zainstalowana na lokalnym dysku**i kliknij przycisk **dalej** dodawania Funkcja.