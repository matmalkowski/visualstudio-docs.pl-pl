---
title: Markupcompilepass2 — zadanie | Dokumentacja firmy Microsoft
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
- performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task
- MarkupCompilePass2 task [WPF MSBuild]
- MarkupCompilePass2 task [WPF MSBuild], parameters
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9b275a26da94e2d22bd3b347e7671b9fb3f3f333
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 — Zadanie

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> Zadania wykonuje oznaczenia w drugim przebiegu kompilacji na [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] pliki, które odwołują się do typów w tym samym projekcie.

## <a name="task-parameters"></a>Parametry zadania

|Parametr|Opis|
|---------------|-----------------|
|`AlwaysCompileMarkupFilesInSeparateDomain`|Opcjonalne **logiczna** parametru.<br /><br /> Określa, czy można uruchomić zadania w oddzielnej <xref:System.AppDomain>. Jeśli ten parametr zwraca **false**, to zadanie jest uruchamiane w tym samym <xref:System.AppDomain> jako [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)], i szybciej. Jeśli parametr zwraca **true**, to zadanie jest uruchamiane na sekundę <xref:System.AppDomain> jest odizolowana od [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] i działa wolniej.|
|`AssembliesGeneratedDuringBuild`|Opcjonalne **String []** parametru.<br /><br /> Określa odwołania do zestawów, które zmieniają się podczas procesu kompilacji. Na przykład rozwiązanie Visual Studio może zawierać jeden projekt, który odwołuje się do skompilowanych danych wyjściowych z innego projektu. W takim przypadku można dodać skompilowanych danych wyjściowych projektu drugi do **AssembliesGeneratedDuringBuild**.<br /><br /> Uwaga: **AssembliesGeneratedDuringBuild** mogą zawierać odwołań do pełnego zestawu zestawy, które są generowane przez rozwiązanie do kompilacji.|
|`AssemblyName`|Wymagane **ciąg** parametru.<br /><br /> Określa krótką nazwę zestawu, który jest generowany dla projektu. Na przykład, jeśli projekt jest generowanie [!INCLUDE[TLA#tla_win](../msbuild/includes/tlasharptla_win_md.md)] plik wykonywalny, którego nazwa jest **WinExeAssembly.exe**, **AssemblyName** parametr ma wartość **WinExeAssembly**.|
|`GeneratedBaml`|Opcjonalne **[ITaskItem]** parametru wyjściowego.<br /><br /> Zawiera listę plików wygenerowanych w [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] format binarny.|
|`KnownReferencePaths`|Opcjonalne **String []** parametru.<br /><br /> Określa odwołania do zestawów, które nigdy nie są zmieniane podczas procesu kompilacji. Zawiera zestawy, które znajdują się w [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)]w [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] katalogu instalacyjnego i tak dalej.|
|`Language`|Wymagane **ciąg** parametru.<br /><br /> Określa język zarządzanych, który obsługuje kompilatora. Prawidłowe opcje to **C#**, **VB**, **JScript**, i **C++**.|
|`LocalizationDirectivesToLocFile`|Opcjonalne **ciąg** parametru.<br /><br /> Określa sposób generowania informacji o lokalizacji dla każdego źródła [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliku. Prawidłowe opcje to **Brak**, **CommentsOnly**, i **wszystkich**.|
|`OutputPath`|Wymagane **ciąg** parametru.<br /><br /> Określa katalog, w którym wygenerowany [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] wygenerowanych plików binarnych.|
|`OutputType`|Wymagane **ciąg** parametru.<br /><br /> Określa typ zestawu, który został wygenerowany przez projekt. Prawidłowe opcje to **winexe**, **exe**, **biblioteki**, i **modułu netmodule**.|
|`References`|Opcjonalne **[ITaskItem]** parametru.<br /><br /> Określa listę odwołań z plików do zestawów, które zawierają typy, które są używane w [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plików. Jest jedno odwołanie do zestawu, który został wygenerowany przez <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> zadań, które należy uruchomić przed <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> zadań.|
|`RootNamespace`|Opcjonalne **ciąg** parametru.<br /><br /> Określa przestrzeń nazw korzenia dla klasy, które znajdują się wewnątrz projektu. **RootNamespace** jest również używany jako domyślny obszar nazw wygenerowanego kodu zarządzanego gdy pliku odpowiadającego [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plik nie zawiera `x:Class` atrybutu.|
|`XAMLDebuggingInformation`|Opcjonalne **logiczna** parametru.<br /><br /> Gdy **true**, informacje diagnostyczne jest generowany i zawarty w skompilowanych [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] w celu ułatwienia debugowania.|

## <a name="remarks"></a>Uwagi

Przed uruchomieniem **markupcompilepass2 —**, należy wygenerować tymczasowej zestawu, który zawiera typy, które są używane przez [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliki zostały odłożone której przebieg kompilacji znaczników. Generowanie tymczasowego zestawu uruchamiając **generatetemporarytargetassembly —** zadań.

Odwołanie do wygenerowanego zestawu tymczasowe są dostarczane do <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> po uruchomieniu, dzięki czemu [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] przekazać pliki, których Kompilacja została odroczona w pierwszej kompilacji znaczników teraz zestawiane na format binarny.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia użycie <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> zadanie do wykonania drugiej przekazywanie kompilacji.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask 
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass2" 
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MarkupCompilePass2Task">
    <MarkupCompilePass2 
      AssemblyName="WPFMSBuildSample"
      Language="C#"
      OutputType="WinExe"
      OutputPath="obj\Debug\"
      References=".\obj\debug\WPFMSBuildSample.exe;c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />
  </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

[Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)  
[Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)  
[Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)  
[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)  
[Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)  
[Aplikacje przeglądarek WPF XAML — omówienie](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)