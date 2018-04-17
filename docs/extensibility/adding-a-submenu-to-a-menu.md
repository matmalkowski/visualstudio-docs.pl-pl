---
title: Dodawanie do Menu podmenu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f6998c275aead7b12b107f700e699f5a82edd84e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-submenu-to-a-menu"></a>Dodawanie do Menu podmenu
W tym przewodniku opiera się na pokazu w [Dodawanie Menu na pasku Menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) przez przedstawiająca sposób dodać podmenu do **TestMenu** menu.  
  
 Dodatkowej menu, która jest wyświetlana w innym menu jest podmenu. Podmenu mogą zostać zidentyfikowane na podstawie strzałkę po jego nazwie. Klikając nazwę powoduje podmenu i polecenia do wyświetlenia.  
  
 Ten przewodnik utworzy podmenu w menu na pasku menu programu Visual Studio i umieszcza nowe polecenie w podmenu. Instruktaż implementuje również nowe polecenie.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="adding-a-submenu-to-a-menu"></a>Dodawanie do Menu podmenu  
  
1.  Postępuj zgodnie z instrukcjami [Dodawanie Menu na pasku Menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) można utworzyć elementu projektu i menu. Kroki opisane w tym przewodniku założono, że nazwa projektu VSIX jest `TopLevelMenu`.  
  
2.  Open TestCommandPackage.vsct. W `<Symbols>` Dodaj `<IDSymbol>` element podmenu: jeden dla grupy podmenu i jeden dla polecenia, w `<GuidSymbol>` węzła o nazwie "guidTopLevelMenuCmdSet." To jest tym samym węźle, który zawiera `<IDSymbol>` element menu najwyższego poziomu.  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  Dodaj nowo utworzony podmenu `<Menus>` sekcji.  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     Pary GUID/Identyfikatora elementu nadrzędnego Określa grupę menu, który został wygenerowany w [Dodawanie Menu na pasku Menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), i jest elementem podrzędnym elementu menu najwyższego poziomu.  
  
4.  Dodaj grupę menu zdefiniowane w kroku 2 do `<Groups>` sekcji i Uczyń elementem podrzędnym podmenu.  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  Dodaj nową `<Button>` elementu `<Buttons>` sekcji, aby zdefiniować polecenia utworzony w kroku 2 jako element w podmenu.  
  
    ```xml  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <Strings>  
           <CommandName>cmdidTestSubCommand</CommandName>  
           <ButtonText>Test Sub Command</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
6.  Skompiluj rozwiązanie i Rozpocznij debugowanie. Powinny pojawić się eksperymentalne wystąpienie.  
  
7.  Kliknij przycisk **TestMenu** aby zobaczyć nowe podmenu o nazwie **pod Menu**. Kliknij przycisk **pod Menu** Otwórz podmenu i zobaczyć nowe polecenie **testu podpolecenie**. Zwróć uwagę, że kliknięcie pozycji **testu podpolecenie** nie działają.  
  
## <a name="adding-a-command"></a>Dodawanie polecenia  
  
1.  Otwórz TestCommand.cs i Dodaj następujący identyfikator polecenia po istniejący identyfikator polecenia.  
  
    ```csharp  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  Dodaj polecenie podrzędne. Znajdź Konstruktor polecenia. Dodaj następujące wiersze zaraz po wywołaniu `AddCommand` metody.  
  
    ```csharp  
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     `SubItemCallback` Program obsługi poleceń zostanie zdefiniowana później. Konstruktor powinien teraz wyglądać następująco:  
  
    ```csharp  
    private TestCommand(Package package)  
            {  
                if (package == null)  
                {  
                    throw new ArgumentNullException("package");  
                }  
  
                this.package = package;  
  
                OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
                if (commandService != null)  
                {  
                    var menuCommandID = new CommandID(CommandSet, CommandId);  
                    var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);  
                    commandService.AddCommand(menuItem);  
                    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);  
                    MenuCommand subItem = new MenuCommand(  
                        new EventHandler(SubItemCallback), subCommandID);  
                    commandService.AddCommand(subItem);  
                }  
    ```  
  
3.  Dodaj SubItemCallback(). Jest to metoda, wywoływana, gdy zostanie kliknięty nowe polecenie w podmenu.  
  
    ```csharp  
    private void SubItemCallback(object sender, EventArgs e)  
    {  
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetService(  
            typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "TestCommand",  
            string.Format(CultureInfo.CurrentCulture,  
            "Inside TestCommand.SubItemCallback()",  
            this.ToString()),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result);  
    }  
    ```  
  
4.  Skompiluj projekt i Rozpocznij debugowanie. Eksperymentalne wystąpienie powinny być wyświetlane.  
  
5.  Na **TestMenu** menu, kliknij przycisk **pod Menu** , a następnie kliknij przycisk **testu podpolecenie**. Okno komunikatu powinno występować i wyświetlenie tekst "Test polecenia wewnątrz TestCommand.SubItemCallback()".  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie Menu na pasku Menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
