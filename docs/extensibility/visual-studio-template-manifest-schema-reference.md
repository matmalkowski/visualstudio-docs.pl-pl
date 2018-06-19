---
title: Odwołanie do schematu manifestu szablonu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26f346329e4c0fa2defe6bc4ff6373226be72beb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142583"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Odwołanie do schematu manifestu szablonu programu Visual Studio
Ten schemat opisuje formatu plików manifestu (.vstman) szablonu Visual Studio wygenerowany dla szablonów projektów lub elementów programu Visual Studio oraz lokalizacja oraz inne istotne informacje o szablonie.  
  
 : Ponieważ istnieją oddzielne elementu i katalogi szablonu projektu, manifestu nigdy nie powinien mieć różnych szablonów elementów i projektu.  
  
> [!IMPORTANT]
>  Tego manifestu jest dostępne w programie Visual Studio 2017 r.  
  
## <a name="vstemplatemanifest-element"></a>VSTemplateManifest Element  
 Główny element manifestu.  
  
### <a name="attributes"></a>Atrybuty  
  
-   **Wersja**: ciąg reprezentujący wersji manifestu szablonu. Wymagany.  
  
-   **Ustawienia regionalne**: ciąg reprezentujący ustawień regionalnych lub ustawień regionalnych manifestu szablonu. Wartości ustawień regionalnych ma zastosowanie do wszystkich szablonów, należy użyć oddzielnych manifestu dla poszczególnych ustawień regionalnych. Opcjonalny.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
-   **VSTemplateContainer** opcjonalne.  
  
-   **VSTemplateDir** opcjonalne.  
  
### <a name="parent-element"></a>Element nadrzędny  
 Brak.  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 Kontener szablonu manifestu elementów. Manifest ma jeden kontener szablonu dla każdego szablonu, który definiuje.  
  
### <a name="attributes"></a>Atrybuty  
 **VSTemplateType** : wartość ciągu, która określa typ szablonu (`"Project"`, `"Item"`, lub `"ProjectGroup"`). Wymagane  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
-   **RelativePathOnDisk**: ścieżki względnej pliku szablonu na dysku. Ta lokalizacja definiuje również umieszczania szablonu w drzewie szablonu pokazano w **nowy projekt** lub **nowy element** okna dialogowego. Dla szablonów wdrożony jako katalog i pojedyncze pliki ta ścieżka odwołuje się do katalog zawierający pliki szablonu. Dla szablonów wdrożony jako plik zip powinien to być ścieżka do pliku zip.  
  
-   **VSTemplateHeader** : A [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) element, który opisuje nagłówka.  
  
### <a name="parent-element"></a>Element nadrzędny  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 Opisuje katalog, w którym znajduje się szablon. Manifest może zawierać wiele **VSTemplateDir** wpisy zlokalizowanej nazwy i sortowania dla katalogów do kontrolowania sposobu ich wyświetlania w drzewie kategorii szablonu.  
  
 Z powodu ich projektowania **VSTemplateDir** zapisy mają być wyświetlane tylko w manifestach określonej — ustawienia regionalne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
-   **RelativePath**: ścieżka szablonu. Może istnieć tylko jeden wpis na ścieżkę, pierwsza z nich będzie win dla wszystkich manifestów.  
  
-   **LocalizedName**: A **NameDescriptionIcon** element, który określa zlokalizowana nazwa. Opcjonalny.  
  
-   **SortOrder** : ciąg, który określa porządek sortowania. Opcjonalny.  
  
-   **ParentFolderOverrideName**: przesłoniętych nazwę folderu nadrzędnego. Opcjonalny. Ten element ma **nazwa** atrybut, który jest wartość ciągu, który określa nazwę.  
  
### <a name="parent-element"></a>Element nadrzędny  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 Określa nazwę i opis, prawdopodobnie zlokalizowane szablony. Zobacz **LocalizedName** powyżej.  
  
### <a name="attributes"></a>Atrybuty  
  
-   **Pakiet**: wartość ciągu, która określa pakietu. Opcjonalny.  
  
-   **Identyfikator**: wartość ciągu, który określa identyfikator. Opcjonalny.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-element"></a>Element nadrzędny  
 **LocalizedName**  
  
## <a name="examples"></a>Przykłady  
 Poniżej przedstawiono przykładowy plik .vstman szablonu projektu.  
  
```xml  
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Project">  
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>  
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>TestProjectTemplate</Name>  
        <Description>TestProjectTemplate</Description>  
        <Icon>TestProjectTemplate.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <SortOrder>1000</SortOrder>  
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>  
        <CreateNewFolder>true</CreateNewFolder>  
        <DefaultName>TestProjectTemplate</DefaultName>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 Poniżej przedstawiono przykładowy plik .vstman szablonu elementu.  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Item">  
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ItemTemplate1</Name>  
        <Description>ItemTemplate1</Description>  
        <Icon>ItemTemplate1.ico</Icon>  
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <DefaultName>Class.cs</DefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```