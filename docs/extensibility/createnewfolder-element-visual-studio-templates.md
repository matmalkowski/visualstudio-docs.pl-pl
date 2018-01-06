---
title: "Createnewfolder — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#CreateNewFolder
helpviewer_keywords: CreateNewFolder element [Visual Studio project templates]
ms.assetid: acef2016-4140-45d6-ace8-b8160eabd676
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dab5b47904360fbc87b6799affe290cd3ab94398
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="createnewfolder-element-visual-studio-templates"></a>CreateNewFolder — Element (szablony Visual Studio)
Określa, czy należy sprawdzić, czy katalog docelowy, na którym ma być utworzony projekt nie istnieje. Jeśli katalog istnieje, można utworzyć nowego katalogu projektu. To ustawienie jest zazwyczaj zastępowany przez `NewProjectRequiresNewFolder(VsTemplate)` flagę rejestru (`HKEY_LOCAL_MACHINE/SOFTWARE(/Wow6432Node)/Microsoft/VisualStudio/<version number>/Projects/<project GUID>`) czy wszystkie popularne typy projektu umożliwia określenie, czy należy utworzyć nowy projekt w nowym katalogu.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<Createnewfolder — >  
  
## <a name="syntax"></a>Składnia  
  
```  
<CreateNewFolder>  
    true/false  
</CreateNewFolder>  
```  
  
## <a name="type"></a>Typ  
 `Boolean`  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Kategoryzuje szablonu i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Tekst musi być równa albo `true` lub `false`, wskazujące, czy nowy folder kontenera powinien zostać utworzony podczas projektu jest tworzona na podstawie szablonu.  
  
## <a name="remarks"></a>Uwagi  
 `CreateNewFolder`to opcjonalny element. Wartość domyślna to `true`.  
  
 Wartość określona w `CreateNewFolder` element jest tylko honorowane przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Jeśli projekt źródłowy system obsługuje tę funkcję.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu określa nie można utworzyć nowego folderu, gdy projekt jest tworzony na podstawie szablonu.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <CreateNewFolder>false</CreateNewFolder>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)