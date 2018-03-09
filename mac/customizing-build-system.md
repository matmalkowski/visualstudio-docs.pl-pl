---
title: Dostosowywanie System kompilacji | Dokumentacja firmy Microsoft
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.openlocfilehash: 6ef9084e5cd571c0f3f2b60e2c08d8d7bb0b8518
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2018
---
# <a name="customizing-the-build-system"></a>Dostosowywanie systemu kompilacji

MSbuild jest aparatem kompilacji, opracowaną przez firmę Microsoft, umożliwiające dla budynku głównie aplikacji .NET. Mono framework również ma własną implementację firmy Microsoft kompilacji aparatu, nazywany **xbuild**. Jednak xbuild ma zostały wycofane, na rzecz przy użyciu programu MSBuild we wszystkich systemach operacyjnych.

**MSbuild** jest używany głównie dla jako system kompilacji dla projektów programu Visual Studio dla komputerów Mac. 

MSBuild działa wykonując zestaw składników, takich jak pliki źródłowe, a przekształca je do wyjścia, takich jak pliki wykonywalne. Za pomocą narzędzi, takich jak kompilator powoduje osiągnięcie tego raportu. 


## <a name="msbuild-file"></a>Plik programu MSBuild

Program MSBuild używa pliku XML o nazwie pliku projektu, który definiuje *elementów* które są częścią projektu (takich jak zasoby obrazów) i *właściwości* wymagane do tworzenia projektu. Ten plik projektu ma zawsze rozszerzenie pliku kończy się rozszerzeniem `proj`, takich jak `.csproj` dla projektów C#. 

### <a name="viewing-the-msbuild-file"></a>Wyświetlanie pliku MSBuild

Zlokalizuj plik MSBuild prawym przyciskiem myszy nazwę projektu i wybierając **ujawnić w wyszukiwarce**. Okno wyszukiwania zawiera wszystkie pliki i foldery, związane z projektem, w tym `.csproj` plików, jak pokazano na poniższej ilustracji:

![](media/customizing-build-system-image1.png)

Aby wyświetlić `.csproj` na nowej karcie w programie Visual Studio for Mac, kliknij prawym przyciskiem myszy nazwę projektu i przejdź do **Narzędzia > Edytuj plik**:

![](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>Kompozycja plik programu MSBuild

Wszystkie pliki programu MSBuild zawiera obowiązkowe głównego `Project` element, w następujący sposób:

```
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

Zwykle, projekt zostanie również zaimportować `.targets` pliku. Ten plik zawiera wiele reguł, które opisują sposób przetwarzania i utworzyć różne pliki. Importowanie są zwykle widoczne w dolnej części Twojego `proj` pliku, a dla projektów C# wyglądać mniej więcej tak:

```
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

Obiekty docelowe jest inny plik MSBuild. Ten plik zawiera kod MSBuild wielokrotnego użytku przez wiele projektów. Na przykład `Microsoft.CSharp.targets` pliku, który znajduje się w katalogu reprezentowany przez `MSBuildBinPath` właściwości (lub zmienna) zawiera logikę do tworzenia zestawów języka C# przy użyciu plików źródłowych w języku C#.

### <a name="items-and-properties"></a>Elementy i właściwości

Istnieją dwa typy podstawowe dane w programie MSBuild: *elementów* i *właściwości*, opisano szczegółowo w poniższych sekcjach.

#### <a name="properties"></a>Właściwości

Właściwości są pary klucz wartość, które są używane do przechowywania ustawień, które mają wpływ na kompilacji, takich jak opcje kompilatora.

Są ustawione, przy użyciu PropertyGroup i może zawierać dowolną liczbę PropertiesGroups, która może zawierać dowolną liczbę właściwości. 

Na przykład PropertyGroup dla prostej aplikacji konsolowej może wyglądać następujący kod XML:

```
<PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <Platform Condition=" '$(Platform)' == '' ">x86</Platform>
        <ProjectGuid>{E248730E-1393-43CC-9183-FFA42F63BE81}</ProjectGuid>
        <OutputType>Exe</OutputType>
        <RootNamespace>refactoring</RootNamespace>
        <AssemblyName>refactoring</AssemblyName>
        <TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
    </PropertyGroup>
```

Właściwości mogą być przywoływane z wyrażenia `$()` składni. Na przykład `$(Foo)` zostaną ocenione jako wartość `Foo` właściwości. Jeśli nie ustawiono właściwości, będą oceniać pusty ciąg znaków, bez żadnych błędów.

#### <a name="items"></a>Elementy

Elementy zapewniają sposób postępowania z danych wejściowych w systemie kompilacji zgodnie z listy lub ustawia i zwykle odpowiadają pliki. Każdy element ma element *typu*, element *spec*i opcjonalnie dowolnego *metadanych*. Należy pamiętać, że program MSBuild nie działa na poszczególne elementy zajmuje na wszystkie elementy z danego typu wywołuje element *ustawić*

Elementy są tworzone przez zadeklarowanie `ItemGroup`. Może być dowolną liczbę ItemGroups, która może zawierać dowolną liczbę elementów. 

Na przykład poniższy fragment kodu tworzy uruchamianie ekrany z systemem iOS. Ekrany Uruchom ma typ kompilacji `BundleResource`, z spec jako ścieżkę do obrazu:

```
 <ItemGroup>
    <BundleResource Include="Resources\Default-568h%402x.png" />
    <BundleResource Include="Resources\Default%402x.png" />
    <BundleResource Include="Resources\Default.png" />
    <BundleResource Include="Resources\Default-Portrait.png" />
    <BundleResource Include="Resources\Default-Portrait%402x.png" />
    <BundleResource Include="Resources\Default-Landscape%402x.png" />
  </ItemGroup>
 ```
 
 Element zestawów można odwoływać się od wyrażenia przy użyciu `@()` składni. Na przykład `@(BundleResource)` zostaną ocenione jako zestawu elementu BundleResource, co oznacza, że wszystkie elementy BundleResource. Jeśli nie ma żadnych towarów tego typu, będzie pusta, bez żadnych błędów.

## <a name="resources-for-learning-msbuild"></a>Zasoby umożliwiające uzyskiwanie MSBuild

Dowiedz się więcej o MSBuild bardziej szczegółowo można następujące zasoby:

* [MSDN — omówienie](https://msdn.microsoft.com/library/dd393574.aspx)
* [MSDN — pojęcia](https://msdn.microsoft.com/library/dd637714.aspx)


