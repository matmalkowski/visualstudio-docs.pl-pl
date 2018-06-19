---
title: Zdalne debugowanie projektu Visual C++ | Dokumentacja firmy Microsoft
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 8b8eca0d-122f-4eda-848a-cf0945f207d0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 334a0b964033282458c211d69af30aad20dbd6bc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31478112"
---
# <a name="remote-debugging-a-visual-c-project-in-visual-studio"></a>Zdalne debugowanie projektu Visual C++ w programie Visual Studio
Debugowanie aplikacji Visual Studio na innym komputerze, zainstalować i uruchomić narzędzia zdalnej na komputerze, których będą wdrażać aplikacji, należy skonfigurować z projektem, aby połączyć się z komputerem zdalnym z programu Visual Studio, a następnie wdrożyć i uruchom aplikację.

![Składniki zdalnego debugera](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Informacje debugowania uniwersalnych aplikacji systemu Windows (UWP) zdalnego, zobacz [Debuguj zainstalowany pakiet aplikacji](debug-installed-app-package.md).

## <a name="requirements"></a>Wymagania

Zdalny debuger jest obsługiwane w systemie Windows 7 i nowsze (nie phone) i wersji systemu Windows Server, począwszy od systemu Windows Server 2008 Service Pack 2. Aby uzyskać pełną listę wymagań, zobacz [wymagania](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Debugowanie między dwoma komputerami połączone za pośrednictwem serwera proxy nie jest obsługiwane. Debugowanie za pośrednictwem duże opóźnienie lub połączenia o niskiej przepustowości, takich jak Internet, połączenia telefonicznego lub przez Internet między krajów nie jest zalecana i może się nie powieść lub zbyt wolno.
  
## <a name="download-and-install-the-remote-tools"></a>Pobierz i zainstaluj narzędzia zdalnej

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
> [!TIP]
> W niektórych scenariuszach może być najbardziej efektywny do uruchamiania zdalnego debugera z udziału plików. Aby uzyskać więcej informacji, zobacz [uruchamiania zdalnego debugera z udziału plików](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a> Konfigurowanie zdalnego debugera

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Jeśli należy dodać uprawnienia dla dodatkowych użytkowników do zmiany trybu uwierzytelniania lub numer portu dla zdalnego debugera, zobacz [skonfigurować debugera zdalnego](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote_cplusplus"></a> Zdalne debugowanie projektu Visual C++  
 W poniższej procedurze, nazwa i ścieżka projektu jest C:\remotetemp\MyMfc i nazwa komputera zdalnego jest **MJO DL**.  
  
1.  Tworzenie aplikacji MFC o nazwie **mymfc.**  
  
2.  Ustaw punkt przerwania gdzieś w aplikacji, które łatwo osiągnięciu, na przykład w **MainFrm.cpp**, na początku `CMainFrame::OnCreate`.  
  
3.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **właściwości**. Otwórz **debugowanie** kartę.  
  
4.  Ustaw **debugera, aby uruchomić** do **zdalnego debugera systemu Windows**.  
  
     ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5.  Wprowadź następujące zmiany do właściwości:  
  
    |Ustawienie|Wartość|
    |-|-|  
    |Polecenia zdalnego|C:\remotetemp\mymfc.exe|  
    |Katalog roboczy|C:\remotetemp|  
    |Nazwa serwera zdalnego|MJO DL:*numer_portu*|  
    |Połączenia|Zdalny z uwierzytelnianiem systemu Windows|  
    |Typ debugera|Tylko kod natywny|  
    |Katalog wdrożenia|C:\remotetemp.|  
    |Dodatkowe pliki do wdrożenia|C:\data\mymfcdata.txt.|  
  
     W przypadku wdrożenia dodatkowych plików (opcjonalnie), folder musi istnieć na obu komputerach.  
  
6.  W Eksploratorze rozwiązań kliknij rozwiązanie prawym przyciskiem myszy i wybierz polecenie **programu Configuration Manager**.  
  
7.  Aby uzyskać **debugowania** konfigurację, kliknij **Wdróż** pole wyboru.  
  
     ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8.  Rozpocznij debugowanie (**Debuguj > Rozpocznij debugowanie**, lub **F5**).  
  
9. Plik wykonywalny jest automatycznie wdrażane na komputerze zdalnym.  
  
10. Jeśli zostanie wyświetlony monit, wprowadź poświadczenia sieci, aby połączyć z komputerem zdalnym.  
  
     Wymagane poświadczenia są specyficzne dla konfiguracji zabezpieczeń sieci. Na przykład na komputerze domeny, możesz wybrać certyfikat zabezpieczeń, lub wprowadź nazwę domeny i hasło. Na komputerze z systemem innym niż domeny, wprowadzić nazwę komputera i nazwę konta użytkownika prawidłowy tak samo, jak **MJO-DL\name@something.com**, oraz prawidłowe hasło.  
  
11. Na komputerze programu Visual Studio powinny być widoczne czy wykonanie jest zatrzymana na punkt przerwania.  
  
    > [!TIP]
    >  Alternatywnie można wdrożyć pliki w osobnym kroku. W **Eksploratora rozwiązań** kliknij prawym przyciskiem myszy **mymfc** węzeł, a następnie wybierz **Wdróż**.  
  
 Jeśli masz plików z systemem innym niż kodu, które będzie używane przez aplikację, należy je uwzględnić w projekcie programu Visual Studio. Tworzenie folderu projektu dla dodatkowych plików (w **Eksploratora rozwiązań**, kliknij przycisk **Dodaj > Nowy Folder**.) Następnie dodaj pliki do folderu (w **Eksploratora rozwiązań**, kliknij przycisk **Dodaj > istniejący element**, następnie wybierz pliki). Na **właściwości** strony dla każdego pliku, ustaw **Kopiuj do katalogu wyjściowego** do **skopiuj zawsze**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Konfigurowanie debugowania przy użyciu zdalnego symboli 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)] 
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie w programie Visual Studio](../debugger/index.md)  
 [Przegląd funkcji debugera](../debugger/debugger-feature-tour.md)   
 [Konfigurowanie Zapory systemu Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Przypisania portów debugera zdalnego](../debugger/remote-debugger-port-assignments.md)   
 [Zdalne debugowanie ASP.NET na komputerze zdalnym usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [Zdalne debugowanie błędów i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)