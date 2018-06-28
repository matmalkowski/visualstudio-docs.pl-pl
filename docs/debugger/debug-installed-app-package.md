---
title: Debugowanie pakietu zainstalowanych aplikacji (UWP) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 6bb43288b7e5a4dd9241a7492baeed9de1c49890
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37059343"
---
# <a name="debug-an-installed-app-package-in-visual-studio-uwp"></a>Debugowanie pakietu aplikacji zainstalowanych w programie Visual Studio (UWP)

Można debugować dowolny pakiet zainstalowaną aplikację, klikając **Debuguj > innych celów debugowania > Debuguj zainstalowany pakiet aplikacji**. Ta metoda debugowania jest dostępna dla uniwersalnych aplikacji systemu Windows (UWP) na tych urządzeniach:

* Windows 10 (nieobsługiwane w telefonach)
* XBox
* HoloLens
* IoT

Aby uzyskać więcej informacji o tych funkcjach, zobacz blogu na aktualizacje [debugowania zainstalowane pakiety aplikacji](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/30/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) i post na [tworzenia uniwersalnych aplikacji systemu Windows (UWP)](https://blogs.msdn.microsoft.com/visualstudio/2016/08/02/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-app-package-or-running-app-on-a-local-machine-or-device"></a>Debugowanie zainstalowanego pakietu aplikacji lub aplikacja uruchomiona na komputerze lokalnym lub urządzeniu

1. Otwórz w programie Visual Studio projektu platformy uniwersalnej systemu Windows, kliknij polecenie **debugowania > innych celów debugowania > Debuguj zainstalowany pakiet aplikacji**.

2. Wybierz opcję **komputera lokalnego** lub **urządzenia**.

     Jeśli wybierzesz **urządzenia**, komputer musi być fizycznie podłączeni do urządzenia z systemem Windows 10.

     ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

     Aktualnie uruchomiona zainstalowanych aplikacji pakiety będą wyświetlane w obszarze **systemem** węzła. Zainstalowane pakiety aplikacji, które nie są uruchomione Pokaż się na **nieuruchomiona**.

3. Wybierz nazwę aplikacji, którą chcesz debugować w obszarze **systemem** lub **nieuruchomiona** i wybierz polecenie **Start** lub, jeśli aplikacja jest już uruchomiona, wybierz **Attach**.

     W przypadku wybrania **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu**, to spowoduje, że debuger programu Visual Studio można dołączyć do aplikacji, podczas uruchamiania niestandardowych naraz. Jest to efektywny sposób debugowania ścieżki kontroli z [uruchomienia różnych metod](/windows/uwp/xbox-apps/automate-launching-uwp-apps), takie jak protokół aktywacji z użyciem niestandardowych parametrów.

> [!NOTE]
> Visual Studio można również dołączyć każdy uruchomiony proces aplikacji platformy uniwersalnej systemu Windows, wybierając **debugowania**, a następnie **dołączyć do procesu**. Dołączanie do uruchomionego procesu nie wymaga oryginalnego projektu programu Visual Studio, ale ładowanie symboli procesu pomogą znacznie podczas debugowania procesu, który nie ma oryginalny kod.
  
## <a name="remote"></a> Debugowanie aplikacji zainstalowany lub włączony na komputerze zdalnym 

Podczas debugowania pakietu aplikacji zainstalowanych na komputerze zdalnym po raz pierwszy, program Visual Studio instaluje poprawną wersję narzędzi remote Tools dla urządzenia docelowego. Urządzenia docelowego musi być komputer z systemem Windows 10, XBox, HoloLens i IoT urządzenia.

1. Na urządzeniu z systemem Windows 10, należy włączyć [tryb dewelopera](/windows/uwp/get-started/enable-your-device-for-development).

2. Jeśli łączysz się z Komputerem zdalnym wersją wstępną twórcy aktualizacji systemu Windows 10, najpierw ręcznie [Zainstaluj i uruchom zdalny debuger](../debugger/remote-debugging.md).

     Dla konsoli XBox, HoloLens i IoT urządzenia, a systemem Windows 10 Creator aktualizacji urządzenia z systemem Windows nie trzeba ręcznie zainstalować zdalny debuger. Narzędzia zdalnej zostanie automatycznie zainstalowana podczas wdrażania aplikacji.

3. Kliknij przycisk **Debuguj > innych celów debugowania > debugowanie zainstalowanego pakietu aplikacji**.

4. Z pierwszej listy rozwijanej wybierz **maszyny zdalnej**.

5. Wpisz nazwę lub adres IP komputera, który chcesz dołączyć do.

     ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

     Jeśli nie można dołączyć przy użyciu nazwy komputera (po wybraniu **Start**), zamiast tego użyj adresu IP. Użyj adresu IP dla urządzeń z konsoli XBox, HoloLens i IoT.

5. Wybierz sposób uwierzytelniania, zaznaczając odpowiednią opcję w **tryb uwierzytelniania**.

    W większości aplikacji zachować wartość domyślną, **uniwersalnego (nieszyfrowanego protokołu)**.

6. Wybierz nazwę aplikacji, którą chcesz debugować w obszarze **systemem** lub **nieuruchomiona** i wybierz polecenie **Start** lub (do uruchamiania aplikacji) **Attach**.

     W przypadku wybrania **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu**, to spowoduje, że debuger programu Visual Studio do dołączenia do pakietu aplikacji, podczas uruchamiania niestandardowych naraz. Jest to efektywny sposób debugowania ścieżki kontroli z [uruchomienia różnych metod](/windows/uwp/xbox-apps/automate-launching-uwp-apps), takie jak protokół aktywacji z użyciem niestandardowych parametrów.

     Podczas debugowania pakietu aplikacji zainstalowanych na połączonym urządzeniu XBox HoloLens i IoT po raz pierwszy, program Visual Studio instaluje poprawną wersję zdalnego debugera na urządzeniu docelowym. Może to potrwać chwilę czasu i zostanie wyświetlony komunikat ``Starting remote debugger`` podczas zdarza się to.

     > [!NOTE]
> Przedstawia XBox lub urządzenia HoloLens uruchomi aplikację w debugerze, jeśli jest już uruchomiona.

Informacje na Zaawansowane opcje zdalnego wdrażania usług aplikacji platformy uniwersalnej systemu Windows Zobacz [wdrażanie i debugowanie apps]((/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) platformy uniwersalnej systemu Windows. 
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie w programie Visual Studio](../debugger/index.md)  
 [Przegląd funkcji debugera](../debugger/debugger-feature-tour.md)  
 [Debugowanie zdalne](../debugger/remote-debugging.md)  
 [Konfigurowanie Zapory systemu Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md)  
 [Przypisania portów debugera zdalnego](../debugger/remote-debugger-port-assignments.md)  
 [Zdalne debugowanie błędów i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)