---
title: Zmiana tekstu polecenia Menu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 717e360e08cbdfee23221b9384a5574530f92e23
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="changing-the-text-of-a-menu-command"></a>Zmiana tekstu polecenia Menu
Poniższe kroki pokazują, jak zmienić etykietę tekstową polecenia menu za pomocą <xref:System.ComponentModel.Design.IMenuCommandService> usługi.  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Zmiana etykiety polecenia menu z IMenuCommandService  
  
1.  Tworzenie projektu VSIX o nazwie `MenuText` za pomocą polecenia menu o nazwie **ChangeMenuText**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  W pliku .vstc Dodaj `TextChanges` Flaga polecenia menu, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <Button guid="guidChangeMenuTextPackageCmdSet" id="ChangeMenuTextId" priority="0x0100" type="Button">  
        <Parent guid="guidChangeMenuTextPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <CommandFlag>TextChanges</CommandFlag>  
        <Strings>  
            <ButtonText>Invoke ChangeMenuText</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
3.  W pliku ChangeMenuText.cs utworzyć program obsługi zdarzeń, która będzie wywoływana przed wyświetleniem polecenia menu.  
  
    ```csharp  
    private void OnBeforeQueryStatus(object sender, EventArgs e)  
    {  
        var myCommand = sender as OleMenuCommand;  
        if (null != myCommand)  
        {  
            myCommand.Text = "New Text";  
        }  
    }  
    ```  
  
     Stan polecenia menu w ramach tej metody można także zaktualizować, zmieniając <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>, <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>, i <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> właściwości <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiektu.  
  
4.  W Konstruktorze ChangeMenuText Zastąp oryginalny kod inicjowania i rozmieszczenie polecenia kod, który tworzy <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (zamiast `MenuCommand`) który reprezentuje polecenie menu, dodaje <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> obsługi zdarzeń oraz udostępnia menu polecenie usługi polecenia menu.  
  
     Oto, jak jego powinna wyglądać:  
  
    ```csharp  
    private ChangeMenuText(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.ShowMessageBox;  
            OleMenuCommand menuItem = new OleMenuCommand(ShowMessageBox, menuCommandID);  
            menuItem.BeforeQueryStatus +=  
                new EventHandler(OnBeforeQueryStatus);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
5.  Skompiluj projekt i Rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie programu Visual Studio.  
  
6.  Na **narzędzia** menu powinny pojawić się polecenie o nazwie **ChangeMenuText wywołania**.  
  
7.  Kliknij polecenie. Powinny zostać wyświetlone okno komunikatu o MenuItemCallback została wywołana. Gdy zamknąć okno komunikatu, powinny pojawić się teraz jest nazwa polecenia w menu narzędzia **nowy tekst**.
