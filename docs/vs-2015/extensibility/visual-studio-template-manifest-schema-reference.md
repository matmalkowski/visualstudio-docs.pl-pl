---
title: Szablon programu Visual Studio Manifest odwołanie do schematu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b079e6b7356cdd84a98314beef95f4b1a8fbc5ee
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42673543"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Odwołanie do schematu manifestu szablonu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Visual Studio Manifest odwołanie do schematu szablonu](https://docs.microsoft.com/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).  
  
Ten schemat opisuje formatu plików manifestu (vstman) szablonu programu Visual Studio wygenerowany dla szablonów projektu lub elementu programu Visual Studio oraz lokalizację i inne istotne informacje o szablonie.  
  
 : Ponieważ osobnym i katalogi szablonu projektu, manifest nigdy nie powinna mieć różne szablony elementów i projektów.  
  
> [!IMPORTANT]
>  Tego manifestu jest dostępna, począwszy od programu Visual Studio "15" (wersja zapoznawcza) 2.  
  
## <a name="vstemplatemanifest-element"></a>VSTemplateManifest Element  
 Element główny manifestu.  
  
### <a name="attributes"></a>Atrybuty  
  
-   **Wersja**: ciąg reprezentujący wersja manifestu szablonu. Wymagane.  
  
-   **Ustawienia regionalne**: ciąg reprezentujący ustawień regionalnych lub ustawień regionalnych manifestu szablonu. Wartości ustawień regionalnych ma zastosowanie do wszystkich szablonów, więc należy użyć oddzielnych manifestu dla poszczególnych ustawień regionalnych. Opcjonalna.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
-   **VSTemplateContainer** opcjonalne.  
  
-   **VSTemplateDir** opcjonalne.  
  
### <a name="parent-element"></a>Element nadrzędny  
 Brak.  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 Kontener szablonu manifestu elementów. Manifest zawiera jeden kontener szablonu dla każdego szablonu, który go definiuje.  
  
### <a name="attributes"></a>Atrybuty  
 **VSTemplateType** : wartość ciągu, który określa typ szablonu (`"Project"`, `"Item"`, lub `"ProjectGroup"`). Wymagane  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
-   **RelativePathOnDisk**: ścieżka względna pliku szablonu na dysku. Ta lokalizacja definiuje również umieszczania szablonu w drzewie szablonu wyświetlane w **nowy projekt** lub **nowy element** okna dialogowego. Dla wdrożonych jako katalog i poszczególnych plików szablonów ta ścieżka odwołuje się do katalogu zawierającego pliki szablonów. Dla szablonów wdrożony jako plik zip ta ścieżka powinna być ścieżką do pliku zip.  
  
-   **VSTemplateHeader** : A [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) element, który opisuje nagłówka.  
  
### <a name="parent-element"></a>Element nadrzędny  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 W tym artykule opisano katalog, w którym znajduje się szablon. Manifest może zawierać więcej niż jednego **VSTemplateDir** wpisy zlokalizowane nazwy i sortowania kolejności w przypadku katalogów do kontrolowania sposobu ich wyświetlania w drzewie kategorii szablonu.  
  
 Ze względu na ich projektu **VSTemplateDir** zapisy mają być wyświetlane tylko w określonych manifestów — ustawienia regionalne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
-   **RelativePath**: ścieżka szablonu. Może istnieć tylko jeden zapis dla ścieżki, więc pierwszy z nich zostanie zarejestrowane dla wszystkich manifestów.  
  
-   **LocalizedName**: A **NameDescriptionIcon** element, który określa zlokalizowana nazwa. Opcjonalna.  
  
-   **SortOrder** : ciąg, który określa kolejność sortowania. Opcjonalna.  
  
-   **ParentFolderOverrideName**: zastąpiona nazwa folderu nadrzędnego. Opcjonalna. Ten element ma **nazwa** atrybut, który jest wartością ciągu, który określa nazwę.  
  
### <a name="parent-element"></a>Element nadrzędny  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 Określa nazwę i opis, prawdopodobnie zlokalizowane szablony. Zobacz **LocalizedName** powyżej.  
  
### <a name="attributes"></a>Atrybuty  
  
-   **Pakiet**: wartość ciągu, który określa pakiet. Opcjonalna.  
  
-   **Identyfikator**: wartość ciągu, który określa identyfikator. Opcjonalna.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-element"></a>Element nadrzędny  
 **LocalizedName**  
  
## <a name="examples"></a>Przykłady  
 Oto przykład pliku vstman szablonu projektu.  
  
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
  
 Oto przykład pliku vstman szablonu elementu.  
  
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

