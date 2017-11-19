---
title: "Porady: ręczne tworzenie szablonów sieci Web | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5d5f34e421160e8cca56897e6530ff47da7b1a84
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-manually-create-web-templates"></a>Porady: ręczne tworzenie szablonów sieci Web
Tworzenie szablonów sieci Web różni się od tworzenia inne rodzaje szablonów. Ponieważ szablony projektów sieci Web są wyświetlane w **Dodaj nową witrynę sieci Web** okno dialogowe i elementy projektu sieci Web są pogrupowane według języka programowania, plik .vstemplate musi określić szablon jako szablon sieci Web i zidentyfikować programowania język.  
  
> [!NOTE]
>  Szablony sieci Web musi zawierać .webproj pusty plik, który jest określana za pomocą `File` atrybutu `Project` elementu. Mimo że projekty sieci Web nie jest wymagane pliki projektu, ten plik jest wymagany, aby szablon sieci Web działa prawidłowo.  
  
### <a name="to-manually-create-a-web-template"></a>Aby ręcznie utworzyć szablon sieci Web  
  
1.  Utwórz projekt sieci Web.  
  
2.  Zmodyfikować lub usunąć pliki w projekcie lub dodanie nowych plików do projektu.  
  
3.  Tworzenie pliku XML i zapisz go przy użyciu rozszerzenie nazwy pliku .vstemplate w tym samym katalogu co projektu. Nie należy dodawać do projektu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Tworzenie pliku XML .vstemplate do udostępnienia metadanych szablonu projektu. Aby uzyskać więcej informacji zobacz przykład w następnej sekcji.  
  
5.  Zlokalizuj `ProjectType` element w pliku .vstemplate i Ustaw tekst do wartości `Web`.  
  
6.  Po `ProjectType` elementu, Dodaj `ProjectSubType` element i ustaw wartość tekstową na język programowania szablonu. Język programowania może być jedną z następujących wartości:  
  
    -   CSharp  
  
    -   Języka Visual Basic  
  
     Na przykład:  
  
    ```  
    <TemplateData>  
        ...  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        ...  
    </TemplateData>  
    ```  
  
7.  Wybierz pliki do szablonu (w tym pliku .vstemplate), kliknij prawym przyciskiem myszy zaznaczenie, kliknij przycisk **Wyślij do**, a następnie kliknij przycisk **skompresowany Folder (zip)**. Pliki są kompresowane do pliku zip.  
  
8.  Umieść plik zip szablonu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] katalogu szablonu projektu. Domyślnie ten katalog jest \My Studio *wersji*\My wyeksportowane szablony\\.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono plik podstawowy .vstemplate szablonu projektu sieci Web.  
  
```  
<VSTemplate Version="2.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
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
 [Tworzenie szablony projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)