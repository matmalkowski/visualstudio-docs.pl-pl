---
title: Tworzenie szablonów sieci web dla programu Visual Studio
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: aeaeea5ee4d1d8e65cdc13ca11192a70e0459be1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942412"
---
# <a name="how-to-manually-create-web-templates"></a>Porady: ręczne tworzenie szablonów sieci web

Tworzenie szablonów sieci web różni się od tworzenia inne rodzaje szablonów. Ponieważ szablony projektów sieci web są wyświetlane w **Dodaj nową witrynę sieci Web** okno dialogowe i projekt sieci web elementy są podzielone według języków programowania, *vstemplate* pliku należy określić szablon jako szablon sieci web i zidentyfikuj języka programowania.

> [!NOTE]
> Szablony sieci Web musi zawierać pole *.webproj* pliku który musi odwoływać się do *vstemplate* w pliku `File` atrybutu `Project` elementu. Mimo że projekty sieci Web nie wymagają *.proj* pliku projektu jest niezbędne do utworzenia tego pliku klasy zastępczej dla szablonu sieci web mógł działać poprawnie.

## <a name="to-manually-create-a-web-template"></a>Aby ręcznie utworzyć szablon sieci web

1. Utwórz projekt sieci web.

1. Zmodyfikować lub usunąć pliki w projekcie lub dodanie nowych plików do projektu.

1. Tworzenie pliku XML i zapisz go przy użyciu *vstemplate* rozszerzeniem, w tym samym katalogu co projektu. Nie należy dodawać go do projektu programu Visual Studio.

1. Edytuj *vstemplate* pliku XML do udostępnienia metadanych szablonu projektu. Aby uzyskać więcej informacji, zobacz [przykładzie](#example).

1. Zlokalizuj `ProjectType` element *vstemplate* pliku i ustaw wartości tekstowej `Web`.

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

1. Wybierz pliki do szablonu (w tym *vstemplate* pliku), kliknij prawym przyciskiem myszy zaznaczenie i wybierz **przesyłają** > **skompresowanego folderu (zip)**. Pliki są skompresowane w *.zip* pliku.

1. Umieść *.zip* pliku szablonu w katalogu szablonu projektu programu Visual Studio. Domyślnie ten katalog jest *%USERPROFILE%\Documents\Visual Studio \<wersji\>\ProjectTemplates*.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono podstawowego *vstemplate* pliku szablonu projektu sieci web:

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

- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Visual Studio odwołanie do schematu szablonu (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)