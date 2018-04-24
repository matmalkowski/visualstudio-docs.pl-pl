---
title: Generateresource — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateResource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateResource task
- GenerateResource task [MSBuild]
ms.assetid: c0aff32f-f2cc-46f6-9c3e-a5c9f8f912b1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e26aae610407ceb1ebe050081f5b555d82badc92
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="generateresource-task"></a>GenerateResource — Zadanie
Wykonuje konwersję między txt i pliki resx (format zasobów opartych na języku XML) i wspólnego języka środowiska uruchomieniowego binarne .resources plików, które może być osadzony w pliku wykonywalnym na binarne środowiska uruchomieniowego lub skompilowany w zestawy satelickie. To zadanie służy zwykle do konwersji plików txt lub .resx .resource plików. `GenerateResource` Zadanie jest podobne do [resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `GenerateResource` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AdditionalInputs`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Zawiera dodatkowe dane wejściowe, aby sprawdzanie zależności wykonywane przez to zadanie. Na przykład plików projektów i elementów docelowych zazwyczaj powinno należeć wejść, dzięki czemu, jeśli zostaną zaktualizowane, wszystkie zasoby są generowane.|  
|`EnvironmentVariables`|Opcjonalne `String[]` parametru.<br /><br /> Określa tablicę pary nazwa wartość w środowisku zmiennych, które powinny zostać przekazane do uruchomionego resgen.exe, oprócz (lub selektywnie zastępowanie) blok środowiska regularne.|  
|`ExcludedInputPaths`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa tablicę elementów, które Określ ścieżki z których śledzonych wejścia zostaną zignorowane podczas sprawdzania aktualne.|  
|`ExecuteAsTool`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, uruchamia tlbimp.exe i aximp.exe z odpowiedniego docelowego framework poza procesem do generowania otoki niezbędne zestawy. Ten parametr umożliwia wielowersyjności z `ResolveComReferences`.|  
|`FilesWritten`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Zawiera nazwy wszystkich plików zapisywane na dysku. Jeśli w tym pliku pamięci podręcznej. Ten parametr jest przydatna do implementacji Oczyść.|  
|`MinimalRebuildFromTracking`|Opcjonalne `Boolean` parametru.<br /><br /> Pobiera lub ustawia przełącznik, który określa, czy będzie używana śledzonych kompilacji przyrostowej. Jeśli `true`, wzrostowe jest włączone; w przeciwnym razie zostanie wymuszone odbudowie.|  
|`NeverLockTypeAssemblies`|Opcjonalne `Boolean` parametru.<br /><br /> Pobiera lub ustawia wartość logiczna określająca, czy do tworzenia nowego [elementu AppDomain](/dotnet/api/system.appdomain) oceń pliki zasobów (resx) (true) lub Utwórz nową [elementu AppDomain](/dotnet/api/system.appdomain) tylko gdy pliki zasobów odwołują się użytkownika zestaw (false).|  
|`OutputResources`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Określa nazwę wygenerowanego plików, na przykład plików .resources. Jeśli nie określisz nazwy, używana jest nazwa pliku wejściowego dopasowywania i utworzony plik .resources znajduje się w katalogu, który zawiera plik wejściowy.|  
|`PublicClass`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, tworzy klasę zasobu o jednoznacznie jako klasa publiczna.|  
|`References`|Opcjonalne `String[]` parametru.<br /><br /> Odwołania można załadować typów w pliki resx. Elementy danych pliku ResX może mieć typu .NET. Podczas odczytywania pliku .resx to muszą zostać rozwiązane. Zazwyczaj problemu pomyślnie przy użyciu standardowej ładowania reguł. Jeśli podasz zestawów w `References`, ich pierwszeństwo.<br /><br /> Ten parametr nie jest wymagany dla jednoznacznie zasobów.|  
|`SdkToolsPath`|Opcjonalne `String` parametru.<br /><br /> Określa ścieżkę do narzędzia zestawu SDK, takich jak resgen.exe.|  
|`Sources`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa elementy do konwersji. Pozycji przekazanych do tego parametru musi mieć jedną z następujących rozszerzeń:<br /><br /> -   `.txt`: Określa rozszerzenie pliku tekstowego do konwersji. Pliki tekstowe może zawierać tylko zasoby ciągów.<br />-   `.resx`: Określa rozszerzenie pliku zasobów opartych na języku XML do konwersji.<br />-   `.restext`: Określa ten sam format jak .txt. To rozszerzenie innej jest przydatne, jeśli chcesz umożliwić łatwe rozróżnienie plików źródłowych, które zawierają zasoby z innych plików źródłowych w procesie kompilacji.<br />-   `.resources`: Określa rozszerzenie pliku zasobu do konwersji.|  
|`StateFile`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa ścieżkę do pliku opcjonalne pamięci podręcznej, który służy do przyspieszenia sprawdzania łączy pliki wejściowe .resx zależności.|  
|`StronglyTypedClassName`|Opcjonalne `String` parametru.<br /><br /> Określa nazwę klasy dla klasy zasobu o jednoznacznie. Jeśli ten parametr nie jest określony, używany jest podstawową nazwę pliku zasobu.|  
|`StronglyTypedFilename`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa nazwę pliku dla pliku źródłowego. Jeśli ten parametr nie jest określony, nazwa klasy jest używany jako podstawowej nazwy pliku z rozszerzeniem zależne od języka. Na przykład: `MyClass.cs`.|  
|`StronglyTypedLanguage`|Opcjonalne `String` parametru.<br /><br /> Określa język do użycia podczas generowania klasy źródła dla zasobu o jednoznacznie. Ten parametr musi odpowiadać dokładnie jeden z języków używanych przez CodeDomProvider. Na przykład: `VB` lub `C#`.<br /><br /> Przez przekazanie wartości do tego parametru, można nakazać zadań do generowania zasobów o jednoznacznie.|  
|`StronglyTypedManifestPrefix`|Opcjonalne `String` parametru.<br /><br /> Określa prefiks przestrzeni nazw lub manifest zasobu do użycia w źródle wygenerowanej klasy dla zasobu o jednoznacznie.|  
|`StronglyTypedNamespace`|Opcjonalne `String` parametru.<br /><br /> Określa przestrzeń nazw do użycia dla zasobu o jednoznacznie źródła wygenerowanej klasy. Jeśli ten parametr nie jest określony, wszystkie zasoby jednoznacznie znajdują się w globalnej przestrzeni nazw.|  
|`TLogReadFiles`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru tylko do odczytu.<br /><br /> Pobiera tablicę elementów, które reprezentują dzienniki śledzenia odczytów.|  
|`TLogWriteFiles`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru tylko do odczytu.<br /><br /> Pobiera tablicę elementów, które reprezentują zapisu dziennikach śledzenia.|  
|`ToolArchitecture`|Opcjonalne <xref:System.String?displayProperty=fullName> parametru.<br /><br /> Używany do określenia, czy Tracker.exe musi zostać użyte do zduplikować ResGen.exe.<br /><br /> Powinien być można przeanalizować do elementu członkowskiego <xref:Microsoft.Build.Utilities.ExecutableType> wyliczenia. Jeśli `String.Empty`, używa heurystyki w celu określenia architektura domyślne. Powinien być można przeanalizować do elementu członkowskiego wyliczenia Microsoft.Build.Utilities.ExecutableType.|  
|`TrackerFrameworkPath`|Opcjonalne `String` parametru.<br /><br /> Określa ścieżkę do odpowiedniej lokalizacji .NET Framework, który zawiera FileTracker.dll.<br /><br /> Jeśli zestawu, które użytkownik ma odpowiedzialność za zapewnienie, że liczba bitów FileTracker.dll, które przekazują odpowiada bitowości ResGen.exe które będą one używane. Jeśli nie zestawu, zadanie decyduje o odpowiednią lokalizację, w oparciu o bieżącą wersję systemu .NET Framework.|  
|`TrackerLogDirectory`|Opcjonalne `String` parametru.<br /><br /> Określa katalog pośredni, w której zostaną umieszczone w dziennikach śledzenia uruchomienie tego zadania.|  
|`TrackerSdkPath`|Opcjonalne `String` parametru.<br /><br /> Określa ścieżkę w odpowiedniej lokalizacji zestawu Windows SDK, który zawiera Tracker.exe.<br /><br /> Jeśli zestawu, które użytkownik ma odpowiedzialność za zapewnienie, że liczba bitów Tracker.exe które przechodzą odpowiada bitowości ResGen.exe które będą one używane. Jeśli nie zestawu, zadanie decyduje o odpowiednią lokalizację, w oparciu o bieżący zestaw Windows SDK.|  
|`TrackFileAccess`|Opcjonalne <xref:System.Boolean> parametru.<br /><br /> Jeśli PRAWDA, katalog pliku wejściowego służy do rozpoznawania względne ścieżki do pliku.|  
|`UseSourcePath`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, określa, że plik wejściowy katalog służący do rozpoznawania względne ścieżki do pliku.|  
  
## <a name="remarks"></a>Uwagi  
 Pliki .resx może zawierać łącza do innych plików zasobów, nie jest wystarczająca do porównania po prostu .resx i .resource sygnatury czasowe plików do sprawdzenia, czy dane wyjściowe są aktualne. Zamiast tego `GenerateResource` zadań wykonał linki w pliku .resx ale sprawdza znacznikami czasu plików połączonych. Oznacza to, że nie należy zwykle używać `Inputs` i `Outputs` atrybuty zawierające docelowej `GenerateResource` zadań, ponieważ może to spowodować, aby był pomijany podczas faktycznie powinno być uruchamiane.  
  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
 Za pomocą programu MSBuild 4.0 projektów docelowych .NET 3.5, kompilacja może zakończyć się niepowodzeniem na x86 zasobów. Aby obejść ten problem, można utworzyć obiektu docelowego zestawu AnyCPU.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `GenerateResource` zadań na wygenerowanie plików .resources z plików określone przez `Resx` Kolekcja elementów.  
  
```xml  
<GenerateResource  
    Sources="@(Resx)"  
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">  
    <Output  
        TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
 `GenerateResource` Zadań używa \<LogicalName > Metadane \<EmbeddedResource > element, aby nazwa zasobu, który jest osadzony w zestawie.  
  
 Przy założeniu, że zestaw jest nazwane myAssembly, poniższy kod generuje osadzony zasób o nazwie someQualifier.someResource.resources:  
  
```xml  
<ItemGroup>   <EmbeddedResource Include="myResource.resx">       <LogicalName>someQualifier.someResource.resources</LogicalName>   </EmbeddedResource></ItemGroup>  
```  
  
 Bez \<LogicalName > metadanych, zasobu będą miały postać myAssembly.myResource.resources.  Ten przykład dotyczy tylko dla procesu kompilacji Visual Basic i Visual C#.  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
