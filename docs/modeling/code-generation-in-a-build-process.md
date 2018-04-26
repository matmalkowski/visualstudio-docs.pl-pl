---
title: Generowanie kodu w procesie kompilacji w programie Visual Studio
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1d08aafd31d93c7a07d57dcd5b831b8ae41a6c17
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="code-generation-in-a-build-process"></a>Generowanie kodu w procesie kompilacji

[Transformacji tekstu](../modeling/code-generation-and-t4-text-templates.md) może być wywoływany jako część [proces kompilacji](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692) z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania. Istnieją zadania kompilacji, które są przeznaczone do przekształcania tekstu. Zadania kompilacji T4 uruchamiają szablon tekstowy czasu projektowania, a także kompilują szablony tekstowe czasu wykonywania (wstępnie przetworzone).

Istnieją pewne różnice w czynnościach, które mogą wykonać zadania kompilacji, wszystko zależy od użytego aparatu kompilacji. Podczas kompilowania rozwiązania w programie Visual Studio szablonu tekstowego może uzyskać dostęp do programu Visual Studio interfejsu API programu (EnvDTE), jeśli [hostspecific = "true"](../modeling/t4-template-directive.md) ustawiono atrybut. Ale który nie ma wartość true w przypadku kompilowania rozwiązania z wiersza polecenia lub po zainicjowaniu kompilacji serwera za pomocą programu Visual Studio. W tych przypadkach kompilację wykonuje MSBuild i użyty zostaje inny host T4.

Oznacza to, że nie masz dostępu do elementów, jak nazwy plików projektu w taki sam sposób jak podczas tworzenia szablonu tekstowego w programie MSBuild. Można jednak [przekazania informacji o środowisku do szablonów tekstowych i procesory dyrektywy przy użyciu parametrów kompilacji](#parameters).

##  <a name="buildserver"></a> Skonfiguruj komputery

Aby włączyć zadania kompilacji na komputerze deweloperskim, należy zainstalować modelowania zestawu SDK dla programu Visual Studio.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Jeśli [serwera kompilacji](http://msdn.microsoft.com/Library/788443c3-0547-452e-959c-4805573813a9) działa na komputerze, na którym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest nie jest zainstalowany, skopiuj następujące pliki na komputerze kompilacji z komputerze deweloperskim. Zastępuje numerów wersji najnowszych "*".

-   $(ProgramFiles)\MSBuild\Microsoft\VisualStudio\v*.0\TextTemplating

    -   Microsoft.VisualStudio.TextTemplating.Sdk.Host.*.0.dll

    -   Microsoft.TextTemplating.Build.Tasks.dll

    -   Microsoft.TextTemplating.targets

-   $(ProgramFiles) \Microsoft Visual Studio *.0\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

    -   Microsoft.VisualStudio.TextTemplating.*.0.dll

    -   Microsoft.VisualStudio.TextTemplating.Interfaces.*.0.dll (kilka plików)

    -   Microsoft.VisualStudio.TextTemplating.VSHost.*.0.dll

-   $(ProgramFiles) \Microsoft Visual Studio *.0\Common7\IDE\PublicAssemblies\

    -   Microsoft.VisualStudio.TextTemplating.Modeling.*.0.dll

## <a name="to-edit-the-project-file"></a>Aby edytować plik projektu

Należy edytować plik projektu, aby skonfigurować niektóre funkcje w programie MSBuild.

W Eksploratorze rozwiązań wybierz **zwolnienie** z menu kontekstowego projektu. Pozwala to na edycję pliku .csproj lub .vbproj w edytorze XML.

Po zakończeniu edycji wybierz **Załaduj ponownie**.

## <a name="import-the-text-transformation-targets"></a>Importowanie elementów docelowych przekształcania tekstu

W pliku .vbproj lub .csproj znajdź taki wiersz:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- lub -

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

Po tym wierszu wstaw import szablonu tekstu:

```xml
<!-- Optionally make the import portable across VS versions -->
  <PropertyGroup>
    <!-- Get the Visual Studio version - defaults to 10: -->
    <VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">10.0</VisualStudioVersion>
    <!-- Keep the next element all on one line: -->
    <VSToolsPath Condition="'$(VSToolsPath)' == ''">$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)</VSToolsPath>
  </PropertyGroup>

<!-- This is the important line: -->
  <Import Project="$(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets" />
```

## <a name="transform-templates-in-a-build"></a>Przekształć szablony kompilacji

Istnieje kilka właściwości, które można wstawić do pliku projektu, aby móc kontrolować zadanie przekształcenia:

-   Należy uruchomić zadanie przekształceń na początku każdej kompilacji:

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

-   Zastąp pliki, które są tylko do odczytu, ponieważ np. nie zostały wyewidencjonowane:

    ```xml
    <PropertyGroup>
        <OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>
    </PropertyGroup>
    ```

-   Za każdym razem przekształcaj każdy szablon:

    ```xml
    <PropertyGroup>
        <TransformOutOfDateOnly>false</TransformOutOfDateOnly>
    </PropertyGroup>
    ```

     Domyślnie, zadanie programu MSBuild T4 odtwarza plik wyjściowy, jeżeli jest starszy niż jego plik szablonu, a także wszystkie pliki, które są dołączone, lub wszystkie pliki, które zostały wcześniej odczytane przez szablon lub przez procesor dyrektywy, którego używa szablon. Zwróć uwagę, że jest to o wiele bardziej rozbudowany test zależności, niż test używany przez polecenie Transform All Templates w programie Visual Studio, który jedynie porównuje daty szablonu i pliku wyjściowego.

 Aby wykonać tylko przekształcenia tekstu w projekcie, należy wywołać zadanie TransformAll:

 `msbuild myProject.csproj /t:TransformAll`

 Aby przekształcić określony szablon tekstowy:

 `msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

 Można używać symboli wieloznacznych w TransformFile:

 `msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>Kontrola źródła

Nie ma żadnych szczególnych wbudowanych funkcji integracji z systemem kontroli źródła. Można jednak dodać własne rozszerzenia, na przykład aby wyewidencjonować i zaewidencjonować wygenerowany plik. Domyślnie zadanie przekształcenia tekstu pozwala uniknąć zastąpienia pliku, który jest oznaczony jako tylko do odczytu, i po napotkaniu takiego pliku zostanie zarejestrowany błąd na liście błędów Visual Studio, a zadanie się nie powiedzie.

 Aby określić, że pliki tylko do odczytu powinny być zastąpione, wstaw tę właściwość:

 `<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOuputFiles>`

 O ile nie dostosujesz kroku przetwarzania końcowego, zastąpienie pliku spowoduje, że na liście błędów zostanie zarejestrowane ostrzeżenie.

## <a name="customize-the-build-process"></a>Dostosowywanie procesu kompilacji

Transformacja tekstu ma miejsce przed innymi zadaniami w procesie kompilacji. Można zdefiniować zadania, które są wywoływane przed i po przekształceniu przez ustawienie właściwości `$(BeforeTransform)` i `$(AfterTransform)`:

```xml
<PropertyGroup>
    <BeforeTransform>CustomPreTransform</BeforeTransform>
    <AfterTransform>CustomPostTransform</AfterTransform>
  </PropertyGroup>
  <Target Name="CustomPreTransform">
    <Message Text="In CustomPreTransform..." Importance="High" />
  </Target>
  <Target Name="CustomPostTransform">
    <Message Text="In CustomPostTransform..." Importance="High" />
  </Target>
```

W `AfterTransform`, możesz odwoływać się do listy plików:

-   GeneratedFiles — lista plików zapisanych przez proces. Dla tych plików, które zastąpią istniejące pliki tylko do odczytu, %(GeneratedFiles.ReadOnlyFileOverwritten) będzie prawdziwe. Pliki te można wyewidencjonować z kontroli źródła.

-   NonGeneratedFiles — lista plików tylko do odczytu, które nie zostały nadpisane.

Na przykład, można zdefiniować zadanie do wyewidencjonowania GeneratedFiles.

## <a name="outputfilepath-and-outputfilename"></a>OutputFilePath i OutputFileName

Właściwości te są stosowane tylko przez program MSBuild. Nie wpływają one na generowanie kodu w programie Visual Studio. Przekierowują one wygenerowany plik wyjściowy do innego folderu lub pliku. Folder docelowy musi już istnieć.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFilePath>MyFolder</OutputFilePath>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

 Jest przydatne folderu przekierowania `$(IntermediateOutputPath).`

 Jeśli zostanie określona nazwa pliku wyjściowego, będzie ona miała wyższy priorytet nad rozszerzeniem określonym w dyrektywie wyjścia w szablonach.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

 Określanie Nazwa_pliku_wyjściowego lub OutputFilePath nie jest zalecane, jeśli są również transformowanie szablonów w wersji programu VS przy użyciu wszystkich transformacji lub systemem generatora pojedynczych plików. Ostatecznie uzyskasz różne ścieżki do plików, w zależności od tego, jak uruchamiane jest przekształcenie. Może to być bardzo mylące.

## <a name="add-reference-and-include-paths"></a>Dodaj odwołanie oraz ścieżki dołączanych plików

Host ma domyślny zestaw ścieżek wyszukiwania zestawów, do których odwołują się szablony. Aby dodać do tego zestawu:

```xml
<ItemGroup>
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />
    <!-- Add more T4ReferencePath items here -->
</ItemGroup>
```

Aby ustawić foldery, w których będą wyszukiwane pliki nagłówkowe, należy dostarczyć listę oddzieloną średnikami. Zwykle dodaje się je do istniejącej listy folderów.

```xml
<PropertyGroup>
    <IncludeFolders>
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>
</PropertyGroup>
```

##  <a name="parameters"></a> Przekaż dane kontekstu kompilacji do szablonów

Można ustawić wartości parametrów w pliku projektu. Na przykład można przekazać [kompilacji](../msbuild/msbuild-properties.md) właściwości i [zmiennych środowiskowych](../msbuild/how-to-use-environment-variables-in-a-build.md):

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

 W szablonie tekstu, należy ustawić `hostspecific` w dyrektywie template. Użyj [parametru](../modeling/t4-parameter-directive.md) dyrektywy można pobrać wartości:

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

W procesora dyrektywy, można wywołać [ITextTemplatingEngineHost.ResolveParameterValue](https://msdn.microsoft.com/library/microsoft.visualstudio.texttemplating.itexttemplatingenginehost.resolveparametervalue.aspx):

```csharp
string value = Host.ResolveParameterValue("-", "-", "parameterName");
```

```vb
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")
```

> [!NOTE]
> `ResolveParameterValue` pobiera dane z `T4ParameterValues` tylko jeśli używasz programu MSBuild. Kiedy przekształcasz szablon przy użyciu Visual Studio, parametry mają wartości domyślne.

##  <a name="msbuild"></a> Użyj właściwości projektu w zestawie i dyrektyw

Visual Studio makra podobnego do $(SolutionDir) nie działają w programie MSBuild. Zamiast tego można użyć właściwości projektu.

Wyedytuj plik .csproj lub .vbproj, aby zdefiniować właściwość projektu. W tym przykładzie definiuje właściwość o nazwie `myLibFolder`:

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

Teraz możesz korzystać ze swojej właściwości projektu w dyrektywach zestawu i dołączania:

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
<#@ include file="$(myLibFolder)\MyIncludeFile.t4" #>
```

 Te dyrektywy pobierają wartości z T4parameterValues zarówno w hostach MSBuild, jak i Visual Studio.

## <a name="q--a"></a>Pytania i odpowiedzi

 **Dlaczego chcesz transformacji szablonów na serwerze kompilacji? Szablony programu Visual Studio I już przekształcone zanim I sprawdzone w kodzie.**

 Po zaktualizowaniu pliku dołączanego lub innego pliku do odczytu przez szablon programu Visual Studio nie automatycznie przekształcić plik. Transformowanie szablonów jako część kompilacji upewnia się, że wszystko jest aktualny.

 **Jakie inne opcje są do transformacji szablonów tekstowych?**

-   [Narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) może być używana w skryptach poleceń. W większości przypadków łatwiej Użyj programu MSBuild.

-   [Wywoływanie transformacji tekstu w rozszerzeniu VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)

-   [Szablony tekstowe czasu projektowania](../modeling/design-time-code-generation-by-using-t4-text-templates.md) są przekształcane przez program Visual Studio.

-   [Szablony tekstowe czas uruchomienia](../modeling/run-time-text-generation-with-t4-text-templates.md) są przekształcane w czasie wykonywania w aplikacji.

## <a name="see-also"></a>Zobacz także

- Dobrą wskazówkę znajdziesz w szablonie T4 MSbuild, $(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets
- [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)
- [OLEG Sych: Opis T4:MSBuild integracji](http://www.olegsych.com/2010/04/understanding-t4-msbuild-integration/)
- [!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]