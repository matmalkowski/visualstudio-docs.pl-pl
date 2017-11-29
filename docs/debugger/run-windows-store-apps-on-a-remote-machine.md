---
title: Uruchamianie aplikacji platformy uniwersalnej systemu Windows na zdalnym komputerze | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 07/17/2017
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
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
caps.latest.revision: "43"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e1b298f8088adf05992f7ebf8b5afbb743ec995
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="run-uwp-apps-on-a-remote-machine"></a>Uruchamianie aplikacji platformy uniwersalnej systemu Windows na komputerze zdalnym
![Dotyczy tylko systemów Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
Uruchamianie aplikacji platformy uniwersalnej systemu Windows na komputerze zdalnym, należy dołączyć do niego za pomocą narzędzi zdalnego programu Visual Studio. Narzędzia Remote Tools umożliwiają uruchamianie, debugowanie profilu i testowanie aplikacji platformy uniwersalnej systemu Windows, który jest uruchomiony na jednym urządzeniu z drugiego komputera, na którym działa program Visual Studio. Uruchamianie na urządzeniu zdalnym mogą być szczególnie przydatny, gdy komputer programu Visual Studio nie obsługuje funkcje, które są określone do aplikacji platformy uniwersalnej systemu Windows, takich jak touch, lokalizacja geograficzna i orientację fizycznych. W tym temacie opisano procedury, aby skonfigurować i uruchomić sesję zdalną.

W niektórych scenariuszach narzędzia zdalnej są automatycznie instalowane podczas wdrażania na urządzeniu zdalnym.

- Systemem aktualizacji twórców i nowszych wersjach komputerów z systemem Windows 10, zobacz [Debuguj zainstalowany pakiet aplikacji](debug-installed-app-package.md#remote). Narzędzia do zdalnego zostaną zainstalowane automatycznie.
- W przypadku urządzeń z systemem Windows 10 w konsoli Xbox, IOT i HoloLens, zobacz [Debuguj zainstalowany pakiet aplikacji](debug-installed-app-package.md#remote). Narzędzia do zdalnego zostaną zainstalowane automatycznie.
- Windows Phone, musi być fizycznie podłączeni do telefonu, należy najpierw zainstaluj [licencji dewelopera](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh974578.aspx) (Windows Phone 8 i 8.1) lub Włącz [tryb dewelopera](/windows/uwp/get-started/enable-your-device-for-development) (Windows Mobile 10), a także Wybierz **urządzenia** jako cel debugowania. Zdalne narzędzia są wymagane lub nie obsługiwane.

Dla komputerów Windows 8.1 i Windows 10 komputerami z systemem pre twórcy zaktualizowanej wersji systemu Windows należy zainstalować narzędzia zdalnej na komputerze zdalnym ręcznie przed debugowaniem. Postępuj zgodnie z instrukcjami w tym temacie.
  
##  <a name="BKMK_Prerequisites"></a> Wymagania wstępne  
 Aby debugować na urządzeniu zdalnym:  
  
-   Urządzenie zdalne i komputer z programem Visual Studio muszą być połączone przez sieć lub podłączone bezpośrednio za pomocą kabla Ethernet. Debugowanie przez Internet nie jest obsługiwane.  

- Zdalne urządzenie musi być włączony do tworzenia aplikacji.

    - W przypadku urządzeń z systemem Windows 8 i Windows 8.1 [licencji dewelopera](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh974578.aspx) musi być zainstalowany na urządzeniu zdalnym.
    - Dla urządzeń z systemem Windows 10, należy włączyć [tryb dewelopera](/windows/uwp/get-started/enable-your-device-for-development). 
  
-   Systemem Windows 10 w wersji starszej niż Windows 10 Creator aktualizacji komputerów z systemem Windows 10 należy zainstalować i uruchomić składniki zdalnego debugowania.
  
-   Musi być administratorem na urządzeniu zdalnym Skonfiguruj zaporę podczas instalacji. Musi mieć dostęp użytkownika do urządzenia zdalnego, aby uruchomić lub połączyć się ze zdalnym debugerem.  
  
##  <a name="BKMK_Security"></a>Zabezpieczeń  
 Domyślnie program zdalny debuger używa uwierzytelniania systemu Windows.  
  
> [!WARNING]
>  Można również uruchomić w trybie bez uwierzytelniania zdalny debuger, ale ten tryb jest zalecane. Po uruchomieniu w tym trybie nie ma zabezpieczeń sieci. Wybierz tryb Bez uwierzytelniania tylko wtedy, gdy masz pewność, że sieć nie jest zagrożona przez złośliwe lub wrogie działania.  
  
##  <a name="BKMK_DirectConnect"></a>Jak połączyć się bezpośrednio do urządzenia zdalnego  
 Aby połączyć się bezpośrednio do urządzenia zdalnego, podłącz komputer programu Visual Studio do urządzenia za pomocą kabla Ethernet standardowa. Jeśli urządzenie nie ma portu sieci Ethernet, można użyć USB do Ethernet do nawiązania połączenia kabel.  
  
## <a name="BKMK_download"></a>Pobierz i zainstaluj narzędzia zdalnej

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
## <a name="BKMK_setup"></a>Konfigurowanie zdalnego debugera

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]
  
##  <a name="BKMK_ConnectVS"></a>Konfigurowanie projektu programu Visual Studio zdalne debugowanie  
 Należy określić urządzenie zdalne, aby nawiązać połączenie we właściwościach projektu. Procedura zależy od języka programowania. Możesz wpisać nazwę sieciową urządzenie zdalne lub można wybrać w oknie dialogowym Wybierz połączenia zdalnego debugera.  
  
 ![Wybierz okno dialogowe połączenia zdalnego debugera](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 Okno dialogowe wyświetla tylko te urządzenia, które są w podsieci lokalnej komputera programu Visual Studio i działają zdalnego debugera.  
  
> [!TIP]
>  Jeśli masz problemy z połączeniem urządzenie zdalne, spróbuj wprowadzić adres IP urządzenia. Aby określić adres IP urządzenia, Otwórz okno polecenia, a następnie wpisz **ipconfig**. Adres IP jest wymieniony jako **adres IPv4**.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a>Wybranie urządzenia zdalnego dla projektów C# i Visual Basic  
 ![Właściwości projektu zdalne debugowanie zarządzane](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1.  Wybierz nazwę projektu w Eksploratorze rozwiązań, a następnie wybierz pozycję **właściwości** z menu skrótów.  
  
2.  Wybierz **debugowania**.  
  
3.  Wybierz **maszyny zdalnej** z **urządzenie docelowe** listy.  
  
4.  Wprowadź nazwę sieci urządzenie zdalne w **maszyny zdalnej** wpisz lub wybierz **znaleźć** aby wybrać urządzenie z **wybierz połączenia zdalnego debugera** okno dialogowe.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a>Wybranie urządzenia zdalnego dla projektów języka JavaScript i C++  
 ![& C &43; 43; właściwości do zdalnego debugowania projektu](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1.  Wybierz nazwę projektu w Eksploratorze rozwiązań, a następnie wybierz pozycję **właściwości** z menu skrótów.  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzeł, a następnie wybierz **debugowanie**.  
  
3.  Wybierz **zdalnego debugera** z **debugera, aby uruchomić** listy.  
  
4.  Wprowadź nazwę sieci urządzenie zdalne w **Nazwa maszyny** wpisz lub wybierz strzałkę w dół w polu, aby wybrać urządzenie z **wybierz połączenia zdalnego debugera** okno dialogowe.  
  
##  <a name="BKMK_RunRemoteDebug"></a>Uruchomiona sesja debugowania zdalnego  
 Uruchom, Zatrzymaj, a nawigowanie po sesji debugowania zdalnego tak samo jak sesji lokalnej. Przed rozpoczęciem debugowania, upewnij się, że Monitor debugera zdalnego działa na urządzeniu zdalnym.  
  
 Następnie wybierz pozycję **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5). Projekt jest ponownie kompilowana, następnie wdrożyć i uruchomić na urządzeniu zdalnym. Debuger wstrzymuje wykonywanie w punktów przerwania i można przejść do, za pośrednictwem i z kodu. Wybierz **Zatrzymaj debugowanie** zakończyć sesję debugowania i zamknij aplikację zdalnego. Aby uzyskać więcej informacji, zobacz [debugowania aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Testowanie aplikacji platformy uniwersalnej systemu Windows za pomocą programu Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)