---
title: 'Porady: uruchamianie procesu roboczego na koncie użytkownika | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- user accounts, aspnet_wp.exe
- ASP.NET, debugging Web applications
- tools, aspnet_wp.exe
- ASP.NET, tools
- aspnet_wp.exe
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad6407e4768acbeaf32cf4bebaf7064f04f21fba
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>Porady: uruchamianie procesu roboczego z konta użytkownika
Aby skonfigurować komputer, co umożliwia uruchamianie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy (aspnet_wp.exe lub w3wp.exe) przy użyciu konta użytkownika, wykonaj następujące kroki.  

 > [!IMPORTANT]
 > Począwszy od systemu Windows Server 2008 R2, firma Microsoft zaleca użycie [puli](/iis/manage/configuring-security/application-pool-identities) jako tożsamość, dla każdej puli aplikacji.
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-run-aspnetwpexe-under-a-user-account"></a>Aby uruchomić aspnet_wp.exe przy użyciu konta użytkownika  
  
1.  Otwórz plik machine.config, znajduje się na komputerze w folderze CONFIG ścieżka, w którym zainstalowano środowiska wykonawczego.  
  
2.  Znajdź &lt;processModel&gt; sekcji i zmienić atrybuty użytkownika i hasło do nazwy i hasła konta użytkownika, ma aspnet_wp.exe do uruchamiania.  
  
3.  Zapisz plik machine.config.  
  
4.  Na [!INCLUDE[winxpsvr](../debugger/includes/winxpsvr_md.md)], usług IIS 6.0 jest instalowany domyślnie. Odpowiedni proces roboczy jest w3wp.exe.To uruchamiania w trybie aspnet_wp.exe jako proces roboczy usług IIS 6.0, wykonaj następujące kroki:  
  
    1.  Kliknij przycisk **Start**, kliknij przycisk **narzędzia administracyjne** , a następnie wybierz **Internetowe usługi informacyjne**.  
  
    2.  W **Internetowe usługi informacyjne** okno dialogowe, kliknij prawym przyciskiem myszy **witryn sieci Web** folder i wybierz polecenie **właściwości**.  
  
    3.  W **właściwości witryn sieci Web** oknie dialogowym wybierz **usługi**.  
  
    4.  Wybierz **Uruchom usługę WWW w trybie izolacji IIS6.0**.  
  
    5.  Zamknij **właściwości** okno dialogowe i **Menedżera internetowych usług**.  
  
5.  Otwórz wiersz polecenia systemu Windows i zresetuj serwera, uruchamiając:  
  
    ```  
    iisreset  
    ```  
    — lub —  
  
    ```  
    net stop iisadmin /y  
    net start w3svc  
    ```  
  
6.  Zlokalizuj tymczasowy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] folderu plików, która powinna być w tej samej ścieżce co folder konfiguracji. Kliknij prawym przyciskiem myszy tymczasowy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] folder plików i wybierz polecenie **właściwości** menu skrótów.  
  
7.  W **tymczasowe pliki właściwości programu ASP.NET** okno dialogowe, kliknij przycisk **zabezpieczeń** kartę.  
  
8.  Kliknij przycisk **zaawansowane**.  
  
9. W **Zaawansowane ustawienia zabezpieczeń dla Temporary ASP.Net Files** okno dialogowe, kliknij przycisk **Dodaj**.  
  
    **Okno dialogowe Wybieranie użytkownika, komputera lub grupy** pojawi się.  
  
10. Wpisz nazwę użytkownika w **wprowadź nazwę obiektu do wybrania** , a następnie kliknij przycisk **OK**. Nazwa użytkownika musi odpowiada temu formatowi: nazwa_domeny azwa użytkownika.  
  
11. W **wpis uprawnienia dla Temporary ASP.NET Files** okna dialogowego pozycję dla użytkownika **Pełna kontrola**, a następnie kliknij przycisk **OK** zamknąć **wpis dla tymczasowych ASP Pliki .NET** okno dialogowe.  
  
12. A **zabezpieczeń** pojawi się okno dialogowe i zapyta, czy na pewno chcesz zmienić uprawnienia do folderu systemu. Kliknij przycisk **Tak**.  
  
13. Kliknij przycisk **OK** zamknąć **tymczasowe pliki właściwości programu ASP.NET** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
[Debugowanie aplikacji ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
[ASP.NET debugowanie: Wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md)  
  
