---
title: "Supportslanguagedropdown — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: be21f7d98a897df6f44208c6224c1db5c56b70e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>SupportsLanguageDropDown — Element (szablony Visual Studio)
Określa, czy szablon elementu sieci Web jest identyczny dla wielu języków oraz czy **języka** jest włączona opcja **Dodaj nowy element** okno dialogowe.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<Supportslanguagedropdown — >  
  
## <a name="syntax"></a>Składnia  
  
```  
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>  
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
  
 Tekst musi być równa albo `true` lub `false`, wskazujące, czy **języka** opcja jest dostępna z **Dodaj nowy element** okno dialogowe.  
  
## <a name="remarks"></a>Uwagi  
 `SupportsLanguageDropDown`to opcjonalny element. Wartość domyślna to `false`.  
  
 `SupportsLanguageDropDown` Element jest dostępny tylko dla szablonów elementów sieci Web.  
  
 Jeśli ustawiono wartość dla tego elementu `true`, a następnie szablon elementu jest taka sama dla wszystkich języków programowania i **języka** opcja jest włączona w **Dodaj nowy element** okno dialogowe. Ta opcja umożliwia wybranie języka programowania nowego elementu, który ma zostać utworzona na podstawie szablonu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie do wyświetlenia **języka** listy rozwijanej opcję.  
  
```  
<VSTemplate Version="3.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)