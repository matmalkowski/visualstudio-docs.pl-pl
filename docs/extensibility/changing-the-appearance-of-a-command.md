---
title: "Zmiana wyglądu polecenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7ffb8aed183b50958c8835b2a1e79b808ac20174
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="changing-the-appearance-of-a-command"></a>Zmiana wyglądu polecenia
Zmiana wyglądu polecenia zapewniają opinię do użytkownika. Na przykład możesz polecenie wyglądać inaczej, gdy jest ona niedostępna. Można wprowadzić polecenia dostępne lub niedostępne, Ukryj lub widoczne, lub sprawdź lub usuń zaznaczenie ich w menu.  
  
 Aby zmienić wygląd polecenia, wykonaj jedną z następujących działań:  
  
-   Określ odpowiednie flagi w definicji poleceń w pliku poleceń tabeli.  
  
-   Użyj <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> usługi.  
  
-   Implementowanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu i modyfikowania obiektów pierwotnych polecenia.  
  
 Poniższe kroki przedstawiają sposób odnaleźć i zaktualizować wyglądu polecenia przy użyciu Framework zarządzane pakietu (MPF).  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>Aby zmienić wygląd polecenia menu  
  
1.  Postępuj zgodnie z instrukcjami [zmiana tekstu polecenia Menu](../extensibility/changing-the-text-of-a-menu-command.md) Aby utworzyć element menu o nazwie `New Text`.  
  
2.  W pliku ChangeMenuText.cs, dodaj następującą instrukcję using:  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3.  W pliku ChangeMenuTextPackageGuids.cs Dodaj następujący wiersz:  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  W pliku ChangeMenuText.cs Zastąp kod w metodzie ShowMessageBox następujące czynności:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  Uzyskaj polecenie, które mają zostać zaktualizowane z <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> obiekt, a następnie ustaw odpowiednie właściwości w obiekcie command. Na przykład następująca metoda sprawia, że określone polecenie polecenia pakiet VSPackage dostępne lub niedostępne. Poniższy kod sprawia, że element menu o nazwie `New Text` niedostępne po zostanie kliknięta.  
  
    ```csharp  
    public bool ChangeMyCommand(int cmdID, bool enableCmd)  
    {  
        bool cmdUpdated = false;  
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))  
            as OleMenuCommandService;  
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);  
        MenuCommand mc = mcs.FindCommand(newCmdID);  
        if (mc != null)  
        {  
            mc.Enabled = enableCmd;  
            cmdUpdated = true;  
        }  
        return cmdUpdated;    }  
    }  
    ```  
  
6.  Skompiluj projekt i Rozpocznij debugowanie. Powinna zostać wyświetlona eksperymentalne wystąpienie programu Visual Studio.  
  
7.  Na **narzędzia** menu, kliknij przycisk **wywołania ChangeMenuText** polecenia. W tym momencie jest nazwa polecenia **ChangeMenuText wywołania**, dlatego program obsługi poleceń nie wywołać ChangeMyCommand().  
  
8.  Na **narzędzia** menu powinien zostać wyświetlony **nowy tekst**. Kliknij przycisk **nowy tekst**. Polecenie powinny teraz wygaszone.  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia, menu i pasków narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Jak VSPackages dodać elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)   
 [Tabela polecenia programu Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)