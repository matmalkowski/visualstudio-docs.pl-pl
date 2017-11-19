---
title: "Porady: Tworzenie szablonów wielu projektów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, creating multi-project templates
- project templates, creating multi-project templates
- multi-project templates
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9d4ffd6c3aa23ebc2b801de2d581876ff5afd480
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-multi-project-templates"></a>Porady: tworzenie szablonów wielu projektów
Szablony wieloprojektowe działają jak kontenery dla dwóch lub więcej projektów. Jeśli projekt na podstawie wielu projektów szablonu jest tworzona na podstawie **nowy projekt** okno dialogowe, każdy projekt w szablonie zostanie dodany do rozwiązania.  
  
 Szablon wielu projektów musi zawierać następujące elementy skompresowane w pliku .zip:  
  
-   Główny plik .vstemplate całego szablonu wielu projektów. Ten plik .vstemplate głównego zawiera metadanych który **nowy projekt** okno dialogowe wyświetla i określa, gdzie można znaleźć pliku .vstemplate dla projektów w tym szablonie. Ten plik musi znajdować się w katalogu głównym pliku zip.  
  
-   Jeden lub więcej folderów zawierających pliki, które są wymagane dla szablonu kompletnego projektu. W tym wszystkie pliki kodu dla projektu i pliku .vstemplate dla projektu.  
  
 Na przykład plik .zip szablonów wielu projektów, który zawiera dwa projekty mają następujące pliki i katalogi:  
  
 MultiProjectTemplate.vstemplate  
  
 \Project1\Project1.vstemplate  
  
 \Project1\Project1.vbproj  
  
 \Project1\Class.VB  
  
 \Project2\Project2.vstemplate  
  
 \Project2\Project2.vbproj  
  
 \Project2\Class.VB  
  
 Główny plik .vstemplate szablonu wielu projektów różni się od szablonu pojedynczych projektów w następujący sposób:  
  
-   `Type` Atrybutu `VSTemplate` element zawiera wartość `ProjectGroup`. Na przykład:  
  
    ```  
    <VSTemplate Version="2.0.0" Type="ProjectGroup"  
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    ```  
  
-   `TemplateContent` Element zawiera `ProjectCollection` element, który ma co najmniej jeden `ProjectTemplateLink` elementów, które określają ścieżki do plików .vstemplate dołączone projektów. Na przykład:  
  
    ```  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink>  
                Project1\Project1.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink>  
                Project2\Project2.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
    ```  
  
 Szablony wielu projektów także zachowywać się inaczej niż normalne szablonów. Szablony wielu projektów ma następującą charakterystykę unikatowy:  
  
-   Poszczególnych projektów w szablonie wielu projektów nie można przypisać nazwy **nowy projekt** okno dialogowe. Zamiast tego należy użyć `ProjectName` atrybutu `ProjectTemplateLink` element, aby określić nazwę dla każdego projektu. Aby uzyskać więcej informacji zobacz przykład pierwszy w następnej sekcji.  
  
-   Szablony wielu projektów może zawierać projekty napisane w różnych językach, ale cały szablonu mogą być dopuszczone w jednej kategorii przez przy użyciu `ProjectType` elementu.  
  
### <a name="to-create-a-multi-project-template"></a>Aby utworzyć szablon wielu projektów  
  
1.  Tworzenie projektów do uwzględnienia w szablonie wielu projektów.  
  
2.  Tworzenie plików .vstemplate dla każdego projektu. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md).  
  
3.  Utwórz plik .vstemplate głównego do przechowywania metadanych dla szablonów wielu projektów. Aby uzyskać więcej informacji zobacz przykład pierwszy w następnej sekcji.  
  
4.  Wybierz pliki i foldery, aby uwzględnić w szablonie, kliknij prawym przyciskiem myszy zaznaczenie, kliknij przycisk **Wyślij do**, a następnie kliknij przycisk **skompresowany Folder (zip)**. Pliki i foldery są kompresowane do pliku zip.  
  
5.  Umieść plik zip szablonu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] katalogu szablonu projektu. Domyślnie ten katalog jest \My Studio *wersji*\Templates\ProjectTemplates\\.  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia plik .vstemplate podstawowe głównego wielu projektów. W tym przykładzie szablon zawiera dwa projekty `My Windows Application` i `My Class Library`. `ProjectName` Atrybutu `ProjectTemplateLink` element ustawia nazwę [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] można przypisać tego projektu. Jeśli `ProjectName` atrybut nie istnieje, nazwa pliku .vstemplate jest używana jako nazwa projektu.  
  
```  
<VSTemplate Version="2.0.0" Type="ProjectGroup"  
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
            <ProjectTemplateLink ProjectName="My Class Library">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `SolutionFolder` elementu, aby podzielić na dwie grupy projektów `Math Classes` i `Graphics Classes`. Szablon zawiera cztery projektów, z których dwa są umieszczane w każdym folderze rozwiązania.  
  
```  
<VSTemplate Version="2.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <SolutionFolder Name="Math Classes">  
                <ProjectTemplateLink ProjectName="MathClassLib1">  
                    MathClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="MathClassLib2">  
                    MathClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
            <SolutionFolder Name="Graphics Classes">  
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">  
                    GraphicsClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">  
                    GraphicsClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie szablony projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Porady: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)   
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [SolutionFolder — Element (szablony Visual Studio)](../extensibility/solutionfolder-element-visual-studio-templates.md)   
 [Projecttemplatelink — Element (szablony Visual Studio)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)