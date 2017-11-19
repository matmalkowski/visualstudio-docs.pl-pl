---
title: "Często zadawane pytania: Konwertowanie dodatki do rozszerzeń pakiet VSPackage | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7ef1e10f0f19d7134b00d6dd3d37f7e7e6a1ede5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="faq-converting-add-ins-to-vspackage-extensions"></a>Często zadawane pytania: konwertowanie dodatków na rozszerzenia pakietu VSPackage
Dodatki obecnie są przestarzałe. Aby utworzyć nowe rozszerzenie programu Visual Studio, musisz utworzyć rozszerzenia VSIX. Poniżej przedstawiono odpowiedzi na często zadawane pytania dotyczące sposób konwertowania dodatku programu Visual Studio do rozszerzenia VSIX.  
  
> [!WARNING]
>  Począwszy od programu Visual Studio 2015, dla projektów C# i Visual Basic, można korzystać z projektu VSIX i dodać szablony elementów dla polecenia menu okna narzędzi i VSPackages. Aby uzyskać więcej informacji, zobacz [What's New in Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
> [!IMPORTANT]
>  W wielu przypadkach można po prostu przenieś swój kod dodatku do projektu VSIX z elementem projektu pakiet VSPackage. Obiekt automatyzacji DTE można uzyskać przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> w <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.  
>   
>  `DTE2 dte = (DTE2)GetService(typeof(DTE));`  
>   
>  Aby uzyskać więcej informacji, zobacz [jak mogę uruchomić Moje kodu dodatku w pakiet VSPackage?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin) poniżej.  
  
## <a name="what-software-do-i-need-to-develop-vsix-extensions"></a>Jakie oprogramowanie należy opracowywania rozszerzeń VSIX?  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="wheres-the-extension-documentation"></a>Gdzie znajduje się dokumentacja rozszerzenie?  
 Rozpoczynać [uruchamianie opracowywania rozszerzeń programu Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md). Inne artykuły dotyczące VSSDK rozszerzenia Programowanie w witrynie MSDN jest niższy niż jeden.  
  
## <a name="can-i-convert-my-add-in-project-to-a-vsix-project"></a>Czy mogę przekonwertować dodatku projektu do projektu VSIX  
 Nie można przekonwertować projekt Dodaj bezpośrednio do projektu VSIX, ponieważ mechanizmów użycia w projektach VSIX nie są takie same, jak w projektach w dodatku. Szablon projektu VSIX oraz szablony elementów projektu zawiera wiele kodu, który ułatwia stosunkowo łatwa do uruchomienia i działa jako rozszerzenia VSIX.  
  
##  <a name="BKMK_StartDeveloping"></a>Jak rozpocząć tworzenie rozszerzenia VSIX  
 Oto, jak utworzyć VSIX, które ma polecenia menu:  
  
#### <a name="to-make-a-vsix-extension-that-has-a-menu-command"></a>Aby rozszerzenie VSIX, który ma polecenia menu  
  
1.  Tworzenie projektu VSIX. (**Pliku**, **nowy**, **projektu**, lub typ **projektu** w **Szybkie uruchamianie** okno). W **nowy projekt** okna dialogowego rozwiń **Visual C# / rozszerzalności** lub **Visual Basic / rozszerzalności** i wybierz **projektu VSIX**.) Nazwij projekt **TestExtension** i określ lokalizację dla niego.  
  
2.  Dodaj **polecenia niestandardowych** szablonu elementu projektu. (Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **Add / nowy element**. W **nowy projekt** okna dialogowego Visual C# lub Visual Basic, wybierz **rozszerzalności** a następnie wybierz węzeł **polecenia niestandardowych**.)  
  
3.  Naciśnij klawisz F5, aby skompilować i uruchomić projekt w trybie debugowania.  
  
     Zostanie wyświetlone drugie wystąpienie programu Visual Studio. To drugie wystąpienie jest nazywany eksperymentalne wystąpienie i nie może mieć tych samych ustawień, gdy wystąpienie programu Visual Studio do pisania kodu. Podczas pierwszego uruchomienia eksperymentalne wystąpienie, użytkownik jest proszony Zaloguj się do wersji programu VS w trybie Online i określ profil i motywu.  
  
     Na **narzędzia** menu (w eksperymentalnym wystąpieniu) powinny pojawić się przycisk o nazwie **nazwa polecenia Moje**. Jeśli ten przycisk powinien zostać wyświetlony komunikat: **wewnątrz TestVSPackagePackage.MenuItemCallback()**.  
  
##  <a name="BKMK_RunAddin"></a>Jak mogę uruchomić Moje kodu dodatku w pakiet VSPackage  
 Dodatek zwykle działa w jednym z dwóch sposobów:  
  
-   Wyzwalane za pomocą polecenia menu (kod znajduje się w `IDTCommandTarget.Exec` metody)  
  
-   Automatycznie podczas uruchamiania (kod znajduje się w `OnConnection` obsługi zdarzeń.)  
  
 Możesz to zrobić te same działania co w pakiet VSPackage. Poniżej przedstawiono sposób dodawania kodu dodatku niektóre metody wywołania zwrotnego:  
  
#### <a name="to-implement-a-menu-command-in-a-vspackage"></a>Do wykonania polecenia menu w pakiet VSPackage  
  
1.  Utwórz pakiet VSPackage, który zawiera polecenie menu. (Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).)  
  
2.  Otwórz plik, który zawiera definicję pakiet VSPackage. (W projekcie C# ma  *\<nazwę projektu >*Package.cs.)  
  
3.  Dodaj następujące `using` instrukcje do pliku:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Znajdź `MenuItemCallback` metody. Dodaj wywołanie do <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> uzyskanie <xref:EnvDTE80.DTE2> obiektu:  
  
    ```csharp  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Dodaj kod, który dodatku była w jego `IDTCommandTarget.Exec` metody. Na przykład poniżej przedstawiono niektóre kod, który dodaje nowe okienko do **dane wyjściowe** i odbitek "Niektóre Text" w okienku okna.  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));  
        OutputWindow outputWindow = dte.ToolWindows.OutputWindow;  
  
        OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");  
        outputWindowPane.OutputString("Some Text");  
    }  
  
    ```  
  
6.  Tworzenie i uruchamianie tego projektu. Naciśnij klawisz F5 lub wybierz **Start** na **debugowania** paska narzędzi. W eksperymentalne wystąpienie programu Visual Studio **narzędzia** menu powinien mieć przycisk o nazwie **nazwa polecenia Moje**. Po wybraniu tego przycisku wyrazy **niektóre tekst** powinny być wyświetlane w **dane wyjściowe** okienka. (Być może trzeba otworzyć **dane wyjściowe** okna.)  
  
 Można również mieć kodu podczas uruchamiania. Jednak ta metoda nie jest zwykle zalecane dla rozszerzeń pakiet VSPackage. Jeśli zbyt wiele rozszerzeń próbuje załadować podczas uruchamiania programu Visual Studio, godzina rozpoczęcia mogą stać się znacznie dłużej. Rozwiązaniem lepiej jest automatycznie załadować pakiet VSPackage tylko wtedy, gdy niektóre warunek jest spełniony (na przykład rozwiązanie otwierany).  
  
 W tej procedurze pokazano, jak uruchamianie kodu w dodatku w pakiet VSPackage, który jest ładowana automatycznie po otwarciu rozwiązania:  
  
#### <a name="to-autoload-a-vspackage"></a>Aby automatycznie załadować pakiet VSPackage  
  
1.  Tworzenie projektu VSIX z elementem projektu pakietu Visual Studio. (Aby uzyskać instrukcje to zrobić, zobacz [jak rozpocząć tworzenie rozszerzenia VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping). Po prostu Dodaj **pakiet programu Visual Studio** zamiast tego elementu projektu.) Nazwa projektu VSIX **TestAutoload**.  
  
2.  Otwórz TestAutoloadPackage.cs. Znajdź wiersz, w którym zadeklarowana jest klasa pakietu:  
  
    ```csharp  
    public sealed class <name of your package>Package : Package  
    ```  
  
3.  Powyżej tego wiersza to zestaw atrybutów. Dodaj ten atrybut:  
  
    ```csharp  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    ```  
  
4.  Ustaw punkt przerwania `Initialize()` — metoda i rozpocząć debugowanie (F5).  
  
5.  Otwórz projekt w eksperymentalnym wystąpieniu. Pakiet VSPackage powinny zostać załadowane, a powinien trafiony punkt przerwania.  
  
 Można określić innych kontekstach, w którym można załadować VSPackage za pomocą pola <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>. Aby uzyskać więcej informacji, zobacz [ładowania VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="how-can-i-get-the-dte-object"></a>Jak można uzyskać obiektu DTE?  
 Jeśli dodatek nie wyświetla interfejsu użytkownika — na przykład poleceń menu, przycisków paska narzędzi lub narzędzia windows — można użyć kodu jako — jest tak długo, jak uzyskać obiektu DTE automatyzacji z pakiet VSPackage. Oto jak:  
  
#### <a name="to-get-the-dte-object-from-a-vspackage"></a>Aby uzyskać obiektu DTE z pakiet VSPackage  
  
1.  W projekcie VSIX z szablonem elementu pakiet programu Visual Studio, wyszukaj  *\<Nazwa projektu >*Package.cs pliku. Jest to klasa, która jest pochodną <xref:Microsoft.VisualStudio.Shell.Package>; może pomóc w interakcję z programem Visual Studio. W takim przypadku należy użyć jego <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> uzyskanie <xref:EnvDTE80.DTE2> obiektu.  
  
2.  Dodaj te `using` instrukcji:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
3.  Znajdź `Initialize` metody. Ta metoda obsługuje polecenie, które są określone w kreatorze pakietu. Dodaj wywołanie do <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> uzyskać obiektu DTE:  
  
    ```csharp  
    DTE dte = (DTE)GetService(typeof(DTE));  
    ```  
  
 Po utworzeniu <xref:EnvDTE.DTE> obiekt automatyzacji z resztą kodu dodatku można dodać do projektu. Jeśli potrzebujesz <xref:EnvDTE80.DTE2> obiektu, możesz zrobić to samo.  
  
## <a name="how-do-i-change-menu-commands-and-toolbar-buttons-in-my-add-in-to-the-vspackage-style"></a>Jak zmienić przyciski paska narzędzi i poleceń menu w moich dodatku do stylu pakiet VSPackage?  
 Pakiet VSPackage rozszerzenia przy użyciu pliku vsct można utworzyć większość poleceń menu, pasków narzędzi, przycisków paska narzędzi i innych interfejsu użytkownika. **Polecenia niestandardowych** szablonu elementu projektu udostępnia opcję, aby utworzyć polecenie na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Aby uzyskać więcej informacji o plikach vsct, zobacz [jak VSPackages Dodaj elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md). Aby uzyskać wskazówki dotyczące pokazują, jak przy użyciu pliku vsct Dodaj elementy menu, pasków narzędzi i przycisków paska narzędzi, zobacz [rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md).  
  
## <a name="how-do-i-add-custom-tool-windows-in-the-vspackage-way"></a>Jak dodać niestandardowe narzędzie systemu windows w taki sposób, pakiet VSPackage?  
 Szablon elementu okna narzędzia niestandardowe projektu z opcją można utworzyć okna narzędzia. Aby uzyskać więcej informacji dotyczących tego szablonu elementu projektu, zobacz [Tworzenie rozszerzenia z okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md). Informacji o narzędzia windows, temacie [rozszerzanie i dostosowywanie okien narzędzi](../extensibility/extending-and-customizing-tool-windows.md) i artykułów w nim, szczególnie [Dodawanie okna narzędzia](../extensibility/adding-a-tool-window.md).  
  
## <a name="how-do-i-manage-visual-studio-windows-in-the-vspackage-way"></a>Jak zarządzać windows Visual Studio w sposób pakiet VSPackage?  
 Jeśli dodatek Visual Studio, windows, kod dodatku powinny działać w pakiet VSPackage. Na przykład w tej procedurze pokazano, jak dodać kod, który zarządza **listy zadań** do `MenuItemCallback` metody pakiet VSPackage.  
  
#### <a name="to-insert-window-management-code-from-an-add-in-into-a-vspackage"></a>Aby wstawić kod zarządzania systemem Windows z dodatku do pakiet VSPackage  
  
1.  Utwórz pakiet VSPackage, który zawiera polecenie menu, podobnie jak w [jak rozpocząć tworzenie rozszerzenia VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) sekcji.  
  
2.  Otwórz plik, który zawiera definicję pakiet VSPackage. (W projekcie C# ma  *\<nazwę projektu >*Package.cs.)  
  
3.  Dodaj te `using` instrukcji:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Znajdź `MenuItemCallback` metody. Dodaj wywołanie do <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> uzyskanie <xref:EnvDTE80.DTE2> obiektu:  
  
    ```csharp  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Dodaj kod z dodatku. Na przykład poniżej przedstawiono niektóre kod, który dodaje nowe zadania, aby **listy zadań**, wyświetla liczbę zadań i usuwa jedno zadanie.  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)   
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));   
  
        TaskList tl = (TaskList)dte.ToolWindows.TaskList;   
        askItem tlItem;   
  
        // Add a couple of tasks to the Task List.   
        tlItem = tl.TaskItems.Add(" ", " ", "Test task 1.",    
            vsTaskPriority.vsTaskPriorityHigh, vsTaskIcon.vsTaskIconUser,   
            true, "", 10, true, true);  
        tlItem = tl.TaskItems.Add(" ", " ", "Test task 2.",   
            vsTaskPriority.vsTaskPriorityLow, vsTaskIcon.vsTaskIconComment, true, "", 20, true,true);  
  
        // List the total number of task list items after adding the new task items.  
        System.Windows.Forms.MessageBox.Show("Task Item 1 description: "+tl.TaskItems.Item(2).Description);  
        System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);   
  
        // Remove the second task item. The items list in reverse numeric order.   
        System.Windows.Forms.MessageBox.Show("Deleting the second task item");  
        tl.TaskItems.Item(2).Delete();  
        System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);   
    }  
    ```  
  
## <a name="how-do-i-manage-projects-and-solutions-in-a-vspackage"></a>Jak zarządzać projektów i rozwiązań w pakiet VSPackage?  
 Jeśli dodatek zarządza projektów i rozwiązań, kod dodatku powinny działać w pakiet VSPackage. Na przykład w tej procedurze pokazano, jak Dodaj kod, który pobiera projekt startowy.  
  
1.  Utwórz pakiet VSPackage, który zawiera polecenie menu, podobnie jak w [jak rozpocząć tworzenie rozszerzenia VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) sekcji.  
  
2.  Otwórz plik, który zawiera definicję pakiet VSPackage. (W projekcie C# ma  *\<nazwę projektu >*Package.cs.)  
  
3.  Dodaj te `using` instrukcji:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Znajdź `MenuItemCallback` metody. Dodaj wywołanie do <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> uzyskanie <xref:EnvDTE80.DTE2> obiektu:  
  
    ```csharp  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Dodaj kod z dodatku. Na przykład następujący kod pobiera nazwę projektu startowego w rozwiązaniu. (Rozwiązania wielu projektów musi być otwarte po uruchomieniu tego pakietu.)  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));   
  
        SolutionBuild2 sb = (SolutionBuild2)dte.Solution.SolutionBuild;   
        Project startupProj;   
        string msg = "";  
  
        foreach (String item in (Array)sb.StartupProjects)   
        {  
            msg += item;   
        }  
        System.Windows.Forms.MessageBox.Show("Solution startup Project: "+msg);   
        startupProj = dte.Solution.Item(msg);   
        System.Windows.Forms.MessageBox.Show("Full name of solution's startup project: "+"/n"+startupProj.FullName);   
    }  
    ```  
  
## <a name="how-do-i-set-keyboard-shortcuts-in-a-vspackage"></a>Jak ustawić skróty klawiaturowe w pakiet VSPackage?  
 Możesz użyć `<KeyBindings>` element pliku vsct. W poniższym przykładzie skrótu klawiaturowego dla polecenia `idCommand1` Alt + A i skrótu klawiaturowego dla polecenia `idCommand2` jest Alt + Ctrl + A. Zwróć uwagę, składnia nazwy kluczy.  
  
```xml  
<KeyBindings>  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand1" editor="guidVSStd97" key1="A" mod1="ALT" />  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand2" editor="guidVSStd97" key1="A" mod1="CONTROL" mod2="ALT" />  
</KeyBindings>  
```  
  
## <a name="how-do-i-handle-automation-events-in-a-vspackage"></a>Sposób obsługi zdarzeń automatyzacji w pakiet VSPackage?  
 Obsługa zdarzeń automatyzacji w pakiet VSPackage w taki sam sposób jak odbywa się w dodatku. Poniższy kod przedstawia sposób obsługi `OnItemRenamed` zdarzeń. (Założono, że ich już zaakceptujesz obiekt DTE.)  
  
```csharp  
Events2 dteEvents = (Events2)dte.Events;  
dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;   
. . .  
public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)   
{  
    string s = "[Event] Renamed " + oldName + " to " + Path.GetFileName(projItem.get_FileNames(1) + " in project " + projItem.ContainingProject.Name;   
}  
```