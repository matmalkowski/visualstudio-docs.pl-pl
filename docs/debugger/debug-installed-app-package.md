---
title: Debugowanie zainstalowanego pakietu aplikacji (systemu Windows UWP) | Dokumentacja firmy Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 07/17/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 291f24c6ffdf885cf3d24c5ff163c2f4f911d7ce
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279562"
---
# <a name="debug-an-installed-app-package-in-visual-studio-uwp"></a>Debugowanie zainstalowanego pakietu aplikacji w programie Visual Studio (platformy UWP)

Można debugować wszelkie zainstalowanego pakietu aplikacji, klikając **Debuguj > inne cele debugowania > debugowanie zainstalowanego pakietu aplikacji**. Debugowania metoda ta jest dostępna dla uniwersalnej aplikacji Windows (UWP) na tych urządzeniach:

* Windows 10 (nieobsługiwane na telefonach)
* XBox
* HoloLens
* IoT

Aby uzyskać więcej informacji o tych funkcjach, zobacz w blogu aktualizacji dla [debugowania zainstalowanych pakietów aplikacji](https://blogs.msdn.microsoft.com/devops/2016/03/30/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) i wpis na [tworzenia Windows aplikacji Uniwersalnej](https://blogs.msdn.microsoft.com/visualstudio/2016/08/02/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-app-package-or-running-app-on-a-local-machine-or-device"></a>Debugowanie zainstalowanego pakietu aplikacji lub uruchomionej aplikacji na urządzeniu lub komputerze lokalnym

1. Otwórz w programie Visual Studio projekt platformy uniwersalnej systemu Windows kliknij **Debuguj > inne cele debugowania > debugowanie zainstalowanego pakietu aplikacji**.

2. Wybierz opcję **komputera lokalnego** lub **urządzenia**.

     Jeśli wybierzesz **urządzenia**, komputer musi być fizycznie połączone urządzenia z systemem Windows 10.

     ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

     Aktualnie uruchomione zainstalowana aplikacja pakietów wyświetlane w obszarze **systemem** węzła. Zainstalowane pakiety aplikacji, które nie są uruchomione show się na **nieuruchomiona**.

3. Wybierz nazwę aplikacji, który chcesz debugować w obszarze **systemem** lub **nieuruchomiona** i wybierz polecenie **Start** lub, jeśli aplikacja jest już uruchomiony, wybierz opcję **Dołącz**.

     Jeśli wybierzesz **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu**, spowoduje to debuger programu Visual Studio dołączyć do aplikacji, gdy można uruchomić jednocześnie niestandardowych. To efektywny sposób debugowania ścieżek kontroli [uruchomienia różnych metod](/windows/uwp/xbox-apps/automate-launching-uwp-apps), takich jak protokół aktywacji z użyciem niestandardowych parametrów.

> [!NOTE]
> Program Visual Studio do można również dołączyć każdy uruchomiony proces aplikacji platformy uniwersalnej systemu Windows, wybierając **debugowania**, a następnie **dołączyć do procesu**. Dołączanie do uruchomionego procesu nie wymaga oryginalnego projektu programu Visual Studio, ale ładowanie symboli procesu pomogą znacznie podczas debugowania procesu, które nie mają oryginalny kod.
  
## <a name="remote"></a> Debugowanie aplikacji zainstalowany lub włączony na komputerze zdalnym 

Podczas debugowania zainstalowanego pakietu aplikacji na komputerze zdalnym po raz pierwszy, program Visual Studio instaluje poprawną wersję narzędzi remote tools dla Twojego urządzenia docelowego. Twoje urządzenie docelowe musi być komputer z systemem Windows 10 oraz urządzenia XBox, HoloLens i IoT.

1. Na urządzeniu z systemem Windows 10, należy włączyć [tryb dewelopera](/windows/uwp/get-started/enable-your-device-for-development).

2. Jeśli łączysz się z Komputerem zdalnym wstępnie twórcy zaktualizowanej wersji systemu Windows 10, najpierw ręczne uruchomienie [zainstalować i uruchomić zdalny debuger](../debugger/remote-debugging.md).

     Dla urządzenia XBox, HoloLens i IoT, a aktualizacja dla twórców 10 systemem Windows nie trzeba ręcznie zainstalować debuger zdalny. Remote tools zostanie automatycznie zainstalowana podczas wdrażania aplikacji.

3. Kliknij przycisk **Debuguj > inne cele debugowania > debugowanie zainstalowanego pakietu aplikacji**.

4. Z pierwszej listy rozwijanej wybierz **maszyny zdalnej**.

5. Wpisz nazwę lub adres IP komputera, który chcesz dołączyć do.

     ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

     Jeśli nie można dołączyć, przy użyciu nazwy komputera (po wybraniu **Start**), zamiast tego użyj adresu IP. Użyj adresu IP dla urządzeń z konsoli XBox, HoloLens i IoT.

5. Wybierz sposób uwierzytelniania, wybierając opcję **tryb uwierzytelniania**.

    W przypadku większości aplikacji zachować wartość domyślną, **uniwersalny (protokół niezaszyfrowanym)**.

6. Wybierz nazwę aplikacji, który chcesz debugować w obszarze **systemem** lub **nieuruchomiona** i wybierz polecenie **Start** lub (w przypadku uruchamiania aplikacji) **Dołącz**.

     Jeśli wybierzesz **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu**, to spowoduje, że debuger programu Visual Studio można dołączyć do pakietu aplikacji, po uruchomieniu niestandardowej naraz. To efektywny sposób debugowania ścieżek kontroli [uruchomienia różnych metod](/windows/uwp/xbox-apps/automate-launching-uwp-apps), takich jak protokół aktywacji z użyciem niestandardowych parametrów.

     Podczas debugowania zainstalowanego pakietu aplikacji na konsoli XBox, HoloLens i IoT na podłączonym urządzeniu po raz pierwszy, program Visual Studio instaluje poprawną wersję zdalnego debugera na urządzeniu docelowym. Może to zająć trochę czasu i zostanie wyświetlony komunikat ``Starting remote debugger`` podczas, gdy to się dzieje.

     > [!NOTE]
> Obecnie, XBox lub urządzenia HoloLens spowoduje ponowne uruchomienie aplikacji w debugerze, jeśli jest już uruchomiona.

Aby uzyskać informacji na temat Zaawansowane opcje zdalnego wdrażania aplikacji platformy uniwersalnej systemu Windows Zobacz [wdrażania i debugowania apps]((/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) platformy uniwersalnej systemu Windows. 
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie w programie Visual Studio](../debugger/index.md)  
 [Przewodnik po funkcjach debugera](../debugger/debugger-feature-tour.md)  
 [Debugowanie zdalne](../debugger/remote-debugging.md)  
 [Konfigurowanie zapory systemu Windows na potrzeby debugowania zdalnego](../debugger/configure-the-windows-firewall-for-remote-debugging.md)  
 [Przypisania portów debugera zdalnego](../debugger/remote-debugger-port-assignments.md)  
 [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)