---
title: Folder — Element (szablony projektu Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ec8a5520716f6073d49ab2b5a64becfb760092d2
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36234926"
---
# <a name="folder-element-visual-studio-project-templates"></a>Folder — Element (szablony projektów Visual Studio)
Określa folder, który zostanie dodany do projektu.  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<Project>  
 \<Folder >  
  
## <a name="syntax"></a>Składnia  
  
```  
<Folder Name="Project Folder">  
    <Folder> ... </Folder>  
    <ProjectItem> ... </ProjectItem>  
</Folder>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Atrybut wymagany.<br /><br /> Nazwa folderu projektu.|  
|`TargetFolderName`|Atrybut opcjonalny.<br /><br /> Określa nazwę folderu zwracanie projektu jest tworzona na podstawie szablonu. Ten atrybut jest przydatny do utworzenia nazwy folderu przy użyciu wymiany parametru lub folder z ciągiem międzynarodowe nazwy nie można użyć bezpośrednio w pliku zip.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`Folder`|Określa folder do dodania do projektu. `Folder` elementy mogą zawierać elementu podrzędnego `Folder` elementów.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Określa plik, aby dodać do projektu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|Element podrzędny opcjonalne [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|  
  
## <a name="remarks"></a>Uwagi  
 `Folder` jest opcjonalne podrzędnym `Project`.  
  
 Do organizowania elementów projektu do folderów w szablonie, można użyć dowolnej z następujących metod:  
  
-   Będą one wyświetlane w pliku .zip szablon i dodaj je do projektu w pliku .vstemplate, określając ścieżkę do pliku w `ProjectItem` elementów, których nie `Folder` elementów. Jest to zalecana metoda. Na przykład:  
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Będą one wyświetlane w pliku .zip szablon i dodaj je do projektu w pliku .vstemplate `Folder` elementów. Na przykład:  
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Nie dołączaj folderów w pliku zip szablonu, ale. Dodaj foldery przy użyciu `TargetFileName` atrybutu `ProjectItem` elementu. Na przykład:  
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia metadane szablonu projektu dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji systemu Windows.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <Folder Name="Properties">  
                <ProjectItem>AssemblyInfo.cs</ProjectItem>  
                <ProjectItem>Resources.resx</ProjectItem>  
                <ProjectItem>Resources.Designer.cs</ProjectItem>  
                <ProjectItem>Settings.settings</ProjectItem>  
                <ProjectItem>Settings.Designer.cs</ProjectItem>  
            </Folder>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablony projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [ProjectItem, element (szablony elementów Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)