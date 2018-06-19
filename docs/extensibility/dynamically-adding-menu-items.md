---
title: Dynamiczne dodawanie elementów Menu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf7c9f8da800e827ac4b1993c55d4d96c8ca9d89
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133279"
---
# <a name="dynamically-adding-menu-items"></a>Dynamiczne dodawanie elementów Menu
Można dodać elementów menu w czasie wykonywania, określając `DynamicItemStart` polecenia flagi na przycisku definicji symbolu zastępczego w plik tabeli poleceń (vsct) programu Visual Studio, a następnie definiowanie (w kodzie) liczbę menu elementów do wyświetlenia i obsługi poleceń. Po załadowaniu pakiet VSPackage symbol zastępczy jest zastępowany dynamicznych elementów menu.  
  
 Visual Studio używa dynamicznej listy w **ostatnio używanych** listy, który wyświetla nazwy dokumentów, które zostały ostatnio otwarte, i **Windows** listę, która wyświetla nazwy systemu windows które są aktualnie otwarte.   `DynamicItemStart` Flagi na definicji polecenia określa, że polecenie jest symbol zastępczy, aż pakiet VSPackage jest otwarty. Po otwarciu pakiet VSPackage symbol zastępczy jest zastępowany 0 lub więcej poleceń, które są tworzone w czasie wykonywania i dodane do listy dynamicznych. Nie można wyświetlić pozycja w menu, których dynamicznej listy pojawia się, dopóki nie zostanie otwarty pakiet VSPackage.  Do wypełnienia listy dynamicznych, Visual Studio zapyta pakiet VSPackage szukać polecenia o identyfikatorze którego pierwsze znaki są takie same jak identyfikator symbol zastępczy. Jeśli program Visual Studio znajdzie odpowiedniego polecenia, dodaje nazwę polecenia do listy dynamicznych. Następnie zwiększa identyfikator i wyszukuje innego polecenia pasującego do dodania do listy dynamicznych, dopóki istnieją polecenia nie jest bardziej dynamiczne.  
  
 W tym przewodniku przedstawiono sposób ustawiania projekt startowy w rozwiązaniu Visual Studio za pomocą polecenia na **Eksploratora rozwiązań** paska narzędzi. Używa kontrolera menu, która ma listę rozwijaną dynamiczne projektów w aktywnym rozwiązaniu. Aby uniknąć tego polecenia pojawia się, gdy żadne rozwiązanie jest otwarte lub Otwórz rozwiązanie po tylko jeden projekt pakiet VSPackage jest ładowany tylko wtedy, gdy rozwiązanie zawiera wiele projektów.  
  
 Aby uzyskać więcej informacji o plikach vsct, zobacz [tabeli poleceń w usłudze Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Tworzenie rozszerzenia za pomocą polecenia Menu  
  
1.  Tworzenie projektu VSIX o nazwie `DynamicMenuItems`.  
  
2.  Po otwarciu projektu Dodawanie polecenia niestandardowego szablonu elementu i nadaj mu nazwę **DynamicMenu**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="setting-up-the-elements-in-the-vsct-file"></a>Definiowanie elementów w pliku vsct  
 Aby utworzyć kontroler menu z dynamicznych elementów menu na pasku narzędzi, należy określić następujące elementy:  
  
-   Polecenie dwie grupy, która zawiera menu kontrolera i inny, który zawiera elementy menu, liście rozwijanej  
  
-   Element menu jednego typu `MenuController`  
  
-   Dwa przyciski, który działa jako symbol zastępczy dla elementów menu oraz innego, który zawiera ikonę i etykietkę narzędzia na pasku narzędzi.  
  
1.  W DynamicMenuPackage.vsct należy zdefiniować identyfikatory poleceń. Przejdź do sekcji symboli i Zastąp elementy z IDSymbol **guidDynamicMenuPackageCmdSet** GuidSymbol bloku. Musisz zdefiniować elementy IDSymbol na dwie grupy, kontrolera menu polecenie symbolu zastępczego i polecenia zakotwiczenia.  
  
    ```csharp  
    <GuidSymbol name="guidDynamicMenuPackageCmdSet" value="{ your GUID here }">  
        <IDSymbol name="MyToolbarItemGroup" value="0x1020" />  
        <IDSymbol name="MyMenuControllerGroup" value="0x1025" />  
        <IDSymbol name="MyMenuController" value ="0x1030"/>  
        <IDSymbol name="cmdidMyAnchorCommand" value="0x0103" />  
        <!-- NOTE: The following command expands at run time to some number of ids.  
         Try not to place command ids after it (e.g. 0x0105, 0x0106).  
         If you must add a command id after it, make the gap very large (e.g. 0x200) -->  
        <IDSymbol name="cmdidMyDynamicStartCommand" value="0x0104" />  
    </GuidSymbol>    
    ```  
  
2.  W sekcji grupy Usuń istniejące grupy i Dodaj dwie grupy, który został zdefiniowany:  
  
    ```  
    <Groups>  
        <!-- The group that adds the MenuController on the Solution Explorer toolbar.   
             The 0x4000 priority adds this group after the group that contains the  
             Preview Selected Items button, which is normally at the far right of the toolbar. -->  
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" priority="0x4000" >  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN" />  
        </Group>  
        <!-- The group for the items on the MenuController drop-down. It is added to the MenuController submenu. -->  
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" priority="0x4000" >  
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" />  
        </Group>  
    </Groups>  
    ```  
  
     Dodaj MenuController. Ustaw wartość flagi polecenia DynamicVisibility, ponieważ nie jest zawsze widoczne. ButtonText nie jest wyświetlana.  
  
    ```  
    <Menus>  
        <!-- The MenuController to display on the Solution Explorer toolbar.  
             Place it in the ToolbarItemGroup.-->  
        <Menu guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" priority="0x1000" type="MenuController">  
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" />  
            <CommandFlag>DynamicVisibility</CommandFlag>  
            <Strings>  
               <ButtonText></ButtonText>  
           </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
3.  Dodaj dwa przyciski: jeden jako symbol zastępczy dynamicznych elementów menu, a drugi jako swojej kotwicy dla MenuController.  
  
     Element nadrzędny przycisku symbol zastępczy jest **MyMenuControllerGroup**. Dodawanie flagi polecenia DynamicItemStart, DynamicVisibility i TextChanges do przycisku symbol zastępczy. ButtonText nie jest wyświetlana.  
  
     Przycisk zakotwiczenia zawiera ikonę i tekst etykietki narzędzia. Element nadrzędny przycisku zakotwiczenia jest również **MyMenuControllerGroup**. Należy dodać polecenie NoShowOnMenuController flagi upewnij się, że przycisk faktycznie nie jest wyświetlane w menu rozwijanym kontrolera i Flaga polecenia FixMenuController dokonanie stałe zakotwiczenia.  
  
    ```  
    <!-- The placeholder for the dynamic items that expand to N items at runtime. -->  
    <Buttons>  
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyDynamicStartCommand" priority="0x1000" >  
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />  
          <CommandFlag>DynamicItemStart</CommandFlag>  
          <CommandFlag>DynamicVisibility</CommandFlag>  
          <CommandFlag>TextChanges</CommandFlag>  
          <!-- This text does not appear. -->  
          <Strings>  
            <ButtonText>Project</ButtonText>  
          </Strings>  
        </Button>  
  
        <!-- The anchor item to supply the icon/tooltip for the MenuController -->  
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyAnchorCommand" priority="0x0000" >  
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />  
          <!-- This is the icon that appears on the Solution Explorer toolbar. -->  
          <Icon guid="guidImages" id="bmpPicArrows"/>  
          <!-- Do not show on the menu controller's drop down list-->  
          <CommandFlag>NoShowOnMenuController</CommandFlag>  
          <!-- Become the permanent anchor item for the menu controller -->  
          <CommandFlag>FixMenuController</CommandFlag>  
          <!-- The text that appears in the tooltip.-->  
          <Strings>  
            <ButtonText>Set Startup Project</ButtonText>  
          </Strings>  
        </Button>  
    </Buttons>  
    ```  
  
4.  Dodać ikony do projektu (w folderze Zasoby), a następnie dodaj odwołanie do niej w pliku vsct. W tym przewodniku używamy ikonę strzałki, która jest zawarta w szablonie projektu.  
  
5.  Dodaj sekcję VisibilityConstraints poza sekcji poleceń, bezpośrednio przed sekcji symboli. (Może wystąpić ostrzeżenie, jeśli dodasz po symbole.) W tej sekcji upewnia się, że kontroler menu pojawi się tylko po załadowaniu rozwiązania z wieloma projektami.  
  
    ```  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## <a name="implementing-the-dynamic-menu-command"></a>Implementacja polecenia menu dynamiczne  
 Tworzenie klasy poleceń menu dynamiczne, która dziedziczy <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>. W tej implementacji konstruktora określa predykat do użycia na potrzeby uzgadniania poleceń. Konieczne jest przesłonięcie <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> metodę, aby użyć tego predykatu można ustawić <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> właściwości, które identyfikuje polecenie do wywołania.  
  
1.  Utwórz nowy C# klasy plik o nazwie DynamicItemMenuCommand.cs, a następnie Dodaj klasę o nazwie **DynamicItemMenuCommand** dziedziczący po <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:  
  
    ```csharp  
    class DynamicItemMenuCommand : OleMenuCommand  
    {  
  
    }  
  
    ```  
  
2.  Dodaj następujące instrukcje using:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Dodaj pole prywatne do przechowywania predykatu dopasowania:  
  
    ```csharp  
    private Predicate<int> matches;  
  
    ```  
  
4.  Dodaj Konstruktor, który dziedziczy z <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Konstruktor i określa programem obsługi i <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> obsługi. Dodaj predykat dopasowanie polecenia:  
  
    ```csharp  
    public DynamicItemMenuCommand(CommandID rootId, Predicate<int> matches, EventHandler invokeHandler, EventHandler beforeQueryStatusHandler)  
        : base(invokeHandler, null /*changeHandler*/, beforeQueryStatusHandler, rootId)  
    {  
        if (matches == null)  
        {  
            throw new ArgumentNullException("matches");  
        }  
  
        this.matches = matches;  
    }  
    ```  
  
5.  Zastąpienie <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> metodę, tak że wywołuje dopasowań predykat i zestawy <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> właściwości:  
  
    ```csharp  
    public override bool DynamicItemMatch(int cmdId)  
    {  
        // Call the supplied predicate to test whether the given cmdId is a match.  
        // If it is, store the command id in MatchedCommandid   
        // for use by any BeforeQueryStatus handlers, and then return that it is a match.  
        // Otherwise clear any previously stored matched cmdId and return that it is not a match.  
        if (this.matches(cmdId))  
        {  
            this.MatchedCommandId = cmdId;  
            return true;  
        }  
  
        this.MatchedCommandId = 0;  
        return false;  
    }  
    ```  
  
## <a name="adding-the-command"></a>Dodawanie polecenia  
 Konstruktor DynamicMenu jest skonfigurowanie poleceń menu, w tym menu dynamiczne i elementów menu.  
  
1.  W DynamicMenuPackage.cs Dodaj identyfikator GUID zestawu poleceń i identyfikator polecenia:  
  
    ```csharp  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2.  W pliku DynamicMenu.cs, Dodaj następujące instrukcje using:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3.  W klasie DynamicMenu Dodaj pole prywatne **dte2**.  
  
    ```csharp  
    private DTE2 dte2;  
    ```  
  
4.  Dodaj pole prywatne rootItemId:  
  
    ```csharp  
    private int rootItemId = 0;  
    ```  
  
5.  W Konstruktorze DynamicMenu Dodawanie polecenia menu. W następnej sekcji zdefiniujemy program obsługi poleceń `BeforeQueryStatus` obsługi zdarzeń i predykatu dopasowania.  
  
    ```csharp  
    private DynamicMenu(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            // Add the DynamicItemMenuCommand for the expansion of the root item into N items at run time.   
            CommandID dynamicItemRootId = new CommandID(new Guid(DynamicMenuPackageGuids.guidDynamicMenuPackageCmdSet), (int)DynamicMenuPackageGuids.cmdidMyCommand);  
            DynamicItemMenuCommand dynamicMenuCommand = new DynamicItemMenuCommand(dynamicItemRootId,  
                IsValidDynamicItem,  
                OnInvokedDynamicItem,  
                OnBeforeQueryStatusDynamicItem);  
                commandService.AddCommand(dynamicMenuCommand);  
                }  
  
        dte2 = (DTE2)this.ServiceProvider.GetService(typeof(DTE));  
    }  
    ```  
  
## <a name="implementing-the-handlers"></a>Implementowanie obsługi  
 Aby zaimplementować dynamicznych elementów menu na kontrolerze menu, musi obsługiwać polecenia po kliknięciu elementów dynamicznych. Musi także implementować logikę, która ustawia stan elementu menu. Dodawanie obsługi do klasy DynamicMenu.  
  
1.  Aby zaimplementować **Ustaw projekt startowy** polecenia, należy dodać **OnInvokedDynamicItem** obsługi zdarzeń. Wygląda na to dla projektu, którego nazwa jest taka sama jak tekst polecenia, które zostało wywołane i ustawia go jako projekt startowy, ustawiając jego ścieżki bezwzględnej w <xref:EnvDTE.SolutionBuild.StartupProjects%2A> właściwości.  
  
    ```csharp  
    private void OnInvokedDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;  
        // If the command is already checked, we don't need to do anything  
        if (invokedCommand.Checked)  
            return;  
  
        // Find the project that corresponds to the command text and set it as the startup project  
        var projects = dte2.Solution.Projects;  
        foreach (Project proj in projects)  
        {  
            if (invokedCommand.Text.Equals(proj.Name))  
            {  
                dte2.Solution.SolutionBuild.StartupProjects = proj.FullName;  
                return;  
            }  
        }  
    }  
    ```  
  
2.  Dodaj `OnBeforeQueryStatusDynamicItem` obsługi zdarzeń. To jest program obsługi wywołana przed `QueryStatus` zdarzeń. Określa, czy element menu jest elementem "rzeczywiste", czyli nie symbol zastępczy elementu, i określa, czy element jest już wyewidencjonowany (co oznacza, że projekt jest już ustawiony jako projekt startowy).  
  
    ```csharp  
    private void OnBeforeQueryStatusDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand matchedCommand = (DynamicItemMenuCommand)sender;  
        matchedCommand.Enabled = true;  
        matchedCommand.Visible = true;  
  
        // Find out whether the command ID is 0, which is the ID of the root item.  
        // If it is the root item, it matches the constructed DynamicItemMenuCommand,  
         // and IsValidDynamicItem won't be called.  
        bool isRootItem = (matchedCommand.MatchedCommandId == 0);  
  
        // The index is set to 1 rather than 0 because the Solution.Projects collection is 1-based.  
        int indexForDisplay = (isRootItem ? 1 : (matchedCommand.MatchedCommandId - (int) DynamicMenuPackageGuids.cmdidMyCommand) + 1);  
  
        matchedCommand.Text = dte2.Solution.Projects.Item(indexForDisplay).Name;  
  
        Array startupProjects = (Array)dte2.Solution.SolutionBuild.StartupProjects;  
        string startupProject = System.IO.Path.GetFileNameWithoutExtension((string)startupProjects.GetValue(0));  
  
        // Check the command if it isn't checked already selected  
        matchedCommand.Checked = (matchedCommand.Text == startupProject);  
  
        // Clear the ID because we are done with this item.  
        matchedCommand.MatchedCommandId = 0;  
    }  
    ```  
  
## <a name="implementing-the-command-id-match-predicate"></a>Implementowanie predykatu dopasowania identyfikator polecenia  
  
1.  Teraz można zaimplementować predykatu dopasowania. Należy określić dwie czynności: najpierw, czy identyfikator polecenia jest nieprawidłowa (jest większa niż lub równa identyfikator polecenia zadeklarowane) i drugie, czy określa możliwości projektu (jest mniejsza niż liczba projektów w rozwiązaniu).  
  
    ```csharp  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## <a name="setting-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Ustawienie pakiet VSPackage załadować tylko wtedy, gdy rozwiązanie wielu projektów  
 Ponieważ **Ustaw projekt startowy** polecenia nie ma sensu, chyba że aktywne rozwiązanie ma więcej niż jeden projekt, można ustawić VSPackage na automatyczne ładowanie tylko w takim przypadku. Możesz użyć <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> wraz z kontekstu interfejsu użytkownika <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>. W pliku DynamicMenuPackage.cs do klasy DynamicMenuPackage należy dodać następujące atrybuty:  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
[ProvideMenuResource("Menus.ctmenu", 1)]  
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]  
[Guid(DynamicMenuPackage.PackageGuidString)]  
public sealed class DynamicMenuItemsPackage : Package  
{}  
```  
  
## <a name="testing-the-set-startup-project-command"></a>Testowanie polecenia Ustaw projekt startowy  
 Teraz możesz przetestować kodu.  
  
1.  Skompiluj projekt i Rozpocznij debugowanie. Eksperymentalne wystąpienie powinny być wyświetlane.  
  
2.  W eksperymentalnym wystąpieniu Otwórz rozwiązanie, które ma więcej niż jeden projekt.  
  
     Powinny pojawić ikonę strzałki na **Eksploratora rozwiązań** paska narzędzi. Po rozwinięciu go powinna pojawić się elementy menu, które reprezentują różnych projektów w rozwiązaniu.  
  
3.  Po zaznaczeniu jednego z projektów staje się projekt startowy.  
  
4.  Zamknij rozwiązanie lub Otwórz rozwiązanie, która ma tylko jeden projekt, powinien zniknąć ikony paska narzędzi.  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia, menu i pasków narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)