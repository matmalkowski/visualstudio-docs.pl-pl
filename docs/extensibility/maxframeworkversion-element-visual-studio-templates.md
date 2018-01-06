---
title: "Maxframeworkversion — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c473b3253809c09f9ba0af90f7a0fed349dedb93
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion — Element (szablony Visual Studio)
Określa maksymalną wersję programu .NET Framework, która jest wymagana przez szablon. Określa, czy szablon jest wyświetlany w **szablony** sekcji **Dodawanie nowego projektu** okno dialogowe, na podstawie wartości, który wybrano w **wersja docelowego Frameworka** pole **Dodawanie nowego projektu** okno dialogowe.  
  
 \<VSTemplate >  
 \<Maxframeworkversion — >  
  
## <a name="syntax"></a>Składnia  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
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
  
 Tekst musi być najwyższym numerze wersji programu .NET Framework, która jest dozwolona przez szablon.  
  
## <a name="remarks"></a>Uwagi  
 `MaxFrameworkVersion`to opcjonalny element. Element w `TemplateData` sekcji w pliku .vstemplate działa jako filtr dla **szablony** sekcji **Dodawanie nowego projektu** okno dialogowe. Tylko szablony, w których wymagania .NET Framework są mniej niż `MaxFrameworkVersion` wartości elementu pojawi się na podstawie wartości, który wybrano w **wersja docelowego Frameworka** pole **Dodawanie nowego projektu**okno dialogowe. `MaxFrameworkVersion` Elementu należy pominąć, chyba że jest wymagane w celu mogą przypadkowo spowodować szablony będą wyświetlane, gdy są one używane z nowszymi wersjami programu .NET Framework.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia metadanych dla standardowej [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] szablonu klasy.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 W tym przykładzie maksymalna wersja .NET Framework, która jest wymagana przez szablon, reprezentowany przez `MaxFrameworkVersion`, jest 3.5. Powyższego szablonu będą wyświetlane tylko po wybraniu 3.0 lub 3.5 w **wersja docelowego Frameworka** polu **Dodawanie nowego projektu** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)