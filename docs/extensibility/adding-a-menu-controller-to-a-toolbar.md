---
title: "Dodawanie kontrolera Menu do paska narzędzi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: "38"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 786d7c8841f680d5af5c539e30723289df4db0f5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="adding-a-menu-controller-to-a-toolbar"></a>Dodawanie kontrolera Menu do paska narzędzi
Ten przewodnik jest oparty na [Dodawanie paska narzędzi do okna narzędzia](../extensibility/adding-a-toolbar-to-a-tool-window.md) wskazówki i przedstawiono sposób dodawania kontrolera menu do paska narzędzi okna narzędzia. Kroki opisane w tym miejscu można zastosować też w pasku narzędzi, która jest tworzona w [Dodawanie paska narzędzi](../extensibility/adding-a-toolbar.md) wskazówki.  
  
 Kontroler menu jest formantem podziału. Z lewej strony kontrolera menu przedstawia ostatnio używane polecenia i aby można było uruchomić, klikając go. Strzałka jest kontrolera menu z prawej strony, po kliknięciu otwiera listę dodatkowych poleceń. Po kliknięciu polecenia na liście, uruchamia polecenia i zastępuje polecenia po lewej stronie kontrolera menu. W ten sposób kontroler menu działa jak przycisk polecenia zawsze pokazujący polecenia ostatnio używane z listy.  
  
 Kontrolery menu mogą być wyświetlane w menu, ale są najczęściej używane na paskach narzędzi.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-controller"></a>Tworzenie kontrolera Menu  
  
#### <a name="to-create-a-menu-controller"></a>Aby utworzyć kontroler menu  
  
1.  Wykonaj procedury opisane w temacie [Dodawanie paska narzędzi do okna narzędzia](../extensibility/adding-a-toolbar-to-a-tool-window.md) można utworzyć okna narzędzia, która ma paska narzędzi.  
  
2.  W TWTestCommandPackage.vsct przejdź do sekcji symboli. W elemencie GuidSymbol o nazwie **guidTWTestCommandPackageCmdSet**, ogłasza kontroler menu, grupy menu kontrolera i trzech elementów menu.  
  
    ```xml  
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
    ```  
  
3.  W sekcji menu po ostatniej pozycji menu, zdefiniuj kontrolera menu jako menu.  
  
    ```xml  
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <CommandFlag>TextChanges</CommandFlag>  
        <CommandFlag>TextIsAnchorCommand</CommandFlag>  
        <Strings>  
            <ButtonText>Test Menu Controller</ButtonText>  
            <CommandName>Test Menu Controller</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     `TextChanges` i `TextIsAnchorCommand` flagi muszą być włączone, aby włączyć kontrolera menu w celu odzwierciedlenia ostatnich wybranego polecenia.  
  
4.  W grupie sekcji od ostatniego zapisu grupy dodać grupy menu kontrolera.  
  
    ```xml  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
    </Group>  
    ```  
  
     Ustawiając kontrolera menu jako element nadrzędny, wszelkie polecenia umieszczone w tej grupie będą wyświetlane w menu kontrolera. `priority` Atrybut nie jest określony, który ustawia wartość domyślna 0, ponieważ będzie ona tylko grupy na kontrolerze menu.  
  
5.  W sekcji przycisków po ostatni wpis przycisku Dodaj element przycisku dla każdego z elementów menu.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 1</ButtonText>  
            <CommandName>MC Item 1</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 2</ButtonText>  
            <CommandName>MC Item 2</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPicSearch" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 3</ButtonText>  
            <CommandName>MC Item 3</CommandName>  
        </Strings>  
    </Button>  
    ```  
  
6.  W tym momencie można przyjrzeć się kontrolera menu. Skompiluj projekt i Rozpocznij debugowanie. Powinny pojawić się eksperymentalne wystąpienie.  
  
    1.  Na **widoku / inne okna** menu, otwórz **ToolWindow testu**.  
  
    2.  Kontroler menu pojawia się na pasku narzędzi w oknie narzędzia.  
  
    3.  Kliknij strzałkę po prawej stronie kontrolera menu, aby wyświetlić trzy polecenia możliwe.  
  
     Zwróć uwagę, że po kliknięciu polecenia tytuł kontrolera menu zmienia się do wyświetlenia tego polecenia. W następnej sekcji dodamy kod, aby aktywować te polecenia.  
  
## <a name="implementing-the-menu-controller-commands"></a>Wdrażanie kontrolera poleceń Menu  
  
1.  W TWTestCommandPackageGuids.cs Dodaj identyfikatory elementów menu trzy polecenia po poleceniu istniejących identyfikatorów.  
  
    ```csharp  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  W TWTestCommand.cs Dodaj następujący kod w górnej części klasy TWTestCommand.  
  
    ```csharp  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  W Konstruktorze TWTestCommand po ostatnim wywołaniem `AddCommand` metody, Dodaj kod, aby trasy dla każdego polecenia za pomocą tej samej procedury obsługi zdarzeń.  
  
    ```csharp  
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=  
        TWTestCommandPackageGuids.cmdidMCItem3; i++)  
    {  
        CommandID cmdID = new  
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);  
        OleMenuCommand mc = new OleMenuCommand(new  
          EventHandler(OnMCItemClicked), cmdID);  
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);  
        commandService.AddCommand(mc);  
        // The first item is, by default, checked.   
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)  
        {  
            mc.Checked = true;  
            this.currentMCCommand = i;  
        }  
    }  
    ```  
  
4.  Dodaj program obsługi zdarzeń do klasy TWTestCommand, aby oznaczyć wybrane polecenie jako zaznaczone.  
  
    ```csharp  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  Dodawanie obsługi zdarzeń, który zawiera element MessageBox, gdy użytkownik wybierze polecenie na kontrolerze menu:  
  
    ```csharp  
    private void OnMCItemClicked(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            string selection;  
            switch (mc.CommandID.ID)  
            {  
                case c.cmdidMCItem1:  
                    selection = "Menu controller Item 1";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem2:  
                    selection = "Menu controller Item 2";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem3:  
                    selection = "Menu controller Item 3";  
                    break;  
  
                default:  
                    selection = "Unknown command";  
                    break;  
            }  
            this.currentMCCommand = mc.CommandID.ID;  
  
            IVsUIShell uiShell =  
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));  
            Guid clsid = Guid.Empty;  
            int result;  
            uiShell.ShowMessageBox(  
                       0,  
                       ref clsid,  
                       "Test Tool Window Toolbar Package",  
                       string.Format(CultureInfo.CurrentCulture,  
                                     "You selected {0}", selection),  
                       string.Empty,  
                       0,  
                       OLEMSGBUTTON.OLEMSGBUTTON_OK,  
                       OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
                       OLEMSGICON.OLEMSGICON_INFO,  
                       0,  
                       out result);  
        }  
    }  
    ```  
  
## <a name="testing-the-menu-controller"></a>Testowanie kontrolera Menu  
  
1.  Skompiluj projekt i Rozpocznij debugowanie. Powinny pojawić się eksperymentalne wystąpienie.  
  
2.  Otwórz **ToolWindow testu** na **widoku / inne okna** menu.  
  
     Zostanie wyświetlony w pasku narzędzi w oknie narzędzia kontrolera menu i **1 elementu MC**.  
  
3.  Kliknij przycisk menu kontrolera strzałki w lewo.  
  
     Powinny pojawić się trzy elementy, z których pierwszy jest zaznaczony i ma pole wyróżnienia wokół jego ikonę. Kliknij przycisk **elementu MC 3**.  
  
     Zostanie wyświetlone okno dialogowe z komunikatem **wybranego kontrolera Menu 3 elementu**. Należy zauważyć, że komunikat odpowiada tekst przycisku menu kontrolera. Przycisk menu kontrolera są obecnie wyświetlane **3 elementu MC**.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie do okna narzędzi paska narzędzi](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Dodawanie paska narzędzi](../extensibility/adding-a-toolbar.md)