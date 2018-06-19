---
title: Zarządzanie projektami uniwersalnych systemu Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d251818d9fba0c025b94fa17611a725daad3cec8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31147597"
---
# <a name="managing-universal-windows-projects"></a>Zarządzanie projektami uniwersalnych systemu Windows
Aplikacje uniwersalne systemu Windows są aplikacje, które odnoszą się do zarówno Windows 8.1 i Windows Phone 8.1, co pozwala deweloperom korzystać z kodu oraz innych zasobów na obu platform. Udostępnionego kodu i zasobów są przechowywane w projekcie udostępnionym podczas kodu określonych platform i zasobów, które są przechowywane w oddzielnych projekty: jeden dla systemu Windows, a drugie dla Windows Phone. Aby uzyskać więcej informacji na temat uniwersalnych aplikacji systemu Windows, zobacz [uniwersalnych aplikacji systemu Windows](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Rozszerzenia programu Visual Studio, które zarządzają projektów należy zwrócić uwagę, że struktura, która różni się od aplikacji pojedynczej platformy uniwersalne projekty aplikacji systemu Windows. W tym przewodniku przedstawiono sposób Przejdź projektu udostępnionego i zarządzanie nimi udostępnione elementy.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="navigate-the-shared-project"></a>Przejdź do projektu udostępnionego  
  
1.  Tworzenie projektu VSIX C# o nazwie **TestUniversalProject**. (**Pliku, nowe, projekt** , a następnie **pakiet programu Visual Studio C#, rozszerzalności,**). Dodaj **polecenia niestandardowych** szablonu elementu projektu (w Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**, następnie przejdź do **rozszerzalności**). Nadaj nazwę plikowi **TestUniversalProject**.  
  
2.  Dodaj odwołanie do Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll i Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll (w **rozszerzenia** sekcji).  
  
3.  Otwórz TestUniversalProject.cs i dodaj następujące `using` instrukcji:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.Internal.VisualStudio.PlatformUI;   
    using System.Collections.Generic;   
    using System.IO;  
    using System.Windows.Forms;  
    ```  
  
4.  W klasie TestUniversalProject Dodaj pole prywatne wskazuje **dane wyjściowe** okna.  
  
    ```csharp  
    public sealed class TestUniversalProject   
    {  
        IVsOutputWindowPane output;  
    . . .  
    }  
    ```  
  
5.  Ustaw odwołanie do wewnątrz konstruktora TestUniversalProject w okienku danych wyjściowych:  
  
    ```csharp  
    private TestUniversalProject(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.ShowMessageBox;  
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
        // get a reference to the Output window  
                    output = (IVsOutputWindowPane)ServiceProvider.GetService(typeof(SVsGeneralOutputWindowPane));  
    }  
    ```  
  
6.  Usuń istniejący kod z `ShowMessageBox` metody:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)   
    {  
    }  
    ```  
  
7.  Pobierz obiekt DTE, który zostanie wykorzystany do kilku różnych celów, w tym przewodniku. Ponadto upewnij się, że rozwiązanie jest załadowany po kliknięciu przycisku menu.  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {   
        var dte = (EnvDTE.DTE)this.ServiceProvider.GetService(typeof(EnvDTE.DTE));  
        if (dte.Solution != null)   
        {  
            . . .  
        }  
        else   
        {  
            MessageBox.Show("No solution is open");  
            return;   
        }  
    }  
    ```  
  
8.  Znajdź projektu udostępnionego. Projektu udostępnionego jest kontenerem czysty; nie Konstruuj lub tworzyć dane wyjściowe. Następująca metoda znajduje pierwszy udostępnionego projektu w rozwiązaniu, wyszukując <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiekt, który ma możliwość projektu udostępnionego.  
  
    ```csharp  
    private IVsHierarchy FindSharedProject()  
    {  
        var sln = (IVsSolution)this.ServiceProvider.GetService(typeof(SVsSolution));  
        Guid empty = Guid.Empty;  
        IEnumHierarchies enumHiers;  
  
        //get all the projects in the solution  
        ErrorHandler.ThrowOnFailure(sln.GetProjectEnum((uint)__VSENUMPROJFLAGS.EPF_LOADEDINSOLUTION, ref empty, out enumHiers));  
        foreach (IVsHierarchy hier in ComUtilities.EnumerableFrom(enumHiers))  
        {  
            if (PackageUtilities.IsCapabilityMatch(hier, "SharedAssetsProject"))  
            {  
                return hier;  
            }  
        }  
        return null;  
    }  
    ```  
  
9. W `ShowMessageBox` metody output podpis (nazwa projektu, która jest wyświetlana w **Eksploratora rozwiązań**) projektu udostępnionego.  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
  
        if (dte.Solution != null)  
        {  
            var sharedHier = this.FindSharedProject();  
            if (sharedHier != null)  
            {  
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,  
                     (int)__VSHPROPID.VSHPROPID_Caption);  
                output.OutputStringThreadSafe(string.Format("Found shared project: {0}\n", sharedCaption));  
            }  
            else  
            {  
                MessageBox.Show("Solution has no shared project");  
                return;  
            }  
                }  
        else  
        {  
            MessageBox.Show("No solution is open");  
            return;  
        }  
    }  
    ```  
  
10. Pobieranie projektu aktywnej platformy. Projekty platformy są projekty zawierające kod specyficzne dla platformy i zasobów. Następująca metoda używa nowego pola <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7> można pobrać aktywnej platformy projektu.  
  
    ```csharp  
    private IVsHierarchy GetActiveProjectContext(IVsHierarchy hierarchy)  
    {  
        IVsHierarchy activeProjectContext;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,  
             (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, out activeProjectContext))  
        {  
            return activeProjectContext;  
        }  
        else  
        {  
            return null;  
        }  
    }  
    ```  
  
11. W `ShowMessageBox` metody output podpis aktywnej platformy projektu.  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
  
        if (dte.Solution != null)  
        {  
            var sharedHier = this.FindSharedProject();  
            if (sharedHier != null)  
            {  
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,  
                     (int)__VSHPROPID.VSHPROPID_Caption);  
                output.OutputStringThreadSafe(string.Format("Shared project: {0}\n", sharedCaption));  
  
                var activePlatformHier = this.GetActiveProjectContext(sharedHier);  
                if (activePlatformHier != null)  
                {  
                    string activeCaption = HierarchyUtilities.GetHierarchyProperty<string>(activePlatformHier,  
                         (uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_Caption);  
                    output.OutputStringThreadSafe(string.Format("Active platform project: {0}\n", activeCaption));  
                }  
                else  
                {  
                MessageBox.Show("Shared project has no active platform project");  
                }  
            }  
            else  
            {  
                MessageBox.Show("Solution has no shared project");  
                return;  
            }  
        }  
        else  
            {  
                MessageBox.Show("No solution is open");  
                return;  
            }  
        }  
  
    ```  
  
12. Iterację projektów platformy. Następująca metoda pobiera wszystkie importowania projekty (platform) z projektu udostępnionego.  
  
    ```csharp  
    private IEnumerable<IVsHierarchy> EnumImportingProjects(IVsHierarchy hierarchy)  
    {  
        IVsSharedAssetsProject sharedAssetsProject;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,  
            (int)__VSHPROPID7.VSHPROPID_SharedAssetsProject, out sharedAssetsProject)  
            && sharedAssetsProject != null)  
        {  
            foreach (IVsHierarchy importingProject in sharedAssetsProject.EnumImportingProjects())  
            {  
                yield return importingProject;  
            }  
        }  
    }  
    ```  
  
    > [!IMPORTANT]
    >  Jeśli użytkownik otworzył projekt aplikacji Windows universal języka C++ w eksperymentalnym wystąpieniu, powyższy kod zgłasza wyjątek. Jest to znany problem. Aby uniknąć tego wyjątku, Zastąp `foreach` zablokować powyżej następującym kodem:  
  
    ```csharp  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  
  
13. W `ShowMessageBox` podpis każdego projektu platformy danych wyjściowych metody. Wstaw następujący kod po wierszu, który wyprowadza podpis aktywnej platformy projektu. Projekty platformy, które są ładowane są wyświetlane na tej liście.  
  
    ```csharp  
    output.OutputStringThreadSafe("Platform projects:\n");  
  
    IEnumerable<IVsHierarchy> projects = this.EnumImportingProjects(sharedHier);  
  
    bool isActiveProjectSet = false;  
    foreach (IVsHierarchy platformHier in projects)  
    {  
        string platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,  
            (int)__VSHPROPID.VSHPROPID_Caption);  
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));  
    }  
    ```  
  
14. Zmień projekt aktywnej platformy. Ustawia następującą metodę w aktywnym projekcie przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  
  
    ```csharp  
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)  
    {  
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);  
    }  
    ```  
  
15. W `ShowMessageBox` metody, zmień aktywnej platformy projektu. Wstaw ten kod wewnątrz `foreach` bloku.  
  
    ```csharp  
    bool isActiveProjectSet = false;  
    string platformCaption = null;  
    foreach (IVsHierarchy platformHier in projects)  
    {  
        platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,  
             (int)__VSHPROPID.VSHPROPID_Caption);  
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));  
  
        // if this project is neither the shared project nor the current active platform project,   
        // set it to be the active project  
        if (!isActiveProjectSet && platformHier != activePlatformHier)  
        {  
            this.SetActiveProjectContext(sharedHier, platformHier);  
            activePlatformHier = platformHier;  
            isActiveProjectSet = true;  
        }  
    }  
    output.OutputStringThreadSafe("set active project: " + platformCaption +'\n');  
    ```  
  
16. Teraz wypróbować jej możliwości. Naciśnij klawisz F5, aby uruchomić eksperymentalne wystąpienie. Utwórz projekt aplikacji uniwersalnej Centrum C# w eksperymentalnym wystąpieniu (w **nowy projekt** okno dialogowe **Visual C# / Windows / Windows 8 / uniwersalnych / aplikacji Centrum**). Po załadowaniu rozwiązania, przejdź do **narzędzia** menu i kliknij przycisk **wywołania TestUniversalProject**, a następnie sprawdź tekst **dane wyjściowe** okienka. Powinny zostać wyświetlone informacje podobne do następujących:  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  
  
### <a name="manage-the-shared-items-in-the-platform-project"></a>Zarządzanie udostępnione elementy w projekcie platformy  
  
1.  Znajdź elementy udostępnionych w projekcie platformy. Elementy w projekcie udostępnionym są wyświetlane w projekcie platformy jako elementy udostępnionych. Nie widać je w **Eksploratora rozwiązań**, ale możesz zapoznać się z hierarchii projektu, aby je znaleźć. Następująca metoda przeprowadzi hierarchii i zbiera wszystkie udostępnione elementy. Opcjonalnie danych wyjściowych podpis każdego elementu. Udostępnione elementy, które są identyfikowane przez nową właściwość <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>.  
  
    ```csharp  
    private void InspectHierarchyItems(IVsHierarchy hier, uint itemid, int level, List<uint> itemIds, bool getSharedItems, bool printItems)  
    {  
        string caption = HierarchyUtilities.GetHierarchyProperty<string>(hier, itemid, (int)__VSHPROPID.VSHPROPID_Caption);  
        if (printItems)  
            output.OutputStringThreadSafe(string.Format("{0}{1}\n", new string('\t', level), caption));  
  
        // if getSharedItems is true, inspect only shared items; if it's false, inspect only unshared items  
        bool isSharedItem;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID7.VSHPROPID_IsSharedItem, out isSharedItem)  
            && (isSharedItem == getSharedItems))  
        {  
            itemIds.Add(itemid);  
        }  
  
        uint child;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID.VSHPROPID_FirstChild, Unbox.AsUInt32, out child)  
            && child != (uint)VSConstants.VSITEMID.Nil)  
        {  
            this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);  
  
            while (HierarchyUtilities.TryGetHierarchyProperty(hier, child, (int)__VSHPROPID.VSHPROPID_NextSibling, Unbox.AsUInt32, out child)  
                && child != (uint)VSConstants.VSITEMID.Nil)  
            {  
                this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);  
            }  
                    }  
    }  
    ```  
  
2.  W `ShowMessageBox` metody, Dodaj następujący kod do przeszukania elementy hierarchii projektu platformy. Wstaw go w programie `foreach` bloku.  
  
    ```csharp  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  
  
3.  Odczytuj elementy udostępnionych. Udostępnione elementy, które znajdują się w projekcie platformy jako ukryte pliki połączone, i może odczytywać wszystkie właściwości zwykłych plików połączonych. Poniższy kod odczytuje pełną ścieżkę pierwszego elementu udostępnionego.  
  
    ```csharp  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  
  
4.  Teraz wypróbować jej możliwości. Naciśnij klawisz F5, aby uruchomić eksperymentalne wystąpienie. Utwórz projekt aplikacji uniwersalnej Centrum C# w eksperymentalnym wystąpieniu (w **nowy projekt** okno dialogowe **Visual C# / Windows / Windows 8 / uniwersalnych / aplikacji Centrum**) przejdź do **narzędzia** menu i kliknij przycisk **wywołania TestUniversalProject**, a następnie sprawdź tekst **dane wyjściowe** okienka. Powinny zostać wyświetlone informacje podobne do następujących:  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    Walk the active platform project:  
        HubApp.WindowsPhone  
            <HubApp.Shared>  
                App.xaml  
                    App.xaml.cs  
                Assets  
                    DarkGray.png  
                    LightGray.png  
                    MediumGray.png  
                Common  
                    NavigationHelper.cs  
                    ObservableDictionary.cs  
                    RelayCommand.cs  
                    SuspensionManager.cs  
                DataModel  
                    SampleData.json  
                    SampleDataSource.cs  
                HubApp.Shared.projitems  
                Strings  
                    en-US  
                        Resources.resw  
            Assets  
                HubBackground.theme-dark.png  
                HubBackground.theme-light.png  
                Logo.scale-240.png  
                SmallLogo.scale-240.png  
                SplashScreen.scale-240.png  
                Square71x71Logo.scale-240.png  
                StoreLogo.scale-240.png  
                WideLogo.scale-240.png  
            HubPage.xaml  
                HubPage.xaml.cs  
            ItemPage.xaml  
                ItemPage.xaml.cs  
            Package.appxmanifest  
            Properties  
                AssemblyInfo.cs  
            References  
                .NET for Windows Store apps  
                HubApp.Shared  
                Windows Phone 8.1  
            SectionPage.xaml  
                SectionPage.xaml.cs  
    ```  
  
### <a name="detecting-changes-in-platform-projects-and-shared-projects"></a>Wykrywanie zmian w platformie i udostępnionych projektów  
  
1.  Zdarzenia hierarchii i projektu służy do wykrywania zmian z udostępnionych projektów, tak jak w przypadku projektów platformy. Jednak elementów projektu w projekcie udostępnionym nie są widoczne, co oznacza, że określone zdarzenia nie uruchamiają się po zmianie elementów projektu udostępnionego.  
  
     Należy wziąć pod uwagę sekwencję zdarzeń, gdy zostanie zmieniona nazwa pliku w projekcie:  
  
    1.  Nazwa pliku została zmieniona na dysku.  
  
    2.  Plik projektu jest zaktualizowano nową nazwę pliku.  
  
     Zdarzenia hierarchii (na przykład <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>) zwykle śledzenia zmian wyświetlane w Interfejsie użytkownika, jak w **Eksploratora rozwiązań**. Zdarzenia hierarchii należy wziąć pod uwagę na składają się usuwanie plików, a następnie dodanie pliku operacji zmiany nazwy pliku. Jednak po zmianie są niewidoczne elementy generowane system zdarzeń hierarchii <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> zdarzeń, ale nie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> zdarzeń. Dlatego w przypadku zmiany nazwy pliku w projekcie platformy, możesz uzyskać zarówno <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>, ale w przypadku zmiany nazwy pliku w projekcie udostępnionym, możesz uzyskać tylko <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>.  
  
     Aby śledzić zmiany w elementach projektu, można obsługiwać zdarzenia elementu projektu DTE (te znalezione w <xref:EnvDTE.ProjectItemsEventsClass>). Jednak jeśli są obsługi dużej liczby zdarzeń, możesz uzyskać lepszą wydajność obsługi zdarzeń w <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>. W tym przewodniku zostanie przedstawiony tylko zdarzenia hierarchii i DTE. W tej procedurze należy dodać do udostępnionego projektu i projektu platformy odbiornik zdarzeń. Następnie po zmianie nazwy jeden plik w projekcie udostępnionym i innego pliku w projekcie platformy, widać zdarzenia, które są uruchamiane dla każdej operacji zmiany nazwy.  
  
     W tej procedurze należy dodać do udostępnionego projektu i projektu platformy odbiornik zdarzeń. Następnie po zmianie nazwy jeden plik w projekcie udostępnionym i innego pliku w projekcie platformy, widać zdarzenia, które są uruchamiane dla każdej operacji zmiany nazwy.  
  
2.  Dodaj odbiornik zdarzeń. Dodaj nowy plik klasy do projektu i wywołać ją HierarchyEventListener.cs.  
  
3.  Otwórz plik HierarchyEventListener.cs i dodaj następujące instrukcje using:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using System.IO;  
  
    ```  
  
4.  Ma `HierarchyEventListener` implementacji klasy <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:  
  
    ```csharp  
    class HierarchyEventListener : IVsHierarchyEvents  
    { }  
  
    ```  
  
5.  Implementować członków <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>, jak w poniższym kodzie.  
  
    ```csharp  
    class HierarchyEventListener : IVsHierarchyEvents  
    {  
        private IVsHierarchy hierarchy;  
        IVsOutputWindowPane output;   
  
        internal HierarchyEventListener(IVsHierarchy hierarchy, IVsOutputWindowPane outputWindow) {  
             this.hierarchy = hierarchy;  
             this.output = outputWindow;  
        }  
  
        int IVsHierarchyEvents.OnInvalidateIcon(IntPtr hIcon) {  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnInvalidateItems(uint itemIDParent) {  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnItemAdded(uint itemIDParent, uint itemIDSiblingPrev, uint itemIDAdded) {  
            output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemAdded: " + itemIDAdded + "\n");  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnItemDeleted(uint itemID) {  
            output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemDeleted: " + itemID + "\n");  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnItemsAppended(uint itemIDParent) {  
            output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemsAppended\n");  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnPropertyChanged(uint itemID, int propID, uint flags) {  
            output.OutputStringThreadSafe("IVsHierarchyEvents.OnPropertyChanged: item ID " + itemID + "\n");  
            return VSConstants.S_OK;  
        }  
    }  
  
    ```  
  
6.  W tej samej klasy dodać inny program obsługi zdarzeń dla zdarzenia DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>, który występuje, gdy element projektu zostanie zmieniona.  
  
    ```csharp  
    public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
    {  
        output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
             oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
    }  
    ```  
  
7.  Załóż zdarzenia hierarchii. Musisz utworzyć konto osobno dla każdego projektu, które są śledzone. Dodaj następujący kod w `ShowMessageBox`, jeden dla projektu udostępnionego, a drugie dla jednego z projektów platformy.  
  
    ```csharp  
    // hook up the event listener for hierarchy events on the shared project  
    HierarchyEventListener listener1 = new HierarchyEventListener(sharedHier, output);  
    uint cookie1;  
    sharedHier.AdviseHierarchyEvents(listener1, out cookie1);  
  
    // hook up the event listener for hierarchy events on the   
    active project  
    HierarchyEventListener listener2 = new HierarchyEventListener(activePlatformHier, output);  
    uint cookie2;  
    activePlatformHier.AdviseHierarchyEvents(listener2, out cookie2);  
    ```  
  
8.  Załóż zdarzenie elementu projektu DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>. Dodaj następujący kod po Podłączanie drugi odbiornika.  
  
    ```csharp  
    // hook up DTE events for project items  
    Events2 dteEvents = (Events2)dte.Events;  
    dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  
  
    ```  
  
9. Modyfikowanie udostępnionego elementu. Nie można zmodyfikować elementów udostępnionych w projekcie platformy; Zamiast tego należy je zmodyfikować w projekcie udostępnionym, do rzeczywistych właścicielem tych elementów. Można uzyskać odpowiedni identyfikator elementu w projekcie udostępnionym z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>, nadanie mu pełną ścieżkę udostępnionego elementu. Następnie można zmodyfikować udostępnionego elementu. Zmiany są propagowane do projektów platformy.  
  
    > [!IMPORTANT]
    >  Należy sprawdzić, czy element projektu jest udostępniony przed zmodyfikowaniem go.  
  
     Następująca metoda zmienia nazwę pliku element projektu.  
  
    ```csharp  
    private void ModifyFileNameInProject(IVsHierarchy project, string path)  
    {    
        int found;  
        uint projectItemID;  
        VSDOCUMENTPRIORITY[] priority = new VSDOCUMENTPRIORITY[1];  
        if (ErrorHandler.Succeeded(((IVsProject)project).IsDocumentInProject(path, out found, priority, out projectItemID))  
            && found != 0)  
        {  
            var name = DateTime.Now.Ticks.ToString() + Path.GetExtension(path);  
            project.SetProperty(projectItemID, (int)__VSHPROPID.VSHPROPID_EditLabel, name);  
            output.OutputStringThreadSafe(string.Format("Renamed {0} to {1}\n", path,name));  
        }  
    }  
    ```  
  
10. Ta metoda jest wywoływana po wszystkich innych kod w `ShowMessageBox` do modyfikowania pliku nazwa elementu w projekcie udostępnionym. Wstaw to po kod, który pobiera pełną ścieżkę elementu w projekcie udostępnionym.  
  
    ```csharp  
    // change the file name of an item in a shared project  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));   
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));  
    this.ModifyFileNameInProject(sharedHier, fullPath);  
    ```  
  
11. Tworzenie i uruchamianie projektu. Tworzenie aplikacji uniwersalnych Centrum C# w eksperymentalnym wystąpieniu, przejdź do **narzędzia** menu i kliknij przycisk **wywołania TestUniversalProject**i Sprawdź tekst w okienku danych wyjściowych ogólne. Nazwa pierwszego elementu w udostępnionego projektu (oczekujemy, że jest on w pliku App.xaml) powinny być zmieniane i powinna zostać wyświetlona który <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> zdarzenie jest wywoływane. W takim przypadku ponieważ zmiana nazwy pliku App.xaml powoduje App.xaml.cs także zmienić nazwę, powinna zostać wyświetlona czterema zdarzeniami (dwa dla każdego projektu platformy). (DTE zdarzenia nie Śledź elementy w projekcie udostępnionym). Powinny pojawić się dwa <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> zdarzenia (po jednej dla każdego z projektów platformy), ale nie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> zdarzenia.  
  
12. Teraz spróbuj zmienić nazwę pliku w projekcie platformy i widać różnica zdarzenia, które uzyskać były uruchamiane. Dodaj następujący kod w `ShowMessageBox` po wywołaniu `ModifyFileName`.  
  
    ```csharp  
    // change the file name of an item in a platform project  
    var unsharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);  
  
    var unsharedItemId = unsharedItemIds[0];  
    string unsharedPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));  
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));  
  
    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);  
    ```  
  
13. Tworzenie i uruchamianie projektu. Utwórz projekt Universal C# w eksperymentalnym wystąpieniu, przejdź do **narzędzia** menu i kliknij przycisk **wywołania TestUniversalProject**i Sprawdź tekst w okienku danych wyjściowych ogólne. Po zmianie nazwy pliku w projekcie platformy powinny być widoczne oba <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> zdarzeń i <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> zdarzeń. Ponieważ zmiana pliku spowodował żadne inne pliki zostanie zmieniony, a od zmiany do elementów w projekcie platformy nie pobrać propagowane dowolnego miejsca, jest tylko jeden każdego z tych zdarzeń.