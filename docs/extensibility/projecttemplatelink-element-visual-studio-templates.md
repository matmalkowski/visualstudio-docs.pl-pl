---
title: "Projecttemplatelink — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9e614b2ec8ef404ef21e665ac5ae26dd73253f55
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>ProjectTemplateLink — Element (szablony Visual Studio)
Określa ścieżkę do pliku .vstemplate jednego projektu w szablonie wieloprojektowym.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Projectcollection — >  
 \<Projecttemplatelink — >  
—lub—  
\<VSTemplate >  
 \<TemplateContent >  
 \<Projectcollection — >  
 \<SolutionFolder >  
 \<Projecttemplatelink — >  
  
## <a name="syntax"></a>Składnia  
  
```  
<ProjectTemplateLink ProjectName="Name">  
    PathToTemplateFile  
</ProjectTemplateLink>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`ProjectName`|Atrybut opcjonalny.<br /><br /> Określa nazwę każdego indywidualnego projektu w szablonie wieloprojektowym. **Nowy projekt** okno dialogowe nie można przypisać nazwy do poszczególnych projektów.|  
|`CopyParameters`|Umożliwia kopiowanie wszystkich zmiennych z głównego szablonu grupowego do poszczególnych połączonych szablonów.<br /><br /> Parametry w połączonych szablony mają prefiks `"$ext_*$"`. Na przykład, jeśli w szablonie grupy nadrzędnej parametr `$projectname$` ma wartość **ExampleProject1**połączonego szablonu pobiera kolei ma być wykonywana, gdy uzyskuje on parametr `$ext_projectname$`, który jest kopią `$projectname$`parametr szablonu grupy nadrzędnej.<br /><br /> Dzięki temu połączone szablony mogą korzystać z niektórych wspólnych parametrów tworzonych wygodnie tylko w nadrzędnym szablonie grupowym.<br /><br /> Ten atrybut jest opcjonalny i domyślnie automatycznie do `false` gdy nie jest dołączony.<br /><br /> Wprowadzona w programie Visual Studio 2013 Update 2. Aby odwołać wersji produktu jest poprawny, zobacz [odwołania do zestawów dostarczane w Visual Studio 2013 SDK Update 2](http://msdn.microsoft.com/en-us/42b65c3e-e42b-4c39-98c8-bea285f25ffb).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Projectcollection —](../extensibility/projectcollection-element-visual-studio-templates.md)|Określa organizację i zawartość szablonów wieloprojektowych.|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Grupowanie projektów w szablonach wieloprojektowych.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Ten tekst określa ścieżkę do pliku .vstemplate szablonu.  
  
## <a name="remarks"></a>Uwagi  
 Szablony wieloprojektowe działają jak kontenery dla dwóch lub więcej projektów. `ProjectTemplateLink` Element jest używany do określenia lokalizacji pliku .vstemplate dla jednego z projektów w szablonie. Plik .vstemplate szablonu projektu wielu zawiera jeden `ProjectTemplateLink` elementu dla każdego projektu w szablonie. Aby uzyskać więcej informacji dotyczących szablonów wielu projektów, zobacz [porady: Tworzenie szablonów wielu projektów](../ide/how-to-create-multi-project-templates.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano prosty główny plik .vstemplate szablonu wieloprojektowego. W tym przykładzie szablon zawiera dwa projekty `My Windows Application` i `My Class Library`. `ProjectName` Atrybutu `ProjectTemplateLink` element ustawia nazwę [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] można przypisać tego projektu. Jeśli `ProjectName` atrybut nie istnieje, nazwa pliku .vstemplate jest używana jako nazwa projektu.  
  
```  
<VSTemplate Version="3.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink ProjectName="My Windows Application">  
                WindowsApp\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablony projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Instrukcje: Tworzenie szablonów obejmujących wiele projektów](../ide/how-to-create-multi-project-templates.md)