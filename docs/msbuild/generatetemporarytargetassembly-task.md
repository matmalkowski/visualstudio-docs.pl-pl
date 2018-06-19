---
title: Generatetemporarytargetassembly — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- build process [WPF MSBuild], XAML page refers to a locally declared type
- GenerateTemporaryTargetAssembly task [WPF MSBuild]
- GenerateTemporaryTargetAssembly task [WPF MSBuild], parameters
- creating an assembly [WPF MSBuild], XAML page refers to a locally declared type
ms.assetid: 92b6539c-6897-45e0-8989-0c234bbfe782
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: efaeed873630113382630421258338e6624e14ee
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31578549"
---
# <a name="generatetemporarytargetassembly-task"></a>GenerateTemporaryTargetAssembly — Zadanie
<xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> Zadań generuje zestawu, jeśli co najmniej jeden [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] strony w projekcie odwołuje się do typu, która jest zadeklarowana jako lokalnie w tym projekcie. Wygenerowanym zestawie zostaną usunięte po ukończeniu procesu kompilacji, czy Proces kompilacji nie powiedzie się.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AssemblyName`|Wymagane **ciąg** parametru.<br /><br /> Określa krótką nazwę zestawu, który został wygenerowany dla projektu i jest również nazwa zestawu docelowego, który tymczasowo zostanie wygenerowany. Na przykład, jeśli projekt generuje [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] plik wykonywalny, którego nazwa jest **WinExeAssembly.exe**, **AssemblyName** parametr ma wartość **WinExeAssembly**.|  
|`CompileTargetName`|Wymagane **ciąg** parametru.<br /><br /> Określa nazwę [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] docelowego, który służy do generowania zestawy z plików kodu źródłowego. Typowa wartość dla **CompileTargetName** jest **CoreCompile**.|  
|`CompileTypeName`|Wymagane **ciąg** parametru.<br /><br /> Określa typ kompilacji jest wykonywane przez element docelowy, który jest określony przez **CompileTargetName** parametru. Aby uzyskać **CoreCompile** docelowej, ta wartość jest **skompilować**.|  
|`CurrentProject`|Wymagane **ciąg** parametru.<br /><br /> Określa pełną ścieżkę [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] pliku projektu, który wymaga zestawu docelowego tymczasowej.|  
|`GeneratedCodeFiles`|Opcjonalne **[ITaskItem]** parametru.<br /><br /> Określa listę plików specyficzny dla języka kodu zarządzanego, które zostały wygenerowane przez [markupcompilepass1 —](../msbuild/markupcompilepass1-task.md) zadań.|  
|`IntermediateOutputPath`|Wymagane **ciąg** parametru.<br /><br /> Określa katalog wygenerowanego zestawu docelowego tymczasowej.|  
|`MSBuildBinPath`|Wymagane **ciąg** parametru.<br /><br /> Określa lokalizację **MSBuild.exe**, który jest wymagany do kompilacji zestawu docelowego tymczasowej.|  
|`ReferencePath`|Opcjonalne **[ITaskItem]** parametru.<br /><br /> Określa listę zestawów, ścieżka i nazwa pliku, do których odwołuje się według typów, które są kompilowane w zestawie docelowym tymczasowego.|  
|`ReferencePathTypeName`|Wymagane **ciąg** parametru.<br /><br /> Określa parametr, który jest używany przez element docelowy kompilacji (**CompileTargetName**) parametr, który określa listę odwołań do zestawu (**ReferencePath**). Odpowiednia wartość jest **ReferencePath**.|  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy przebiegu kompilacji znaczników, które jest uruchomione przez [markupcompilepass1 —](../msbuild/markupcompilepass1-task.md), kompiluje [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plików na format binarny. W związku z tym, kompilator musi listę zestawów występujących w odwołaniach zawierające typy używane przez [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plików. Jednak jeśli [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliku korzysta z typu, który jest zdefiniowany w tym samym projekcie, odpowiedniego zestawu dla tego projektu jest tworzone dopiero po utworzeniu projektu. W związku z tym odwołania do zestawu nie można podać podczas przebiegu pierwszej kompilacji znaczników.  
  
 Zamiast tego **markupcompilepass1 —** różni się konwersję [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] przekazać pliki, które zawierają odwołania do typów w tym samym projekcie do drugiego kompilację znaczników, który jest wykonywany przez [markupcompilepass2 —](../msbuild/markupcompilepass2-task.md). Przed **markupcompilepass2 —** jest wykonywane, tymczasowego zestawu jest generowany. Ten zestaw zawiera typy, które są używane przez [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliki, których przebiegu kompilacji znaczników została odroczona. Odwołanie do wygenerowanego zestawu został dostarczony do **markupcompilepass2 —** po uruchomieniu umożliwia odroczonego kompilacji [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliki, które ma zostać przekonwertowane na format binarny.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje tymczasowego zestawu, ponieważ `Page1.xaml` zawiera odwołanie do typu, który znajduje się w tym samym projekcie.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask  
    TaskName="Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GenerateTemporaryTargetAssemblyTask">  
    <GenerateTemporaryTargetAssembly  
      AssemblyName="WPFMSBuildSample"  
      CompileTargetName="CoreCompile"  
      CompileTypeName="Compile"  
      CurrentProject="FullBuild.proj"  
      GeneratedCodeFiles="obj\debug\app.g.cs;obj\debug\Page1.g.cs;obj\debug\Page2.g.cs"  
      ReferencePath="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll"  
      IntermediateOutputPath=".\obj\debug\"  
      MSBuildBinPath="$(MSBuildBinPath)"  
      ReferencePathTypeName="ReferencePath"/>  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)   
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)   
 [Aplikacje przeglądarek WPF XAML — omówienie](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)