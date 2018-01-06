---
title: "Tworzenie szablonów sieci Web dla programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/02/2018
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f94823131e568b3f1f254ead9d760210a4c9c1e0
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-manually-create-web-templates"></a>Porady: ręczne tworzenie szablonów sieci Web

Tworzenie szablonów sieci Web różni się od tworzenia inne rodzaje szablonów. Ponieważ szablony projektów sieci Web są wyświetlane w **Dodaj nową witrynę sieci Web** okno dialogowe i elementy projektu sieci Web są pogrupowane według języka programowania, plik .vstemplate musi określić szablon jako szablon sieci Web i zidentyfikować programowania język.

> [!NOTE]
> Szablony sieci Web musi zawierać plik .webproj puste i muszą być przywoływane w pliku .vstemplate `File` atrybutu `Project` elementu. Mimo że projekty sieci Web nie jest wymagana. \*proj pliku projektu jest niezbędne do utworzenia tego pliku klasy zastępczej dla szablonu sieci Web mógł działać poprawnie.

### <a name="to-manually-create-a-web-template"></a>Aby ręcznie utworzyć szablon sieci Web

1. Utwórz projekt sieci Web.

1. Zmodyfikować lub usunąć pliki w projekcie lub dodanie nowych plików do projektu.

1. Tworzenie pliku XML i zapisz go z rozszerzeniem nazwy pliku .vstemplate, w tym samym katalogu co projektu. Nie należy dodawać go do projektu programu Visual Studio.

1. Edytuj plik .vstemplate XML do udostępnienia metadanych szablonu projektu. Aby uzyskać więcej informacji, zobacz [przykładzie](#example).

1. Zlokalizuj `ProjectType` element w pliku .vstemplate i Ustaw tekst do wartości `Web`.

1. Po `ProjectType` elementu, Dodaj `ProjectSubType` element i ustaw wartość tekstową na język programowania szablonu. Język programowania może być jedną z następujących wartości:

    - CSharp
    - Języka Visual Basic

    Na przykład:

    ```xml
    <TemplateData>
        ...
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        ...
    </TemplateData>
    ```

1. Wybierz pliki do szablonu (w tym pliku .vstemplate), kliknij prawym przyciskiem myszy zaznaczenie, a następnie wybierz pozycję **przesyłają** > **skompresowanego folderu (zip)**. Pliki są kompresowane do pliku zip.

1. Umieść plik zip szablonu w katalogu szablonu projektu programu Visual Studio. Domyślnie ten katalog jest %USERPROFILE%\Documents\Visual Studio \<wersji\>\ProjectTemplates.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono plik podstawowy .vstemplate szablonu projektu sieci Web:

```xml
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

## <a name="see-also"></a>Zobacz także

[Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)  
[Odwołanie do schematu szablonu Visual Studio (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)