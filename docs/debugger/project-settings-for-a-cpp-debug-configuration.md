---
title: Ustawienia konfiguracji debugowania C++ projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VC.Project.VCDebugSettings.WebBrowser.DebuggerType
- VC.Project.IVCGPUDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.SymbolPath
- VC.Project.IVCClusterDebugPageObject.ApplicationCommand
- VC.Project.IVCRemoteDebugPageObject.WorkingDirectory
- VC.Project.VCDebugSettings.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.SQLDebugging
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCGPUDebugPageObject.CommandArguments
- VC.Project.VCDebugSettings.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunWorkingDirectory
- VC.Project.IVCLocalDebugPageObject.SQLDebugging
- VC.Project.IVCWebSvcDebugPageObject.HttpUrl
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunCommand
- VC.Project.IVCGPUDebugPageObject.WorkingDirectory
- VC.Project.IVCWebSvcDebugPageObject.DebuggerType
- VC.Project.IVCRemoteDebugPageObject.CommandArguments
- VC.Project.IVCRemoteDebugPageObject.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCRemoteDebugPageObject.RemoteMachine
- VC.Project.IVCClusterDebugPageObject.MPIRunArguments
- VC.Project.IVCClusterDebugPageObject.MPIAcceptFilter
- VC.Project.IVCGPUDebugPageObject.RemoteConnection
- VC.Project.VCDebugSettings.PDBPath
- VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory
- VC.Project.VCDebugSettings.SQLDebugging
- VC.Project.VCDebugSettings.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ShimCommand
- VC.Project.IVCLocalDebugPageObject.Command
- VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCLocalDebugPageObject.Attach
- VC.Project.VCDebugSettings.Command
- VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ApplicationArguments
- VC.Project.IVCLocalDebugPageObject.Environment
- VC.Project.IVCGPUDebugPageObject.DeploymentDirectory
- VC.Project.IVCLocalDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.Environment
- VC.Project.IVCGPUDebugPageObject.BreakpointBehavior
- VC.Project.IVCLocalDebugPageObject.DebuggerType
- VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl
- VC.Project.IVCWebSvcDebugPageObject.SQLDebugging
- VC.Project.IVCGPUDebugPageObject.AcceleratorType
- VC.Project.IVCGPUDebugPageObject.Environment
- VC.Project.VCDebugSettings.RemoteMachine
- VC.Project.IVCGPUDebugPageObject.AdditionalFilesToDeploy
- VC.Project.VCDebugSettings.WorkingDirectory
- vs.debug.builds
- VC.Project.VCDebugSettings.Attach
- VC.Project.VCDebugSettings.HttpUrl
- VC.Project.IVCClusterDebugPageObject.MPIAcceptMode
- VC.Project.IVCGPUDebugPageObject.Attach
- VC.Project.IVCRemoteDebugPageObject.AdditionalFiles
- VC.Project.IVCGPUDebugPageObject.Command
- VC.Project.VCDebugSettings.Remote
- VC.Project.IVCRemoteDebugPageObject.Attach
- VC.Project.VCDebugSettings.EnvironmentMerge
- VC.Project.IVCGPUDebugPageObject.MachineName
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DEBUG linker option
- -PDB linker option
- -Zl compiler option [C++]
- /DEBUG linker option
- /PDBSTRIPPED linker option
- /MAPINFO linker option
- -Zd compiler option [C++]
- -DEBUG linker option
- MAPINFO linker option
- /ZI compiler option [C++]
- ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debugger settings
- project settings [Visual Studio], debug configurations
- mapfiles, project settings
- debug configurations, C++
- project settings [Visual Studio]
- /PDB linker option
- -PDBSTRIPPED linker option
- debug builds, project settings
- PDB linker option
- projects [Visual Studio], debug configurations
- project configurations, debug
- Zd compiler option [C++]
- MAP linker option
- /Z7 compiler option [C++]
- .pdb files, debug build project settings
- -MAP linker option
- -MAPINFO linker option
- /Zd compiler option [C++]
- PDBSTRIPPED linker option
- -Z7 compiler option [C++]
- pdb files, debug build project settings
- /MAP linker option
ms.assetid: 860c7f13-a108-4fe5-8fca-d235cd3ca1cb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 6b323ab51f4be02faaddc1df7ab2dd6902323d63
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Ustawienia projektu dla konfiguracji debugowania języka C++
Możesz zmienić ustawienia projektu dla konfiguracji debugowania języka C lub Visual C++ w **strony właściwości** okno dialogowe, zgodnie z opisem w [porady: Ustaw debugowania i wydania konfiguracje](../debugger/how-to-set-debug-and-release-configurations.md). W poniższych tabelach przedstawiono gdzie można znaleźć ustawień debugera w **strony właściwości** okno dialogowe.  
  
> [!WARNING]
>  Ustawienia projektu debugowania w **konfiguracji właściwości/debugowanie** kategorii dla aplikacji platformy uniwersalnej systemu Windows i składników, które zostały napisane w języku C++ są różne. Zobacz [rozpocząć sesję debugowania: (VB, C#, C++ i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).  
  
 Określ, które debugera do użycia w **debugera, aby uruchomić** pola listy. Wybór wpłynie na właściwości, które są widoczne.  
  
 Ustawienie właściwości każdego debugowania jest automatycznie zapisane i zapisywane w pliku "użytkownika" (. vcxproj.user) dla rozwiązań przy każdym Zapisz swoje rozwiązanie.  
  
## <a name="configuration-properties-folder-debugging-category"></a>Folder właściwości konfiguracji (kategorii debugowanie)  
  
|**Ustawienie**|**Opis**|  
|-----------------|---------------------|  
|**Debuger można uruchomić**|Określa debuger do uruchomienia z następującymi opcjami:<br /><br /> -   **Debuger lokalnego systemu Windows**<br />-   **Debugera zdalnego systemu Windows**<br />-   **Debugera przeglądarki sieci Web**<br />-   **Debugera usługi sieci Web**|  
|**Polecenie** (debugera lokalnego systemu Windows)|Określa polecenie do uruchomienia debugowania programu na komputerze lokalnym.|  
|**Polecenia zdalnego** (debugera zdalnego systemu Windows)|Ścieżka .exe na komputerze zdalnym. Wprowadź ścieżkę, tak samo, jak należy wprowadzić go na komputerze zdalnym.|  
|**Argumenty polecenia** (debugera lokalnego systemu Windows i debugera zdalnego systemu Windows)|— Określa argumenty dla polecenia określony wcześniej.<br /><br /> W tym polu można używać następujących operatorów przekierowania:<br /><br /> < `file`<br /> Odczytuje stdin z pliku.<br /><br /> > `file`<br /> Zapisuje stdout do pliku.<br /><br /> >> `file`<br /> Dołącza stdout do pliku.<br /><br /> 2> `file`<br /> Zapisuje stderr do pliku.<br /><br /> 2>> `file`<br /> Dołącza stderr do pliku.<br /><br /> 2> &1<br /> Wysyła dane wyjściowe stderr (2) do tej samej lokalizacji co stdout (1).<br /><br /> 1> &2<br /> Wysyła stdout (1) dane wyjściowe do tej samej lokalizacji co stderr (2).<br /><br /> W większości przypadków tych operatorów mają zastosowanie tylko do aplikacji konsoli.|  
|**Katalog roboczy**|Określa katalog roboczy programu debugowany względem katalogu projektu, w którym znajduje się danego pliku EXE. Jeśli to pole pozostanie puste, katalog roboczy jest katalogu projektu. Zdalne debugowanie będzie katalogu projektu na serwerze zdalnym.|  
|**Dołącz** (debugera lokalnego systemu Windows i debugera zdalnego systemu Windows)|Określa, czy do uruchamiania lub Dołącz do aplikacji. Domyślne ustawienie to nie.|  
|**Nazwa serwera zdalnego** (debugera zdalnego systemu Windows)|Określa nazwę komputera (innego niż Twój), na którym chcesz debugować aplikację.<br /><br /> Makra kompilacji RemoteMachine ma ustawioną wartość tej właściwości; Aby uzyskać więcej informacji, zobacz [makra dla poleceń kompilacji oraz właściwości](/cpp/ide/common-macros-for-build-commands-and-properties).|  
|**Połączenie** (debugera zdalnego systemu Windows)|Pozwala przełączać się między typami standardowe i bez uwierzytelniania połączenia zdalnego debugowania. Określ nazwę komputera zdalnego w **nazwa serwera zdalnego** pole. Typy połączeń obejmują:<br /><br /> -   **Zdalny z uwierzytelnianiem systemu Windows**<br />-   **Zdalny bez uwierzytelniania**<br /><br /> **Uwaga** debugowania zdalnego z uwierzytelnianiem nie może opuścić narażony na naruszenia zabezpieczeń komputera zdalnego. Tryb uwierzytelniania systemu Windows jest bardziej bezpieczne.<br /><br /> Aby uzyskać więcej informacji, zobacz [instalacji zdalnego debugowania](../debugger/remote-debugging.md).|  
|**Adres URL HTTP** (sieci Web debugera usługi i debugera przeglądarki sieci Web)|Określa adres URL, w którym znajduje się projekt, który debugowania.|  
|**Typ debugera**|Określa typ debugera do użycia: **tylko kod natywny**, **zarządzane tylko**, **GPU tylko**, **Mixed**, **automatycznie**(ustawienie domyślne) lub **skryptu**.<br /><br /> -   **Tylko kod natywny** jest dla niezarządzanego kodu C++.<br />-   **Zarządzane tylko** dla kodu uruchamianego w obszarze środowisko uruchomieniowe języka wspólnego (zarządzany kod).<br />-   **Mieszane** wywołuje debugery dla zarządzanych i niezarządzanych kodu.<br />-   **Automatycznie** Określa typ debugera na podstawie kompilatora i EXE informacji.<br />-   **Skrypt** wywołuje debugera skryptów.<br />-   **Procesor GPU tylko** dla kodu C++ AMP, który jest uruchamiany na urządzeniu procesora GPU lub rasteryzator odwołanie DirectX. Zobacz [debugowanie kodu GPU](../debugger/debugging-gpu-code.md).|  
|**Środowisko** (debugera lokalnego systemu Windows i debugera zdalnego systemu Windows)|Określa zmienne środowiskowe dla programu debugowania. Należy użyć składni zmiennej standardowe środowisko (na przykład `PATH="%SystemRoot%\..."`). Te zmienne zastąpić środowiska systemu lub są łączone ze środowiskiem systemu, w zależności od **Scal środowisko** ustawienie. Po kliknięciu w kolumnie ustawienia "Edytuj" pojawia się. Kliknij łącze do edycji zmiennych środowiskowych.|  
|**Scal środowisko** (debugera lokalnego systemu Windows)|Określa, czy zmienne, które są określone w **środowiska** pole zostaną scalone ze środowiskiem, który jest zdefiniowany przez system operacyjny. Ustawienie domyślne to tak.|  
|**Debugowanie SQL** (wszystkie z wyjątkiem debuger klastra MPI)|Włącza debugowanie SQL procedur z Twojej [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] aplikacji. Domyślne ustawienie to nie.|  
|**Typ akceleratora debugowania** (debugowania GPU tylko)|Określa urządzenie procesora GPU do użycia na potrzeby debugowania. Instalowanie sterowników urządzeń dla urządzeń zgodnych GPU zostaną dodane dodatkowe opcje. Ustawieniem domyślnym jest "GPU - emulatora oprogramowania."|  
|**Domyślne zachowanie punktu przerwania procesora GPU** (debugowania GPU tylko)|Określa, czy dla każdego wątku w SIMD warp powinien być wywoływany zdarzeń punktu przerwania. Ustawieniem domyślnym jest, aby zgłosić zdarzenie punktu przerwania tylko raz na przełamanie.|  
|**Amp domyślnego akceleratora**|Określa domyślny akceleratora AMP podczas debugowania kodu GPU. Wybierz **akceleratora oprogramowania WARP** Zbadaj, czy przyczyną problemu jest sprzętem lub sterownikiem zamiast kodu.|  
|**Katalog wdrożenia** (debugera zdalnego systemu Windows)|Określa ścieżkę na komputerze zdalnym, której dane wyjściowe projektu zostaną skopiowane przed można uruchomić. Może to być udział sieciowy na komputerze zdalnym lub może być ścieżką do folderu na komputerze zdalnym. Ustawieniem domyślnym jest pusty, co oznacza, że dane wyjściowe projektu nie jest kopiowany do udziału sieciowego. Aby włączyć wdrożenie plików, należy również wybrać **Wdróż** pole wyboru w oknie dialogowym programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [porady: tworzenie i edycja konfiguracji](../ide/how-to-create-and-edit-configurations.md).|  
|**Dodatkowe pliki do wdrożenia** (debugera zdalnego systemu Windows)|Właściwość katalog wdrożenia jest ustawiona, to rozdzielaną średnikami listę dodatkowych plików do skopiowania do katalogu wdrożenia. Ustawieniem domyślnym jest pusty, co oznacza, że żadne dodatkowe pliki są kopiowane do katalogu wdrażania. Aby włączyć wdrożenie plików, należy również wybrać **Wdróż** pole wyboru w oknie dialogowym programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [porady: tworzenie i edycja konfiguracji](../ide/how-to-create-and-edit-configurations.md).|  
|**Wdróż biblioteki wykonawcze debugowania Visual C++** (debugera zdalnego systemu Windows)|Jeśli ustawiono właściwość katalogu wdrażania, określa ona, czy biblioteki wykonawcze debugowania Visual C++ dla bieżącej platformy powinny zostać skopiowane do udziału sieciowego. Ustawieniem domyślnym jest tak.|  
  
## <a name="cc-folder-general-category"></a>Folder C/C++ (Kategoria Ogólne)  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Format informacji debugowania** ([/z7, / zi /Zd, Zi,](/cpp/build/reference/z7-zi-zi-debug-information-format))|Określa typ informacji debugowania dla projektu.<br /><br /> Opcja domyślna (/ZI) tworzy bazę danych programu (PDB) w formacie zgodnym Edytuj i Kontynuuj. Aby uzyskać więcej informacji, zobacz [/Zd/z7, / zi, /ZI (Format informacji debugowania)](/cpp/build/reference/z7-zi-zi-debug-information-format).|  
  
## <a name="cc-folder-optimization-category"></a>Folder C/C++ (Optymalizacja kategorii)  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Optymalizacja**|Określa, czy kompilator powinien optymalizować kod, który generuje. Optymalizacja zmienia kod, który jest wykonywany. Kod zoptymalizowany nie zgadza się z kodu źródłowego. W związku z tym debugowanie jest trudne.<br /><br /> Opcja domyślna (**wyłączone (/ 0d**) powoduje pominięcie optymalizacji. Można opracowywania optymalizacji pomijane, a następnie włącz go podczas tworzenia wersji produkcyjnej kodu.|  
  
## <a name="linker-folder-debugging-category"></a>Folder konsolidatora (kategorii debugowanie)  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Generowanie informacji o debugowaniu** ([/DEBUG](/cpp/build/reference/debug-generate-debug-info))|Informuje konsolidator, aby uwzględnić informacje o debugowaniu, który ma format określonych przez/z7, /Zd, Zi lub/zi.|  
|**Generuj plik bazy danych programu** ([/PDB:name](/cpp/build/reference/pdb-use-program-database))|Określ nazwę pliku PDB w tym polu. Należy wybrać ZI lub/zi format informacji debugowania.|  
|**Usuń symbole prywatne** ([/PDBSTRIPPED:filename](/cpp/build/reference/pdbstripped-strip-private-symbols))|Określ nazwę pliku PDB w tym polu, jeśli nie chcesz dołączać prywatne symbole w pliku PDB. Opcja ta tworzy drugi plik bazy danych (PDB) programu podczas tworzenia Twojej obraz programu przy użyciu opcji kompilatora lub konsolidatora opcje, które generują plik PDB, takich jak/Debug, / z7, /Zd. Lub/zi. Ten drugi plik PDB pomija symbole, których nie należy wysłać do klientów. Aby uzyskać więcej informacji, zobacz [/pdbstripped (Usuń symbole prywatne)](/cpp/build/reference/pdbstripped-strip-private-symbols).|  
|**Generuj plik mapy** ([/MAP](/cpp/build/reference/map-generate-mapfile))|Informuje konsolidator, aby wygenerować plik mapy podczas konsolidacji. Domyślne ustawienie to nie. Aby uzyskać więcej informacji, zobacz [/map (Generowanie Mapfile)](/cpp/build/reference/map-generate-mapfile).|  
|**Nazwa pliku mapy** ([/MAP:](/cpp/build/reference/map-generate-mapfile)*nazwa*)|Jeśli wybierzesz Generowanie pliku mapy, w tym polu można określić pliku mapy. Aby uzyskać więcej informacji, zobacz [/map (Generowanie Mapfile)](/cpp/build/reference/map-generate-mapfile).|  
|**Eksporty mapy** ([/MAPINFO:EXPORTS](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Obejmuje funkcje wyeksportowane w pliku mapy. Domyślne ustawienie to nie. Aby uzyskać więcej informacji, zobacz [/MapInfo (obejmują informacje do Mapfile)](/cpp/build/reference/mapinfo-include-information-in-mapfile).|  
|**Zestaw debugowalny** ([/ASSEMBLYDEBUG](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Określa ustawienia dla konsolidator /ASSEMBLYDEBUG opcji. Dopuszczalne są następujące wartości:<br /><br /> -   **Nie emitowania debugowalnych atrybutów**.<br />-   **Środowisko uruchomieniowe śledzenia i wyłączone optymalizacje (/ ASSEMBLYDEBUG)**. Jest to ustawienie domyślne<br />-   **Nie optimizations(/ASSEMBLYDEBUG:DISABLE) śledzenia i Włącz środowiska uruchomieniowego**.<br />-   **\<Dziedzicz nadrzędnym lub domyślnych wartościach projektu >**.<br />— Aby uzyskać więcej informacji, zobacz [/ASSEMBLYDEBUG (Dodaj DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute).|  
  
 Te ustawienia w folderze właściwości konfiguracji (kategoria debugowania) można zmienić programowo przy użyciu interfejsu Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.

## <a name="other-project-settings"></a>Inne ustawienia projektu

Aby debugować typów projektów, takich jak biblioteki statyczne i bibliotek DLL, projektu programu Visual Studio musi mieć możliwość znalezienia odpowiednich plików. Jeśli kod źródłowy jest dostępny, można dodać biblioteki statyczne i bibliotek DLL osobne projekty do tego samego rozwiązania (dzięki temu łatwe debugowanie). Aby uzyskać informacje o tworzeniu tych typów projektów, zobacz [tworzenie i używanie dynamiczne łącze Biblioteka (DLL)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) i [tworzenie, używanie biblioteki statycznej](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp). Z kodem źródłowym jest dostępny, można utworzyć nowy projekt programu Visual Studio, wybierając **Plik > Nowy > Projekt z istniejącego kodu**.

Debugowanie bibliotek DLL, które są zewnętrzne względem projektu, zobacz [projekty DLL debugowania](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal). Jeśli musisz debugować własnego projektu biblioteki DLL, ale nie ma dostępu do projektu aplikacji wywołującej, zobacz [debugowanie z projektu DLL](../debugger/how-to-debug-from-a-dll-project.md).
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)   
 [Ustawienia debugowania i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Tworzenie i zarządzanie projektami Visual C++](/cpp/ide/creating-and-managing-visual-cpp-projects)   
 [/ ASSEMBLYDEBUG (Dodaj DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute)   
 [Typowe makra dla właściwości i poleceń kompilacji](/cpp/ide/common-macros-for-build-commands-and-properties)