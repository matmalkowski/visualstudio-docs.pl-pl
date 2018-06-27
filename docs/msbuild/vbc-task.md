---
title: Vbc — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/12/2018
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Vbc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Vbc task [MSBuild]
- MSBuild, Vbc task
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 511e980b8c312803a82692042d7f88f389265c3a
ms.sourcegitcommit: c842955aa9ee9f149bb63e66e46c5c29be6e9881
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36962583"
---
# <a name="vbc-task"></a>Vbc — Zadanie
Opakowuje *vbc.exe*, które generuje pliki wykonywalne (*.exe*), bibliotek dołączanych dynamicznie (*.dll*), lub kodu modułów (*modułu .netmodule*). Aby uzyskać więcej informacji na temat *vbc.exe*, zobacz [wiersza polecenia kompilatora Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `Vbc` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Opcjonalne `String[]` parametru.<br /><br /> Określa dodatkowe foldery, w którym ma zostać wyszukane określone w atrybucie odwołania do zestawów.|  
|`AddModules`|Opcjonalne `String[]` parametru.<br /><br /> Powoduje, że kompilator wszystkie wpisz informacje z określonym dostępnych plików do projektu są obecnie kompilacji. Ten parametr odpowiada [- addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) przełącznika z *vbc.exe* kompilatora.|  
|`BaseAddress`|Opcjonalne `String` parametru.<br /><br /> Określa adres podstawowy biblioteki dll. Ten parametr odpowiada [- baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) przełącznika z *vbc.exe* kompilatora.|  
|`CodePage`|Opcjonalne `Int32` parametru.<br /><br /> Określa stronę kodową do używania wszystkich plików kodu źródłowego w kompilacji. Ten parametr odpowiada [- codepage](/dotnet/visual-basic/reference/command-line-compiler/codepage) przełącznika z *vbc.exe* kompilatora.|  
|`DebugType`|Opcjonalne `String[]` parametru.<br /><br /> Powoduje, że kompilator generuje informacje o debugowaniu. Ten parametr może mieć następujące wartości:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Wartość domyślna to `full`, która umożliwia dołączanie debugera do działającego programu. Wartość `pdbonly` umożliwia debugowanie kodu źródłowego, gdy program jest uruchamiany w debugerze, ale wyświetla kod języka zestawu tylko wtedy, gdy jest uruchomiony program jest podłączony do debugera. Aby uzyskać więcej informacji, zobacz [-debugowania (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|`DefineConstants`|Opcjonalne `String[]` parametru.<br /><br /> Definiuje warunkowe stałe kompilatora. Pary symboli i wartości są oddzielone średnikami i są określane za pomocą następującej składni:<br /><br /> *symbol1* `=` *wartość1* `;` *symbol2* `=` *wartość2*<br /><br /> Ten parametr odpowiada [— Zdefiniuj](/dotnet/visual-basic/reference/command-line-compiler/define) przełącznika z *vbc.exe* kompilatora.|  
|`DelaySign`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie zostanie umieszczone klucz publiczny w zestawie. Jeśli `false`, zadanie pełni podpisuje zestawu. Wartość domyślna to `false`. Ten parametr nie obowiązuje, chyba że używana z `KeyFile` parametru lub `KeyContainer` parametru. Ten parametr odpowiada [- delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) przełącznika z *vbc.exe* kompilatora.|  
|`Deterministic`|Opcjonalne `Boolean` parametru.<br/><br/> Jeśli `true`, powoduje, że kompilator output zestawu, którego zawartość binarna jest identyczna w kompilacji, jeśli dane wejściowe są identyczne.<br/><br/>Aby uzyskać więcej informacji, zobacz [-deterministyczne](/dotnet/visual-basic/reference/command-line-compiler/deterministic).|
|`DisabledWarnings`|Opcjonalne `String` parametru.<br /><br /> Pomija określonych ostrzeżeń. Należy określić numeryczna część identyfikatora ostrzeżenie. Wiele ostrzeżeń są oddzielone średnikami. Ten parametr odpowiada [- nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) przełącznika z *vbc.exe* kompilatora.|  
|`DocumentationFile`|Opcjonalne `String` parametru.<br /><br /> Przetwarza komentarzy do dokumentacji w określonym pliku XML. Ten parametr zastępuje `GenerateDocumentation` atrybutu. Aby uzyskać więcej informacji, zobacz [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc).|  
|`EmitDebugInformation`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie generuje informacje o debugowaniu i umieszcza je w pliku PDB. Aby uzyskać więcej informacji, zobacz [-debugowania (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|`ErrorReport`|Opcjonalne `String` parametru.<br /><br /> Określa, jak zadanie powinno zgłosić wewnętrzne błędy kompilatora. Ten parametr może mieć następujące wartości:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Jeśli `prompt` określono i wystąpi błąd wewnętrzny kompilatora, użytkownik zostanie poproszony o możliwości czy wysyłać dane błędów do firmy Microsoft.<br /><br /> Jeśli `send` określono i wystąpi błąd wewnętrzny kompilatora, zadanie wysyła dane błędów do firmy Microsoft.<br /><br /> Wartość domyślna to `none`, które raporty błędów w danych wyjściowych tylko tekst.<br /><br /> Ten parametr odpowiada [- errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) przełącznika z *vbc.exe* kompilatora.|  
|`FileAlignment`|Opcjonalne `Int32` parametru.<br /><br /> Określa w bajtach, where były wyrównane w sekcjach pliku wyjściowego. Ten parametr może mieć następujące wartości:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Ten parametr odpowiada [- filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) przełącznika z *vbc.exe* kompilatora.|  
|`GenerateDocumentation`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, generuje informacje o dokumentacji i umieszcza je w pliku XML o nazwie pliku wykonywalnego lub biblioteki, który tworzy zadanie. Aby uzyskać więcej informacji, zobacz [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc).|  
|`Imports`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Importuje przestrzeni nazw z kolekcji określony element. Ten parametr odpowiada [-importuje](/dotnet/visual-basic/reference/command-line-compiler/imports) przełącznika z *vbc.exe* kompilatora.|  
|`KeyContainer`|Opcjonalne `String` parametru.<br /><br /> Określa nazwę kontenera kluczy kryptograficznych. Ten parametr odpowiada [- keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) przełącznika z *vbc.exe* kompilatora.|  
|`KeyFile`|Opcjonalne `String` parametru.<br /><br /> Określa nazwę pliku zawierającego klucz kryptograficzny. Aby uzyskać więcej informacji, zobacz [- keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile).|  
|`LangVersion`|Opcjonalne <xref:System.String?displayProperty=fullName> parametru.<br /><br /> Określa wersję języka, "9" lub "10".|  
|`LinkResources`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Tworzy łącze do zasobu .NET Framework w pliku wyjściowym; plik zasobu nie jest umieszczony w pliku wyjściowym. Ten parametr odpowiada [- linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) przełącznika z *vbc.exe* kompilatora.|  
|`MainEntryPoint`|Opcjonalne `String` parametru.<br /><br /> Określa klasę lub moduł, który zawiera `Sub Main` procedury. Ten parametr odpowiada [-głównym](/dotnet/visual-basic/reference/command-line-compiler/main) przełącznika z *vbc.exe* kompilatora.|  
|`ModuleAssemblyName`|Opcjonalne `String` parametru.<br /><br /> Określa zestaw, do którego należy ten moduł.|  
|`NoConfig`|Opcjonalne `Boolean` parametru.<br /><br /> Określa, że kompilator powinien używać *vbc.rsp* pliku. Ten parametr odpowiada [- noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) parametr *vbc.exe* kompilatora.|  
|`NoLogo`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, Pomija wyświetlanie informacji o transparentu kompilatora. Ten parametr odpowiada [- nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) przełącznika z *vbc.exe* kompilatora.|  
|`NoStandardLib`|Opcjonalne `Boolean` parametru.<br /><br /> Powoduje, że kompilator nie do standardowych bibliotek. Ten parametr odpowiada [- nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) przełącznika z *vbc.exe* kompilatora.|  
|`NoVBRuntimeReference`|Opcjonalne `Boolean` parametru.<br /><br /> Tylko do użytku wewnętrznego. Jeśli PRAWDA, uniemożliwia automatyczne odwołanie do pliku Microsoft.VisualBasic.dll...|  
|`NoWarnings`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie pomija wszystkie ostrzeżenia. Aby uzyskać więcej informacji, zobacz [- nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).|  
|`Optimize`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, włącza optymalizacje kompilatora. Ten parametr odpowiada [-zoptymalizować](/dotnet/visual-basic/reference/command-line-compiler/optimize) przełącznika z *vbc.exe* kompilatora.|  
|`OptionCompare`|Opcjonalne `String` parametru.<br /><br /> Określa, jak zostały wprowadzone porównywania ciągów. Ten parametr może mieć następujące wartości:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Wartość `binary` Określa, że zadanie używa porównania ciągu binarnego. Wartość `text` Określa, że zadanie używa porównania ciągów tekstu. Wartością domyślną tego parametru jest `binary`. Ten parametr odpowiada [- optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) przełącznika z *vbc.exe* kompilatora.|  
|`OptionExplicit`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, jawnej deklaracji zmiennych jest wymagana. Ten parametr odpowiada [- optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) przełącznika z *vbc.exe* kompilatora.|  
|`OptionInfer`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, pozwala na wnioskowanie typów zmiennych.|  
|`OptionStrict`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie wymusza ścisłe zasady semantyki ograniczyć niejawne konwersje typów. Ten parametr odpowiada [- optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) przełącznika z *vbc.exe* kompilatora.|  
|`OptionStrictType`|Opcjonalne `String` parametru.<br /><br /> Określa, które semantyki typu strict wygenerowanie ostrzeżenia. Aktualnie obsługiwana jest tylko "custom". Ten parametr odpowiada [- optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) przełącznika z *vbc.exe* kompilatora.|  
|`OutputAssembly`|Opcjonalne `String` parametru wyjściowego.<br /><br /> Określa nazwę pliku wyjściowego. Ten parametr odpowiada [-out](/dotnet/visual-basic/reference/command-line-compiler/out) przełącznika z *vbc.exe* kompilatora.|  
|`Platform`|Opcjonalne `String` parametru.<br /><br /> Określa platformę procesora, które ma zostać skonfigurowany przy użyciu pliku wyjściowego. Ten parametr może mieć wartość `x86`, `x64`, `Itanium`, lub `anycpu`. Wartość domyślna to `anycpu`. Ten parametr odpowiada [-platformy](/dotnet/visual-basic/reference/command-line-compiler/platform) przełącznika z *vbc.exe* kompilatora.|  
|`References`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Powoduje, że zadanie zaimportować informacje typu publicznego z określonych elementów do bieżącego projektu. Ten parametr odpowiada [— odwołanie](/dotnet/visual-basic/reference/command-line-compiler/reference) przełącznika z *vbc.exe* kompilatora.|  
|`RemoveIntegerChecks`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, wyłącza sprawdzanie błędów przepełnienie liczby całkowitej. Wartość domyślna to `false`. Ten parametr odpowiada [- removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) przełącznika z *vbc.exe* kompilatora.|  
|`Resources`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Osadza zasobu .NET Framework do pliku wyjściowego. Ten parametr odpowiada [-zasobów](/dotnet/visual-basic/reference/command-line-compiler/resource) przełącznika z *vbc.exe* kompilatora.|  
|`ResponseFiles`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa plik odpowiedzi, który zawiera polecenia dla tego zadania. Ten parametr odpowiada [@ (Określ plik odpowiedzi)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) opcji *vbc.exe* kompilatora.|  
|`RootNamespace`|Opcjonalne `String` parametru.<br /><br /> Określa przestrzeń nazw korzenia dla wszystkich deklaracji typów. Ten parametr odpowiada [- rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) przełącznika z *vbc.exe* kompilatora.|  
|`SdkPath`|Opcjonalne `String` parametru.<br /><br /> Określa lokalizację *mscorlib.dll* i *pliku microsoft.visualbasic.dll*. Ten parametr odpowiada [- sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) przełącznika z *vbc.exe* kompilatora.|  
|`Sources`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa co najmniej jeden plik źródłowy języka Visual Basic.|  
|`TargetCompactFramework`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, cele zadań [!INCLUDE[Compact](../extensibility/includes/compact_md.md)]. Ta opcja odnosi się do [- netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) przełącznika z *vbc.exe* kompilatora.|  
|`TargetType`|Opcjonalne `String` parametru.<br /><br /> Określa format pliku wyjściowego pliku. Ten parametr może mieć wartość `library`, która tworzy bibliotekę kodu `exe`, co powoduje aplikacji konsoli, `module`, który tworzy moduł, lub `winexe`, co powoduje programu dla systemu Windows. Wartość domyślna to `library`. Ten parametr odpowiada [-docelowy](/dotnet/visual-basic/reference/command-line-compiler/target) przełącznika z *vbc.exe* kompilatora.|  
|`Timeout`|Opcjonalne `Int32` parametru.<br /><br /> Określa ilość czasu, w milisekundach, po których plik wykonywalny zadania zostanie zakończony. Wartość domyślna to `Int.MaxValue`, wskazując, że to nie okres limitu czasu.|  
|`ToolPath`|Opcjonalne `String` parametru.<br /><br /> Określa lokalizację, z której zadanie zostanie załadowany podstawowy plik wykonywalny (*vbc.exe*). Jeśli ten parametr nie jest określony, zadanie użyje ścieżki instalacji zestawu SDK, odpowiadający wersji framework, na którym działa [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|`TreatWarningsAsErrors`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, wszystkie ostrzeżenia są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [- warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).|  
|`UseHostCompilerIfAvailable`|Opcjonalne `Boolean` parametru.<br /><br /> Powoduje, że zadania, użyj obiektu wewnątrzprocesowego kompilatora, jeśli jest dostępna. Wykorzystania tylko przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|`Utf8Output`|Opcjonalne `Boolean` parametru.<br /><br /> Rejestruje kompilatora, dane wyjściowe przy użyciu kodowania UTF-8. Ten parametr odpowiada [-utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) przełącznika z *vbc.exe* kompilatora.|  
|`Verbosity`|Opcjonalne `String` parametru.<br /><br /> Określa poziom szczegółowości danych wyjściowych kompilatora. Szczegółowość może być `Quiet`, `Normal` (ustawienie domyślne) lub `Verbose`.|  
|`WarningsAsErrors`|Opcjonalne `String` parametru.<br /><br /> Określa listę ostrzeżeń, które mają być traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [- warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Ten parametr zastępuje `TreatWarningsAsErrors` parametru.|  
|`WarningsNotAsErrors`|Opcjonalne `String` parametru.<br /><br /> Określa listę ostrzeżeń, które nie są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [- warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Ten parametr jest przydatna, jeśli `TreatWarningsAsErrors` ustawiono parametr `true`.|  
|`Win32Icon`|Opcjonalne `String` parametru.<br /><br /> Wstawia *.ico* pliku w zestawie, co daje pliku wyjściowego żądanego wyglądu w Eksploratorze plików. Ten parametr odpowiada [-win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) przełącznika z *vbc.exe* kompilatora.|  
|`Win32Resources`|Opcjonalne `String` parametru.<br /><br /> Wstawia zasobów Win32 (*.res*) plików w pliku wyjściowym. Ten parametr odpowiada [-win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) przełącznika z *vbc.exe* kompilatora.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.ToolTaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [tooltaskextension — klasa podstawowa](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy projekt Visual Basic.  
  
```xml  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Kompilator w wierszu polecenia programu Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
