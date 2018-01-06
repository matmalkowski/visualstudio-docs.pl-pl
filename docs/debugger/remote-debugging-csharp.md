---
title: Zdalne debugowanie C# i VB projektu programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords: remote debugging, setup
ms.assetid: a9753fbb-e7f4-47f0-9dbe-9de90c6c8457
caps.latest.revision: "65"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 959622dff7770d314dc5fa2da1e8a81ade34cac4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Zdalne debugowanie projektu C# lub Visual Basic w programie Visual Studio
Debugowanie aplikacji Visual Studio, która została wdrożona na innym komputerze, zainstalować i uruchomić narzędzia zdalnej na komputerze, których wdrożono aplikację, skonfigurować projekt do nawiązania połączenia z komputerem zdalnym z programu Visual Studio, a następnie uruchom aplikację.

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
  
## <a name="BKMK_setup"></a>Konfigurowanie zdalnego debugera

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Jeśli należy dodać uprawnienia dla dodatkowych użytkowników do zmiany trybu uwierzytelniania lub numer portu dla zdalnego debugera, zobacz [skonfigurować debugera zdalnego](../debugger/remote-debugging.md#configure_msvsmon).
  
## <a name="remote_csharp"></a>Zdalne debugowanie projektu
Debuger nie może wdrożyć Visual C# lub Visual Basic aplikacje klasyczne z komputerem zdalnym, ale nadal można je zdalnie w następujący sposób debugowania. W poniższej procedurze przyjęto, że chcesz debugować go na komputerze o nazwie **MJO DL**, jak pokazano na poniższej ilustracji.
  
1.  Utwórz projekt WPF o nazwie **MyWpf**.  
  
2.  Ustaw punkt przerwania gdzieś w kodzie, łatwo osiągnięcia.  
  
     Na przykład można ustawić punktu przerwania w obsłudze przycisku. Aby to zrobić, otwórz MainWindow.xaml, Dodaj formant Button z przybornika, a następnie kliknij dwukrotnie przycisk, aby otworzyć jego obsługi.
  
3.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **właściwości**.  
  
4.  Na **właściwości** wybierz pozycję **debugowania** kartę.  
  
     ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5.  Upewnij się, że **katalog roboczy** pole tekstowe jest puste.  
  
6.  Wybierz **komputera zdalnego użyj**i wpisz **MJO-DL:4022** w polu tekstowym. (4022 jest wyświetlany w oknie zdalnego debugera numer portu. Numer portu zwiększa 2 w każdej wersji programu Visual Studio).
  
7.  Upewnij się, że **Włącz debugowanie kodu natywnego** nie jest zaznaczone.  
  
8.  Skompiluj projekt.  
  
9. Utwórz folder na zdalnym komputerze, który ma taką samą ścieżkę **debugowania** folderu na komputerze programu Visual Studio:  **\<ścieżki źródłowej > \MyWPF\MyWPF\bin\Debug**.  
  
10. Skopiuj plik wykonywalny, który właśnie utworzono z komputera program Visual Studio do nowo utworzonego folderu na komputerze zdalnym.
  
    > [!CAUTION]
    >  Nie należy wprowadzać zmiany kodu lub rebuild (lub ten krok należy powtórzyć). Plik wykonywalny skopiowane na komputer zdalny musi dokładnie odpowiadać lokalnego źródłowe i symboli.

    Można ręcznie skopiować projektu, użyj polecenia Xcopy, Robocopy, programu Powershell lub inne opcje.
  
11. Upewnij się, że debuger zdalny jest uruchomiony na komputerze docelowym (Jeśli nie jest, wyszukaj **zdalnego debugera** w **Start** menu). Zdalny debuger okno wygląda następująco.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. W programie Visual Studio, Rozpocznij debugowanie (**Debuguj > Rozpocznij debugowanie**, lub **F5**).  
  
13. Jeśli zostanie wyświetlony monit, wprowadź poświadczenia sieci, aby połączyć z komputerem zdalnym.  
  
     Wymagane poświadczenia się różnić w zależności od konfiguracji zabezpieczeń sieci. Na przykład na komputerze domeny, można wprowadzić nazwę domeny i hasła. Na komputerze z systemem innym niż domeny, wprowadzić nazwę komputera i nazwę konta użytkownika prawidłowy tak samo, jak  **MJO-DL\name@something.com** , oraz prawidłowe hasło.

     Powinny być widoczne czy głównego okna aplikacji WPF jest otwarty na komputerze zdalnym.
  
14. W razie potrzeby podjąć działania w celu trafiony punkt przerwania. Powinny być widoczne czy punkt przerwania jest aktywny. Jeśli nie, nie załadowano symboli dla aplikacji. Spróbuj ponownie, a jeśli to nie zadziała, uzyskać informacje dotyczące ładowania symboli i jak rozwiązać je pod adresem [Opis plików symboli i Visual Studio symbolu ustawienia](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/05/understanding-symbol-files-and-visual-studio-s-symbol-settings.aspx).
  
15. Na komputerze programu Visual Studio powinny być widoczne czy wykonywanie zostało zatrzymane na punkt przerwania.
  
 Jeśli masz plików z systemem innym niż kodu, które będzie używane przez aplikację, należy je uwzględnić w projekcie programu Visual Studio. Tworzenie folderu projektu dla dodatkowych plików (w **Eksploratora rozwiązań**, kliknij przycisk **Dodaj > Nowy Folder**). Następnie dodaj pliki do folderu (w **Eksploratora rozwiązań**, kliknij przycisk **Dodaj > istniejący element**, następnie wybierz pliki). Na **właściwości** strony dla każdego pliku, ustaw **Kopiuj do katalogu wyjściowego** do **skopiuj zawsze**.

## <a name="set-up-debugging-with-remote-symbols"></a>Konfigurowanie debugowania przy użyciu zdalnego symboli 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie w programie Visual Studio](../debugger/index.md)  
 [Przegląd funkcji debugera](../debugger/debugger-feature-tour.md)   
 [Konfigurowanie Zapory systemu Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Przypisania portów debugera zdalnego](../debugger/remote-debugger-port-assignments.md)   
 [Zdalne debugowanie ASP.NET na komputerze zdalnym usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [Zdalne debugowanie błędów i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)