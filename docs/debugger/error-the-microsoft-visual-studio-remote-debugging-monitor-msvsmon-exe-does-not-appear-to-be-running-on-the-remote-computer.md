---
title: 'Błąd: Monitor debugera zdalnego Microsoft Visual (MSVSMON.EXE) zdaje się nie być uruchomiony na komputerze zdalnym. | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.server_machine_no_default
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 683af8cf0c75068a58b5e8cf4732cdf69c586d4f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-msvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a>Błąd: Monitor debugera zdalnego Microsoft Visual (MSVSMON.EXE) zdaje się nie być uruchomiony na komputerze zdalnym.
Ten komunikat o błędzie oznacza, że program Visual Studio nie można odnaleźć prawidłowe wystąpienie programu Visual Studio Monitor debugera zdalnego na komputerze zdalnym. Musi być zainstalowany program Visual Studio Monitor debugera zdalnego do zdalnego debugowania do pracy. Aby uzyskać informacje dotyczące pobierania i konfigurowania zdalnego debugera, zobacz [zdalnego debugowania](../debugger/remote-debugging.md).  
  
> [!IMPORTANT]
>  Jeśli uważasz, otrzymano tego komunikatu z powodu błędu w produkcie, skontaktuj się z [Zgłoś problem do programu Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Jeśli potrzebujesz więcej pomocy, zobacz [Porozmawiaj z nami](../ide/talk-to-us.md) sposobów kontakt z firmą Microsoft.  
  
## <a name="i-got-this-message-while-i-was-debugging-in-visual-studio-2010-or-earlier"></a>Został wyświetlony komunikat, gdy został I debugowania w programie Visual Studio 2010 lub starszy  
 Wersja programu Visual Studio, które są używane w przypadku programu Visual Studio 2010 lub starszy, ten błąd może też pojawić Jeśli nie jest włączone udostępnianie plików i drukarek. Aby dowiedzieć się więcej na temat tego problemu, zapoznaj się z programu Visual Studio 2010 w niniejszej dokumentacji: [błąd: Monitor Microsoft Visual Studio zdalne debugowanie (polecenia MSVSMON. Wywołanie pliku EXE) nie jest uruchomiona na komputerze zdalnym. — Program visual Studio 2010](https://msdn.microsoft.com/en-us/library/ms164726\(v=vs.100\).aspx)  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Został wyświetlony komunikat podczas I debugowanie zostało lokalnie  
 W przypadku uzyskiwania tego komunikatu podczas debugowania lokalnie, oprogramowanie antywirusowe lub zapory innych firm mogą być stronę. Program Visual Studio jest 32-bitowej aplikacji, więc używa 64-bitowej wersji zdalnego debugera do debugowania aplikacji 64-bitowych. Dwa procesy komunikują się za pomocą sieci lokalnej na komputerze lokalnym. Dlatego żaden ruch do komputera, ale istnieje możliwość, że oprogramowanie zabezpieczające innych firm może blokować komunikację.  
  
 W poniższych sekcjach wymieniono niektóre inne przyczyny, dlaczego użytkownik może stają się coraz ten komunikat i co można zrobić, aby rozwiązać ten problem.  
  
## <a name="the-remote-machine-is-not-reachable"></a>Komputer zdalny jest nieosiągalny  
 Spróbuj [ping](https://technet.microsoft.com/en-us/library/ee624059\(v=ws.10\).aspx) komputera zdalnego. Jeśli go nie odpowiada na polecenie ping, nie będzie można nawiązać połączenia albo narzędzia zdalnej. Spróbuj ponownie uruchamia komputer zdalny, a w przeciwnym razie upewnieniu się, że został on poprawnie skonfigurowany w sieci.  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Wersja zdalnego debugera nie pasuje do wersji programu Visual Studio  
 Wersji programu Visual Studio, które działają lokalnie musi być zgodna z wersją monitor debugera zdalnego działa na komputerze zdalnym. Aby rozwiązać ten problem, Pobierz i zainstaluj zgodną wersję monitor debugera zdalnego. Przejdź do [Centrum pobierania](http://www.microsoft.com/en-us/download) można znaleźć właściwej wersji zdalnego debugera.  
  
## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Tryby uwierzytelniania inny ma maszyny lokalne i zdalne  
 Maszyny lokalne i zdalne muszą używać tego samego trybu uwierzytelniania. Aby rozwiązać ten problem, upewnij się, że obie maszyny używają tego samego trybu uwierzytelniania. Aby uzyskać więcej informacji na temat trybów uwierzytelniana, zobacz [omówienie uwierzytelniania systemu Windows](https://technet.microsoft.com/en-us/library/hh831472.aspx).  
  
## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>Zdalny debuger działa w ramach innego konta użytkownika  
 Użytkownik może rozwiązać ten problem w jednym z następujących sposobów:  
  
-   Można zatrzymać debuger zdalny i uruchom go ponownie przy użyciu konta, którego używasz na komputerze lokalnym.  
  
-   Zdalny debuger można uruchomić z wiersza polecenia z **/ Zezwalaj \<nazwa użytkownika >** parametru: `msvsmon /allow <username@computer>`  
  
-   Można dodać użytkownika do zdalnego debugera uprawnień (w oknie zdalnego debugera **Narzędzia > uprawnienia**).  
  
-   Nie można użyć metody w poprzednich krokach, można zezwolić użytkownikowi czy zdalne debugowanie. W oknie zdalnego debugera, przejdź do **Narzędzia > Opcje** okna dialogowego. Po wybraniu **bez uwierzytelniania**, można sprawdzić **Zezwalaj dowolnemu użytkownikowi na debugowanie**. Jednak należy użyć tej opcji tylko wtedy, gdy użytkownik nie mają wyboru lub w sieci prywatnej.  
  
## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>Zapora na zdalnym komputerze nie zezwalać na połączenia przychodzące do zdalnego debugera  
 Zapora na maszynie programu Visual Studio i zapory na zdalnym komputerze muszą być skonfigurowane do zezwalania na komunikację między i zdalny debuger programu Visual Studio. Informacje o portach używa zdalnego debugera, zobacz [przypisania portów usługi zdalnego debugera](../debugger/remote-debugger-port-assignments.md). Aby uzyskać informacje o konfigurowaniu zapory systemu Windows, zobacz [konfigurowania Zapory systemu Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="anti-virus-software-is-blocking-the-connections"></a>Oprogramowanie antywirusowe blokuje połączenia  
 Oprogramowanie antywirusowe systemu Windows zezwala na połączenia zdalnego debugera, ale niektóre programy antywirusowe innych firm mogą je zablokować. Sprawdź dokumentację oprogramowanie antywirusowe dowiedzieć się, jak zezwolić na te połączenia.  
  
## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Zasady zabezpieczeń sieci blokuje komunikację między komputerem zdalnym i Visual Studio  
 Przejrzyj zabezpieczenia sieci, aby upewnić się, że nie blokuje komunikacji. Aby uzyskać więcej informacji dotyczących zasad zabezpieczeń sieciowych systemu Windows, zobacz [ustawienia zasad zabezpieczeń](/windows/device-security/security-policy-settings/security-policy-settings).  
  
## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Sieć jest zbyt zajęty, aby zapewnić obsługę zdalnego debugowania  
 Może być konieczne zdalnego debugowania w innym czasie, lub Zmień harmonogram pracy w sieci przez inny czas.  
  
## <a name="more-help"></a>Więcej informacji  
 Aby uzyskać pomoc debuger zdalny, w tym przełączniki wiersza polecenia, kliknij przycisk **Pomoc > użycia** w oknie zdalnego debugera. Jeśli nie masz otwarty zostanie wyświetlona strona sieci web, kopiując następujący wiersz do **Eksploratora plików** okna. (Aby zastąpić \<katalogu instalacyjnego programu Visual Studio > z lokalizacji instalacji programu Visual Studio.)  
  
 res: / /*\<katalogu instalacyjnego programu Visual Studio >* \Common7\IDE\Remote%20Debugger\x64\msvsmon.exe/help.htm  
  
## <a name="see-also"></a>Zobacz też  
 [Zdalne debugowanie błędów i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)