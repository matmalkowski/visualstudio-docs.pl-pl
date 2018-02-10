---
title: "Wspólne właściwości projektów MSBuild | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2018
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- msbuild, common properties
- msbuild, project file properties
- ExcludeDeploymentUrl property
- project file properties (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 359dda28fa02711d4def9f26f2859dcc3c2bc65d
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="common-msbuild-project-properties"></a>Wspólne właściwości projektów MSBuild
W poniższej tabeli przedstawiono często używane właściwości, które są zdefiniowane w plikach projektu programu Visual Studio lub zawarte w plikach TARGETS, które zapewnia MSBuild.  
  
 Pliki projektu w programie Visual Studio (.csproj, vbproj, vcxproj i inne) zawiera kod XML programu MSBuild, który jest uruchamiany podczas tworzenia projektu za pomocą środowiska IDE. Projekty zwykle zaimportować co najmniej jeden plik .targets do definiowania procesu kompilacji. Aby uzyskać więcej informacji, zobacz [. Celem pliki](../msbuild/msbuild-dot-targets-files.md).  
  
## <a name="list-of-common-properties-and-parameters"></a>Lista typowych właściwości i parametrów  
  
|Właściwości lub nazwa parametru|Opis|  
|--------------------------------|-----------------|  
|AdditionalLibPaths|Określa dodatkowe foldery, w których kompilatory szukać zestawów odwołań.|  
|AddModules|Powoduje, że kompilator wszystkie typu informacji z określonego pliki do projektu, kompilacja. Ta właściwość jest odpowiednikiem `/addModules` przełącznika kompilatora.|  
|ALToolPath|Ścieżka, gdzie można znaleźć AL.exe. Ta właściwość zastępuje bieżącą wersję AL.exe umożliwia korzystanie z innej wersji.|  
|ApplicationIcon|Plik ikony .ico do przekazania do kompilatora osadzania jako ikona Win32. Właściwość jest odpowiednikiem `/win32icon` przełącznika kompilatora.|  
|ApplicationManifest|Określa ścieżkę pliku, który jest używany do generowania zewnętrznych informacji manifestu kontroli konta użytkownika (UAC). Dotyczy tylko przeznaczonych dla projektów programu Visual Studio [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].<br /><br /> W większości przypadków jest osadzony plik manifestu. Jednak jeśli używasz bezpłatnej COM rejestracji lub [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia, a następnie manifest może być zewnętrzny plik jest zainstalowany razem z zestawów aplikacji. Aby uzyskać więcej informacji zobacz właściwość NoWin32Manifest w tym temacie.|  
|AssemblyOriginatorKeyFile|Określa plik używany do podpisywania zestawu (.snk — lub pfx) i które są przekazywane do [resolvekeysource — zadanie](../msbuild/resolvekeysource-task.md) do generowania rzeczywiste klucz, który jest używany do podpisywania zestawu.|  
|AssemblySearchPaths|Lista lokalizacji do przeszukania podczas rozpoznawania zestawu odwołania czasu kompilacji. Kolejność wyświetlania ścieżek na tej liście jest przydatne, ponieważ wymienione wcześniej ścieżki mają pierwszeństwo przed później wpisów.|  
|AssemblyName|Nazwa zestawu ostateczne dane wyjściowe po utworzeniu projektu.|  
|BaseAddress|Określa adres bazowy zestawu wyjściowego głównego. Ta właściwość jest odpowiednikiem `/baseaddress` przełącznika kompilatora.|  
|BaseOutputPath|Podstawowa ścieżka do pliku wyjściowego. Jeśli jest ustawiona, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] użyje `OutputPath = $(BaseOutputPath)\$(Configuration)\`. Przykład składni:`<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>`|  
|BaseIntermediateOutputPath|Folder najwyższego poziomu, w której tworzone są wszystkie foldery specyficzne dla konfiguracji pośrednich danych wyjściowych. Wartość domyślna to `obj\`. Następujący kod jest przykładem:`<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>`|  
|BuildInParallel|Wartość logiczna, która wskazuje, czy odwołania projektu są wbudowane lub oczyszczone równoległe, gdy wiele procesów [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] jest używany. Wartość domyślna to `true`, co oznacza, że projekty zostaną skompilowane w równoległe, gdy system ma wiele rdzeni lub procesorów.|  
|BuildProjectReferences|Wartość logiczna, która wskazuje, czy odwołania projektu są tworzone przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Automatycznie `false` Jeśli tworzysz projekt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE) `true` Jeśli inaczej. `/p:BuildProjectReferences=false`można określić w wierszu polecenia, aby uniknąć sprawdzanie, czy przywoływane projekty są aktualne.|  
|CleanFile|Nazwa pliku, która będzie służyć jako "czysta pamięci podręcznej." Wyczyść pamięć podręczną znajduje się lista wygenerowanych plików do usunięcia podczas oczyszczania operacji. Plik jest przekazywany w ścieżce pośrednich danych wyjściowych przez proces kompilacji.<br /><br /> Ta właściwość określa tylko nazwy plików, które nie mają informacje o ścieżce.|  
|Strona kodowa|Określa stronę kodową do użycia dla wszystkich plików kodu źródłowego w kompilacji. Ta właściwość jest odpowiednikiem `/codepage` przełącznika kompilatora.|  
|CompilerResponseFile|Plik odpowiedzi opcjonalne, które mogą zostać przekazane do zadania kompilatora.|  
|Konfiguracja|Konfiguracji, które tworzysz, "Debug" lub "Wersja".|  
|CscToolPath|Ścieżka csc.exe, [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] kompilatora.|  
|CustomBeforeMicrosoftCommonTargets|Nazwa pliku projektu lub plik elementów docelowych, który ma być importowany automatycznie przed wspólnej importu obiektów docelowych.|  
|DebugSymbols|Wartość logiczna wskazująca, czy symbole są generowane przez kompilację.<br /><br /> Ustawienie **/p:DebugSymbols = false** w wierszu polecenia powoduje wyłączenie generowania plików symboli (.pdb) bazy danych programu.|  
|DefineConstants|Definiuje warunkowe stałe kompilatora. Pary symboli i wartości są oddzielone średnikami i są określane przy użyciu następującej składni:<br /><br /> *symbol1 = wartość1; Symbol2 = wartość2*<br /><br /> Właściwość jest odpowiednikiem `/define` przełącznika kompilatora.|  
|DefineDebug|Wartość logiczna, która wskazuje, czy stała debugowania zdefiniowane.|  
|DefineTrace|Wartość logiczna, która wskazuje, czy stała śledzenia zdefiniowane.|  
|DebugType|Określa poziom informacji o debugowaniu, które mają być generowane. Prawidłowe wartości to "Pełna", "pdbonly" i "none."|  
|DelaySign|Wartość logiczna wskazująca, czy ma opóźnienie Podpisz zestaw z zamiast pełnego logowania.|  
|Deterministyczna|Wartość logiczna wskazująca, czy kompilator powinien wywoływać identyczne zestawy dla identyczne dane wejściowe. Ten parametr odpowiada `/deterministic` przełącznika z `vbc.exe` i `csc.exe` kompilatory.|
|DisabledWarnings|Pomija określonych ostrzeżeń. Numeryczna część identyfikatora ostrzeżenie musi być określona. Wiele ostrzeżeń są oddzielone średnikami. Ten parametr odpowiada `/nowarn` przełącznika kompilatora vbc.exe.|  
|DisableFastUpToDateCheck|Wartość logiczna, która ma zastosowanie do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tylko. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Kompilacji manager używa w procesie nazywanym FastUpToDateCheck w celu ustalenia, czy projekt musi zostać również przebudowany być aktualne. Ten proces jest szybsza niż przy użyciu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do określenia. Ustawienie właściwości DisableFastUpToDateCheck `true` pozwala pominąć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Menedżera kompilacji i wymusić użycie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do ustalenia, czy projekt jest aktualny.|  
|DocumentationFile|Nazwa pliku, który zostanie wygenerowany jako plik dokumentacji XML. Ta nazwa zawiera tylko nazwę pliku i nie ma ścieżki informacji.|  
|ErrorReport|Określa, jak zadanie kompilator powinien zgłosić wewnętrzne błędy kompilatora. Prawidłowe wartości to "Monituj", "Wyślij" lub "none." Ta właściwość jest odpowiednikiem `/errorreport` przełącznika kompilatora.|  
|ExcludeDeploymentUrl|[Generatedeploymentmanifest — zadanie](../msbuild/generatedeploymentmanifest-task.md) dodaje deploymentprovider — tag do manifestu wdrożenia, jeśli plik projektu zawiera dowolną z następujących elementów:<br /><br /> -   UpdateUrl<br />-InstallUrl<br />-PublishUrl<br /><br /> Przy użyciu ExcludeDeploymentUrl, jednak uniemożliwia deploymentprovider — tag dodawany do manifest wdrażania, nawet jeżeli niektóre powyżej adresów URL. Aby to zrobić, dodaj następującą właściwość w pliku projektu:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>`**Uwaga:** ExcludeDeploymentUrl nie jest widoczna w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE i można ustawić tylko przez ręczna Edycja pliku projektu. Ustawienie tej właściwości nie ma wpływu na publikowanie w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]; oznacza to, że deploymentprovider — tag nadal zostanie dodany adres URL określony przez PublishUrl.|  
|FileAlignment|Określa w bajtach, where były wyrównane w sekcjach pliku wyjściowego. Prawidłowe wartości to 512, 1024, 2048, 4096, 8192. Ta właściwość jest odpowiednikiem `/filealignment` przełącznika kompilatora.|  
|FrameworkPathOverride|Określa lokalizację pliku mscorlib.dll i pliku microsoft.visualbasic.dll. Ten parametr jest odpowiednikiem `/sdkpath` przełącznika kompilatora vbc.exe.|  
|GenerateDocumentation|(Tylko w języku Visual Basic) Parametrów typu boolean wskazującą, czy dokumentacji jest generowany przez kompilację. Jeśli `true`, kompilacja generuje informacje o dokumentacji i umieszczenie go w pliku XML z nazwą pliku wykonywalnego lub biblioteki utworzonym przez zadanie kompilacji.|
|IntermediateOutputPath|Ścieżka wyjściowa pełnej pośrednie wynikające z `BaseIntermediateOutputPath`, jeśli nie określono ścieżki. Na przykład \obj\debug\\. Jeśli ta właściwość nie zostanie zastąpiona, następnie ustawienie `BaseIntermediateOutputPath` nie ma wpływu.|  
|KeyContainerName|Nazwa kontenera klucza silnej nazwy.|  
|KeyOriginatorFile|Nazwa pliku klucza silnej nazwy.|  
|ModuleAssemblyName|Nazwa modułu skompilowanego jest włączona do zestawu. Właściwość jest odpowiednikiem `/moduleassemblyname` przełącznika kompilatora.|  
|NoLogo|Wartość logiczna, która wskazuje, czy logo kompilatora, które ma zostać wyłączone. Ta właściwość jest odpowiednikiem `/nologo` przełącznika kompilatora.|  
|NoStdLib|Wartość logiczna, która wskazuje, czy w celu uniknięcia odwołanie do biblioteki standardowej (mscorlib.dll). Wartość domyślna to `false`.|  
|NoVBRuntimeReference|Wartość logiczna, która wskazuje, czy [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] środowiska uruchomieniowego (w pliku Microsoft.VisualBasic.dll) mają być dołączane jako odwołanie do projektu.|  
|NoWin32Manifest|Wartość logiczna, która wskazuje, czy informacje manifestu kontroli konta użytkownika (UAC) zostaną osadzone w aplikacji użytkownika pliku wykonywalnego. Dotyczy tylko przeznaczonych dla projektów programu Visual Studio [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. W projektach wdrażane za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i COM bez rejestrowania lub element ten zostanie zignorowany. `False`(wartość domyślna) określa, że informacje manifestu kontroli konta użytkownika (UAC) można osadzić w pliku wykonywalnym aplikacji. `True`Określa, że informacje manifestu kontroli konta użytkownika nie można osadzić.<br /><br /> Ta właściwość jest stosowana tylko do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektów przeznaczonych dla [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. W projektach wdrażane za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i COM bez rejestrowania, ta właściwość jest ignorowana.<br /><br /> NoWin32Manifest należy dodawać tylko wtedy, gdy nie chcesz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] celu osadzania manifestów wszelkich jego pliku wykonywalnego informacji w aplikacji; ten proces jest nazywany *wirtualizacji*. Aby użyć wirtualizacji, ustaw `<ApplicationManifest>` w połączeniu z `<NoWin32Manifest>` w następujący sposób:<br /><br /> — Dla [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektów, Usuń `<ApplicationManifest>` węzła. (W [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektów, `<NoWin32Manifest>` jest ignorowana, jeśli `<ApplicationManifest>` istnieje węzeł.)<br />— Dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektów, ustaw `<ApplicationManifest>` do `False` i `<NoWin32Manifest>` do `True`. (W [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektów, `<ApplicationManifest>` zastępuje `<NoWin32Manifest>`.)<br /> Ta właściwość jest odpowiednikiem `/nowin32manifest` przełącznika kompilatora vbc.exe.|  
|Optymalizacja|Wartość logiczna, która wartość `true`, włącza optymalizacje kompilatora. Ta właściwość jest odpowiednikiem `/optimize` przełącznika kompilatora.|  
|OptionCompare|Określa, jak zostały wprowadzone porównywania ciągów. Prawidłowe wartości to "binary" lub "text". Ta właściwość jest odpowiednikiem `/optioncompare` przełącznika kompilatora vbc.exe.|  
|OptionExplicit|Wartość logiczna, która wartość `true`, wymaga jawnej deklaracji zmiennych w kodzie źródłowym. Ta właściwość jest odpowiednikiem `/optionexplicit` przełącznika kompilatora.|  
|OptionInfer|Wartość logiczna, która wartość `true`, umożliwia wnioskowanie zmiennych. Ta właściwość jest odpowiednikiem `/optioninfer` przełącznika kompilatora.|  
|OptionStrict|Wartość logiczna, która wartość `true`, powoduje, że zadania kompilacji wymusić semantyki typu strict do ograniczenia niejawne konwersje typów. Ta właściwość jest odpowiednikiem `/optionstrict` przełącznika kompilatora vbc.exe.|  
|OutputPath|Określa ścieżkę do katalogu wyjściowego względem katalogu projektu, na przykład "bin\Debug".|  
|Atrybut OutputType|Określa format pliku wyjściowego pliku. Ten parametr może mieć jedną z następujących wartości:<br /><br /> -Biblioteki. Tworzy bibliotekę kodu. (Wartość domyślna).<br />-Exe. Tworzy aplikację konsoli.<br />-Module. Tworzy moduł.<br />-Winexe. Tworzy program opartych na systemie Windows.<br /><br /> Ta właściwość jest odpowiednikiem `/target` przełącznika kompilatora vbc.exe.|  
|OverwriteReadOnlyFiles|Wartość logiczna wskazująca, czy chcesz włączyć kompilacji do wyzwalacza błąd lub zastąpienie plików tylko do odczytu.|  
|PdbFile|Nazwa pliku są emitowanie pliku PDB. Ta właściwość jest odpowiednikiem `/pdb` przełącznika csc.exe kompilatora.|  
|Platforma|System operacyjny, które tworzysz dla. Prawidłowe wartości to "Any CPU", "x 86" i "x64".|  
|ProduceReferenceAssembly|Wartość logiczna, która wartość `true` umożliwia produkcji [odwołuje się do zestawów](https://github.com/dotnet/roslyn/blob/master/docs/features/refout.md) dla bieżącego zestawu. `Deterministic`powinien być `true` podczas używania tej funkcji. Ta właściwość odpowiada `/refout` przełącznika z `vbc.exe` i `csc.exe` kompilatory.|
|RemoveIntegerChecks|Wartość logiczna wskazująca, czy należy wyłączyć sprawdzanie błędów przepełnienie liczby całkowitej. Wartość domyślna to `false`. Ta właściwość jest odpowiednikiem `/removeintchecks` przełącznika kompilatora vbc.exe.|  
|SGenUseProxyTypes|Wartość logiczna wskazująca, czy typy serwer proxy ma być generowany przez SGen.exe.<br /><br /> Element docelowy SGen używa tej właściwości można ustawić flagi UseProxyTypes. Tej właściwości wartość domyślna to true i nie bez interfejsu użytkownika, aby zmienić to ustawienie. Aby wygenerować zestawu serializacji dla typów innych niż Usługa sieci Web, Dodaj tę właściwość w pliku projektu i ustawić ją na wartość false przed zaimportowaniem Microsoft.Common.Targets lub C#/VB.targets.|  
|SGenToolPath|Ścieżka narzędzia opcjonalne, która wskazuje, gdzie można uzyskać SGen.exe, gdy bieżąca wersja SGen.exe zostanie zastąpiona.|  
|StartupObject|Określa klasę lub moduł, który zawiera metody Main lub procedury Sub Main. Ta właściwość jest odpowiednikiem `/main` przełącznika kompilatora.|  
|Element ProcessorArchitecture|Architektura procesora używany, gdy odwołania do zestawów zostaną rozwiązane. Prawidłowe wartości to "msil", "x86", "amd64" lub "ia64."|  
|RootNamespace|Przestrzeń nazw głównego do użycia podczas Nazwa osadzonego zasobu. Ta przestrzeń nazw jest częścią nazwy osadzonego zasobu manifestu.|  
|Satellite_AlgorithmId|Identyfikator algorytmu wyznaczania wartości skrótu AL.exe do użycia podczas zestawy satelickie są tworzone.|  
|Satellite_BaseAddress|Adres podstawowy do użycia podczas zestawy satelickie specyficzne dla kultury są tworzone przy użyciu `CreateSatelliteAssemblies` docelowej.|  
|Satellite_CompanyName|Nazwa firmy do przekazania do AL.exe podczas generowania zestawu satelity.|  
|Satellite_Configuration|Nazwa konfiguracji do przekazania do AL.exe podczas generowania zestawu satelity.|  
|Satellite_Description|Tekst opisu do przekazania do AL.exe podczas generowania zestawu satelity.|  
|Satellite_EvidenceFile|Osadza określony plik w zestawu satelickiego z nazwą zasobu "Security.Evidence."|  
|Satellite_FileVersion|Określa ciąg dla pola wersji pliku w zestawie satelity.|  
|Satellite_Flags|Określa wartość dla pola flagi w zestawie satelity.|  
|Satellite_GenerateFullPaths|Powoduje, że zadania kompilacji użyć ścieżek bezwzględnych pliki zgłosił błąd.|  
|Satellite_LinkResource|Łącza do zestawu satelickiego pliki określonego zasobu.|  
|Satellite_MainEntryPoint|Określa pełną nazwę (czyli class.method) metoda do użycia jako punkt wejścia po przekonwertowaniu do pliku wykonywalnego modułu podczas generowania zestawu satelity.|  
|Satellite_ProductName|Określa ciąg dla pola produktu w zestawu satelickiego.|  
|Satellite_ProductVersion|Określa ciąg dla pola ProductVersion w zestawu satelickiego.|  
|Satellite_TargetType|Określa format pliku satelickie zestawu wyjściowego pliku jako "library", "exe","lub"Windows". Wartość domyślna to "library".|  
|Satellite_Title|Określa ciąg w polu Tytuł w zestawu satelickiego.|  
|Satellite_Trademark|Określa ciąg znaków towarowych pola w zestawu satelickiego.|  
|Satellite_Version|Określa informacje o wersji dla zestawu satelickiego.|  
|Satellite_Win32Icon|Wstawia plik .ico ikony zestawu satelickiego.|  
|Satellite_Win32Resource|Wstawia zasób Win32 (.res plik) do zestawu satelickiego.|  
|SubsystemVersion|Określa minimalną wersję podsystemu używanego w wygenerowanym pliku wykonywalnego. Ta właściwość jest odpowiednikiem `/subsystemversion` przełącznika kompilatora. Aby uzyskać informacje o wartość domyślna tej właściwości, zobacz [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) lub [/subsystemversion (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option).|  
|TargetCompactFramework|Wersja programu .NET Compact Framework, która jest wymagana do uruchamiania aplikacji, które tworzysz. Określenie tej umożliwia utworzenie odwołania niektórych zestawów struktury, których nie można się odwołać, w przeciwnym razie wartość.|  
|targetFrameworkVersion|Wersja [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] , co jest wymagane do uruchomienia aplikacji, które tworzysz. Określenie tej umożliwia utworzenie odwołania niektórych zestawów struktury, których nie można się odwołać, w przeciwnym razie wartość.|  
|TreatWarningsAsErrors|Parametrów typu boolean, jeśli `true`, powoduje, że wszystkie ostrzeżenia, należy go traktować jako błędy. Ten parametr jest odpowiednikiem `/nowarn` przełącznika kompilatora.|  
|UseHostCompilerIfAvailable|Parametrów typu boolean, jeśli `true`, powoduje, że zadania kompilacji do używania obiektu wewnątrzprocesowego kompilatora, jeśli jest dostępna. Ten parametr jest używany tylko przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|Utf8Output|Parametrów typu boolean, jeśli `true`, rejestruje dane wyjściowe kompilatora przy użyciu kodowania UTF-8. Ten parametr jest odpowiednikiem `/utf8Output` przełącznika kompilatora.|  
|VbcToolPath|Opcjonalna ścieżka wskazującą inną lokalizację dla vbc.exe, gdy bieżąca wersja vbc.exe zostanie zastąpiona.|  
|VbcVerbosity|Określa poziom szczegółowości [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] danych wyjściowych kompilatora. Prawidłowe wartości to "Quiet", "Normal" (wartość domyślna) lub "Pełne."|  
|VisualStudioVersion|Określa wersję programu Visual Studio, w którym należy traktować tego projektu jest uruchomiona. Jeśli ta właściwość nie jest określony, program MSBuild ustawia ją na wartość domyślną uzasadnione.<br /><br /> Ta właściwość jest używana w kilku typów projektów, aby określić zestaw obiektów docelowych, które są używane dla kompilacji. Jeśli `ToolsVersion` ustawiono 4.0 lub nowszy w projekcie, `VisualStudioVersion` służy do określania, które sub-zestaw narzędzi do użycia. Aby uzyskać więcej informacji, zobacz [zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).|  
|WarningsAsErrors|Określa listę ostrzeżeń, które mają być traktowane jako błędy. Ten parametr jest odpowiednikiem `/warnaserror` przełącznika kompilatora.|  
|WarningsNotAsErrors|Określa listę ostrzeżeń, które nie są traktowane jako błędy. Ten parametr jest odpowiednikiem `/warnaserror` przełącznika kompilatora.|  
|Win32Manifest|Nazwa pliku manifestu, który powinien być osadzony w zestawie końcowym. Ten parametr jest odpowiednikiem `/win32Manifest` przełącznika kompilatora.|  
|Win32Resource|Nazwa pliku zasobów Win32 do osadzenia w zestawie końcowym. Ten parametr jest odpowiednikiem `/win32resource` przełącznika kompilatora.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wspólne elementy projektów MSBuild](../msbuild/common-msbuild-project-items.md)
