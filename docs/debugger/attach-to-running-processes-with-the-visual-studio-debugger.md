---
title: "Dołączanie do uruchomionego procesu za pomocą debugera programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: "53"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 28126f9c832f55d63bd1b477599cf83ac8a57d59
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Dołączanie do uruchomionego procesu za pomocą debugera programu Visual Studio
Możesz dołączyć debuger programu Visual Studio do uruchomionego procesu na komputerze lokalnym lub zdalnym. Po uruchomieniu procesu kliknij **debugowania > dołączyć do procesu** (lub naciśnij klawisz **CTRL + ALT + P**) można otworzyć **dołączyć do procesu** okno dialogowe.

Ta funkcja służy do debugowania aplikacji, które są uruchomione na komputerze lokalnym lub zdalnym, jednocześnie debugowanie wielu procesów lub debugowania aplikacji, która nie została utworzona w programie Visual Studio. Często jest przydatne, gdy chcesz debugować aplikację, ale (niezależnie od przyczyn) nie zostało rozpoczęte aplikacji z programu Visual Studio w debugerze. Na przykład jeśli używasz aplikacji bez debugera i trafień wyjątek, może następnie dołączeniu do procesu, w którym uruchomiono aplikację, aby rozpocząć debugowanie.

> [!TIP]
> Nie masz pewności czy należy użyć **dołączyć do procesu** dla danego scenariusza debugowania? Zobacz [typowych scenariuszy debugowania](#BKMK_Scenarios). Jeśli chcesz debugować aplikacje ASP.NET, które zostały wdrożone w usługach IIS, zobacz temat [zdalnego debugowania ASP.NET na komputerze zdalnym IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

##  <a name="BKMK_Attach_to_a_running_process"></a>Dołączanie do uruchomionego procesu na komputerze lokalnym  
 Aby można było dołączyć do procesu, musisz znać nazwę procesu (zobacz [typowych scenariuszy debugowania](#BKMK_Scenarios) kilka typowych nazw proces).
  
1.  W programie Visual Studio, wybierz **Debuguj > dołączyć do procesu** (lub naciśnij klawisz **CTRL + ALT + P**).

    Jeśli chcesz szybko ponownie dołączyć do procesu zamiast tego zobacz [ponownie dołączyć do procesu](#BKMK_reattach).
  
2.  W **dołączyć do procesu** okna dialogowego należy znaleźć program, który chcesz dołączyć do z **dostępne procesy** listy.  

     Aby szybko zaznaczyć procesu, który ma, wpisz pierwszą literę nazwy procesu. Jeśli nie znasz nazwy procesu, zobacz [typowych scenariuszy debugowania](#BKMK_Scenarios).
     
     ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process") 
  
     Jeśli proces jest uruchomiony w ramach innego konta użytkownika, wybierz **Pokaż procesy wszystkich użytkowników** pole wyboru.
  
3.  W **dołączyć do** upewnij się, czy wymieniony jest typ kodu zostanie debugowania. Wartość domyślna **automatyczne** ustawienie usiłuje ustaleniu, jaki typ kodu do debugowania. Aby ręcznie ustawić typ kodu, wykonaj następujące czynności  
  
    1.  W **dołączyć do** kliknij **wybierz**.  
  
    2.  W **wybór typu kodu** okno dialogowe, kliknij przycisk **Debuguj te typy kodu** a następnie wybierz typy do debugowania.  
  
    3.  Kliknij przycisk **OK**.  
  
4.  Kliknij przycisk **dołączyć**.

##  <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>Dołączanie do procesu na komputerze zdalnym  
 Aby można było dołączyć do procesu, musisz znać nazwę procesu (zobacz [typowych scenariuszy debugowania](#BKMK_Scenarios) kilka typowych nazw proces). Aby uzyskać bardziej szczegółowy wskazówki dla aplikacji ASP.NET, które zostały wdrożone w usługach IIS, zobacz [zdalnego debugowania ASP.NET na komputerze zdalnym IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). W przypadku innych aplikacji można znaleźć nazwy procesu w Menedżerze zadań.
  
 Jeśli używasz **dołączyć do procesu** okno dialogowe, można wybrać inny komputer, który nie został skonfigurowany do zdalnego debugowania. Aby uzyskać więcej informacji, zobacz [zdalnego debugowania](../debugger/remote-debugging.md). Po wybraniu komputera zdalnego można wyświetlić listę dostępnych procesów uruchomionych na tym komputerze i Dołącz do co najmniej jeden z procesów do debugowania.
  
 **Aby wybrać komputer zdalny:**  

1. W programie Visual Studio, wybierz **Debuguj > dołączyć do procesu** (lub naciśnij klawisz **CTRL + ALT + P**).

    Jeśli chcesz szybko ponownie dołączyć do procesu zamiast tego zobacz [ponownie dołączyć do procesu](#BKMK_reattach).

2.  W **dołączyć do procesu** okno dialogowe, wybierz odpowiednie połączenie typu z **transportu** listy. **Domyślna** jest prawidłowe ustawienie w większości przypadków.

    **Transportu** ustawienie pozostaje między sesji debugowania. 
  
3.  Użyj **kwalifikator** pola listy, aby wybrać nazwę komputera zdalnego za pomocą jednej z następujących metod:  
  
    1.  Wpisz nazwę w **kwalifikator** pola listy.
    
        >**Uwaga** Jeśli w kolejnych krokach, nie można połączyć przy użyciu nazwy komputera zdalnego, użyj adresu IP. (Numer portu może pojawić się automatycznie po wybraniu procesu. Można również wprowadzić go ręcznie. Na poniższej ilustracji 4020 jest domyślny port dla debugera zdalnego).  

        Jeśli chcesz użyć **znaleźć** przycisku, konieczne może być [Otwórz UDP port 3702](../debugger/remote-debugger-port-assignments.md) na serwerze.
  
    2.  Kliknij strzałkę listy rozwijanej dołączony do **kwalifikator** pola listy, a następnie wybierz nazwę komputera z listy rozwijanej.  
  
    3.  Kliknij przycisk **znaleźć** znajdujący się obok**kwalifikator** listy, aby otworzyć **wybierz połączenia zdalnego debugera** okno dialogowe. **Wybierz połączenia zdalnego debugera** okno dialogowe wyświetla wszystkie urządzenia, które znajdują się w sieci lokalnej net podrzędne i każdego urządzenia, który jest podłączony bezpośrednio do komputera za pośrednictwem kabla Ethernet. Kliknij komputer lub urządzenie, a następnie kliknij przycisk **wybierz**. 
  
     **Kwalifikator** ustawienie pozostaje między debugowania sesji tylko wtedy, gdy występuje udane połączenie debugowania z tego kwalifikatora.
     
4.  Kliknij przycisk **Odśwież**.

      **Dostępne procesy** zostanie wyświetlona lista automatycznie podczas otwierania **procesów** okno dialogowe. Procesy można uruchomić i zatrzymać w tle, gdy jest otwarte okno dialogowe. Jednak zawartość nie jest zawsze bieżący. W dowolnym momencie, aby wyświetlić bieżącą listę procesów, klikając można odświeżyć listy **Odśwież**. 
     
4.  W **dołączyć do procesu** okna dialogowego należy znaleźć program, który chcesz dołączyć do z **dostępne procesy** listy.

     Aby szybko zaznaczyć procesu, który ma, wpisz pierwszą literę nazwy procesu. Jeśli nie znasz nazwy procesu, zobacz [typowych scenariuszy debugowania](#BKMK_Scenarios).
  
     Jeśli proces jest uruchomiony w ramach innego konta użytkownika, wybierz **Pokaż procesy wszystkich użytkowników** pole wyboru.
     
5.  Kliknij przycisk **dołączyć**.

## <a name="BKMK_reattach"></a>Ponownie dołączyć do procesu

Można szybko ponownie dołączyć do procesów, które zostały wcześniej dołączone do, wybierając **Debuguj > ponownie dołączyć do procesu...** (**Shift + Alt + P**). Po wybraniu tego polecenia debugera natychmiast podejmie próbę dołączenia do ostatniego procesów dołączonych przy użyciu **dołączyć do procesu** okno dialogowe.

Debuger będzie ponownie dołączyć przy pierwszej próby jest zgodny z poprzednim Identyfikatorem procesu, a następnie, jeśli się nie powiedzie, dopasowując do wcześniejszej nazwy procesu. W przypadku nieodnalezienia żadnych dopasowań lub jeśli istnieje wiele procesów znaleziono o takiej samej nazwie, a następnie **dołączyć do procesu** zostanie wyświetlone okno dialogowe, dzięki czemu można wybrać korygowania procesu.

> [!NOTE]
> **Ponownie dołączyć do procesu** polecenia jest nowa w programie Visual Studio 2017 r.

## <a name="additional-info"></a>Informacje dodatkowe

Użytkownik może zostać dołączona wielu programach, podczas debugowania, ale tylko jeden program jest aktywny w debugerze w dowolnym momencie. Można ustawić aktywny w **debugowania lokalizacji** paska narzędzi lub **procesów** okna.  
  
Jeśli użytkownik próbuje dołączyć do procesu należących do niezaufanych konta, pojawi się ostrzeżenie potwierdzenia — okno dialogowe Zabezpieczenia. Aby uzyskać więcej informacji, zobacz [ostrzeżenie o zabezpieczeniach: dołączanie do procesu należących do niezaufanych użytkownika może być niebezpieczne. Jeśli nie wiesz, poniższe informacje wyglądają podejrzanie, nie dołączaj do tego procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
W niektórych przypadkach podczas debugowania w sesji pulpitu zdalnego (usług terminalowych) **dostępne procesy** listy nie będą wyświetlane wszystkie dostępne procesy. Jeśli używasz programu Visual Studio jako użytkownik, który ma konto użytkownika standardowego, **dostępne procesy** listy nie będą widoczne procesów uruchomionych w sesji 0, który służy do usługi i inne procesy serwera, w tym w3wp.exe. Problem można rozwiązać, uruchamiając [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] przy użyciu konta administratora lub uruchamiając [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] za pomocą konsoli serwera zamiast sesji usług terminalowych. Jeśli żadna z tych rozwiązań jest możliwe, trzecia opcja ma dołączyć do procesu, uruchamiając `vsjitdebugger.exe -p` *ProcessId* z wiersza polecenia systemu Windows. Można określić za pomocą tlist.exe identyfikator procesu. Aby uzyskać tlist.exe, Pobierz i zainstaluj debugowania narzędzi dla systemu Windows, dostępne pod adresem [WDK i WinDbg pliki do pobrania](http://go.microsoft.com/fwlink/?LinkId=168279).

## <a name="BKMK_Scenarios"></a>Typowe scenariusze debugowania

Aby ustalić, czy należy użyć **dołączyć do procesu** i jakie procesy, aby dołączyć do, poniżej przedstawiono kilka typowych scenariuszy debugowania (lista nie jest wyczerpująca). Jeżeli dostępne są dodatkowe instrukcje, firma Microsoft udostępnia łącza.

W przypadku niektórych typów aplikacji (takich jak aplikacje platformy uniwersalnej systemu Windows), nie podłączone bezpośrednio do nazwę procesu, ale użyj **Debuguj zainstalowany pakiet aplikacji** menu opcji w zamian (patrz tabela).

> [!NOTE]
> Informacje dotyczące podstawowych debugowania w programie Visual Studio, zobacz [wprowadzenie do debugera](../debugger/getting-started-with-the-debugger.md).

|Scenariusz|Debug — metoda|Nazwa procesu|Uwagi i łącza|
|-|-|-|-|
|Debugowanie zarządzanego i natywnego aplikacji na komputerze lokalnym|Użyj dołączyć do procesu lub [standardowe debugowania](../debugger/getting-started-with-the-debugger.md)|*AppName*.exe|Aby szybko uzyskać dostęp do okna dialogowego, należy użyć **CTRL + ALT + P** , a następnie wpisz pierwszą literę nazwy procesu.|
|Debugowanie aplikacji ASP.NET na komputerze lokalnym po uruchomieniu aplikacji bez debugera|Użyj dołączyć do procesu|iiexpress.exe|Może to być przydatne zapewnić aplikacji załadować szybszy, takich jak (na przykład) podczas profilowania. |
|Zdalnego debugowania programu ASP.NET 4 lub 4.5 na serwerze IIS|Za pomocą narzędzi zdalnego i dołączyć do procesu|W3wp.exe|Zobacz [zdalnego debugowania ASP.NET na komputerze zdalnym usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Zdalne debugowanie platformy ASP.NET Core na serwerze IIS|Za pomocą narzędzi zdalnego i dołączyć do procesu|DotNet.exe|Do wdrożenia aplikacji, zobacz [publikowania w usługach IIS](https://docs.asp.net/en/latest/publishing/iis.html). Do debugowania, zobacz [zdalnego debugowania ASP.NET Core na zdalnym komputerze usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Debugowanie innych typów obsługiwanej aplikacji na proces serwera|Narzędzia zdalne (Jeśli serwer jest zdalny) i dołączyć do procesu|Iexplore.exe lub inne procesy|W razie potrzeby identyfikowania procesu za pomocą Menedżera zadań. Zobacz [zdalnego debugowania](../debugger/remote-debugging.md) i nowszym sekcje w tym temacie|
|Zdalne debugowanie aplikacji klasycznej systemu Windows|Zdalne narzędzia i F5|Brak| Zobacz [debugowanie zdalne](../debugger/remote-debugging.md)|
|Zdalne debugowanie aplikacji Uniwersalnej, systemem OneCore, HoloLens i IoT|Debuguj zainstalowany pakiet aplikacji|Brak|Zobacz [Debuguj zainstalowany pakiet aplikacji](debug-installed-app-package.md) zamiast **dołączyć do procesu**|
|Debugowanie aplikacji uniwersalnych aplikacji systemu Windows (UWP), systemem OneCore, HoloLens i IoT, który nie został uruchomiony z programu Visual Studio|Debuguj zainstalowany pakiet aplikacji|Brak|Zobacz [Debuguj zainstalowany pakiet aplikacji](debug-installed-app-package.md) zamiast **dołączyć do procesu**|  
  
> [!NOTE]
>  Dla debugera do dołączenia do kodu w języku C++ kod musi Emituj `DebuggableAttribute`. Można dodać tego kodu automatycznie przez łączenie z [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) — opcja konsolidatora.

## <a name="what-debugger-features-can-i-use"></a>Jakie funkcje debugera można użyć?

Aby korzystać z funkcji pełnego debugera programu Visual Studio (na przykład naciśnięcie punktów przerwania) podczas dołączania do procesu, plik wykonywalny musi dokładnie odpowiadać lokalnego źródłowe i symboli (to znaczy debuger musi być w stanie załadować poprawny [symboli plików (.pbd) ](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). Domyślnie wymaga to kompilację debugowania.

W przypadku scenariuszy debugowania zdalnego musi mieć kodu źródłowego (lub kopię kodu źródłowego) już otwarty w programie Visual Studio. Plików binarnych skompilowanych aplikacji na komputerze zdalnym musi pochodzić z tego samego kompilacji na komputerze lokalnym.

W niektórych scenariuszach debugowania lokalnego można debugować w programie Visual Studio bez dostępu do źródła, jeśli symbol poprawne pliki znajdują się w aplikacji (domyślnie wymaga kompilację debugowania). Aby uzyskać więcej informacji, zobacz [plików źródłowych i określić Symbol](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  
##  <a name="BKMK_Troubleshoot_attach_errors"></a>Rozwiązywanie problemów z dołączyć błędów  
 Gdy dołącza debuger do uruchomionego procesu, proces może zawierać jeden lub więcej typów kodu. Typy kodu do można dołączyć debugera są wyświetlane i wybrana w **wybór typu kodu** okno dialogowe.  
  
 Czasami debuger pomyślnie można dołączyć do typu jeden kod, ale nie do innego typu kodu. Taka sytuacja może wystąpić, jeśli chcesz dołączyć do procesu, który działa na komputerze zdalnym. Komputer zdalny może być zdalnego debugowania składniki zainstalowane w przypadku niektórych typów kodu, ale nie do innych użytkowników. Może również wystąpić, jeśli próby dołączenia do dwóch lub więcej procesów do debugowania bezpośredniego bazy danych. Debugowanie SQL obsługuje związane z tylko jednego procesu.  
  
 Jeśli debuger może dołączyć do niektórych, ale nie wszystkie typy kodu, zobaczysz jest komunikat informujący, typy, które nie można dołączyć.  
  
 Jeśli debuger pomyślnie łączy się co najmniej jeden kod typu, możesz przejść do debugowania procesu. Będzie można debugować typy kodu, które pomyślnie zostały dołączone. Poprzedni komunikat przykład pokazuje, że typ kodu skryptu nie można dołączyć. W związku z tym czy nie można debugować kodu skryptu w ramach procesu. Kod skryptu w procesie będą nadal działać, ale nie będzie można ustawić punktów przerwania, wyświetlania danych lub wykonywać inne operacje debugowania w skrypcie.  
  
 Jeśli chcesz bardziej szczegółowe informacje dotyczące niepowodzenia debugera do dołączenia do typ kodu, możesz spróbować ponownie dołączyć do tego typu kodu.  
  
 **Aby uzyskać szczegółowe informacje na temat przyczyny niepowodzenia typ kodu do dołączenia**  
  
1.  Odłączyć od procesu. Na **debugowania** menu, kliknij przycisk **Odłącz wszystkie**.  
  
2.  Ponownie dołączyć do procesu, wybór typu kodu pojedynczego.  
  
    1.  W **dołączyć do procesu** oknie dialogowym Wybierz proces w ramach **dostępne procesy** listy.  
  
    2.  Kliknij przycisk **wybierz**.  
  
    3.  W **wybór typu kodu** okno dialogowe, wybierz **Debuguj te typy kodu** i nie można dołączyć typ kodu. Wyczyść innego kodu.  
  
    4.  Kliknij przycisk **OK**. **Wybór typu kodu** okno dialogowe zostanie zamknięte.  
  
    5.  W **dołączyć do procesu** okno dialogowe, kliknij przycisk **Attach**.  
  
     Ten czas, Podłączanie nie powiedzie się całkowicie i otrzymasz komunikat o błędzie.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie wielu procesów](../debugger/debug-multiple-processes.md)   
 [Debugowanie Just In Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)