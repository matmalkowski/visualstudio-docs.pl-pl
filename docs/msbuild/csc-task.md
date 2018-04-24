---
title: CSC — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Csc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Csc task [MSBuild]
- MSBuild, Csc task
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d35f1dee5c2f3d4f91a6d59e001bc9f16fd7b52a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="csc-task"></a>Csc — Zadanie
Opakowuje CSC.exe i tworzy pliki wykonywalne (pliki .exe), bibliotek dołączanych dynamicznie (pliki dll) lub moduły kodu (pliki modułu .netmodule). Aby uzyskać więcej informacji o CSC.exe, zobacz [opcje kompilatora C#](/dotnet/csharp/language-reference/compiler-options/index).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `Csc` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Opcjonalne `String[]` parametru.<br /><br /> Określa dodatkowe katalogi do wyszukiwania odwołań. Aby uzyskać więcej informacji, zobacz [/lib (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option).|  
|`AddModules`|Opcjonalne `String` parametru.<br /><br /> Określa co najmniej jednego modułu jako część zestawu. Aby uzyskać więcej informacji, zobacz [/addmodule (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option).|  
|`AllowUnsafeBlocks`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, kompiluje kod, który używa [niebezpieczne](/dotnet/csharp/language-reference/keywords/unsafe) — słowo kluczowe. Aby uzyskać więcej informacji, zobacz [/ unsafe (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).|  
|`ApplicationConfiguration`|Opcjonalne `String` parametru.<br /><br /> Określa plik konfiguracyjny aplikacji zawierający ustawienia powiązania zestawu.|  
|`BaseAddress`|Opcjonalne `String` parametru.<br /><br /> Określa preferowany adres podstawowy, w którym można załadować biblioteki DLL. Domyślny adres podstawowy biblioteki DLL jest ustawiana przez [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] środowisko uruchomieniowe języka wspólnego. Aby uzyskać więcej informacji, zobacz [/baseAddress (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).|  
|`CheckForOverflowUnderflow`|Opcjonalne `Boolean` parametru.<br /><br /> Określa, czy liczba całkowita arytmetyczne, który przepełnienie granic o typie danych powoduje, że wystąpił wyjątek w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [/ checked (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).|  
|`CodePage`|Opcjonalne `Int32` parametru.<br /><br /> Określa stronę kodową do używania wszystkich plików kodu źródłowego w kompilacji. Aby uzyskać więcej informacji, zobacz [/CODEPAGE (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option).|  
|`DebugType`|Opcjonalne `String` parametru.<br /><br /> Określa typ debugowania. `DebugType` może być `full` lub `pdbonly`. Wartość domyślna to `full`, co pozwala debuger jest dołączony do działającego programu. Określanie `pdbonly` źródła umożliwia debugowanie kodu, gdy program jest uruchamiany w debugerze, ale wyświetla asemblera tylko, jeśli uruchomiony program jest podłączony do debugera.<br /><br /> Ten parametr zastępuje `EmitDebugInformation` parametru.<br /><br /> Aby uzyskać więcej informacji, zobacz [/Debug (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).|  
|`DefineConstants`|Opcjonalne `String` parametru.<br /><br /> Definiuje symbole preprocesora. Aby uzyskać więcej informacji, zobacz [/ define (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).|  
|`DelaySign`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, określa, czy zestawem całkowicie podpisane. Jeśli `false`, określa, że chcesz umieścić klucz publiczny w zestawie.<br /><br /> Ten parametr nie obowiązuje, chyba że używana w trybie `KeyFile` lub `KeyContainer` parametru.<br /><br /> Aby uzyskać więcej informacji, zobacz [/DelaySign (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option).|  
|`DisabledWarnings`|Opcjonalne `String` parametru.<br /><br /> Określa listę ostrzeżeń, które mają zostać wyłączone. Aby uzyskać więcej informacji, zobacz [/nowarn (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).|  
|`DocumentationFile`|Opcjonalne `String` parametru.<br /><br /> Przetwarza komentarzy do dokumentacji do pliku XML. Aby uzyskać więcej informacji, zobacz [/doc (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).|  
|`EmitDebugInformation`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie generuje informacje o debugowaniu i umieszcza je w pliku bazy danych (.pdb) program. Jeśli `false`, zadanie emituje informacji debugowania. Wartość domyślna to `false`. Aby uzyskać więcej informacji, zobacz [/Debug (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).|  
|`ErrorReport`|Opcjonalne `String` parametru.<br /><br /> Zapewnia to wygodny sposób zgłosić firmie Microsoft C# błąd wewnętrzny. Ten parametr może mieć wartość `prompt`, `send`, lub `none`. Jeśli ustawiono parametr `prompt`, zostanie wyświetlony monit, gdy wystąpi błąd wewnętrzny kompilatora. Monit umożliwia elektronicznie Wyślij raport o błędzie do firmy Microsoft. Jeśli ustawiono parametr `send`, raport o usterce są wysyłane automatycznie. Jeśli ustawiono parametr `none`, zgłaszany jest błąd tylko w tekstowych danych wyjściowych kompilatora. Wartość domyślna to `none`. Aby uzyskać więcej informacji, zobacz [/errorreport (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).|  
|`FileAlignment`|Opcjonalne `Int32` parametru.<br /><br /> Określa rozmiar sekcji w pliku wyjściowym. Aby uzyskać więcej informacji, zobacz [/filealign (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).|  
|`GenerateFullPaths`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, określa bezwzględną ścieżkę do pliku w danych wyjściowych kompilatora. Jeśli `false`, określa nazwę pliku. Wartość domyślna to `false`. Aby uzyskać więcej informacji, zobacz [/fullpaths (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option).|  
|`KeyContainer`|Opcjonalne `String` parametru.<br /><br /> Określa nazwę kontenera kluczy kryptograficznych. Aby uzyskać więcej informacji, zobacz [/KeyContainer (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option).|  
|`KeyFile`|Opcjonalne `String` parametru.<br /><br /> Określa nazwę pliku zawierającego klucz kryptograficzny. Aby uzyskać więcej informacji, zobacz [/KeyFile (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option).|  
|`LangVersion`|Opcjonalne `String` parametru.<br /><br /> Określa wersję języka. Aby uzyskać więcej informacji, zobacz [/langversion (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).|  
|`LinkResources`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Tworzy łącze do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zasobów w pliku wyjściowym; plik zasobu nie jest umieszczony w pliku wyjściowym.<br /><br /> Pozycji przekazanych do tego parametru może mieć wpisy opcjonalne metadanych o nazwie `LogicalName` i `Access`. `LogicalName` odpowiada `identifier` parametr `/linkresource` przełącznika, i `Access` odpowiada `accessibility-modifier` parametru. Aby uzyskać więcej informacji, zobacz [/linkresource (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option).|  
|`MainEntryPoint`|Opcjonalne `String` parametru.<br /><br /> Określa lokalizację `Main` metody. Aby uzyskać więcej informacji, zobacz [/main (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option).|  
|`ModuleAssemblyName`|Opcjonalne `String` parametru.<br /><br /> Określa nazwę zestawu, którego częścią ma być ten moduł.|  
|`NoConfig`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, informuje kompilator, nie można skompilować przy użyciu pliku csc.rsp. Aby uzyskać więcej informacji, zobacz [/noconfig (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option).|  
|`NoLogo`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, Pomija wyświetlanie informacji o transparentu kompilatora. Aby uzyskać więcej informacji, zobacz [/nologo (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option).|  
|`NoStandardLib`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, uniemożliwia importowanie pliku mscorlib.dll, która określa całą przestrzeń nazw systemu. Użyj tego parametru, jeśli chcesz zdefiniować lub utworzyć własne systemową przestrzenią nazw i obiektów. Aby uzyskać więcej informacji, zobacz [/nostdlib (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).|  
|`NoWin32Manifest`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, nie dołączaj domyślnego manifestu Win32.|  
|`Optimize`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, włącza optymalizacje. Jeśli `false`, wyłącza optymalizacje. Aby uzyskać więcej informacji, zobacz [/ optimize (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).|  
|`OutputAssembly`|Opcjonalne `String` parametru wyjściowego.<br /><br /> Określa nazwę pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [/out (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).|  
|`OutputRefAssembly`|Opcjonalne `String` parametru.<br /><br /> Określa nazwę pliku wyjściowego odwołanie do zestawu. Aby uzyskać więcej informacji, zobacz [/refout (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option).|  
|`PdbFile`|Opcjonalne `String` parametru.<br /><br /> Określa nazwę pliku informacji debugowania. Domyślna nazwa to nazwa pliku wyjściowego z rozszerzeniem .pdb.|  
|`Platform`|Opcjonalne `String` parametru.<br /><br /> Określa platformę procesora, które ma zostać skonfigurowany przy użyciu pliku wyjściowego. Ten parametr może mieć wartość `x86`, `x64`, lub `anycpu`. Wartość domyślna to `anycpu`. Aby uzyskać więcej informacji, zobacz [/platform (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).|  
|`References`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Powoduje, że zadanie zaimportować informacje typu publicznego z określonych elementów do bieżącego projektu. Aby uzyskać więcej informacji, zobacz [/Reference (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Można określić [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] odwołania aliasu w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] przez dodanie metadanych `Aliases` do oryginalnego elementu "Reference". Na przykład, aby ustawić alias "LS1" w wierszu polecenia poniższy tekst CSC:<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> należy użyć:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Osadza [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zasobów w pliku wyjściowym.<br /><br /> Pozycji przekazanych do tego parametru może mieć wpisy opcjonalne metadanych o nazwie `LogicalName` i `Access`. `LogicalName` odpowiada `identifier` parametr `/resource` przełącznika, i `Access` odpowiada `accessibility-modifier` parametru. Aby uzyskać więcej informacji, zobacz [/Resource (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option).|  
|`ResponseFiles`|Opcjonalne `String` parametru.<br /><br /> Określa plik odpowiedzi, który zawiera polecenia dla tego zadania. Aby uzyskać więcej informacji, zobacz [@ (Określ plik odpowiedzi)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option).|  
|`Sources`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa co najmniej jeden [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] plików źródłowych.|  
|`TargetType`|Opcjonalne `String` parametru.<br /><br /> Określa format pliku wyjściowego pliku. Ten parametr może mieć wartość `library`, która tworzy bibliotekę kodu `exe`, co powoduje aplikacji konsoli, `module`, który tworzy moduł, lub `winexe`, co powoduje programu dla systemu Windows. Wartość domyślna to `library`. Aby uzyskać więcej informacji, zobacz [/TARGET (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).|  
|`TreatWarningsAsErrors`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, traktuje wszystkie ostrzeżenia jako błędy. Aby uzyskać więcej informacji, zobacz [/warnaserror (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).|  
|`UseHostCompilerIfAvailable`|Opcjonalne `Boolean` parametru.<br /><br /> Powoduje, że zadania, użyj obiektu wewnątrzprocesowego kompilatora, jeśli jest dostępna. Wykorzystania tylko przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|`Utf8Output`|Opcjonalne `Boolean` parametru.<br /><br /> Rejestruje kompilatora, dane wyjściowe przy użyciu kodowania UTF-8. Aby uzyskać więcej informacji, zobacz [/utf8output (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option).|  
|`WarningLevel`|Opcjonalne `Int32` parametru.<br /><br /> Określa poziom ostrzeżeń kompilatora do wyświetlenia. Aby uzyskać więcej informacji, zobacz [/ warn (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).|  
|`WarningsAsErrors`|Opcjonalne `String` parametru.<br /><br /> Określa listę ostrzeżeń, które mają być traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [/warnaserror (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Ten parametr zastępuje `TreatWarningsAsErrors` parametru.|  
|`WarningsNotAsErrors`|Opcjonalne `String` parametru.<br /><br /> Określa listę ostrzeżeń, które nie są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [/warnaserror (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Ten parametr jest przydatna, jeśli `TreatWarningsAsErrors` ustawiono parametr `true`.|  
|`Win32Icon`|Opcjonalne `String` parametru.<br /><br /> Wstawia plik .ico w zestawie, co daje pliku wyjściowego żądanego wyglądu w Eksploratorze plików. Aby uzyskać więcej informacji, zobacz [/win32icon (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option).|  
|`Win32Manifest`|Opcjonalne `String` parametru.<br /><br /> Określa manifestu Win32, które zostaną uwzględnione.|  
|`Win32Resource`|Opcjonalne `String` parametru.<br /><br /> Wstawia plik zasobów (.res) Win32 w pliku wyjściowym. Aby uzyskać więcej informacji, zobacz [/win32res (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option).|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z `Microsoft.Build.Tasks.ManagedCompiler` klasy, która dziedziczy <xref:Microsoft.Build.Tasks.ToolTaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [tooltaskextension — klasa podstawowa](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Csc` zadanie, aby skompilować plik wykonywalny przy użyciu plików źródłowych w `Compile` Kolekcja elementów.  
  
```xml  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)
