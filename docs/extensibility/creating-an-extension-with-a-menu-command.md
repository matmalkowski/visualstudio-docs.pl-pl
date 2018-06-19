---
title: Tworzenie rozszerzenia za pomocą polecenia Menu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 00c80692929ac19b55f68b8aa20306f39ddceae6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108157"
---
# <a name="creating-an-extension-with-a-menu-command"></a>Tworzenie rozszerzenia za pomocą polecenia Menu
W tym przewodniku przedstawiono sposób tworzenia rozszerzenia za pomocą polecenia menu, który uruchamia program Notatnik.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-command"></a>Tworzenie polecenia Menu  
  
1.  Tworzenie projektu VSIX o nazwie **FirstMenuCommand**. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C# / rozszerzalności**.  
  
2.  Po otwarciu projektu Dodawanie polecenia niestandardowego szablonu elementu o nazwie **FirstCommand**. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. W **Dodaj nowy element** okno dialogowe, przejdź do **Visual C# / rozszerzalności** i wybierz **polecenia niestandardowych**. W **nazwa** u dołu okna, Zmień nazwę pliku polecenia, aby **FirstCommand.cs**.  
  
3.  Skompiluj projekt i Rozpocznij debugowanie.  
  
     Pojawi się eksperymentalne wystąpienie programu Visual Studio. Aby uzyskać więcej informacji na temat eksperymentalne wystąpienie, zobacz [eksperymentalne wystąpienie](../extensibility/the-experimental-instance.md).  
  
4.  Otwórz w eksperymentalnym wystąpieniu **narzędzia / rozszerzenia i aktualizacje** okna. Powinny pojawić się **FirstMenuCommand** rozszerzenia tutaj. (Jeśli otworzysz **rozszerzenia i aktualizacje** wystąpienia pracy programu Visual Studio, nie zobaczysz **FirstMenuCommand**).  
  
     Teraz przejdź do **narzędzia** menu w eksperymentalnym wystąpieniu. Powinny pojawić się **wywołania FirstCommand** polecenia. W tym momencie ją po prostu wywołuje okno komunikatu potwierdzającego "FirstCommandPackage wewnątrz FirstMenuCommand.FirstCommand.MenuItemCallback()". Firma Microsoft będzie Zobacz jak uruchamia Notatnik z tego polecenia w następnej sekcji.  
  
## <a name="changing-the-menu-command-handler"></a>Zmiana program obsługi poleceń Menu  
 Teraz załóżmy zaktualizować program obsługi poleceń uruchom program Notatnik.  
  
1.  Zatrzymaj debugowanie i wróć do wystąpienia pracy programu Visual Studio. Otwórz plik FirstCommand.cs i dodaj następującą instrukcję using:  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2.  Znajdź Konstruktor prywatny FirstCommand. Jest to gdzie polecenia jest podłączony do usługi polecenia i jest określony program obsługi poleceń. Zmień nazwę programu obsługi poleceń do StartNotepad, w następujący sposób:  
  
    ```csharp  
    private FirstCommand(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
         OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(CommandSet, CommandId);  
            // Change to StartNotepad handler.  
            MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
3.  Usuń metodę MenuItemCallback i Dodawanie metody StartNotepad, która po prostu rozpocznie Notatnik:  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  Teraz wypróbować jej możliwości. Kiedy rozpocząć debugowania projektu i kliknij przycisk **narzędzi / wywołania FirstCommand**, powinny pojawić się wystąpienia Notatnika znaleziona.  
  
     Można użyć wystąpienia <xref:System.Diagnostics.Process> klasy do uruchamiania każdego pliku wykonywalnego, a nie tylko Notatnik. Próba przy calc.exe, np.  
  
## <a name="cleaning-up-the-experimental-environment"></a>Czyszczenie środowiska eksperymentalne  
 Jeśli tworzysz wiele rozszerzeń lub eksploracji tylko wyniki z różnymi wersjami kodzie rozszerzenia, eksperymentalne środowiska mogą przestać działać sposób którą powinno. W takim przypadku należy uruchomić skrypt resetowania. Jest to **Zresetuj Visual Studio 2015 eksperymentalne wystąpienie programu**, a ten składnik jest dostarczany jako część programu Visual Studio SDK. Ten skrypt powoduje usunięcie wszystkich odwołań do rozszerzeń ze środowiska eksperymentalne, aby rozpocząć od początku.  
  
 Aby wyświetlić ten skrypt w jeden z dwóch sposobów:  
  
1.  Na pulpicie, Znajdź **Zresetuj Visual Studio 2015 eksperymentalne wystąpienie programu**.  
  
2.  W wierszu polecenia Uruchom następujące polecenie:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>Wdrażanie rozszerzenia  
 Teraz, gdy masz uruchomiony w taki sposób, który ma rozszerzenie narzędzia nadszedł czas na Pomyśl o udostępnianiu znajomymi. To łatwe, jak długo mają zainstalowany program Visual Studio 2015. Wystarczy, że będzie wysyłać je pliku .vsix, które zostały utworzone. (Upewnij się go skompilować w trybie wersji.)  
  
 Plik .vsix dla tego rozszerzenia można znaleźć w katalogu bin FirstMenuCommand. W szczególności przy założeniu, że utworzono do konfiguracji wydania, będzie w:  
  
 **\<katalog kodu > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix**  
  
 Aby zainstalować rozszerzenie, znajomych musi Zamknij wszystkie otwarte wystąpienia programu Visual Studio, a następnie kliknij dwukrotnie plik .vsix, który wywołuje **Instalatora VSIX**. Pliki są kopiowane do **%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions** katalogu.  
  
 Gdy znajomych wywołuje Visual Studio ponownie, on znaleźć rozszerzenia FirstMenuCommand w **narzędzia / rozszerzenia i aktualizacje**. Może on przejść do **rozszerzenia i aktualizacje** należy odinstalować lub wyłączyć rozszerzenie, zbyt.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku wykazało tylko niewielką częścią co można zrobić rozszerzenia programu Visual Studio. Poniżej przedstawiono krótką listę innymi (przystępny), które można wykonać za pomocą rozszerzeń programu Visual Studio:  
  
1.  Można wykonywać wiele więcej opcji za pomocą polecenia menu prosty:  
  
    1.  Dodaj własną ikonę: [dodawanie ikon do poleceń Menu](../extensibility/adding-icons-to-menu-commands.md)  
  
    2.  Zmień tekst polecenia menu: [zmiana tekstu polecenia Menu](../extensibility/changing-the-text-of-a-menu-command.md)  
  
    3.  Dodaj do polecenia menu skrótów: [powiązanie skróty do elementów Menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2.  Dodaj różnych rodzajów polecenia, menu i pasków narzędzi: [rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)  
  
3.  Dodawanie do okien narzędzi i rozszerzanie wbudowanych okien narzędzi Visual Studio: [rozszerzanie i dostosowywanie okna narzędzi](../extensibility/extending-and-customizing-tool-windows.md)  
  
4.  Dodawanie funkcji IntelliSense, sugestie kodu i inne funkcje do istniejącego kodu edytory: [rozszerzanie edytora i usług języka](../extensibility/extending-the-editor-and-language-services.md)  
  
5.  Dodawanie do rozszerzenia strony opcji i właściwości i ustawienia użytkownika: [rozszerzanie właściwości i w oknie właściwości](../extensibility/extending-properties-and-the-property-window.md) i [opcje i rozszerzanie ustawień użytkownika](../extensibility/extending-user-settings-and-options.md)  
  
 Inne rodzaje rozszerzenia wymaga nieco więcej pracy, takich jak tworzenie nowego typu projektu ([rozszerzanie projektów](../extensibility/extending-projects.md)), tworzenie nowego typu edytora ([projektanci i tworzenie niestandardowych edytory](../extensibility/creating-custom-editors-and-designers.md)), lub Wdrażanie rozszerzenia w programu isolated shell: [programu Visual Studio Isolated Shell.](../extensibility/visual-studio-isolated-shell.md)