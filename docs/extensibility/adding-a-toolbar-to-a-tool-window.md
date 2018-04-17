---
title: Dodawanie paska narzędzi do okna narzędzia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47ff5f69ff559ea1c08d0ae9bdd7192a257c844e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-toolbar-to-a-tool-window"></a>Dodawanie do okna narzędzi paska narzędzi
W tym przewodniku przedstawiono sposób dodawania paska narzędzi okna narzędzia.  
  
 Pasek narzędzi jest pasek pozioma lub pionowa zawierający przyciski powiązany z poleceń. Długość paska narzędzi w oknie narzędzia jest zawsze taki sam jak szerokość lub wysokość okna narzędzia, w zależności od tego, gdzie jest zadokowany pasku narzędzi.  
  
 W odróżnieniu od paski narzędzi w środowisku IDE narzędzi w oknie narzędzia musi być zadokowane i nie można przenosić ani dostosowane. Jeśli pakiet VSPackage są zapisywane w kodzie umanaged, pasek narzędzi może być zadokowany na dowolnej krawędzi.  
  
 Aby uzyskać więcej informacji na temat dodawania paska narzędzi, zobacz [Dodawanie paska narzędzi](../extensibility/adding-a-toolbar.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-toolbar-for-a-tool-window"></a>Tworzenia paska narzędzi okna narzędzi  
  
1.  Tworzenie projektu VSIX o nazwie `TWToolbar` mający zarówno polecenia menu o nazwie **TWTestCommand** i okna narzędzia o nazwie **TestToolWindow**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md) i [Tworzenie rozszerzenia z okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md). Należy dodać szablon elementu polecenia przed dodaniem szablonu okna narzędzia.  
  
2.  TWTestCommandPackage.vsct poszukaj w sekcji symboli. W węźle GuidSymbol o nazwie guidTWTestCommandPackageCmdSet zadeklarować paska narzędzi i grupę narzędzi, w następujący sposób.  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3.  W górnej części `Commands` sekcji, Utwórz `Menus` sekcji. Dodaj `Menu` element, aby zdefiniować na pasku narzędzi.  
  
    ```xml  
    <Menus>  
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     Nie można zagnieżdżać paski narzędzi takich jak podmenu. W związku z tym nie trzeba przypisać element nadrzędny. Ponadto nie masz można ustawić priorytet, ponieważ użytkownik może przenieść pasków narzędzi. Zazwyczaj początkowe położenie paska narzędzi zdefiniowano programowo, ale kolejne zmiany przez użytkownika są zachowywane.  
  
4.  W sekcji grupy definiują grupę zawiera poleceń dla paska narzędzi.  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5.  W sekcji przycisków zmienić element nadrzędny istniejącego elementu przycisk grupę narzędzi, dzięki czemu będzie wyświetlany pasek narzędzi.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     Domyślnie jeśli pasek narzędzi nie ma żadnych poleceń nie ma.  
  
     Ponieważ nowy pasek narzędzi nie zostanie automatycznie dodany do okna narzędzia, jawnie należy dodać paska narzędzi. Ta czynność została omówiona w następnej sekcji.  
  
## <a name="adding-the-toolbar-to-the-tool-window"></a>Dodawanie do okna narzędzia na pasku narzędzi  
  
1.  W TWTestCommandPackageGuids.cs Dodaj następujące wiersze.  
  
    ```csharp  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2.  W TestToolWindow.cs Dodaj następującą instrukcję using.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    ```  
  
3.  W Konstruktorze TestToolWindow Dodaj następujący wiersz.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="testing-the-toolbar-in-the-tool-window"></a>Testowanie na pasku narzędzi w oknie narzędzia  
  
1.  Skompiluj projekt i Rozpocznij debugowanie. Powinna zostać wyświetlona eksperymentalne wystąpienie programu Visual Studio.  
  
2.  Na **widoku / inne okna** menu, kliknij przycisk **ToolWindow testu** do wyświetlenia okna narzędzia.  
  
     Powinien pojawić się w pozostałych narzędzi (prawdopodobnie domyślną ikonę) u góry okna narzędzia bezpośrednio pod tytułem.  
  
3.  Na pasku narzędzi kliknij ikonę, aby wyświetlić komunikat **TWTestCommandPackage wewnątrz TWToolbar.TWTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie paska narzędzi](../extensibility/adding-a-toolbar.md)