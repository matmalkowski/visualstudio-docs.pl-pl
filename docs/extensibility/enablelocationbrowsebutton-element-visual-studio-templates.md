---
title: "EnableLocationBrowseButton — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton
helpviewer_keywords: EnableLocationBrowseButton [Visual Studio project templates]
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e9271df96f5fa84044b33550e0d73750030d7e66
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>EnableLocationBrowseButton — Element (szablony Visual Studio)
Określa, czy **Przeglądaj** przycisk jest dostępny w **nowy projekt** okna dialogowego, dzięki czemu użytkownicy mogą łatwo modyfikować domyślny katalog, w której jest zapisywany nowy projekt.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<EnableLocationBrowseButton >  
  
## <a name="syntax"></a>Składnia  
  
```  
<EnableLocationBrowseButton> true/false </EnableLocationBrowseButton>  
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
  
 Tekst musi być równa albo `true` lub `false`, wskazującą, czy należy wyświetlić **Przeglądaj** znajdującego się na **nowy projekt** okno dialogowe.  
  
## <a name="remarks"></a>Uwagi  
 `EnableLocationBrowseButton`to opcjonalny element. Wartość domyślna to `true`, która wyświetla **Przeglądaj** przycisk **nowy projekt** okno dialogowe.  
  
 W **nowy projekt** okno dialogowe **lokalizacji** pola tekstowego określa katalog, w której jest zapisywany nowy projekt. **Przeglądaj** przycisk pomaga zmodyfikować tego katalogu, wyświetlając **lokalizacji projektu** okno dialogowe, które umożliwia łatwe przejście do innego katalogu, który jest dostępny z komputera, a następnie wybierz go jako katalog, w której jest zapisywany nowy projekt.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia metadanych dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji systemu Windows.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>  
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