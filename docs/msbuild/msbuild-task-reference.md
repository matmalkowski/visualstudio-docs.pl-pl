---
title: Odwołanie do zadania MSBuild | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
caps.latest.revision: 32
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1d3bd0cb011dd99183e3d7318693261e19e01791
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="msbuild-task-reference"></a>Odwołanie do zadania MSBuild
Zadania Podaj kod uruchamiany podczas procesu kompilacji. Zadania na poniższej liście uwzględniono z [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Gdy [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] jest zainstalowany, dodatkowe zadania są dostępne, które są używane do tworzenia [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projektów. Aby uzyskać więcej informacji, zobacz [zadania w programie Visual C++](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).  
  
 Oprócz parametrów wymienionych w tematach w tej sekcji każde zadanie ma następujące parametry:  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Condition`|Opcjonalne `String` parametru.<br /><br /> A `Boolean` wyrażenie który [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] aparat używa w celu określenia, czy będzie można wykonać tego zadania. Aby uzyskać informacje o warunkach, które są obsługiwane przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], zobacz [warunki](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Parametr opcjonalny. Może zawierać jedną z następujących wartości:<br /><br /> -   **WarnAndContinue** lub **true**. Jeśli zadanie nie powiedzie się, kolejne zadania w [docelowej](../msbuild/target-element-msbuild.md) element i kompilacji, nadal można wykonać, a wszystkie błędy z zadania są traktowane jako ostrzeżenia.<br />-   **ErrorAndContinue**. Jeśli zadanie nie powiedzie się, kolejne zadania w `Target` element i kompilacji, nadal można wykonać, a wszystkie błędy z zadania są traktowane jako błędy.<br />-   **ErrorAndStop** lub **false** (ustawienie domyślne). Jeśli zadanie nie powiedzie się, kolejnych zadań na `Target` element i kompilacji nie są wykonywane i całą `Target` element i kompilacji jest traktowane jako powiodła się.<br /><br /> Wersje programu .NET Framework, przed 4.5 obsługiwane tylko `true` i `false` wartości.<br /><br /> Aby uzyskać więcej informacji, zobacz [porady: ignorowanie błędów w zadaniach](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Klasa podstawowa zadania](../msbuild/task-base-class.md)  
 Dodaje kilka parametrów do zadań, które pochodzą z <xref:Microsoft.Build.Utilities.Task> klasy.  
  
 [TaskExtension, klasa podstawowa](../msbuild/taskextension-base-class.md)  
 Dodaje kilka parametrów do zadań, które pochodzą z <xref:Microsoft.Build.Tasks.TaskExtension> klasy.  
  
 [ToolTaskExtension, klasa podstawowa](../msbuild/tooltaskextension-base-class.md)  
 Dodaje kilka parametrów do zadań, które pochodzą z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy.  
  
 [AL (Assembly Linker), zadanie](../msbuild/al-assembly-linker-task.md)  
 Tworzy zestaw z manifestu z jednego lub więcej plików, które moduły albo lub plików zasobów.  
  
 [AspNetCompiler, zadanie](../msbuild/aspnetcompiler-task.md)  
 Wraps aspnet_compiler.exe, a utility to precompile ASP.NET applications.  
  
 [AssignCulture, zadanie](../msbuild/assignculture-task.md)  
 Przypisuje kultury identyfikatory elementów.  
  
 [AssignProjectConfiguration, zadanie](../msbuild/assignprojectconfiguration-task.md)  
 Akceptuje listy ciągów konfiguracji i przypisuje je do określonych projektów.  
  
 [AssignTargetPath, zadanie](../msbuild/assigntargetpath-task.md)  
 Akceptuje listę plików i dodaje `<TargetPath>` atrybuty, jeśli nie są już określony.  
  
 [CallTarget, zadanie](../msbuild/calltarget-task.md)  
 Wywołuje element docelowy w pliku projektu.  
  
 [CombinePath, zadanie](../msbuild/combinepath-task.md)  
 Scala określonych ścieżek w pojedynczą ścieżkę.  
  
 [ConvertToAbsolutePath, zadanie](../msbuild/converttoabsolutepath-task.md)  
 Konwertuje ścieżką bezwzględną ścieżkę względną lub odwołanie.  
  
 [Copy, zadanie](../msbuild/copy-task.md)  
 Kopiuje pliki do nowej lokalizacji.  
  
 [CreateCSharpManifestResourceName, zadanie](../msbuild/createcsharpmanifestresourcename-task.md)  
 Tworzy [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]— styl nazwy manifestu z nazwę pliku .resx danego lub innego zasobu.  
  
 [CreateItem, zadanie](../msbuild/createitem-task.md)  
 Wypełnia kolekcji elementów z elementów wejściowych, umożliwiając elementów do skopiowania z listy jeden do innego.  
  
 [CreateProperty, zadanie](../msbuild/createproperty-task.md)  
 Wypełnia właściwości z wartości wejściowe, umożliwiając wartości do skopiowania z jedną właściwość lub ciągu na inny.  
  
 [CreateVisualBasicManifestResourceName, zadanie](../msbuild/createvisualbasicmanifestresourcename-task.md)  
 Tworzy [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]— styl nazwy manifestu z nazwę pliku .resx danego lub innego zasobu.  
  
 [Csc, zadanie](../msbuild/csc-task.md)  
 Wywołuje kompilatora Visual C# do tworzenia plików wykonywalnych, biblioteki DLL lub moduły kodu.  
  
 [Delete, zadanie](../msbuild/delete-task.md)  
 Usuwa określone pliki.  
  
 [Error, zadanie](../msbuild/error-task.md)  
 Zatrzymuje kompilację i rejestruje błąd oparte na obliczane instrukcji warunkowej.  
  
 [Exec, zadanie](../msbuild/exec-task.md)  
 Uruchamia określony program lub poleceń z określonymi argumentami.  
  
 [FindAppConfigFile, zadanie](../msbuild/findappconfigfile-task.md)  
 Umożliwia znalezienie pliku app.config, w podanych list.  
  
 [FindInList, zadanie](../msbuild/findinlist-task.md)  
 Odnajduje element w określonej listy, która ma pasującego specyfikacja_elementu.  
  
 [FindUnderPath, zadanie](../msbuild/findunderpath-task.md)  
 Określa, które elementy w kolekcji określony element istnieje w określonym folderze i wszystkie jego podfoldery.  
  
 [FormatUrl, zadanie](../msbuild/formaturl-task.md)  
 Konwertuje adres URL poprawny format adresu URL.  
  
 [FormatVersion, zadanie](../msbuild/formatversion-task.md)  
 Dołącza numer poprawki numer wersji.  
  
 [GenerateApplicationManifest, zadanie](../msbuild/generateapplicationmanifest-task.md)  
 Generuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji lub natywny manifest.  
  
 [GenerateBootstrapper, zadanie](../msbuild/generatebootstrapper-task.md)  
 Umożliwia automatyczne wykrywanie, pobieranie i instalowanie aplikacji i jego wymagań wstępnych.  
  
 [GenerateDeploymentManifest, zadanie](../msbuild/generatedeploymentmanifest-task.md)  
 Generuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest wdrażania.  
  
 [GenerateResource, zadanie](../msbuild/generateresource-task.md)  
 Konwertuje pliki txt i .resx wspólne pliki binarne .resources środowiska uruchomieniowego języka.  
  
 [GenerateTrustInfo, zadanie](../msbuild/generatetrustinfo-task.md)  
 Generuje zaufanie aplikacji w manifeście podstawowej i z `TargetZone` i `ExcludedPermissions` parametrów.  
  
 [GetAssemblyIdentity, zadanie](../msbuild/getassemblyidentity-task.md)  
 Pobiera tożsamości zestawu z określonych plików i wyświetla informacje o tożsamości.  
  
 [GetFrameworkPath, zadanie](../msbuild/getframeworkpath-task.md)  
 Pobiera ścieżkę do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zestawów.  
  
 [GetFrameworkSdkPath, zadanie](../msbuild/getframeworksdkpath-task.md)  
 Pobiera ścieżkę do [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  
  
 [GetReferenceAssemblyPaths, zadanie](../msbuild/getreferenceassemblypaths-task.md)  
 Zwraca odwołanie ścieżki zestawu z różnych platform.  
  
 [LC, zadanie](../msbuild/lc-task.md)  
 Generuje plik .license z .licx — plik.  
  
 [MakeDir, zadanie](../msbuild/makedir-task.md)  
 Tworzy katalogi i w razie potrzeby dominujące katalogów.  
  
 [Message, zadanie](../msbuild/message-task.md)  
 Rejestruje komunikat podczas kompilacji.  
  
 [Move, zadanie](../msbuild/move-task.md)  
 Przenosi pliki do nowej lokalizacji.  
  
 [MSBuild, zadanie](../msbuild/msbuild-task.md)  
 Tworzy [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektów z innego [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektu.  
  
 [ReadLinesFromFile, zadanie](../msbuild/readlinesfromfile-task.md)  
 Odczytuje listę elementów z pliku tekstowego.  
  
 [RegisterAssembly, zadanie](../msbuild/registerassembly-task.md)  
 Odczytuje metadanych w określonym zestawie i dodaje niezbędne wpisy do rejestru.  
  
 [RemoveDir, zadanie](../msbuild/removedir-task.md)  
 Usuwa określone katalogi i wszystkie jego pliki i podkatalogi.  
  
 [RemoveDuplicates, zadanie](../msbuild/removeduplicates-task.md)  
 Usuwa zduplikowane elementy z kolekcji określony element.  
  
 [RequiresFramework35SP1Assembly, zadanie](../msbuild/requiresframework35sp1assembly-task.md)  
 Określa, czy aplikacja wymaga platformy .NET Framework 3.5 SP1.  
  
 Zadanie ResGen  
 Nieaktualne. Użyj [generateresource — zadanie](../msbuild/generateresource-task.md) zadań na konwertowanie plików txt i .resx wspólne pliki binarne .resources środowiska uruchomieniowego języka.  
  
 [ResolveAssemblyReference, zadanie](../msbuild/resolveassemblyreference-task.md)  
 Określa wszystkie zestawy, które są zależne od określonych zestawów.  
  
 [ResolveCOMReference, zadanie](../msbuild/resolvecomreference-task.md)  
 Przyjmuje listę nazw bibliotek typu lub .tlb — pliki i usuwa te biblioteki typów do lokalizacji na dysku.  
  
 [ResolveKeySource, zadanie](../msbuild/resolvekeysource-task.md)  
 Określa źródło klucza silnej nazwy  
  
 [ResolveManifestFiles, zadanie](../msbuild/resolvemanifestfiles-task.md)  
 Rozpoznaje następujących elementów w procesie kompilacji do plików do generowania manifestu: wbudowane elementy, zależności satelity, zawartość, symbole debugowania i dokumentacji.  
  
 [ResolveNativeReference, zadanie](../msbuild/resolvenativereference-task.md)  
 Usuwa odwołania natywnego.  
  
 [ResolveNonMSBuildProjectOutput, zadanie](../msbuild/resolvenonmsbuildprojectoutput-task.md)  
 Określa pliki wyjściowe dla innych niż MSBuild odwołania do projektu.  
  
 [SGen, zadanie](../msbuild/sgen-task.md)  
 Tworzy zestaw serializacji XML dla typów w określonym zestawie.  
  
 [SignFile, zadanie](../msbuild/signfile-task.md)  
 Rejestruje określony plik przy użyciu określonego certyfikatu.  
  
 [Touch, zadanie](../msbuild/touch-task.md)  
 Ustawia czas dostępu i modyfikacji plików.  
  
 [UnregisterAssembly, zadanie](../msbuild/unregisterassembly-task.md)  
 Wyrejestrowuje określonych zestawów do COM interop celów.  
  
 [UpdateManifest, zadanie](../msbuild/updatemanifest-task.md)  
 Aktualizuje wybrane właściwości w manifeście i poddały.  
  
 [Vbc, zadanie](../msbuild/vbc-task.md)  
 Wywołuje kompilator Visual Basic, aby utworzyć pliki wykonywalne, biblioteki DLL lub moduły kodu...  
  
 [Warning, zadanie](../msbuild/warning-task.md)  
 Dzienniki ostrzeżenie podczas kompilacji w oparciu obliczane instrukcji warunkowej.  
  
 [WriteCodeFragment, zadanie](../msbuild/writecodefragment-task.md)  
 Generuje plik tymczasowy kod za pomocą fragmentu określonego wygenerowanego kodu. Nie powoduje usunięcia pliku.  
  
 [WriteLinesToFile, zadanie](../msbuild/writelinestofile-task.md)  
 Zapisuje określone elementy do określonego pliku.  
  
 [XmlPeek, zadanie](../msbuild/xmlpeek-task.md)  
 Zwraca wartości określonych przez zapytanie XPath z pliku XML.  
  
 [XmlPoke, zadanie](../msbuild/xmlpoke-task.md)  
 Ustawia wartości określonych przez zapytanie XPath do pliku XML.  
  
 [XslTransformation, zadanie](../msbuild/xsltransformation-task.md)  
 Przekształca dane wejściowe XML przy użyciu *Extensible transformacji języka arkusza stylów* (XSLT) lub skompilowany XSLT i dane wyjściowe do urządzenia wyjściowego lub pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)   
 [Wpisywanie zadania](../msbuild/task-writing.md)   
 [Zadania](../msbuild/msbuild-tasks.md)