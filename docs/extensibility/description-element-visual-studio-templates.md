---
title: "Description — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Description element [Visual Studio project templates]
ms.assetid: 6e12be73-081f-4c7d-898f-027c307a9fe1
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7e58ee9b351acaeaabb842abd1c9e4d04ec1a189
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="description-element-visual-studio-templates"></a>Description — Element (szablony Visual Studio)
Określa opis szablonu, pojawiającą się w jednej **nowy projekt** lub **Dodaj nowy element** okno dialogowe.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<Opis elementu >  
  
## <a name="syntax"></a>Składnia  
  
```  
<Description>  
    Template Description  
</Description>  
```  
  
```  
<Description Package="{PackageID}" ID="ResourceID" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Package`|Opcjonalny atrybut dla użytkowników zaawansowanych scenariuszy.<br /><br /> Identyfikator GUID, który określa pakiet programu Visual Studio.|  
|`ID`|Opcjonalny atrybut dla użytkowników zaawansowanych scenariuszy.<br /><br /> Określa identyfikator zasobu programu Visual Studio.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Kategoryzuje szablonu i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagany, chyba że `Package` i `ID` są używane atrybuty.  
  
 Tekst zawiera opis szablonu.  
  
## <a name="remarks"></a>Uwagi  
 `Description`jest elementem podrzędnym wymagane `TemplateData` elementu.  
  
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
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)