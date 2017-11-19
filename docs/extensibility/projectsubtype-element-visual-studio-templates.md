---
title: "Projectsubtype — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c42cfdd72207fdca7fbbe0b17b0f96f20066f098
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="projectsubtype-element-visual-studio-templates"></a>ProjectSubType — Element (szablony Visual Studio)
Klasyfikuje do podkategorii wartości określonej w szablonie `ProjectType` elementu.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<Projectsubtype — >  
  
## <a name="syntax"></a>Składnia  
  
```  
<ProjectSubType> SubType </ProjectSubType>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.  
  
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
  
 Ta wartość określa rodzaj szablonu.  
  
## <a name="remarks"></a>Uwagi  
 `ProjectSubType`jest elementem podrzędnym opcjonalne `TemplateData`.  
  
 `ProjectSubType` Element udostępnia podkategorię do [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) elementu. Ta wartość może zawierać:  
  
-   `SmartDevice-NETCFv1`: Określa, że elementy docelowe szablonu [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] w wersji 1.0.  
  
-   `SmartDevice-NETCFv2`: Określa, że elementy docelowe tempalate [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] w wersji 2.0.  
  
 Jeśli szablon zawiera `ProjectType` element o wartości `Web`, `ProjectSubType` element określa język programowania szablonu. Ten element może mieć następujące wartości:  
  
-   `CSharp`: Określa, czy szablon tworzy [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] sieci Web projektu lub elementu.  
  
-   `VisualBasic`: Określa, czy szablon tworzy [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] sieci Web projektu lub elementu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono metadanych szablon projektu do [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] element docelowy aplikacji urządzenia [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] w wersji 2.0.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic device template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>  
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
 [Tworzenie szablony projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [ProjectType — Element (szablony Visual Studio)](../extensibility/projecttype-element-visual-studio-templates.md)