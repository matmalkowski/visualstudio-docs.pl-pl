---
title: 'Porady: dołączanie do skryptu | Dokumentacja firmy Microsoft'
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
- script debugging, attaching to script
- script, attaching to
- processes, attaching to script
- remote debugging, attaching to script
ms.assetid: 82013e9a-ef53-4fd2-b451-a6891cdc6307
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c38e965c5d424c7a3a6ffe4047e9422f1f9bb4f0
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="how-to-attach-to-script"></a>Porady: dołączanie do skryptu
W tym temacie wyjaśniono, jak ręcznie dołączyć debuger programu Visual Studio do pliku skryptu w celu debugowania.  
  
### <a name="to-attach-to-a-running-process"></a>Aby dołączyć do uruchomionego procesu  
  
1.  Na **debugowania** menu, wybierz **dołączyć do procesu**. (Jeśli żaden projekt nie jest otwarty, wybierz **dołączyć do procesu** na **narzędzia** menu.)  
  
2.  W **dołączyć do procesu** okno dialogowe, obejrzyj **dostępne procesy** chcesz dołączyć do listy i Znajdź skryptu procedur. Procesy skryptu można określić za **typu** kolumny.  
  
    1.  Jeśli proces, który chcesz debugować jest uruchomiony na innym komputerze, należy najpierw wybrać komputera zdalnego. Aby uzyskać więcej informacji, zobacz [porady: Wybieranie komputera zdalnego](http://msdn.microsoft.com/en-us/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
    2.  Jeśli proces jest uruchomiony w ramach innego konta użytkownika, wybierz **Pokaż procesy wszystkich użytkowników** pole wyboru.  
  
    3.  Po nawiązaniu połączenia za pośrednictwem **Podłączanie pulpitu zdalnego**, wybierz pozycję **Pokaż procesy we wszystkich sesjach** pole wyboru.  
  
3.  Kliknij przycisk procesu, który chcesz dołączyć do.  
  
4.  W **dołączyć do** polu powinny być widoczne **kodu skryptów** lub **automatycznego: kod skryptu**. Jeśli widzisz cokolwiek innego, wykonaj następujące kroki:  
  
    1.  Kliknij przycisk **wybierz**.  
  
    2.  W **wybór typu kodu** okno dialogowe, kliknij przycisk **Debuguj te typy kodu** i wybierz **skryptu**.  
  
    3.  Kliknij przycisk **OK**.  
  
5.  Kliknij przycisk **dołączyć**.  
  
     W tym momencie może zostać wyświetlone ostrzeżenie informujące o tym, że debugowanie skryptów jest wyłączone w programie Internet Explorer. Jeśli to miejsce, zobacz [Ostrzeżenie: wyłączony debugowanie skryptu](../debugger/warning-script-debugging-disabled.md).  
  
 **Dostępne procesy** zostanie wyświetlona lista automatycznie podczas otwierania **procesów** okno dialogowe. Procesy można uruchomić i zatrzymać w tle, gdy jest otwarte okno dialogowe. W związku z tym zawartość może zawsze być nieaktualne. W dowolnym momencie, aby wyświetlić bieżącą listę procesów, naciskając klawisz można odświeżyć listy **Odśwież** przycisku.  
  
 Użytkownik może zostać dołączona wielu programach, podczas debugowania, ale tylko jeden program jest aktywny w debugerze w dowolnym momencie. Na pasku narzędzi debugowania lokalizacji można ustawić aktywny program. Aby uzyskać więcej informacji, zobacz [porady: Ustawianie bieżącego procesu](http://msdn.microsoft.com/en-us/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
 Wszystkie **debugowania** wykonanie polecenia mają wpływ na aktywny program. W oknie dialogowym procesy mogą być dzielone dowolny debugowany program. Zobacz [używanie punktów przerwania](../debugger/using-breakpoints.md).  
  
> [!NOTE]
>  Jeśli użytkownik próbuje dołączyć do procesu, który jest właścicielem konta użytkownika niezaufanych, pojawi się ostrzeżenie okna dialogowego potwierdzenia zabezpieczeń. Aby uzyskać więcej informacji, zobacz [ostrzeżenie o zabezpieczeniach: dołączanie do procesu należących do niezaufanych użytkownika może być niebezpieczne. Jeśli nie wiesz, poniższe informacje wyglądają podejrzanie, nie dołączaj do tego procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).  
  
 W niektórych przypadkach podczas debugowania w sesji usług terminalowych (RDP) na liście dostępnych procesów nie zawiera wszystkich procesów dostępne. Na [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] lub nowsze wersje, jeśli używasz programu Visual Studio jako użytkownik, na liście dostępnych procesy nie wyświetli procesy uruchomione w sesji 0, które jest używane w przypadku usług i inne procesy serwera, w tym w3wp.exe. Problem można rozwiązać, uruchamiając program Visual Studio w kontekście konta administratora lub przez uruchomienie programu Visual Studio z konsoli serwera, a nie sesji usług terminalowych. Jeśli żadna z tych rozwiązań jest możliwe, trzecia opcja ma dołączyć do procesu, wpisując polecenie vsjitdebugger.exe -p ProcessId w wierszu polecenia systemu Windows. Identyfikator procesu można określić za pomocą tlist.exe. Aby uzyskać tlist.exe, Pobierz i zainstaluj debugowania narzędzi dla systemu Windows, dostępne pod adresem [Windows Hardware Developer Central](http://go.microsoft.com/fwlink/?linkid=1651).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie skryptu po stronie klienta](../debugger/client-side-script-debugging.md)   
 [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli nie wiesz, poniższe informacje wyglądają podejrzanie, nie dołączaj do tego procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)