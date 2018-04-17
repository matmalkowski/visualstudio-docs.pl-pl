---
title: AL (Assembly Linker) zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AL
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- AL task [MSBuild]
- MSBuild, AL task
ms.assetid: 2ddefbf2-5662-4d55-99a6-ac383bf44560
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d0fce71e472e006ae23069d6e146cc365e25aa6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="al-assembly-linker-task"></a>AL (Assembly Linker) — Zadanie
AL — zadanie jest zawijana AL.exe, narzędzie, które jest dystrybuowane z [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. To narzędzie Assembly Linker jest używany do utworzenia zestawu z manifestu z jednego lub więcej plików, które moduły albo lub plików zasobów. Kompilatory i środowisk deweloperskich może już udostępniać tych funkcji, co często nie jest konieczne do użycia bezpośrednio tego zadania. Assembly Linker jest użyteczna dla deweloperów konieczności tworzenia w jednym zestawie z wielu plików składników, takich jak te, które mogą być tworzone z wielu języków programowania. To zadanie nie łączyć modułów w jednym zestawie pliku; indywidualne moduły muszą być rozproszone i jest dostępny w kolejności dla wynikowego zestawu można prawidłowo załadować. Aby uzyskać więcej informacji dotyczących AL.exe, zobacz [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `AL` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AlgorithmID`|Opcjonalne `String` parametru.<br /><br /> Określa algorytm wyznaczania wartości skrótu dla wszystkich plików w wieloplikowym zestawie z wyjątkiem pliku, który zawiera manifest zestawu. Aby uzyskać więcej informacji, zobacz dokumentację `/algid` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`BaseAddress`|Opcjonalne `String` parametru.<br /><br /> Określa adres, pod którym zostanie załadowana biblioteka DLL na komputerze użytkownika w czasie wykonywania. Aplikacje załadować szybciej Jeśli określony adres podstawowy biblioteki dll, a nie umożliwienie przemieszczenie biblioteki dll w obszarze procesu systemu operacyjnego. Ten parametr odpowiada /base[adres](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`CompanyName`|Opcjonalne `String` parametru.<br /><br /> Określa ciąg `Company` pole w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/comp[any]` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`Configuration`|Opcjonalne `String` parametru.<br /><br /> Określa ciąg `Configuration` pole w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/config[uration]` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`Copyright`|Opcjonalne `String` parametru.<br /><br /> Określa ciąg `Copyright` pole w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/copy[right]` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`Culture`|Opcjonalne `String` parametru.<br /><br /> Określa ciąg kultury do skojarzenia z zestawem. Aby uzyskać więcej informacji, zobacz dokumentację `/c[ulture]` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`DelaySign`|Opcjonalne `Boolean` parametru.<br /><br /> `true` Aby umieścić tylko klucz publiczny w zestawie; `false` pełni podpisać zestawu. Aby uzyskać więcej informacji, zobacz dokumentację `/delay[sign]` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`Description`|Opcjonalne `String` parametru.<br /><br /> Określa ciąg `Description` pole w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/descr[iption]` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`EmbedResources`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Osadza określonych zasobów obrazu, który zawiera manifest zestawu. To zadanie kopiuje zawartość pliku zasobu do obrazu. Elementy przekazany do tego parametru może być opcjonalne metadane dołączone o nazwie `LogicalName` i `Access`. `LogicalName` Metadanych służy do określania wewnętrzny identyfikator zasobu.  `Access` Metadanych może być ustawiony na `private` aby zasobu nie są widoczne dla innych zestawów. Aby uzyskać więcej informacji, zobacz dokumentację `/embed[resource]` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`EvidenceFile`|Opcjonalne `String` parametru.<br /><br /> Osadza określonego pliku w zestawie z nazwą zasobu `Security.Evidence`.<br /><br /> Nie można użyć `Security.Evidence` regularne zasobów. Ten parametr odpowiada `/e[vidence]` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`ExitCode`|Opcjonalne `Int32` tylko do odczytu parametru wyjściowego.<br /><br /> Określa kod zakończenia podał wykonanego polecenia.|  
|`FileVersion`|Opcjonalne `String` parametru.<br /><br /> Określa ciąg `File Version` pole w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/fileversion` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`Flags`|Opcjonalne `String` parametru.<br /><br /> Określa wartość `Flags` pole w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/flags` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`GenerateFullPaths`|Opcjonalne `Boolean` parametru.<br /><br /> Powoduje zadania za pomocą ścieżki bezwzględnej dla wszystkich plików, które są zgłaszane w komunikacie o błędzie. Ten parametr odpowiada `/fullpaths` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`KeyContainer`|Opcjonalne `String` parametru.<br /><br /> Określa kontener zawierający parę kluczy. Zestaw zostanie podpisany (należy nadać mu silną nazwę) przez wstawienie klucza publicznego do manifestu zestawu. Zadanie będzie Zaloguj się w zestawie końcowym z kluczem prywatnym. Aby uzyskać więcej informacji, zobacz dokumentację `/keyn[ame]` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`KeyFile`|Opcjonalne `String` parametru.<br /><br /> Określa plik, który zawiera pary kluczy lub klucz publiczny, aby podpisać zestaw. Kompilator wstawia klucz publiczny w manifeście zestawu, a następnie podpisuje ostateczny zestaw przy użyciu klucza prywatnego. Aby uzyskać więcej informacji, zobacz dokumentację `/keyf[ile]` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`LinkResources`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Łącza do zestawu plików określonego zasobu. Zasób staje się częścią zestawu, ale plik nie jest kopiowany. Elementy przekazany do tego parametru może być opcjonalne metadane dołączone o nazwie `LogicalName`, `Target`, i `Access`. `LogicalName` Metadanych służy do określania wewnętrzny identyfikator zasobu. `Target` Metadanych można określić ścieżkę i nazwę pliku, do którego zadanie kopiuje plik, po którym kompiluje tego nowego pliku w zestawie. `Access` Metadanych może być ustawiony na `private` aby zasobu nie są widoczne dla innych zestawów. Aby uzyskać więcej informacji, zobacz dokumentację `/link[resource]` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`MainEntryPoint`|Opcjonalne `String` parametru.<br /><br /> Określa w pełni kwalifikowana nazwa (*class.method*) metody do użycia jako punkt wejścia podczas konwertowania modułu do pliku wykonywalnego. Ten parametr odpowiada `/main` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`OutputAssembly`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru wyjściowego.<br /><br /> Określa nazwę pliku wygenerowanego przez to zadanie. Ten parametr odpowiada `/out` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`Platform`|Opcjonalne `String` parametru.<br /><br /> Ogranicza platformy, które można uruchamiać ten kod. musi mieć jedną z `x86`, `Itanium`, `x64`, lub `anycpu`. Wartość domyślna to `anycpu`. Ten parametr odpowiada `/platform` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`ProductName`|Opcjonalne `String` parametru.<br /><br /> Określa ciąg `Product` pole w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/prod[uct]` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`ProductVersion`|Opcjonalne `String` parametru.<br /><br /> Określa ciąg `ProductVersion` pole w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/productv[ersion]` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`ResponseFiles`|Opcjonalne `String[]` parametru.<br /><br /> Określa pliki odpowiedzi, które zawierają dodatkowe opcje do przekazywania do konsolidator zestawów.|  
|`SdkToolsPath`|Opcjonalne `String` parametru.<br /><br /> Określa ścieżkę do narzędzia zestawu SDK, takich jak resgen.exe.|  
|`SourceModules`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Przynajmniej jeden moduł skompilowany w zestawie. Moduły zostaną wyświetlone w manifeście zestawu wynikowego i nadal trzeba rozproszone i jest dostępny w kolejności dla zestawu do załadowania. Elementy przekazany ten parametr może mieć dodatkowe metadane o nazwie `Target`, który określa ścieżkę i nazwę pliku, do którego zadanie kopiuje plik, po którym kompiluje tego nowego pliku w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker). Ten parametr odnosi się do listy modułów przekazany Al.exe bez określonego przełącznika.|  
|`TargetType`|Opcjonalne `String` parametru.<br /><br /> Określa format pliku wyjściowego pliku: `library` (biblioteki kodu), `exe` (aplikacji konsoli) lub `win` (aplikacji systemu Windows). Wartość domyślna to `library`. Ten parametr odpowiada `/t[arget]` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`TemplateFile`|Opcjonalne `String` parametru.<br /><br /> Określa zestaw, z której dziedziczy wszystkie metadane zestawu, z wyjątkiem pola kultury. Określony zestaw musi mieć silnej nazwy.<br /><br /> Utworzonej za pomocą zestawu `TemplateFile` parametr zostanie zestawu satelickiego. Ten parametr odpowiada `/template` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`Timeout`|Opcjonalne `Int32` parametru.<br /><br /> Określa ilość czasu, w milisekundach, po których plik wykonywalny zadania zostanie zakończony. Wartość domyślna to `Int.MaxValue`, wskazując, że to nie okres limitu czasu.|  
|`Title`|Opcjonalne `String` parametru.<br /><br /> Określa ciąg `Title` pole w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/title` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`ToolPath`|Opcjonalne `String` parametru.<br /><br /> Określa lokalizację, z której zadanie zostanie załadowany podstawowy plik wykonywalny (Al.exe). Jeśli ten parametr nie jest określony, zadanie użyje ścieżki instalacji zestawu SDK, odpowiadający wersji framework, na którym działa [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|`Trademark`|Opcjonalne `String` parametru.<br /><br /> Określa ciąg `Trademark` pole w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/trade[mark]` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`Version`|Opcjonalne `String` parametru.<br /><br /> Określa informacje o wersji dla tego zestawu. Format ciągu jest *główna.pomocnicza.kompilacja.poprawka*. Wartość domyślna to 0. Aby uzyskać więcej informacji, zobacz dokumentację `/v[ersion]` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`Win32Icon`|Opcjonalne `String` parametru.<br /><br /> Wstawia plik .ico do zestawu. Plik .ico nadaje plikowi wyjściowemu pożądany wygląd w Eksploratorze plików. Ten parametr odpowiada `/win32icon` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`Win32Resource`|Opcjonalne `String` parametru.<br /><br /> Wstawia zasób Win32 (plik .res) do pliku wyjściowego. Aby uzyskać więcej informacji, zobacz dokumentację `/win32res` opcji [Al.exe (konsolidator zestawów)](/dotnet/framework/tools/al-exe-assembly-linker).|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.ToolTaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [tooltaskextension — klasa podstawowa](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy zestaw z podanych opcji.  
  
```xml  
<AL  
    EmbedResources="@(EmbeddedResource)"  
    Culture="%(EmbeddedResource.Culture)"  
    TemplateFile="@(IntermediateAssembly)"  
    KeyContainer="$(KeyContainerName)"  
    KeyFile="$(KeyOriginatorFile)"  
    DelaySign="$(DelaySign)"  
  
    OutputAssembly=  
       "%(EmbeddedResource.Culture)\$(TargetName).resources.dll">  
  
    <Output TaskParameter="OutputAssembly"  
        ItemName="SatelliteAssemblies"/>  
</AL>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)