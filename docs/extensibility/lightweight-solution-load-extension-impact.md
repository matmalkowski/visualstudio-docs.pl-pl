---
redirect_url: /visualstudio/extensibility/what-s-new-in-the-visual-studio-2017-sdk/
ms.openlocfilehash: 5706797ed88dce5b2f481b17d99e9501b960ddca
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
Tytuł: "lekkie ładowania rozwiązania (LSL) | Ms.custom dokumentacja firmy Microsoft":" "ms.date: ms.reviewer"01 17/2017":" "ms.suite:" "ms.technology: 
  - ms.tgt_pltfrm "vs-ide-sdk": "" ms.topic: "artykuł" helpviewer_keywords: 
  - "VSPackages obciążenia lekkie rozwiązanie"
  - "VSPackages, fast ładowania rozwiązania" ms.assetid: 0a71d91e-dc71-4d6b-bbfe-9e4ecd9e5fd1 caps.latest.revision: 1 autora: ms.author "gregvanl": "gregvanl" Menedżer: ghogen
---
# <a name="lightweight-solution-load-lsl"></a>Lekkie rozwiązanie obciążenia (LSL)

## <a name="background-information-on-lsl"></a>Informacje na LSL

Ładowanie lekkie rozwiązanie jest nową funkcją w 2017 VS, które znacznie zmniejsza czas ładowania rozwiązania, dzięki któremu można szybko uzyskać większą wydajność. Po włączeniu LSL programu Visual Studio nie pełni załaduje projekty do momentu rozpoczęciem pracy z nimi.

LSL mogą wpływać na rozszerzeń programu Visual Studio. Rozszerzeń, których funkcje są zależne od projektu do załadowania może nie działać lub nieprawidłowe działanie bez postępując zgodnie ze wskazówkami w tym dokumencie.

Dla dalszego tła na LSL Użyj następujących łączy:

* [Blog obciążenia lekkie rozwiązanie](https://blogs.msdn.microsoft.com/visualstudio/2016/10/11/shorter-solution-load-time-in-visual-studio-15)
* Masz pytania? Skontaktuj się z nami pod adresem[lslsupport@microsoft.com](mailto:lslsupport@microsoft.com)

## <a name="enable-the-setting-to-load-projects-in-deferred-mode"></a>Włącz ustawienie, aby załadować tych projektów w trybie "odroczonego"

1. Zamknij wszystkie aktualnie otwarte rozwiązanie.
2. Przejdź do **narzędzia** > **opcji** > **projekty i rozwiązania** > **ogólne** ustawienia Strona.
3. Sprawdź **ładowania rozwiązania lekkie** pole, aby włączyć ustawienie.

Po otwarciu rozwiązania z włączonymi ustawieniami powyżej IDE przedstawia widok regularne projektów, ale projekty nie zostaną załadowane.

## <a name="differences-between-deferred-load-and-regular-load-of-projects"></a>Różnice między odłożonego ładowania i regularnego obciążenia projektów

Z Lightweight ładowania rozwiązania projekty nie są ładowane podczas otwierania rozwiązania. "Odroczonego projekty te" jest tworzony hierarchii stub. Eksplorator rozwiązań zawiera oczekiwanego widoku ikon i nazwy projektów, nie są interfejsu użytkownika oznaki, że niektóre lub wszystkie projekty znajdują się w "tryb odroczonego".

Przy LSL włączone rozszerzenia może nie oczekiwać, że wymagane projekty pełni już są załadowane po wyzwoleniu operacji. Obiekty wywołujące należy sprawdzić, czy są one zależność od załadowanych projektów. Rozszerzenie wymaga informacji z opóźnieniem projektu, rozszerzenie wykonaj następujące czynności:

1. Załaduj projekty w razie potrzeby.
2. Użyj nowych **API obszaru roboczego** można pobrać informacji z opóźnieniem projektu bez jego ładowania.

Nowy **API obszaru roboczego** Zezwalaj na rozszerzenia uzyskać informacje, takie jak posiadający je projekt w pliku źródłowym i wszystkich plików źródłowych dla określonego projektu z opóźnieniem projektu. W niektórych przypadkach tylko ograniczony zestaw projektów musi być załadowany. Odpowiedniej opcji jest kompromis między częstotliwość operacji, łatwość alternatywnych metod i środowisko pracy użytkownika.

Wszystkie projektu i rozwiązania obciążenia związane z zdarzenia są nadal uruchamiany w trybie LSL. Dzięki temu składniki można odczytać oczekiwane zachowanie VS i działają w taki sam sposób jak podczas projekty zostały załadowane. Pracy podczas Otwórz rozwiązanie znacząco zmniejsza się jednak związanych z ładowania projektu.

## <a name="ui-requirements-and-changes"></a>Wymagania interfejsu użytkownika i zmiany

Wszystkie interfejsu użytkownika należy traktować projektów załadowany i odroczonego jako równe. Oznacza to, że wszelkie działania, które można wykonywać w załadowanym projekcie muszą mieć zastosowanie do odroczonego projektów z kilkoma wyjątkami. Aby pomóc w tym celu funkcji, uległy zmianie niektóre platformy istniejących interfejsów API, a także wprowadzeniem nowych interfejsów API.

### <a name="expectations-for-ui"></a>Oczekiwania dotyczące interfejsu użytkownika

1. Pokaż funkcje musi nie visual różnice w zależności od jeśli projekty nie są ładowane lub odroczone.
2. Wszystkie listy lub wyliczenia za pośrednictwem rozwiązania załadowanych projektów muszą zawierać odroczonego projektów.
3. Żadnych działań, które są dostępne dla projektu i załadować powinny być dostępne dla projektu i opóźnieniem.
4. Funkcje musi żądanie załadowania projekt(-y) tylko wtedy, gdy:
  * Ma bezpośredniej interakcji użytkownika przy użyciu funkcji. Nie ładuj preemptively projektów.
  * Gest "Zobacz więcej wyników" zostało utworzone przez użytkownika. Poniżej znajduje się ta wytyczna interfejsu użytkownika.
  * Całkowitym załadowaniem projektu może służyć do zapewnienia działania. Użyj LSL i otwartych API projektu, jeśli to możliwe, a wysłanie żądania funkcji zapyta, gdy funkcja jest Brak.

### <a name="changes-in-platform-apis-to-help-drive-ui"></a>Zmiany platformy interfejsów API mają wykształcić interfejsu użytkownika

1. Nowe interfejsy API są przekazywane do poproś rozwiązanie, jeśli został on otwarty w trybie Lightweight ładowania rozwiązania i są w stanie odroczonego, ile projektów.
2. Nowe zdarzenie jest dostępna dla wszystkich projektów odroczonego ładowane w rozwiązaniu.
3. Nowe interfejsy API są przekazywane do poproś projektu, jeśli została odroczona.
4. Istniejących interfejsów API zostały zaktualizowane do dołączenia odroczonych projektów podczas pytania o załadowanych projektów.
5. Istniejących interfejsów API są aktualizowane w celu express rozwiązanie zostanie całkowicie załadowany po otwarciu rozwiązania.

### <a name="how-to-add-see-more-results-for-a-feature"></a>Jak dodać "Zobacz więcej wyników" dla funkcji.

Funkcje, które wykonywać zapytania na zawartość projektów należy rozważyć wpływ odroczonego projektów. W niektórych sytuacjach funkcji można uzyskać wyników kwerendy ich z LSL i interfejsów API obszaru roboczego odroczonego projektu. W pozostałych przypadkach funkcja ograniczenia wymagają projekty do załadowania. Zarówno z tych sytuacji powinien zawierać nowy gestu "Zobacz więcej wyników", który umożliwia użytkownikom można całkowicie załadować projektów i Prześlij ponownie zapytanie. Ten gest włącza funkcje zwracanie najlepsze zbliżenia istnieją odroczone projektów podczas przekazywania użytkownika sposób uzyskać doskonałe wyników, gdy projekty są faktycznie załadowana.

Ogólne algorytm funkcji powinny być:

### <a name="when-the-query-is-performed-over-a-single-project"></a>Jeśli zapytanie odbywa się za pośrednictwem jednego projektu

```csharp
// IsInDeferredState() and EnsureProjectIsLoadedHelper() in this sample can be found in the "Helpful code snippets" section of this document
public void Query(IVsHierarchy projectToQuery)
{
    // 1. Perform calculation/query
    DoQuery(projectToQuery);

    // 2. Present results to the user
    ShowResults();

    // 3. If the project was deferred, then present a "See More Results" UI element
    if (IsInDeferredState(projectToQuery))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Ask ask for the project to be loaded
    IVsHierarchy projectFromLastQuery = GetProjectFromLastQuery();
    IVsHierarchy loadedProject = EnsureProjectIsLoadedHelper(projectFromLastQuery);

    if (loadedProject != null)
    {
        // 2. Re-run the query on the loaded projects
        Query(loadedProject);
    }
    else
    {
        ShowErrorMessage();
    }
}
```

### <a name="when-the-query-is-performed-over-the-whole-solution"></a>Jeśli zapytanie odbywa się za pośrednictwem całego rozwiązania

```csharp
// Requires Microsoft.VisualStudio.Shell.Interop.15.0.DesignTime.dll
public void Query()
{
    // 1. Perform calculation/query
    DoQuery();

    // 2. Present results to the user
    ShowResults();

    // 3. If there were deferred projects, then present a "See More Results from all projects" UI element
    var solution = // the solution
    object deferredCount = 0;
    int hr = ((IVsSolution)solution).GetProperty((int)__VSPROPID7.VSPROPID_DeferredProjectCount, out deferredCount);
    if (ErrorHandler.Succeeded(hr) && ((int)deferredCount > 0))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Force the solution to load, as requested by the user. This brings up a UI with a "Cancel" button (unless supppresed with __VSBSLFLAGS.VSBSLFLAGS_NotCancelable)
    var solution = // get IVsSolution4
    int hr = ((IVsSolution4)solution).EnsureSolutionIsLoaded((uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    if (ErrorHandler.Succeeded(hr))
    {
        // 2. Re-run the query
        Query();
    }
    else
    {
        ShowErrorMessage();
    }
}
```

## <a name="api-changes"></a>Zmiany interfejsu API

### <a name="new-api"></a>Nowy interfejs API

IVsSolution7.IsSolutionLoadDeferred (out odroczone wartość logiczna)

Zwraca wartość PRAWDA, jeśli bieżące rozwiązanie został załadowany w trybie opóźnieniem. Należy pamiętać, że jeśli rozwiązanie początkowo została załadowana w trybie odroczonego, nawet jeśli wszystkie projekty z opóźnieniem są ostatecznie załadowany w bieżącej sesji (wymuszone przez operacje lub gestów jawne użytkownika z powodu), ta właściwość nadal zwróci wartość true.

__VSPROPID7. VSPROPID_DeferredProjectCount

Zwraca liczbę projektów aktualnie w trybie opóźnieniem. Ta właściwość będzie mieć wartość z zakresu [0, VSPROPID_ProjectCount].

__VSHPROPID9. VSHPROPID_IsDeferred

Zwraca wartość PRAWDA, jeśli hierarchia projektu jest w stanie odłożonego ładowania.

__VSENUMPROJFLAGS3 z wartościami EPF_DEFERRED i EPF_NOTDEFERRED

Te flagi mogą zostać przekazane do [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx) do wykonywania iteracji odroczonego i nieodroczone projektów.

### <a name="new-events"></a>Nowe zdarzenia

IVsSolutionEvents7.OnAfterLoadAllDeferredProjects()

To zdarzenie jest wywoływane po wszystkich projektów odroczonego zostały załadowane. W tym momencie VSPROPID_DeferredProjectCount jest równa 0. Należy pamiętać, że to zdarzenie nie jest uruchamiany jako część ładowania rozwiązania i może nie być wywoływane w ogóle w sesji. Tylko uruchamiane, jeśli wszystkie projekty z opóźnieniem są ładowane.

### <a name="changes-to-existing-api"></a>Zmiany w istniejących interfejsu API

* Przekazywanie [__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx). EPF_LOADEDINSOLUTION do [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx) zwraca odroczone projektów.
* Przekazywanie [__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx). EPF_UNLOADEDINSOLUTION nie zwraca odroczonego projektów.
* [KnownUIContexts.SolutionExistsAndFullyLoadedContext](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.knownuicontexts.solutionexistsandfullyloadedcontext.aspx) ma ustawioną wartość true na Otwórz rozwiązanie. Odroczone projekty są traktowane jak załadować, dla tego kontekstu jest znacznie ustawić wcześniejsza niż w trybie z systemem innym niż LSL.
* [__VSPROPID](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vspropid.aspx). VSPROPID_ProjectCount zwraca sumę załadowany i odroczonego projektów.

## <a name="helpful-code-snippets"></a>Wstawki kodu przydatne

### <a name="check-if-a-solution-was-opened-in-deferred-load-mode"></a>Sprawdź, czy rozwiązanie zostało otwarte w trybie odłożonego ładowania

```csharp
/// <summary>
/// Checks if the solution was opened in LSL mode.
/// </summary>
/// <returns>True if the solution was opened in LSL mode, false otherwise.</returns> public static bool IsSolutionLoadDeferred()
{
    IVsSolution7 vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution7;
    Assumes.Present(vsSolution);

    return vsSolution.IsSolutionLoadDeferred();
}
```

### <a name="check-if-a-project-is-deferred"></a>Sprawdź, czy projekt jest opóźnione

```csharp
/// <summary>
/// Checks to see if a project is deferred.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <returns>True if the project is deferred. False if it is any other state, such as loaded, unloaded, or virtual.</returns>
/// <remarks>Requires Microsoft.VisualStudio.Shell.Interop.15.0.DesignTime.dll</remarks>
public static bool IsInDeferredState(IVsHierarchy vsHierarchy)
{
    object deferred;
    int hr = vsHierarchy.GetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID9.VSHPROPID_IsDeferred, out deferred);

    if (ErrorHandler.Succeeded(hr))
    {
        return (bool)deferred;
    }

    return false;
}
```

### <a name="load-a-project"></a>Załaduj projekt

```csharp
/// <summary>
/// Ensures a project is fully loaded.
/// </summary> /// <param name="projectToLoad">A deferred or loaded project to ensure is loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IVsHierarchy EnsureProjectIsLoadedHelper(IVsHierarchy projectToLoad)
{
    int hr = VSConstants.S_OK;
    var solution = // get the solution

    // 1. Ask the solution to load the required project. To reduce wait time,
    //    we load only the project we need, not the entire solution.
    hr = projectToLoad.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid);
    hr = ErrorHandler.ThrowOnFailure(hr);
    hr = ((IVsSolution4)solution).EnsureProjectIsLoaded(projectGuid, (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 2. After the project is loaded, grab the latest IVsHierarchy object.
    IVsHierarchy loadedProject = null;
    hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
    hr = ErrorHandler.ThrowOnFailure(hr);

    return loadedProject;
}
```

### <a name="load-a-set-of-projects"></a>Załaduj zestaw projektów

```csharp
/// <summary>
/// Ensures a collection of IVsHierarchys are loaded. To be used when deferred projects absolutely cannot be used.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IReadOnlyCollection<IVsHierarchy> EnsureProjectsAreLoadedHelper(IReadOnlyCollection<IVsHierarchy> projectsToLoad)
{
    if (projectsToLoad == null || projectsToLoad.Count == 0)
        return projectsToLoad;

    int hr = VSConstants.S_OK;
    List<Guid> projectGuids = new List<Guid>(projectsToLoad.Count);
    List<IVsHierarchy> loadedProjects = new List<IVsHierarchy>(projectsToLoad.Count);
    var solution = // get the solution

    // 1. Collect projects to force load
    foreach (var project in projectsToLoad)
    {
        Guid projectGuid;
        hr = project.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid)
        hr = ErrorHandler.ThrowOnFailure(hr);
        projectGuids.Add(projectGuid);
    }

    // 2. Ask the solution to load the required projects. To reduce wait time,
    //    we load only the projects we need, not the entire solution.
    hr = ((IVsSolution4)solution).EnsureProjectsAreLoaded(projectCount, projectGuids.ToArray(), (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 3. After the projects are loaded, grab the latest IVsHierarchy objects
    foreach (var projectGuid in projectGuids)
    {
        IVsHierarchy loadedProject = null;
        hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
        hr = ErrorHandler.ThrowOnFailure(hr);
        loadedProjects.Add(loadedProject);
    }

    return loadedProjects;
}
```

### <a name="checks-if-the-solution-has-deferred-projects"></a>Sprawdza, czy rozwiązanie wstrzymał projektów

```csharp
/// <summary>
/// Checks if the solution has deferred projects
/// </summary>
/// <returns>True if the solution has deferred projects, false otherwise.</returns>
public static bool SolutionHasDeferredProjects()
{
    IVsSolution vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution;
    Assumes.Present(vsSolution);
    object varHasDeferredProjects;
    if (ErrorHandler.Succeeded(vsSolution.GetProperty(
        (int)__VSPROPID7.VSPROPID_DeferredProjectCount, out varHasDeferredProjects)))
    {
        return (int)varHasDeferredProjects != 0;
    }

    return false;
}
```

## <a name="getting-detailed-information-with-workspace-apis"></a>Pobieranie szczegółowych informacji z interfejsami API zestawu roboczego

### <a name="how-to-get-detailed-info-on-a-lsl-solution"></a>Jak uzyskać szczegółowe informacje dotyczące rozwiązania LSL

Nowe interfejsy API obszaru roboczego są dostępne za pośrednictwem IVsSolutionWorkspaceService, aby pobrać szczegółowe informacje o rozwiązaniach.

Te interfejsy API można pobrać bieżący obszar roboczy, aktywne rozwiązanie, informacje o zarządzanych wiersza polecenia, a także usługę indeksu dla obszaru roboczego. Te interfejsy API dalej korzystać z usługi indeksu można pobrać szczegółowych danych, na przykład wszystkich plików źródłowych w projekcie, posiadający je projekt plik źródłowy, wszystkie projekty zawarte w bieżącym rozwiązaniu wszystkich P2P odwołań w projekcie, itp.

Poniższe fragmenty kodu przedstawiają użycia interfejsów API obszaru roboczego.

### <a name="get-ivssolutionworkspaceservice-initially"></a>Pobierz IVsSolutionWorkspaceService początkowo

>**Uwaga:** tylko Uzyskaj IVsSolutionWorkspaceService w scenariuszach LSL, aby uniknąć ładowania pakietu API obszaru roboczego.

```csharp
private readonly Lazy<IVsSolutionWorkspaceService> _solutionWorkspaceService;

[ImportingConstructor]
public DeferredProjectWorkspaceService(SVsServiceProvider serviceProvider)
{
    _solutionWorkspaceService = new Lazy<IVsSolutionWorkspaceService>(
        () => (IVsSolutionWorkspaceService)serviceProvider.GetService(typeof(SVsSolutionWorkspaceService)));
}
```

>**Uwaga:** poniższe fragmenty kodu założono _solutionWorkspaceService już opóźnieniem został zainicjowany.

### <a name="get-managed-command-line-info-for-deferred-projects-for-active-solution-configuration"></a>Pobierz informacje zarządzane wiersza polecenia dla projektów odroczonego dla aktywnej konfiguracji rozwiązania

```csharp
/// <summary>
/// Get the managed command line info for active solution configuration
/// </summary>
/// <param name="cancellationToken"> the cancellation token</param>
/// <returns></returns>
public async Task<IReadOnlyDictionary<string, ManagedCommandLineInfo>> GetManagedCommandLineInfoForConfigurationAsyn(CancellationToken cancellationToken)
{
    var dte = ServiceProvider.GetGlobalService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
    var solutionConfig = (EnvDTE80.SolutionConfiguration2)dte.Solution.SolutionBuild.ActiveConfiguration;

    // Solution configuration is something like "Debug|Any CPU"
    return await _solutionWorkspaceService.Value.GetManagedCommandLineInfoAsync(
        $"{solutionConfig.Name}|{solutionConfig.PlatformName}", cancellationToken).ConfigureAwait(false);
}
```

### <a name="get-the-active-solution-file-in-lsl"></a>Pobierz plik active rozwiązania w LSL

```csharp
/// <summary>
/// Get the active solution file.
/// </summary>
/// <returns>The solution file.</returns>
public string GetActiveSolutionFile()
{
    return _solutionWorkspaceService.Value.SolutionFile;
}
```

### <a name="get-the-owning-project-of-a-source-file"></a>Pobierz projekcie będącym jego właścicielem pliku źródłowego

```csharp
/// <summary>
/// Get the owning projects of a source file.
/// </summary>
/// <param name="filePath">the source file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetOwningProjectAsync(string filePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var result = await indexService.GetFileDependantsAsync(filePath, null, String.Empty, (int)FileReferenceInfoType.Source);
    return result.Select(f => f.Path);
}
```

### <a name="get-all-source-files-from-a-project"></a>Pobierz wszystkie pliki źródłowe z projektem

```csharp
/// <summary>
/// Get all source files from a project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, referenceTypes: (int)FileReferenceInfoType.Source);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-the-p2p-references-in-a-project"></a>Pobierz P2P odwołań w projekcie

```csharp
/// <summary>
/// Get outputs of project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.Output);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-all-the-projects-in-a-solution"></a>Pobierz wszystkie projekty w rozwiązaniu

```csharp
/// <summary>
/// Get the projects in a solution.
/// </summary>
/// <param name="solutionFilePath">the solution file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetProjectsInSolutionAsync(string solutionFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();

    // Passing the configuration|Platform that projects apply to; passing null will return projects with all configurations.
    var result = await indexService.GetFileReferencesAsync(solutionFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.ProjectReference);
    return result.Select(f => f.Path);
}
```

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Ze względu na specyfikę LSL jest zamierzone, że użytkownicy nie widzą różnicy między projektami załadowane i odroczone. To może utrudnić funkcji projektowania i testowania.

Podpowiedzi graficznych w Interfejsie użytkownika dla projektów odroczonego można włączyć w następujący sposób:

1. Zamknij program Visual Studio
2. Regedit.exe
3. Wybierz HKLM
4. Plik > załadować gałęzi
5. `%localappdata%\microsoft\visualstudio\15.0_<instance ID>\privateregistry.bin`
6. Wprowadź "VisualStudio" jako nazwy klucza
7. Ustaw `HKLM\VisualStudio\Software\Microsoft\VisualStudio\15.0_<instanceID>\FeatureFlags\Solution\Loading\Deferred\Hint\Value=1` (DWORD)
8. Wybierz HKLM\VisualStudio
9. Plik > zwolnienia gałęzi
10. Uruchom program Visual Studio

Wszelkie dodatkowe pytania należy dotrzeć do [ lslsupport@microsoft.com ](mailto:lslsupport@microsoft.com).






