---
title: "Nie można nawiązać połączenia z programem Microsoft Visual Studio Monitor debugera zdalnego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 08/24/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.error.remote_debug
- vs.debug.error.firewall.remotemachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: a1d959fc-3817-491c-831b-e6b768a3877a
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3484ac7aa26f630245a471a234dd19468e50ebf0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Nie można połączyć się z Monitorem debugera zdalnego programu Microsoft Visual Studio
Ten komunikat może wystąpić, ponieważ monitor debugera zdalnego nie prawidłowo ustawiono na zdalnym komputerze lub komputer zdalny jest niedostępny z powodu problemów z siecią lub obecności zapory.
  
> [!IMPORTANT]
>  Jeśli uważasz, otrzymano tego komunikatu z powodu błędu w produkcie, skontaktuj się z [Zgłoś problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) dla programu Visual Studio. Jeśli potrzebujesz więcej pomocy, zobacz [Porozmawiaj z nami](../ide/talk-to-us.md) sposobów kontakt z firmą Microsoft.

## <a name="specificerrors"></a>Co to jest szczegółowy komunikat o błędzie?

`Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` Wiadomości jest rodzajowy. Zazwyczaj bardziej szczegółowych komunikatów jest uwzględniona w parametrach błąd i zidentyfikować przyczynę problemu lub Wyszukaj bardziej dokładne poprawkę, mogą pomóc. Poniżej przedstawiono kilka częściej komunikaty o błędach, które są dołączane do głównego komunikat:

- [Debuger nie może połączyć się z komputerem zdalnym. Debuger nie może rozpoznać określonej nazwy komputera](#cannot_connect)
- [Żądanie połączenia zostało odrzucone przez debuger zdalny](#rejected)
- [Nieprawidłowy dostęp do lokalizacji w pamięci](#invalid_access)
- [Serwer nie jest określona nazwa uruchomiony na komputerze zdalnym](#no_server)
- [Żądana nazwa jest prawidłowa, ale nie żądanego typu znaleziono danych](#valid_name)
- [Debuger programu Visual Studio zdalnego na komputerze docelowym nie może połączyć się ponownie z tym komputerem](#cant_connect_back)
- [Odmowa dostępu](#access_denied)
- [Wystąpił błąd określonego pakietu zabezpieczeń](#security_package)

## <a name="cannot_connect"></a>Debuger nie może połączyć się z komputerem zdalnym. Debuger nie może rozpoznać określonej nazwy komputera

Spróbuj wykonać następujące kroki:

1. Upewnij się, że należy wprowadzić prawidłową nazwę komputera i numer portu w **dołączyć do procesu** okno dialogowe lub we właściwościach projektu (można ustawić właściwości, zobacz [te kroki](#server_incorrect)). Nazwa komputera musi mieć następujący format:

    `computername:port`

    > [!NOTE]
    > Numer portu musi być zgodny [numer_portu zdalny debuger](../debugger/remote-debugger-port-assignments.md), który *musi być uruchomiona* na komputerze docelowym.

2. Jeśli nazwa komputera nie działa, spróbuj adres IP i numer portu w zamian.

3. Upewnij się, że wersja zdalnego debugera, które są uruchomione na maszynie docelowej zgodna używanej wersji programu Visual Studio. Aby zainstalować poprawną wersję zdalnego debugera, zobacz [zdalnego debugowania](../debugger/remote-debugging.md).

    > [!TIP]
    > Jeśli dołączania do procesu i uda się nawiązać połączenia, ale nie widzisz procesu, który ma, zaznacz **Pokaż procesy wszystkich pola wyboru Użytkownicy**. To spowoduje Pokaż procesy jeśli nawiązano połączenie przy użyciu konta innego użytkownika.

4. Jeśli te czynności nie rozwiąże ten błąd, zobacz [komputer zdalny jest nieosiągalny](#dns).

## <a name="rejected"></a>Żądanie połączenia zostało odrzucone przez debuger zdalny

W **dołączyć do procesu** okno dialogowe lub we właściwościach projektu, upewnij się, że nazwa komputera zdalnego i numer portu jest zgodna z liczbą portu i wyświetlany w oknie zdalnego debugera. Jeśli jest nieprawidłowy, Usuń i spróbuj ponownie.

Jeśli te wartości są poprawne i uwagi komunikat **uwierzytelniania systemu Windows** tryb, sprawdź, czy zdalny debuger jest poprawny tryb uwierzytelniania (**Narzędzia > Opcje**).

## <a name="invalid_access"></a>Nieprawidłowy dostęp do lokalizacji w pamięci

Wystąpił błąd wewnętrzny. Uruchom ponownie program Visual Studio i spróbuj ponownie.

## <a name="no_server"></a>Serwer nie jest określona nazwa uruchomiony na komputerze zdalnym

Program Visual Studio nie może połączyć się ze zdalnym debugerem. Ten komunikat może wystąpić z kilku powodów:

- Zdalny debuger może być uruchomiony przy użyciu konta innego użytkownika. Zobacz [te kroki](#user_accounts)

- Port jest zablokowany na zaporze. Upewnij się, że Zapora jest [nie blokuje żądania](#firewall), zwłaszcza, jeśli używasz zapory innych firm.

- Wersja zdalnego debugera jest niezgodna z programu Visual Studio. Aby zainstalować poprawną wersję zdalnego debugera, zobacz [debugowanie zdalne](../debugger/remote-debugging.md)


## <a name="#valid_name"></a>Żądana nazwa jest prawidłowa, ale nie żądanego typu znaleziono danych

Komputer zdalny istnieje, ale Visual Studio nie może połączyć się ze zdalnym debugerem. Ten komunikat może wystąpić z kilku powodów:

- Problemy z usługą DNS uniemożliwia połączenie. Zobacz [te kroki](#dns).

- Zdalny debuger może być uruchomiony przy użyciu konta innego użytkownika. Postępuj zgodnie z [te kroki](#user_accounts).

- Port jest zablokowany na zaporze. Upewnij się, że Zapora jest [nie blokuje żądania](#firewall), zwłaszcza, jeśli używasz zapory innych firm.

- Wersja zdalnego debugera jest niezgodna z programu Visual Studio. Aby zainstalować poprawną wersję zdalnego debugera, zobacz [zdalnego debugowania](../debugger/remote-debugging.md).

## <a name="cant_connect_back"></a>Debuger programu Visual Studio zdalnego na komputerze docelowym nie może połączyć się ponownie z tym komputerem

Zdalny debuger może być uruchomiony przy użyciu konta innego użytkownika. Zdalny debuger, otwórz **Narzędzia > uprawnienia** można dodać użytkownika do zdalnego debugera uprawnienia. Aby uzyskać więcej informacji, zobacz [debuger zdalny jest uruchomiony przy użyciu konta innego użytkownika](#user_accounts).

Jeśli komunikat o błędzie zawiera również zapory, zapora na maszynie lokalnej uniemożliwiają komunikacji z komputerem zdalnym, wróć do programu Visual Studio. Zobacz [te kroki](#firewall).

## <a name="access_denied"></a>Odmowa dostępu

Ten błąd może zostać wyświetlony podczas debugowania na zdalnym komputerze 64-bitowych z 32-bitowym komputerze (nieobsługiwane).

## <a name="security_package"></a>Wystąpił błąd określonego pakietu zabezpieczeń

Może to być problemem starszych specyficzne dla systemu Windows XP i Windows 7. Zobacz to [informacji](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package). 

## <a name="causes-and-recommendations"></a>Przyczyny i zalecenia

### <a name="dns"></a>Komputer zdalny jest nieosiągalny 

Jeśli nie można połączyć, używając nazwy komputera zdalnego, spróbuj zamiast adresu IP. Można użyć `ipconfig` w wierszu polecenia na komputerze zdalnym, aby uzyskać adres IPv4. Jeśli korzystasz z pliku HOSTS, sprawdź, czy został on poprawnie skonfigurowany.

Jeśli się nie powiedzie, sprawdź, czy komputer zdalny jest dostępny w sieci ([ping](https://technet.microsoft.com/en-us/library/cc732509(v=ws.10).aspx) maszyny zdalnej). Debugowanie zdalne przez Internet nie jest obsługiwana, chyba że w niektórych scenariuszach Microsoft Azure.
  
### <a name="server_incorrect"></a>Nazwa serwera jest niepoprawna lub uniemożliwiać zdalny debuger oprogramowania innych firm

W programie Visual Studio Sprawdź właściwości projektu i upewnij się, że nazwa serwera jest poprawna. W tematach [C# i Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) i [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus). Dla platformy ASP.NET, otwórz **właściwości / Web / serwery** lub **właściwości / Debug** zależnie od typu projektu.

> [!NOTE]
> Ustawienia zdalnego we właściwościach projektu nie są używane, jeśli dołączania do procesu.

Jeśli nazwa serwera jest poprawna, oprogramowanie antywirusowe lub zapory innych firm mogą być blokowane zdalnego debugera. Podczas debugowania lokalnie, może to się zdarzyć Visual Studio jest 32-bitowej aplikacji, więc używa 64-bitowej wersji zdalnego debugera do debugowania aplikacji 64-bitowych. 32-bitowe i 64-bitowe procesy komunikują się za pomocą sieci lokalnej na komputerze lokalnym. Dlatego ruchu sieciowego do komputera, ale istnieje możliwość, że oprogramowanie zabezpieczające innych firm może blokować komunikację.

### <a name="user_accounts"></a>Zdalny debuger działa w ramach innego konta użytkownika 

Zdalny debuger domyślnie przyjmuje tylko połączenia od użytkownika, który uruchomił zdalny debuger i członkowie grupy Administratorzy. Dodatkowym użytkownikom trzeba jawnie przyznane uprawnienia. 
 
Użytkownik może rozwiązać ten problem w jednym z następujących sposobów:  

-   Dodaj użytkownika programu Visual Studio do zdalnego debugera uprawnień (w oknie zdalnego debugera, wybierz **Narzędzia > uprawnienia**).

-   Na komputerze zdalnym Uruchom ponownie debuger zdalny w ramach tego samego konta użytkownika i hasło, którego używasz na komputerze programu Visual Studio.

    > [!NOTE]
    > Jeśli używasz zdalnego debugera na serwerze zdalnym, kliknij prawym przyciskiem myszy aplikację zdalny debuger i wybierz pozycję **Uruchom jako administrator** (lub, można uruchomić zdalnego debugera jako usługi). Jeśli nie używasz go na serwerze zdalnym, wystarczy ją uruchomić normalnie.
  
-   Zdalny debuger można uruchomić z wiersza polecenia z **/ Zezwalaj \<nazwa użytkownika >** parametru: `msvsmon /allow <username@computer>`. 
  
-   Alternatywnie można zezwolić każdy użytkownik w celu debugowania zdalnego. W oknie zdalnego debugera, przejdź do **Narzędzia > Opcje** okna dialogowego. Po wybraniu **bez uwierzytelniania**, można sprawdzić **Zezwalaj dowolnemu użytkownikowi na debugowanie**. Należy jednak tę opcję tylko wtedy, gdy inne opcje się nie powieść lub jeśli w sieci prywatnej.

### <a name="firewall"></a>Zapora na zdalnym komputerze nie zezwalać na połączenia przychodzące do zdalnego debugera  
 Zapora na maszynie programu Visual Studio i zapory na zdalnym komputerze muszą być skonfigurowane do zezwalania na komunikację między i zdalny debuger programu Visual Studio. Informacje o portach używa zdalnego debugera, zobacz [przypisania portów usługi zdalnego debugera](../debugger/remote-debugger-port-assignments.md). Aby uzyskać informacje o konfigurowaniu zapory systemu Windows, zobacz [konfigurowania Zapory systemu Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).
  
### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Wersja zdalnego debugera nie pasuje do wersji programu Visual Studio  
 Wersji programu Visual Studio, które działają lokalnie musi być zgodna z wersją monitor debugera zdalnego działa na komputerze zdalnym. Aby rozwiązać ten problem, Pobierz i zainstaluj zgodną wersję monitor debugera zdalnego. Aby zainstalować poprawną wersję zdalnego debugera, zobacz [zdalnego debugowania](../debugger/remote-debugging.md).
  
### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Tryby uwierzytelniania inny ma maszyny lokalne i zdalne  
 Maszyny lokalne i zdalne muszą używać tego samego trybu uwierzytelniania. Aby rozwiązać ten problem, upewnij się, że obie maszyny używają tego samego trybu uwierzytelniania. Można zmienić trybu uwierzytelniania. W oknie zdalnego debugera, przejdź do **Narzędzia > Opcje** okno dialogowe.
  
 Aby uzyskać więcej informacji na temat trybów uwierzytelniana, zobacz [omówienie uwierzytelniania systemu Windows](https://technet.microsoft.com/en-us/library/hh831472.aspx).   
  
### <a name="anti-virus-software-is-blocking-the-connections"></a>Oprogramowanie antywirusowe blokuje połączenia  
 Oprogramowanie antywirusowe systemu Windows zezwala na połączenia zdalnego debugera, ale niektóre programy antywirusowe innych firm mogą je zablokować. Sprawdź dokumentację oprogramowanie antywirusowe dowiedzieć się, jak zezwolić na te połączenia.  
  
### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Zasady zabezpieczeń sieci blokuje komunikację między komputerem zdalnym i Visual Studio  
 Przejrzyj zabezpieczenia sieci, aby upewnić się, że nie blokuje komunikacji. Aby uzyskać więcej informacji dotyczących zasad zabezpieczeń sieciowych systemu Windows, zobacz [ustawienia zasad zabezpieczeń](/windows/device-security/security-policy-settings/security-policy-settings).  
  
### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Sieć jest zbyt zajęty, aby zapewnić obsługę zdalnego debugowania  
 Może być konieczne zdalnego debugowania w innym czasie, lub Zmień harmonogram pracy w sieci przez inny czas.  
  
## <a name="more-help"></a>Więcej informacji  
 Aby uzyskać zdalny debuger pomocy, otwórz stronę pomocy zdalny debuger (**Pomoc > użycia** w zdalnym debugerze).
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)