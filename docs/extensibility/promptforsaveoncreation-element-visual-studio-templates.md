---
title: "Promptforsaveoncreation — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#PromptForSaveOnCreation
helpviewer_keywords: PromptForSaveOnCreation element [Visual Studio project templates]
ms.assetid: 75174674-0c3c-4b57-b2fd-6ea8e817b67d
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8ce7e73801b34542bcf1c6be35d950b1fabdc7c3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="promptforsaveoncreation-element-visual-studio-templates"></a>PromptForSaveOnCreation — Element (szablony Visual Studio)
Określa, czy użytkownik jest monitowany o projektu lokalizacji za pośrednictwem zapisywania **nowy projekt** okno dialogowe podczas tworzenia projektu. Jeśli ten element jest ustawiony na `true`, a następnie użytkownik jest monitowany o zapisanie lokalizacji; Jeśli `false`, nie monit. (To znaczy, że projekt tymczasowy jest tworzony.)  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<Promptforsaveoncreation — >  
  
## <a name="syntax"></a>Składnia  
  
```  
<PromptForSaveOnCreation> true/false </PromptForSaveOnCreation>  
```  
  
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
  
 Tekst musi być równa albo `true` lub `false`, `true` wskazujący, że użytkownik będzie monitowany do zapisywania lokalizacji podczas tworzenia nowego projektu.  
  
## <a name="remarks"></a>Uwagi  
 `PromptForSaveOnCreation`to opcjonalny element. Wartość domyślna to `false`.  
  
 Tymczasowe projekty są projektów, które można tworzyć i modyfikować bez zapisywania zawartości tego projektu na dysku. Aby uzyskać więcej informacji, zobacz [NIB tymczasowe projekty](http://msdn.microsoft.com/en-us/9cf1944c-7045-44cc-8701-7b0eb4099f2b).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie ustawiono wartość `PromptForSaveOnCreation` równa `false`, określającej umożliwia projekt do utworzenia jako tymczasowy projektu.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <PromptForSaveOnCreation>false</PromptForSaveOnCreation>  
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