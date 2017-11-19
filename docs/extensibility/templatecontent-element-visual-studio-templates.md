---
title: "TemplateContent — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords: TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1f083097ae79d045891b64d806820a58686b4c95
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="templatecontent-element-visual-studio-templates"></a>TemplateContent — Element (szablony Visual Studio)
Określa zawartość szablonu.  
  
 \<VSTemplate >  
 \<TemplateContent >  
  
## <a name="syntax"></a>Składnia  
  
```  
<TemplateContent>  
    ...  
</TemplateContent>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|Określa, czy Skompiluj rozwiązanie, gdy projekt jest tworzony na podstawie szablonu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Projectcollection —](../extensibility/projectcollection-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa organizację i zawartość szablonów wieloprojektowych.|  
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa plików lub katalogów do dodania do projektu.|  
|[Odwołania](../extensibility/references-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa odwołania do zestawów wymagane przez szablon elementu.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Element opcjonalny.<br /><br /> Określa plik zawarte w szablonie.|  
|[Customparameters —](../extensibility/customparameters-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa wszelkie niestandardowe parametry, które mają być używane podczas tworzenia projektów lub elementów z szablonu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Zawiera wszystkie metadane szablonu projektu, szablon elementu lub startowy.|  
  
## <a name="remarks"></a>Uwagi  
 `TemplateContent`jest wymagany element.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono metadane szablonu projektu dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
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
 [Tworzenie szablony projektów i elementów](../ide/creating-project-and-item-templates.md)