---
title: "MSBuild zarezerwowane i dobrze znane właściwości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords: MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
caps.latest.revision: "29"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 2edee236382b15c8f623acd1f4a650ef9628dd68
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Właściwości MSBuild zarezerwowane i dobrze znane
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]udostępnia zestaw wstępnie zdefiniowanych właściwości, które zawierają informacje o pliku projektu i [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] plików binarnych. Te właściwości są oceniane w taki sam sposób jak inne [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] właściwości. Na przykład, aby użyć `MSBuildProjectFile` właściwości, wpisz `$(MSBuildProjectFile)`.  
  
 Program MSBuild używa wartości w poniższej tabeli można wstępnie właściwości zarezerwowane i dobrze znane. Nie można zastąpić właściwości zastrzeżone, ale może zostać przesłonięta dobrze znanych właściwości za pomocą właściwości środowiska o identycznej nazwie, globalnych właściwości lub właściwości, które są zadeklarowane w pliku projektu.  
  
## <a name="reserved-and-well-known-properties"></a>Właściwości zarezerwowane i dobrze znane  
 W poniższej tabeli opisano [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wstępnie zdefiniowanych właściwości.  
  
|Właściwość|Opis|Zarezerwowane i dobrze znane|  
|--------------|-----------------|-----------------------------|  
|`MSBuildBinPath`|Bezwzględna ścieżka folderu gdzie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zlokalizowane są pliki binarne, które są aktualnie używane (na przykład C:\Windows\Microsoft.Net\Framework\\*Numerwersji*). Ta właściwość jest przydatna, jeśli do odwoływania się do plików w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] katalogu.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości.|Zastrzeżone|  
|`MSBuildExtensionsPath`|Wprowadzone w .NET Framework 4: nie ma żadnej różnicy między wartościami domyślnymi `MSBuildExtensionsPath` i `MSBuildExtensionsPath32`. Można ustawić zmiennej środowiskowej `MSBUILDLEGACYEXTENSIONSPATH` na wartość inną niż null umożliwia zachowanie domyślne wartości `MSBuildExtensionsPath` we wcześniejszych wersjach.<br /><br /> W programie .NET Framework 3.5 i starszych wersjach wartość domyślna `MSBuildExtensionsPath` wskazuje ścieżkę MSBuild podfolderze folderu plików (x86) \Program Files\ lub \Program, w zależności od wartości bitowości bieżącego procesu. Na przykład dla procesu 32-bitowych na komputerze 64-bitowym, ta właściwość wskazuje folderze \Program Files (x86). Dla procesu 64-bitowego na komputerze 64-bitowym ta właściwość wskazuje folderze \Program Files.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości.<br /><br /> Ta lokalizacja jest przydatne miejsce do umieszczania pliki docelowe niestandardowych. Na przykład pliki docelowych można zainstalowane w \Program Files\MSBuild\MyFiles\Northwind.targets i następnie zaimportować w plikach projektu przy użyciu tego kodu XML:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>`|Dobrze znane|  
|`MSBuildExtensionsPath32`|Ścieżka [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] podfolderze \Program Files lub folderu plików (x86) \Program. To zawsze ścieżkę do folderu \Program 32-bitowe pliki na maszynie 32-bitowe i \Program pliki (x86) na komputerze 64-bitowych. Zobacz też `MSBuildExtensionsPath` i `MSBuildExtensionsPath64`.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości.|Dobrze znane|  
`MSBuildExtensionsPath64`|Ścieżka [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] podfolderu w folderze \Program Files. Dla komputera 64-bitowego to zawsze ścieżkę do folderu \Program Files. Dla komputera 32-bitowego ta ścieżka jest pusta. Zobacz też `MSBuildExtensionsPath` i `MSBuildExtensionsPath32`.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości.|Dobrze znane|  
|`MSBuildLastTaskResult`|`true`Jeśli poprzednie zadanie zakończyło się bez żadnych błędów (nawet jeśli wystąpiły ostrzeżenia) lub `false` Jeśli poprzednie zadanie wystąpiły błędy. Zazwyczaj po wystąpieniu błędu w zadaniu, kod błędu to ostateczność w tym projekcie. W związku z tym wartość tej właściwości nie jest nigdy nie `false`, z wyjątkiem w następujących scenariuszach:<br /><br /> -Gdy `ContinueOnError` atrybutu [Task — Element (MSBuild)](../msbuild/task-element-msbuild.md) ustawiono `WarnAndContinue` (lub `true`) lub `ErrorAndContinue`.<br /><br /> -Gdy `Target` ma [OnError — Element (MSBuild)](../msbuild/onerror-element-msbuild.md) jako element podrzędny.|Zastrzeżone|  
|`MSBuildNodeCount`|Maksymalna liczba równoczesnych procesów, które są używane podczas kompilowania. Jest to wartość określona dla **/maxcpucount** w wierszu polecenia. Jeśli określono **/maxcpucount** bez określenia wartości, następnie `MSBuildNodeCount` określa liczbę procesorów w komputerze. Aby uzyskać więcej informacji, zobacz [dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md) i [tworzenie wielu projektów równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).|Zastrzeżone|  
|`MSBuildProgramFiles32`|Lokalizacja folderu program 32-bitowy; na przykład `C:\Program Files (x86)`.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości.|Zastrzeżone|  
|`MSBuildProjectDefaultTargets`|Pełna lista elementów docelowych, które są określone w `DefaultTargets` atrybutu `Project` elementu. Na przykład następująca `Project` byłyby element `MSBuildDefaultTargets` wartość właściwości `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >`|Zastrzeżone|  
|`MSBuildProjectDirectory`|Bezwzględna ścieżka katalogu zawierającego plik projektu, na przykład `C:\MyCompany\MyProduct`.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości.|Zastrzeżone|  
|`MSBuildProjectDirectoryNoRoot`|Wartość `MSBuildProjectDirectory` właściwości, z wyłączeniem katalog główny dysku.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości.|Zastrzeżone|  
|`MSBuildProjectExtension`|Rozszerzenie nazwy pliku z pliku projektu, w tym okresie; na przykład .proj.|Zastrzeżone|  
|`MSBuildProjectFile`|Pełną nazwę pliku projektu, łącznie z rozszerzeniem nazwy pliku; na przykład MyApp.proj.|Zastrzeżone|  
|`MSBuildProjectFullPath`|Ścieżka bezwzględna i Pełna nazwa pliku projektu, łącznie z rozszerzeniem nazwy pliku; na przykład C:\MyCompany\MyProduct\MyApp.proj.|Zastrzeżone|  
|`MSBuildProjectName`|Nazwa pliku bez rozszerzenia nazwy pliku; plik projektu na przykład moja_aplikacja.|Zastrzeżone|  
|`MSBuildRuntimeType`|Typ środowiska uruchomieniowego, który jest aktualnie wykonywany. Wprowadzono w programie MSBuild 15. Wartość może być Niezdefiniowany (przed MSBuild 15) `Full` wskazujący, że MSBuild działa w programie .NET Framework pulpitu, `Core` wskazujący, że program MSBuild działa na .NET Core lub `Mono` wskazujący, że program MSBuild działa na Mono.|Zastrzeżone|  
|`MSBuildStartupDirectory`|Bezwzględna ścieżka folderu gdzie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] jest wywoływana. Przy użyciu tej właściwości, można tworzyć wszystko poniżej określonego punktu w drzewie projektu bez tworzenia plików dirs.proj w każdym katalogu. Zamiast tego należy mieć tylko jeden projekt — na przykład c:\traversal.proj, jak pokazano poniżej:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Aby utworzyć w dowolnym momencie w drzewie, wpisz:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości.|Zastrzeżone|  
|`MSBuildThisFile`|Nazwa pliku i rozszerzenie pliku części `MSBuildThisFileFullPath`.|Zastrzeżone|  
|`MSBuildThisFileDirectory`|Część katalogu `MSBuildThisFileFullPath`.<br /><br /> Zawierać końcowego ukośnika w ścieżce.|Zastrzeżone|  
|`MSBuildThisFileDirectoryNoRoot`|Część katalogu `MSBuildThisFileFullPath`, z wyłączeniem katalog główny dysku.<br /><br /> Zawierać końcowego ukośnika w ścieżce.|Zastrzeżone|  
|`MSBuildThisFileExtension`|Nazwa rozszerzenia część plików `MSBuildThisFileFullPath`.|Zastrzeżone|  
|`MSBuildThisFileFullPath`|Bezwzględna ścieżka pliku projektu lub miejsc docelowych, który zawiera element docelowy z systemem.<br /><br /> Porada: Można określić ścieżkę względną w pliku elementów docelowych, które jest względną do pliku elementy docelowe, a nie względem oryginalnego pliku projektu.|Zastrzeżone|  
|`MSBuildThisFileName`|Nazwa pliku część `MSBuildThisFileFullPath`, bez rozszerzenia nazwy pliku.|Zastrzeżone|  
|`MSBuildToolsPath`|Ścieżka instalacji [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wersji, który został skojarzony z wartością `MSBuildToolsVersion`.<br /><br /> Nie dołączaj końcowego ukośnika w ścieżce.<br /><br /> Ta właściwość nie może zostać zastąpiona.|Zastrzeżone|  
|`MSBuildToolsVersion`|Wersja [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zestawu narzędzi, który jest używany do tworzenia projektu.<br /><br /> Uwaga: [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zestawu narzędzi składa się z zadań, elementy docelowe i narzędzi, które są używane do tworzenia aplikacji. Narzędzia te zawierają kompilatory, takie jak csc.exe i vbc.exe. Aby uzyskać więcej informacji, zobacz [zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), i [standardowe i niestandardowe konfiguracje zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md).|Zastrzeżone|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md) [właściwości programu MSBuild](../msbuild/msbuild-properties.md)