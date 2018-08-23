---
title: Sprawdź swoje środowisko Xamarin | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: fd39882e-06d1-4b39-80d2-4d07b6e4f8f5
ms.prod: visual-studio-dev15
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 9ae697825d0d4a2c380c6f0d540153fbf06d4da4
ms.sourcegitcommit: d7209d61e812b34d06c2aa267bdf50fbc714d0e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2018
ms.locfileid: "42624195"
---
# <a name="verify-your-xamarin-environment"></a>Sprawdzanie środowiska Xamarin

Po ukończeniu ma instalatorów (zobacz [Instalator i instalacja](../cross-platform/setup-and-install.md)), Poświęć kilka minut, aby sprawdzić, wszystko jest gotowe do środowisko programowania Xamarin.

 Po zakończeniu sprawdzania instalacji, spróbuj wykonać jedną lub obie następujące instruktaże:

-   [Dowiedz się, podstawy tworzenia aplikacji przy użyciu zestawu narzędzi Xamarin.Forms w programie Visual Studio](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md) do tworzenia aplikacji platformy Xamarin.Forms.

-   [Tworzenie aplikacji z natywnym interfejsem użytkownika przy użyciu platformy Xamarin w programie Visual Studio](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md) do użycia natywne interfejsy użytkownika na każdej platformie, ale mają jakiś kod w biblioteki .NET Standard.

## <a name="all-platforms"></a>Wszystkie platformy

W programie Visual Studio, należy najpierw wybrać **narzędzia** > **rozszerzenia i aktualizacje** i sprawdź, jeśli którykolwiek ze składników Xamarin wymagają aktualizacji.

Następnie utwórz nowe rozwiązanie Xamarin.Forms przy użyciu programu Visual Studio **pliku** > **nowy projekt**. W oknie dialogowym Rozwiń **Visual C#** > **dla wielu Platform**, wybierz opcję **aplikacja mobilna (Xamarin.Forms)** i kliknij przycisk **OK**. W oknie dialogowym poniżej wybierz **pusta aplikacja**. W obszarze **strategia udostępniania kodu**, wybierz opcję **.NET Standard**. Kliknij przycisk **OK**.

Te akcje tworzenia rozwiązania z czterema projektami: udostępnionego projektu biblioteki .NET Standard 2.0 i projektów aplikacji dla systemów Android, iOS i platformy uniwersalnej Windows (UWP):

![Wyniki tworzenia nowego projektu z szablonu pustej aplikacji platformy Xamarin.Forms](../cross-platform/media/crossplat-xamarin-verify-1.png "CrossPlat Xamarin Sprawdź 1")

## <a name="android"></a>Android

1. Sprawdź, czy jest zainstalowany, przechodząc do najnowszych narzędzi zestawu SDK systemu Android **Narzędzia > Android > Menedżer zestawów SDK**. Zainstalowanie najnowszej wersji Android SDK Tools, narzędzia platformy Android SDK i narzędzi kompilacji zestawu SDK systemu Android. Nie jest konieczne Zawsze instaluj najnowsze poziom interfejsu API systemu Android. Poziom interfejsu API, które są potrzebne, zależy od poziomu platformy, która ma pod kątem. Ogólnie rzecz biorąc instalacji platformy Xamarin, zostanie zainstalowany o wymaganym poziomie platformy systemu Android.

2.  Sprawdzanie poprawności, kompilowania i debugowania na urządzeniu lub w emulatorze:

    -   Kliknij prawym przyciskiem myszy projekt systemu Android w Eksploratorze rozwiązań i wybierz **Ustaw jako projekt startowy**.

    -   Na pasku narzędzi powinien zostać wyświetlony listy rozwijanej, zawierający listę dostępnych urządzeń z systemem Android i emulatorów.

    Urządzenia z systemem android musi być włączona dla debugowania za pomocą opcji dla deweloperów na stronie ustawień urządzenia USB. Urządzenie jest następnie dołączony do komputera za pomocą kabla USB.

    Liście są również emulatorów. Wybierz jedno z urządzeń lub emulatorów programu Visual Studio:

  ![Wybierz pozycję Visual Studio Emulator for Android jako obiekt docelowy debugowania](../cross-platform/media/crossplat-xamarin-verify-3.png "CrossPlat Xamarin Sprawdź 3")

  Aby uzyskać więcej informacji, zobacz [wprowadzenie do programu Visual Studio Emulator for Android](https://blogs.msdn.microsoft.com/devops/2014/11/12/introducing-visual-studios-emulator-for-android/) na blogu Microsoft DevOps. Jeśli wystąpią problemy z integracją emulatora do pracy, zobacz [Rozwiązywanie problemów z emulatorem programu Visual Studio dla systemu Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md). Można również tworzyć nowych profilów urządzeń dla emulatora, wybierając **Narzędzia > Android > Android Emulator Manager**.

3. Naciśnij klawisz **F5** do kompilowania i wdrażania programu na urządzeniu z systemem Android lub w emulatorze.

## <a name="windows"></a>Windows

1.  Kliknij prawym przyciskiem myszy projekt Windows Universal w Eksploratorze rozwiązań i wybierz **Ustaw jako projekt startowy**.

2.  W **platformy rozwiązania** listę rozwijaną, wybierz opcję **x86** lub **x64**. Wybierz **komputera lokalnego**.

3.  Naciśnij klawisz **F5** do wdrożenia programu na pulpicie.

## <a name="ios"></a>iOS

1.  Upewnij się, że komputer Mac jest dostępny w sieci oraz sparowany z programem Visual Studio, zgodnie z opisem na [nawiązywania połączenia z komputerem Mac](/xamarin/ios/get-started/installation/windows/connecting-to-mac/).

2.  Kliknij prawym przyciskiem myszy projekt iOS, w Eksploratorze rozwiązań i wybierz **Ustaw jako projekt startowy**.

3.  Wybierz **iPhoneSimulator** element docelowy z rozwijanej kompilacji programu Visual Studio, jak pokazano poniżej, lub **iPhone** docelowy, jeśli masz urządzenie z pomocą zastosowaniu tetheringu na komputerach Mac.

 ![Wybieranie iPhoneSimulator tworzenia pod kątem](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin Sprawdź 5")

 Jeśli nie są wyświetlane nie symulatorów, uruchom program Xcode na komputerze Mac, wybierz **Xcode** > **preferencje**i kliknij przycisk **Pobierz**. W obszarze **składniki** możesz nagłówka powinien zostać wyświetlony wersji symulator, które są dostępne do pobrania. Dodatkowe instrukcje dotyczące debugowania można znaleźć na [iOS debugowanie](/xamarin/ios/deploy-test/debugging-in-xamarin-ios) strony.

4.  Wybierz obiekt docelowy urządzenia emulatora, z listy rozwijanej programu Visual Studio:

 ![Wybieranie obiektu docelowego debugowania dla telefonu iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin Sprawdź 6")

5. Uruchom debuger, naciskając klawisz **F5**. Symulator jest uruchomiony na komputerze Mac, w którym interakcji z aplikacją, podczas gdy profilowanie odbywa się w programie Visual Studio. Jeśli masz fizycznego dla telefonu iPhone lub iPad nawiązanie połączenia z komputerem Mac, pojawi się na liście i można ją wybrać w zamian. Jeśli nie ma żadnych urządzeń ani symulatorów wymienione, sprawdź połączenie z komputerem Mac. Zapoznaj się z artykułem połączone w kroku 1 powyżej, lub przejdź do **narzędzia** > **iOS** > **Sparuj z komputerem Mac**

6.  Jeśli wystąpią problemy z połączeniem z komputerem Mac, zapoznaj się z [Rozwiązywanie problemów z połączeniem](/xamarin/ios/get-started/installation/windows/connecting-to-mac/troubleshooting/).

7.  Jeśli zostanie wyświetlony błąd informujący o "żaden z zainstalowanych profilów aprowizacji pasuje zainstalowanych kluczy podpisywania systemu iOS", należy spróbować wykonać następujące czynności:

  - Sprawdź, czy konta Apple Id jest dodany w środowisku Xcode na komputerze Mac, zgodnie z opisem na [Dodaj swoje konto w narzędziu Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).  Po dodaniu konta, upewnij się ponownie uruchomić Visual Studio i narzędziu Xcode.

  - Sprawdź w aplikacjach dla systemów iOS właściwości projektu w narzędziu iOS pakietu kartę podpisywania, że pole niestandardowe uprawnienie jest pusta dla konfiguracji debugowania aktywnego.  Uwaga: należy tylko spróbować usuwania tego ustawienia, jeśli wystąpiły powyżej komunikat o błędzie.

  ![CrossPlat Xamarin Sprawdź 8](../cross-platform/media/crossplat-xamarin-verify-8.png "CrossPlat Xamarin Sprawdź 8")
