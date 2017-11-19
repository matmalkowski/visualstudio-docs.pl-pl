---
title: "Włącz debugowanie aplikacji ASP.NET | Dokumentacja firmy Microsoft"
ms.custom: H1HackMay2017
ms.date: 09/21/17
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
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
caps.latest.revision: "37"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9048f965ad2f04b4eed8fe3a753f6fddc280dbfa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="debug-aspnet-applications-in-visual-studio"></a>Debugowanie aplikacji ASP.NET w programie Visual Studio

Można debugować aplikacji ASP.NET w programie Visual Studio.

## <a name="requirements"></a>Wymagania

Postępuj zgodnie z instrukcjami w tym temacie, potrzebne są:

- Usługi IIS Express, który jest dostępny domyślnie w programie Visual Studio 2012 i nowsze

    —lub—

- Lokalny serwer (w wersji 8.0 lub nowszej), który jest poprawnie skonfigurowany i uruchomić aplikację ASP.NET bez błędów sieci web IIS.

W przypadku zdalnego serwera zdalnego debugera musi działać na komputerze zdalnym. Do debugowania na zdalnym serwerze usług IIS, zobacz [zdalnego debugowania ASP.NET na komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). 

## <a name="configure-debug-settings"></a>Skonfiguruj ustawienia debugowania

### <a name="enable-aspnet-debugging-in-the-project-properties"></a>Włącz debugowanie ASP.NET we właściwościach projektu

1. Otwórz projekt ASP.NET w programie Visual Studio.

2. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**, wybierz **właściwości**, a następnie kliknij przycisk **Web** kartę.

    W przypadku niektórych typów projektu, zaznacz **właściwości > debugowanie** zamiast tego. Dla projektu sieci Web formularzy ASP.NET, kliknij prawym przyciskiem myszy projekt i wybierz **strony właściwości > Opcje uruchamiania**.
  
3.  W obszarze **debugery**, wybierz pozycję **ASP.NET** pole wyboru.

    ![Ustawienia debugera](../debugger/media/dbg-aspnet-enable-debugging.png "ustawienia debugera")

> [!NOTE]
> Jeśli tworzysz nowy projekt ASP.NET (**Plik > Nowy projekt**), ustawienia debugowania są już skonfigurowane poprawnie.

### <a name="enable-debugging-in-the-webconfig-file"></a>Włącz debugowanie w pliku web.config  

Debugowanie aplikacji sieci web, muszą być prawidłowo skonfigurowane pliku web.config aplikacji. Plik web.config jest wymagany, jeśli host aplikacji usług IIS lub usług IIS Express.

Dla platformy ASP.NET Core plik web.config jest tworzona automatycznie, gdy aplikacja jest wdrożona (jeśli go nie ma już).

> [!TIP]
> Proces wdrażania może zaktualizować ustawienia pliku web.config. Dlatego przed próbą debugowania, sprawdź ustawienia pliku web.config na serwerze.
  
1.  W programie Visual Studio Otwórz plik web.config projektu.  
  
    > [!NOTE]  
    > Za pomocą przeglądarki sieci Web nie może zdalnie dostępu do pliku web.config. Ze względów bezpieczeństwa [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] umożliwia skonfigurowanie programu Microsoft IIS ułatwia zapobieganie bezpośredni dostęp z przeglądarki w plikach Web.config. Jeśli spróbujesz uzyskać dostęp do pliku konfiguracji za pomocą przeglądarki sieci występuje błąd dostępu HTTP 403 (Dostęp zabroniony).  
  
2.  Zlokalizuj `configuration/system.web/compilation` elementu. Jeśli element kompilacji nie istnieje, należy go utworzyć.

    Web.config jest plikiem XML, a więc zawiera zagnieżdżone sekcje oznaczony według znaczników.
  
3.  Jeśli `compilation` nie zawiera elementu `debug` atrybutu, Dodaj atrybut do elementu.  
  
4.  Upewnij się, że `debug` ma ustawioną wartość atrybutu `true`.  
  
Plik web.config powinna wyglądać następująco:

> [!NOTE]
> W tym przykładzie jest to plik web.config częściowej. Dodatkowe sekcje XML są zwykle dostępne między serwerem konfiguracji i elementy system.web. Element kompilacji może także zawierać inne atrybuty i elementy.
  
#### <a name="example"></a>Przykład  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```

Jeśli używasz zewnętrznego serwera zamiast domyślnego serwera usług IIS Express, użytkownik musi również upewnij się, że `targetFramework` wartość atrybutu jest zgodne z konfiguracją na serwerze.

> [!IMPORTANT]
> Aby uzyskać najlepszą wydajność, ustaw aplikacji produkcyjnej `debug=false` i określ kompilację wersji podczas kompilacji i publikowanie aplikacji.

## <a name="configure-project-settings-for-the-server"></a>Skonfiguruj ustawienia projektu dla serwera

Do debugowania na serwerze sieci web lokalny, ustaw właściwości projektu. Do debugowania na serwerze zdalnym, postępuj zgodnie z instrukcjami wyczerpujący, opisanego w [zdalnego debugowania ASP.NET w usługach IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) zamiast tego.

1. W **Web** projektu na karcie właściwości, wybierz opcję **usług IIS Express** lub **zewnętrznego serwera** w obszarze **serwera** ustawienia. (Dla niektórych typów projektów, te ustawienia są wyświetlane w polu **debugowania** karcie zamiast.)

    ![Ustawienia serwera](../debugger/media/dbg-aspnet-server-settings.png "ustawienia serwera")

    Usługi IIS Express jest serwerem domyślnym dla platformy ASP.NET i zwykle nie wymaga żadnej specjalnej konfiguracji. To jest najprostszym sposobem debugowania aplikacji ASP.NET.

    Dla projektu sieci Web formularzy ASP.NET, kliknij prawym przyciskiem myszy projekt, wybierz **strony właściwości > Opcje uruchamiania**i wybierz opcję **Użyj domyślnego serwera sieci Web** lub **Użyj niestandardowego serwera** () zamiast **zewnętrznego serwera**).

    ![Ustawienia serwera dla aplikacji formularzy sieci Web](../debugger/media/dbg-aspnet-server-settings-webforms.png "ustawień serwera dla aplikacji formularzy sieci Web")

2. Jeśli wybierzesz serwer zewnętrzny (niestandardowy), wprowadź prawidłowy adres URL w **adres URL projektu** (lub **podstawowego adresu URL**) pola.

    Serwer zewnętrzny w przypadku lokalnego usług IIS, usługi IIS musi być zainstalowana i poprawnie skonfigurowany. Na przykład należy skonfigurować odpowiedniej wersji programu ASP.NET w usługach IIS. Aby uzyskać więcej informacji, zobacz [IIS 8.0 przy użyciu programu ASP.NET 3.5 i ASP.NET 4.5](https://docs.microsoft.com/en-us/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). Jeśli chcesz przetestować wdrożenie, a także debugowania, zobacz [wdrażanie do testowania](https://docs.microsoft.com/en-us/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/deploying-to-iis).

    Jeśli serwer zewnętrzny [zdalnego](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), możesz dołączyć do procesu zamiast i te ustawienia projektu nie są używane do debugowania.

## <a name="local-iis-web-server-configure-iis"></a>(Serwer sieci web IIS lokalnych) Konfigurowanie usług IIS

Dla usług IIS Express, nie musisz skonfigurować serwer sieci web (Pomiń tę sekcję). Usługi IIS Express jest zalecane do początkowego testowania.

Jeśli korzystasz z lokalnego serwera sieci web usług IIS, wykonaj następujące kroki.

1. Upewnij się, że prawidłowo zainstalowano usług IIS. Aby uzyskać więcej informacji, zobacz [IIS 8.0 przy użyciu programu ASP.NET 3.5 i ASP.NET 4.5](https://docs.microsoft.com/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    * Upewnij się, zainstaluj poprawną wersję platformy ASP.NET na serwerze. Instalator platformy sieci Web (WebPI) należy zainstalować funkcję ASP.NET 4.5 (z węzła serwera w systemie Windows Server 2012 R2, wybierz **pobrać nowych składników platformy sieci Web** , a następnie wyszukaj ASP.NET). Aby zainstalować program ASP.NET Core, zobacz [publikowania w usługach IIS](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration).

    > [!NOTE]
    > Jeśli używasz systemu Windows Server 2008 R2 można zainstalować programu ASP.NET 4 zamiast za pomocą tego polecenia:

     **C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe - ir**

2. Otwórz **internetowych usług informacyjnych (IIS) Manager**. (W lewym okienku w Menedżerze serwera wybierz **IIS**. Kliknij prawym przyciskiem myszy serwer, a następnie wybierz **Internet Information Services (IIS) Manager**.)

3. W obszarze **połączeń** w okienku po lewej stronie, przejdź do **witryny**.

4. Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** a następnie wybierz węzeł **Dodawanie aplikacji**.

5. Ustaw **Alias** do **MyASPApp**, zaakceptuj wartość domyślną pulę aplikacji (**DefaultAppPool**) i ustaw **ścieżka fizyczna** do  **C:\inetpub\myNewFolder** (Utwórz nowy folder na potrzeby aplikacji).

6. W obszarze **połączeń**, wybierz pozycję **pul aplikacji**. Otwórz **DefaultAppPool** i ustaw pole puli aplikacji na wartość, która jest prawidłowa dla aplikacji (użycie programu ASP.NET 4 dla programu ASP.NET 4.5. Użyj **żadnego kodu zarządzanego** dla platformy ASP.NET Core).

## <a name="local-iis-web-server-deploy-the-app"></a>(Serwer sieci web IIS lokalnych) Wdrażanie aplikacji

Dla usług IIS Express, aplikacji sieci web zostanie wdrożona automatycznie po rozpoczęciu debugowania (Pomiń tę sekcję).

Jeśli korzystasz z lokalnego serwera sieci web usług IIS, wykonaj następujące kroki. Istnieją różne sposoby publikowanie aplikacji w usługach IIS. W tych krokach zostanie przedstawiony sposób tworzenia i używania profil publikowania, dzięki czemu można wdrożyć przy użyciu systemu plików.

1. Uruchom ponownie program Visual Studio jako Administrator.

    Aby wdrożyć przy użyciu tej metody, potrzebne są uprawnienia administratora.

2. W programie Visual Studio, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **publikowania** (formularzy sieci Web, można użyć **publikowania aplikacji sieci Web**).

3. Wybierz **usług IIS, FTP, itp.** i kliknij przycisk **publikowania**.

    ![Publikowanie w usługach IIS](../debugger/media/dbg-aspnet-local-iis.png "publikowanie w usługach IIS")

    W przypadku aplikacji formularzy sieci Web wybierz **niestandardowy** w oknie dialogowym Publikowanie, wprowadź nazwę profilu, a następnie wybierz pozycję **OK**.

4. W **metody publikowania** wybierz **system plików**.

5. Aby uzyskać **lokalizacja docelowa**, kliknij przycisk **Przeglądaj** przycisku.

6. (Platformy ASP.NET Core) Wybierz **systemu plików** i wybierz folder, w którym utworzona uprzednio dla aplikacji.

6. (ASP.NET) Wybierz **lokalne usługi IIS**i wybierz witrynę sieci web, a następnie kliknij wcześniej utworzony **Otwórz**.

    ![Publikowanie w usługach IIS](../debugger/media/dbg-aspnet-local-iis-select-site.png "publikowanie w usługach IIS")

    > [!TIP]
    > Jeśli widzisz, czy komunikat informujący, serwer sieci web nie jest poprawnie skonfigurowana, upewnij się, zainstalowanie odpowiedniej wersji programu ASP.NET w usługach IIS.

7. Kliknij przycisk **dalej** i wybierz polecenie **debugowania** konfiguracji.

    > [!NOTE]
    > W przypadku wdrożenia w wersji konfiguracji, to ustawienie `debug=false` w pliku web.config serwera.

8. Kliknij przycisk **zapisać** można zapisać ustawień publikowania, a następnie kliknij przycisk **publikowania**.

    > [!CAUTION]
    >  Jeśli chcesz dokonać zmian kodu lub skompiluj ponownie, należy ponownie opublikować i powtórz ten krok. Plik wykonywalny skopiowane na komputer zdalny musi dokładnie odpowiadać lokalnego źródłowe i symboli.

## <a name="set-a-breakpoint-and-start-debugging"></a>Ustaw punkt przerwania i Rozpocznij debugowanie

1. W projekcie w programie Visual Studio Ustaw punkt przerwania dla niektórych kodu, który zostanie uruchomiony.

2. Aby rozpocząć debugowanie, naciśnij klawisz **F5** (**Debuguj > Rozpocznij debugowanie**).

3. Podjąć działania w celu uruchomienia kodu, który zawiera punkt przerwania.

    Wstrzymuje działanie debugera, którym można ustawić punktu przerwania.

### <a name="local-iis-troubleshooting-cannot-hit-the-breakpoint"></a>(Lokalne usługi IIS) Rozwiązywanie problemów: Nie można trafiony punkt przerwania

1. Uruchamiają aplikację sieci web za pomocą programu IIS i upewnij się, że działa prawidłowo. Pozostaw uruchomieniu aplikacji sieci web.

2. W programie Visual Studio, wybierz **Debuguj > dołączyć do procesu** i połączyć się z procesem ASP.NET (zazwyczaj **w3wp.exe** lub **dotnet.exe**). Aby uzyskać więcej informacji, zobacz [dołączyć do procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

    Jeśli można nawiązać połączenia przy użyciu **dołączyć do procesu** można trafiony punkt przerwania, ale nie można rozpocząć debugowanie przy użyciu **F5**, a następnie istnieje duże prawdopodobieństwo, że jest to ustawienie jest nieprawidłowe we właściwościach projektu. Jeśli korzystasz z pliku HOSTS, sprawdź, czy został on poprawnie skonfigurowany.

  
## <a name="robust-programming"></a>Niezawodne programowanie  
[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]automatycznie wykrywa zmiany wprowadzone w plikach Web.config i zastosowanie nowych ustawień konfiguracji. Nie trzeba ponownie uruchomić komputer lub uruchom ponownie serwer usług IIS, aby zmiany zaczęły obowiązywać.  
  
Witryny sieci Web może zawierać wiele katalogów wirtualnych i podkatalogów, a pliki Web.config mogą istnieć w każdej z nich. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]aplikacje dziedziczyć ustawień z plików Web.config na wyższych poziomach ścieżkę adresu URL. Pliki konfiguracji hierarchiczna umożliwiają zmianę ustawień dla wielu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji w tym samym czasie, takie jak w przypadku wszystkich aplikacji pod nią w hierarchii. Jednak jeśli `debug` jest ustawiona w pliku niżej w hierarchii, zastępuje on wyższej wartości.  
  
Na przykład można określić `debug="true"` www.microsoft.com/aaa/Web.config i dowolnej aplikacji, w tym folderze aaa lub w dowolnym podfolderze aaa dziedziczy to ustawienie. Jeśli Twoje [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacja znajduje się na www.microsoft.com/aaa/bbb, dziedziczy on, że ustawienie, podobnie jak wszelkie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji w www.microsoft.com/aaa/ccc, www.microsoft.com/aaa/ddd i tak dalej. Jedynym wyjątkiem jest jedną z tych aplikacji zastępuje ustawienie za pomocą własnego niższe pliku Web.config.  
  
> [!IMPORTANT]
> Włączenie trybu debugowania znacznie wpływa na wydajność sieci [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji. Pamiętaj, aby wyłączyć tryb debugowania przed wdrożyć aplikację wersji lub przeprowadzić wskaźników wydajności.  
  
## <a name="see-also"></a>Zobacz też  
[ASP.NET debugowanie: wymagania systemowe](aspnet-debugging-system-requirements.md)   
[Porady: uruchamianie procesu roboczego na koncie użytkownika](how-to-run-the-worker-process-under-a-user-account.md)   
[Porady: znajdowanie nazwy procesu ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)   
[Debugowanie wdrożonych aplikacji sieci Web](debugging-deployed-web-applications.md)   
[Wskazówki: Debugowanie formularzy sieci Web](walkthrough-debugging-a-web-form.md)   
[Porady: debugowanie wyjątków ASP.NET](how-to-debug-aspnet-exceptions.md)   
[Debugowanie aplikacji sieci Web: błędy i rozwiązywanie problemów](debugging-web-applications-errors-and-troubleshooting.md)
  