---
title: Sprawdź środowisku Xamarin | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: fd39882e-06d1-4b39-80d2-4d07b6e4f8f5
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 862af0d8912811aee8e0110b48fa8cc3e8f1c06b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31068400"
---
# <a name="verify-your-xamarin-environment"></a>Sprawdź środowisku Xamarin

Po ukończeniu ma instalatorów (zobacz [Instalatora i zainstaluj](../cross-platform/setup-and-install.md)), spędzają na kilka minut, sprawdź, czy wszystko jest gotowe do środowisko rozwoju Xamarin.  
  
 Po zakończeniu sprawdzania instalacji, spróbuj wykonać jedną lub obie następujące wskazówki:  
  
-   [Dowiedz się podstawowe informacje dotyczące tworzenia aplikacji z platformy Xamarin.Forms w programie Visual Studio](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md) do tworzenia aplikacji platformy Xamarin.Forms.
  
-   [Tworzenie aplikacji za pomocą natywnego interfejsu użytkownika za pomocą platformy Xamarin w programie Visual Studio](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md) używać interfejsów użytkownika natywnego na każdej platformie, ale udostępnianie kodu w bibliotece .NET Standard.
  
## <a name="all-platforms"></a>Wszystkie platformy 
 
W programie Visual Studio, najpierw wybierz **Narzędzia > rozszerzenia i aktualizacje** i sprawdź, czy któregokolwiek ze składników Xamarin wymagają aktualizacji.  
  
Następnie utwórz nowe rozwiązanie platformy Xamarin.Forms przy użyciu programu Visual Studio **Plik > Nowy projekt**. W oknie dialogowym Rozwiń **Visual C# > wieloplatformowych**, wybierz pozycję **aplikacji mobilnej (platformy Xamarin.Forms)** i kliknij przycisk OK. W oknie dialogowym poniżej wybierz **pusta aplikacja**. W obszarze **strategii udostępniania kodu**, wybierz pozycję **.NET Standard**. Kliknij przycisk OK.

Te akcje tworzenie rozwiązania z czterech projektów: udostępnionego projektu biblioteki .NET 2.0 standardowe i projektów aplikacji dla systemu Android, iOS i platformy uniwersalnej systemu Windows (UWP):  
  
![Wyniki tworzenia nowego projektu z szablonu pustą aplikację platformy Xamarin.Forms](../cross-platform/media/crossplat-xamarin-verify-1.png "CrossPlat Xamarin Sprawdź 1")  
   
## <a name="android"></a>Android  
  
1. Sprawdź, czy masz najnowsze narzędzia zestawu SDK systemu Android zainstalowane, przechodząc do **Narzędzia > Android > Android SDK Manager**. Zainstaluj najnowsze wersje narzędzia zestawu SDK systemu Android, narzędzi platformy Android SDK i narzędzia kompilacji zestawu SDK systemu Android. Nie jest konieczne Zawsze instaluj najnowsze poziom interfejsu API systemu Android. Poziom interfejsu API, które są potrzebne, zależy od poziomu platformy, który ma być docelowa. Ogólnie rzecz biorąc instalowanie platformy Xamarin zainstaluje poziom platformy systemu Android, które wymaga.  
  
2.  Sprawdź poprawność kompilowanie i debugowanie na urządzeniu lub emulatorze:  
  
    -   Kliknij prawym przyciskiem myszy projekt systemu Android w Eksploratorze rozwiązań i wybierz **Ustaw jako projekt startowy**.  
  
    -   Na pasku narzędzi powinny zostać wyświetlone menu rozwijane zawierający listę dostępnych urządzeń z systemem Android emulatorów. 
    
    Urządzenia z systemem android musi być włączona dla debugowania w opcjach projektanta strony Ustawienia urządzenia USB. Urządzenie jest następnie dołączony do komputera przy użyciu kabla USB. 
    
    Liście są również emulatory. Wybierz jedno z urządzeń lub emulatory Visual Studio:

  ![Wybieranie programu Visual Studio Emulator for Android jako cel debugowania](../cross-platform/media/crossplat-xamarin-verify-3.png "CrossPlat Xamarin Sprawdź 3")  
  
  Aby uzyskać szczegółowe informacje, zobacz [wprowadzenie do programu Visual Studio Emulator for Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx) (blog Visual Studio ALM). Jeśli wystąpią problemy z uzyskiwaniem emulatora do pracy, zobacz [Rozwiązywanie problemów z programu Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md). Można również utworzyć nowe urządzenie profile dla emulatora, wybierając **Narzędzia > Android > Android Emulator Manager**.  
  
3. Naciśnij klawisz F5, aby skompilować i wdrożyć program dla systemu Android urządzenia lub emulatora.
  
## <a name="windows"></a>Windows 
  
1.  Kliknij prawym przyciskiem myszy projekt uniwersalnej systemu Windows w Eksploratorze rozwiązań i wybierz **Ustaw jako projekt startowy**.  

2.  W **platformy rozwiązania** listy rozwijanej, wybierz pozycję **x86** lub **x64**. Wybierz **komputera lokalnego**.

3.  Naciśnij klawisz F5, aby wdrożyć program na pulpicie.
  
## <a name="ios"></a>iOS  
  
1.  Upewnij się, że komputera Mac jest dostępny w sieci i sparowanego z programem Visual Studio, zgodnie z opisem na [połączenie z komputerem Mac](/xamarin/ios/get-started/installation/windows/connecting-to-mac/).  
  
2.  Kliknij prawym przyciskiem myszy projekt iOS w Eksploratorze rozwiązań i wybierz **Ustaw jako projekt startowy**.  
  
3.  Wybierz **iPhoneSimulator** z rozwijanej kompilacji programu Visual Studio docelową, jak pokazano poniżej, lub **iPhone** docelowych, jeśli masz urządzenie spętane do komputerów Mac.   
  
 ![Wybieranie iPhoneSimulator kompilacji docelowej](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin Sprawdź 5") 

 Jeśli nie są wyświetlane nie symulatorów, uruchom Xcode na komputerze Mac, wybierz **Xcode > Preferencje**i kliknij przycisk **Pobierz**. W obszarze **składniki** możesz nagłówek powinna być widoczna wersji symulator, które są dostępne do pobrania. Dodatkowe instrukcje dotyczące debugowania można znaleźć w [iOS debugowanie](/xamarin/ios/deploy-test/debugging-in-xamarin-ios/?tabs=vsmac#Debugging_on_the_Simulator) strony.
  
4.  Wybierz obiekt docelowy urządzenia emulatora, z listy rozwijanej Visual Studio:

 ![Wybieranie obiektu docelowego debugowania iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin Sprawdź 6")

5. Uruchom debuger, naciskając klawisz F5. Symulator jest uruchamiana w systemie Mac, w którym interakcji z aplikacją, a debugowanie odbywa się w programie Visual Studio. Jeśli fizyczne urządzenia iPhone lub iPad podłączone do komputera Mac, pojawi się na liście i można ją wybrać w zamian. Jeśli nie ma żadnych urządzeń ani symulatorów na liście, sprawdź połączenie z komputerów Mac. Zapoznaj się z artykułem połączone w kroku 1 lub przejdź do **Narzędzia > iOS > pary Mac**  
  
6.  Jeśli wystąpią problemy z połączeniem z adresem MAC odczytu [Rozwiązywanie problemów z połączenia](/xamarin/ios/get-started/installation/windows/connecting-to-mac/troubleshooting/).  
  
7.  Jeśli zostanie wyświetlony błąd informujący o tym, "nie zainstalowanych profilów aprowizacji odpowiada zainstalowanych z systemem iOS kluczy podpisywania", wypróbuj następujące rozwiązania:  
  
  - Sprawdź, że Twoje konto Apple Id został dodany w programie Xcode na komputerze Mac, zgodnie z opisem na [Dodawanie Twoje konto xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).  Po dodaniu konta, należy ponownie uruchom Visual Studio i Xcode.  
    
  - Upewnij się, w dla systemu iOS właściwości projektu w sklepie iOS pakietu podpisywania karcie, czy pole niestandardowe uprawnienie jest pusta dla konfiguracji debugowania aktywnego.  Uwaga: należy tylko spróbować usuwanie to ustawienie, jeśli zostały napotkane powyżej komunikat o błędzie.  
  
  ![Sprawdź 8, CrossPlat Xamarin](../cross-platform/media/crossplat-xamarin-verify-8.png "CrossPlat Xamarin Sprawdź 8")  
