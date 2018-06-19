---
title: Markupcompilepass1 — zadanie | Dokumentacja firmy Microsoft
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
- converting XAML to binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], parameters
- converting XAML projects to compiled binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0abf8f5b2c77281325853f744f54513fb897ecc6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31574951"
---
# <a name="markupcompilepass1-task"></a>MarkupCompilePass1 — Zadanie

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> Zadań konwertuje niemożliwe do zlokalizowania [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] pliki na skompilowany format binarny projektu.

## <a name="task-parameters"></a>Parametry zadania

|Parametr|Opis|
|---------------|-----------------|
|`AllGeneratedFiles`|Opcjonalne **[ITaskItem]** parametru wyjściowego.<br /><br /> Zawiera listę wszystkich plików, które są generowane przez <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> zadań.|
|`AlwaysCompileMarkupFilesInSeparateDomain`|Opcjonalne **logiczna** parametru.<br /><br /> Określa, czy można uruchomić zadania w oddzielnej <xref:System.AppDomain>. Jeśli ten parametr zwraca **false**, to zadanie jest uruchamiane w tym samym <xref:System.AppDomain> jako [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] i uruchomieniu szybciej. Jeśli parametr zwraca **true**, to zadanie jest uruchamiane na sekundę <xref:System.AppDomain> jest odizolowana od [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] i działa wolniej.|
|`ApplicationMarkup`|Opcjonalne **[ITaskItem]** parametru.<br /><br /> Określa nazwę definicji aplikacji [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliku.|
|`AssembliesGeneratedDuringBuild`|Opcjonalne **String []** parametru.<br /><br /> Określa odwołania do zestawów, które zmieniają się podczas procesu kompilacji. Na przykład rozwiązanie Visual Studio może zawierać jeden projekt, który odwołuje się do skompilowanych danych wyjściowych z innego projektu. W takim przypadku można dodać skompilowanych danych wyjściowych projektu drugi do **AssembliesGeneratedDuringBuild** parametru.<br /><br /> Uwaga: **AssembliesGeneratedDuringBuild** parametr może zawierać odwołania do pełnego zestawu zestawy, które są generowane przez rozwiązanie do kompilacji.|
|`AssemblyName`|Wymagane **ciąg** parametru.<br /><br /> Określa krótką nazwę zestawu, który jest generowany dla projektu. Na przykład, jeśli projekt jest generowanie [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] plik wykonywalny, którego nazwa jest **WinExeAssembly.exe**, **AssemblyName** parametr ma wartość **WinExeAssembly**.|
|`AssemblyPublicKeyToken`|Opcjonalne **ciąg** parametru.<br /><br /> Określa token klucza publicznego dla zestawu.|
|`AssemblyVersion`|Opcjonalne **ciąg** parametru.<br /><br /> Określa numer wersji zestawu.|
|`ContentFiles`|Opcjonalne **[ITaskItem]** parametru.<br /><br /> Określa listę utracić plików zawartości.|
|`DefineConstants`|Opcjonalne **ciąg** parametru.<br /><br /> Określa, że bieżąca wartość **DefineConstants**, jest przechowywany. co ma wpływ na generowanie zestawów docelowych; Jeśli ten parametr zostanie zmieniona, może być zmieniona publiczny interfejs API w zestawie docelowym i tworzenia [!INCLUDE[TLA2#tla_titlexaml](../msbuild/includes/tla2sharptla_titlexaml_md.md)] może mieć wpływ na pliki, które lokalnego typy referencyjne.|
|`ExtraBuildControlFiles`|Opcjonalne **[ITaskItem]** parametru.<br /><br /> Określa listę plików, które kontrolują, czy odbudowie jest wyzwalane, gdy <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> zadanie zwracające; odbudowie zostanie wywołany, jeśli jeden z tych plików zmian.|
|`GeneratedBamlFiles`|Opcjonalne **[ITaskItem]** parametru wyjściowego.<br /><br /> Zawiera listę plików wygenerowanych w [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] format binarny.|
|`GeneratedCodeFiles`|Opcjonalne **[ITaskItem]** parametru wyjściowego.<br /><br /> Zawiera listę plików wygenerowanych kodu zarządzanego.|
|`GeneratedLocalizationFiles`|Opcjonalne **[ITaskItem]** parametru wyjściowego.<br /><br /> Zawiera listę plików lokalizacji, które zostały wygenerowane dla każdego Lokalizowalny [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliku.|
|`HostInBrowser`|Opcjonalne **ciąg** parametru.<br /><br /> Określa, czy wygenerowanym zestawie [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)]. Prawidłowe opcje to **true** i **false**. Jeśli **true**, zostaje wygenerowany kod do obsługi przeglądarki.|
|`KnownReferencePaths`|Opcjonalne **String []** parametru.<br /><br /> Określa odwołania do zestawów, które nie zmieniają się podczas procesu kompilacji. Zawiera zestawy, które znajdują się w [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)]w [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] katalogu instalacyjnego i tak dalej.|
|`Language`|Wymagane **ciąg** parametru.<br /><br /> Określa język zarządzanych, który obsługuje kompilatora. Prawidłowe opcje to **C#**, **VB**, **JScript**, i **C++**.|
|`LanguageSourceExtension`|Opcjonalne **ciąg** parametru.<br /><br /> Określa rozszerzenia plików, które są dołączane do rozszerzenia pliku wygenerowanego kodu zarządzanego:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Jeśli **LanguageSourceExtension** nie ustawiono parametru z określoną wartością, będą używane domyślne rozszerzenie nazwy pliku źródłowego dla języka: **.vb** dla [!INCLUDE[TLA#tla_visualb](../msbuild/includes/tlasharptla_visualb_md.md)], **.csharp** dla [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)].|
|`LocalizationDirectivesToLocFile`|Opcjonalne **ciąg** parametru.<br /><br /> Określa sposób generowania informacji o lokalizacji dla każdego źródła [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliku. Prawidłowe opcje to **Brak**, **CommentsOnly**, i **wszystkich**.|
|`OutputPath`|Wymagane **ciąg** parametru.<br /><br /> Określa katalog, w którym wygenerowany plików kodu zarządzanego i [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] wygenerowanych plików binarnych.|
|`OutputType`|Wymagane **ciąg** parametru.<br /><br /> Określa typ zestawu, który został wygenerowany przez projekt. Prawidłowe opcje to **winexe**, **exe**, **biblioteki**, i **modułu netmodule**.|
|`PageMarkup`|Opcjonalne **[ITaskItem]** parametru.<br /><br /> Określa listę [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plików do procesu.|
|`References`|Opcjonalne **[ITaskItem]** parametru.<br /><br /> Określa listę odwołań z plików do zestawów, które zawierają typy, które są używane w [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plików.|
|`RequirePass2ForMainAssembly`|Opcjonalne **logiczna** parametru wyjściowego.<br /><br /> Wskazuje, czy projekt zawiera niemożliwe do zlokalizowania [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliki, które odwołują się do lokalnego typy, które są osadzone w zestawie głównym.|
|`RequirePass2ForSatelliteAssembly`|Opcjonalne **logiczna** parametru wyjściowego.<br /><br /> Wskazuje, czy projekt zawiera Lokalizowalny [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliki, które odwołują się do lokalnego typy, które są osadzone w zestawie głównym.|
|`RootNamespace`|Opcjonalne **ciąg** parametru.<br /><br /> Określa przestrzeń nazw korzenia dla klasy, które znajdują się wewnątrz projektu. **RootNamespace** jest również używany jako domyślny obszar nazw wygenerowanego kodu zarządzanego gdy pliku odpowiadającego [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plik nie zawiera `x:Class` atrybutu.|
|`SourceCodeFiles`|Opcjonalne **[ITaskItem]** parametru.<br /><br /> Określa listę plików kodu dla bieżącego projektu. Lista nie zawiera plików wygenerowanego kodu zarządzanego specyficzny dla języka.|
|`UICulture`|Opcjonalne **ciąg** parametru.<br /><br /> Określa zestaw satelicki kultury interfejsu użytkownika, w którym wygenerowany [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] osadzone plików binarnych. Jeśli **UICulture** nie jest ustawiona, jest wygenerowany [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plików binarnych są osadzone w zestawie głównym.|
|`XAMLDebuggingInformation`|Opcjonalne **logiczna** parametru.<br /><br /> Gdy **true**, informacje diagnostyczne jest generowany i zawarty w skompilowanych [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] w celu ułatwienia debugowania.|

## <a name="remarks"></a>Uwagi

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> Zadań zwykle kompiluje [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] w formacie binarnym i generuje pliki kodu. Jeśli [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plik zawiera odwołania do typów, które są zdefiniowane w tym samym projekcie, jego kompilacja na format binarny została odroczona przez **markupcompilepass1 —** drugim przebiegu kompilacji znaczników ( **Markupcompilepass2 —**). Takie pliki muszą mieć ich kompilacji odroczone, ponieważ ich musi poczekać na wskazanych typów zdefiniowany lokalnie są kompilowane. Jednak jeśli [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plik ma `x:Class` atrybutu <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> generuje plik specyficzny dla języka kodu dla niego.

A [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plik jest Lokalizowalny, jeśli zawiera on elementy, które używają `x:Uid` atrybutu:

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Uid="Page1Uid"
    >
  ...
</Page>
```

A [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliku odwołuje się do typu zdefiniowany lokalnie, gdy deklaruje [!INCLUDE[TLA#tla_xml](../msbuild/includes/tlasharptla_xml_md.md)] przestrzeni nazw, która używa `clr-namespace` wartość do odwoływania się do przestrzeni nazw w bieżącym projekcie:

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:localNamespace="clr-namespace:WPFMSBuildSample"
    >
    <Grid>
      <Grid.Resources>
        <localNameSpace:LocalType x:Key="localType" />
      </Grid.Resources>
      ...
    </Grid>
</Page>
```

Ile [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliku jest Lokalizowalny lub odwołuje się do typu zdefiniowany lokalnie, drugi przebieg kompilacji znaczników jest wymagane, co wymaga uruchomiona [generatetemporarytargetassembly —](../msbuild/generatetemporarytargetassembly-task.md) , a następnie [ Markupcompilepass2 —](../msbuild/markupcompilepass2-task.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak przekonwertować trzy `Page` [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plików do plików binarnych. `Page1` zawiera odwołanie do typu, `Class1`, który znajduje się w głównej przestrzeni nazw projektu i w związku z tym nie jest konwertowana na format binarny pliki w tym przebiegu kompilacji znaczników. Zamiast tego [generatetemporarytargetassembly —](../msbuild/generatetemporarytargetassembly-task.md) jest wykonywany i następuje [markupcompilepass2 —](../msbuild/markupcompilepass2-task.md).

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask 
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass1" 
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MarkupCompilePass1Task">
    <MarkupCompilePass1 
      AssemblyName="WPFMSBuildSample"
      Language="C#"
      OutputType="WinExe"
      OutputPath="obj\Debug\"
      ApplicationMarkup="App.xaml"
      PageMarkup="Page1.xaml;Page2.xaml;Page3.xaml"
      SourceCodeFiles="Class1.cs"
      References="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />
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