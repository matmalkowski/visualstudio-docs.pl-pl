---
title: "Dodawanie danych o interakcji między warstwy z wiersza polecenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
ms.assetid: 5a35647f-03f2-4555-8eeb-fda7e0080e67
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2d639558434e077a6ae09ce79bad6252a10a3711
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="adding-tier-interaction-data-from-the-command-line"></a>Dodawanie danych o interakcji między warstwami za pośrednictwem wiersza polecenia
Profilowanie interakcji między warstwami zawiera dodatkowe informacje dotyczące godziny wykonywania synchroniczne [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] wywołania funkcji aplikacji wielowarstwowych, które komunikują się z jednego lub więcej baz danych.  
  
 **Windows 8 i Windows Server 2012**  
  
 Zbieranie danych o interakcji warstwy o aplikacji klasycznych systemu Windows 8 i Windows Server 2012 aplikacji należy użyć metody instrumentacji. Zbieranie danych o interakcji między warstwy w aplikacji platformy uniwersalnej systemu Windows nie jest obsługiwana.  
  
 **Wersje Visual Studio**  
  
 Informacje o profilowaniu interakcji między warstwami można zbierać w programach [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] i [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)], Jednak interakcja warstwowa profilowania danych jest możliwy tylko w [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] i [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
 **Zbieranie danych Porada na komputerze zdalnym**  
  
 Do zbierania danych o interakcji między warstwy komputera zdalnego, należy skopiować **vs_profiler_***\<platformy >***_**  *\< Język >***.exe** plik z *VSInstallDir %***\Team Tools\Performance Tools\Setups** folderu maszyny do programu Visual Studio komputer zdalny i zainstaluj go. Nie można użyć narzędzi profilowania w [zdalnego debugowania](../debugger/remote-debugging.md) Pobierz pakiet.  
  
 **Porada raportów**  
  
 Warstwa danych o interakcji między mogą być przeglądane tylko w [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] IDE. Interakcja warstwowa plikowym raportów za pośrednictwem [VSPerfReport](../profiling/vsperfreport.md) nie są dostępne.  
  
## <a name="adding-tier-interaction-data-with-vsperfcmd"></a>Dodawanie warstwy interakcji danych za pomocą narzędzia VSPerfCmd  
 Narzędzia wiersza polecenia VSPerfASPNETCmd pozwala uzyskać dostęp do pełnej funkcjonalności dostępne w narzędziach profilowania. Aby dodać dane profilowania zebrane przy użyciu narzędzia VSPerfCmd interakcja warstwowa, należy użyć **VSPerfCLREnv** narzędzie ustawiania i usuwania zmiennych środowiskowych, które umożliwia danych o interakcji między warstwy. Opcje, które określisz i procedur wymaganych do zbierania danych są zależne od typu aplikacji, które są profilowania.  
  
### <a name="profiling-stand-alone-applications"></a>Profilowanie aplikacji autonomicznych  
 Aby dodać warstwę danych o interakcji między do aplikacji, która nie jest uruchamiane przez inny proces, takie jak Windows aplikacja komputerowa, która sprawia, że synchroniczne [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] połączenia z bazą danych SQL, użyj **VSPerfClrEnv /InteractionOn** opcję, aby ustawić zmienne środowiskowe i **VSPerfClrEnv /InteractionOff** opcję, aby je usunąć.  
  
 W poniższym przykładzie aplikacji pulpitu systemu Windows jest profilowane przy użyciu metody Instrumentacji i zbieranych danych o interakcji między warstwy.  
  
##### <a name="profiling-a-windows-desktop-application-example"></a>Profilowanie jest przykład aplikacji komputerowych systemu Windows  
  
1.  Otwórz okno wiersza polecenia z uprawnieniami administratora. Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Akcesoria**. Kliknij prawym przyciskiem myszy **wiersza polecenia**, a następnie kliknij przycisk **Uruchom jako Administrator**.  
  
2.  Zainicjuj profilowania .NET i Porada zmiennych środowiskowych. Wpisz następujące polecenia:  
  
    ```  
    vsperfclrenv /traceon  
    vsperfclrenv /interactionon  
    ```  
  
3.  Uruchom profilera. Wpisz następujące polecenie:  
  
    ```  
    vsperfcmd /start:trace /output:Desktop_tip.vsp   
    ```  
  
4.  Uruchom aplikację z narzędzia VSPerfCmd. Wpisz następujące polecenie:  
  
    ```  
    vsperfcmd /launch:DesktopApp.exe  
    ```  
  
5.  Wykonywanie aplikacji w celu zbierania danych profilowania, a następnie zamknij aplikację w zwykły sposób.  
  
6.  Wyczyść Porada zmiennych środowiskowych. Wpisz następujące polecenie:  
  
    ```  
    vsperfclrenv /off  
    ```  
  
 Aby uzyskać więcej informacji, zobacz [profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md).  
  
### <a name="profiling-services"></a>Usługi profilowania  
 Z profilu usług, w tym [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji, użyj **VSPerfClrEnv /GlobalInteractionOn** opcję, aby ustawić zmienne środowiskowe i **VSPerfClrEnv /GlobalInteractionOff** opcję, aby je usunąć.  
  
 Gdy są profilowania usług, w tym [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web, często konieczne będzie ponowne uruchomienie komputera, aby włączyć profilowanie.  
  
 W poniższym przykładzie usługi systemu Windows jest profilowane przy użyciu metody instrumenation i zbieranych danych o interakcji między warstwy.  
  
##### <a name="profiling-a-windows-service-example"></a>Profilowanie jest przykład usługi systemu Windows  
  
1.  Jeśli to konieczne, zainstaluj usługę.  
  
2.  Otwórz okno wiersza polecenia z uprawnieniami administratora. Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Akcesoria**. Kliknij prawym przyciskiem myszy **wiersza polecenia**, a następnie kliknij przycisk **Uruchom jako Administrator**.  
  
3.  Inicjowanie .NET profilowania zmiennych środowiskowych. Wpisz następujące polecenie:  
  
    ```  
    vsperfclrenv /globaltraceon  
    ```  
  
4.  Inicjowanie zmiennych środowiskowych PORADĘ. Wpisz następujące polecenie  
  
    ```  
    vsperfclrenv /globalinteractionon  
    ```  
  
5.  Uruchom ponownie komputer, aby zarejestrować zmiennych środowiskowych.  
  
6.  Otwórz okno wiersza polecenia z uprawnieniami administratora.  
  
7.  Uruchom profilera. Wpisz następujące polecenie:  
  
    ```  
    vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
8.  W razie potrzeby uruchom usługę.  
  
9. Dołączanie profilera do usługi. Wpisz następujące polecenie:  
  
    ```  
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
10. Usługa wykonywania i zbierania danych profilowania.  
  
11. Zatrzymaj profilera. Wpisz następujące polecenie:  
  
     `vsperfcmd /detach`  
  
12. Wyczyść .NET i Porada profilowania zmiennych środowiskowych. Wpisz następujące polecenie:  
  
    ```  
    vsperfclrenv /globaloff  
    ```  
  
13. Uruchom ponownie komputer, aby zarejestrować zmiennych środowiskowych wyczyszczone.  
  
 Aby uzyskać więcej informacji, zobacz jeden z następujących tematów:  
  
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
  
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)  
  
## <a name="adding-tier-interaction-data-with-vsperfaspnetcmd"></a>Dodawanie danych o interakcji między warstwy za pomocą VSPerfASPNETCmd  
 Narzędzie wiersza polecenia VSPerfASPNETCmd umożliwia łatwe profilu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web. W porównaniu z **VSPerfCmd** narzędzie wiersza polecenia, opcje zostały zredukowane nie zmiennych środowiskowych, które muszą być ustawione i ponowne uruchomienie komputera nie jest wymagane. Te funkcje VSPerfASPNETCmd Ułatw zbierania danych o interakcji między warstwy wyjątkowo.  
  
 Aby dodać dane zbierane za pomocą VSPerfASPNETCmd profilowania interakcja warstwowa, Dodaj **/TIP** opcji wiersza polecenia. Na przykład użyć poniższego wiersza polecenia do zbierania danych o interakcji między warstwy dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web przy użyciu metody Instrumentacji:  
  
```  
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp  
```  
  
 Aby uzyskać więcej informacji na temat VSPerfASPNETCmd, zobacz [szybkie profilowanie witryny sieci Web za pomocą VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).