---
title: "Tworzenie szablonów wielu projektów dla programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, creating multi-project
- project templates, multi-project
- multi-project templates
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 86952d3b742abf3b73b22e17d695717ca8dac9bd
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-create-multi-project-templates"></a>Porady: Tworzenie szablonów wielu projektów

Szablony wieloprojektowe działają jak kontenery dla dwóch lub więcej projektów. Podczas tworzenia projektu jest oparty na szablonie wielu projektów z **nowy projekt** okno dialogowe, każdy projekt w szablonie zostanie dodany do rozwiązania.

Szablon projektu wielu zawiera dwa lub więcej szablonów projektu i szablonu głównego typu `ProjectGroup`.

Szablony wielu projektów zachowywać się inaczej niż szablony pojedynczego projektu. Mają one unikatowe następujące właściwości:

- Poszczególnych projektów w szablonie wielu projektów nie można przypisać nazwy w **nowy projekt** okno dialogowe. Zamiast tego należy użyć `ProjectName` atrybutu `ProjectTemplateLink` elementu w pliku .vstemplate, aby określić nazwę dla każdego projektu.

- Szablony wielu projektów mogą zawierać projektów dla różnych języków, ale cały szablonu mogą być przełączane tylko w jednej kategorii. Określ kategorię szablonu w `ProjectType` elementu w pliku .vstemplate.

Szablon wielu projektów musi zawierać następujące elementy skompresowane w pliku .zip:

- Główny plik .vstemplate całego szablonu wielu projektów. Ten plik .vstemplate głównego zawiera metadanych który **nowy projekt** okno dialogowe wyświetla i określa, gdzie można znaleźć pliku .vstemplate dla projektów w szablonie. Ten plik musi znajdować się w katalogu głównym pliku zip.

- Co najmniej dwa foldery zawierające pliki, które są wymagane dla szablonu kompletnego projektu. W tym wszystkie pliki kodu dla projektu i pliku .vstemplate dla projektu.

Na przykład plik .zip szablonów wielu projektów, który zawiera dwa projekty mają następujące pliki i katalogi:

- MultiProjectTemplate.vstemplate
- \Project1\Project1.vstemplate
- \Project1\Project1.vbproj
- \Project1\Class.VB
- \Project2\Project2.vstemplate
- \Project2\Project2.vbproj
- \Project2\Class.VB

Główny plik .vstemplate szablonu wielu projektów różni się od szablonu pojedynczych projektów w następujący sposób:

- `Type` Atrybutu `VSTemplate` element ma wartość `ProjectGroup` zamiast `Project`. Na przykład:

    ```xml
    <VSTemplate Version="2.0.0" Type="ProjectGroup"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    ```

- `TemplateContent` Element zawiera `ProjectCollection` element, który ma co najmniej jeden `ProjectTemplateLink` elementów, które określają ścieżki do plików .vstemplate dołączone projektów. Na przykład:

    ```xml
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

## <a name="to-create-a-multi-project-template-from-an-existing-solution"></a>Aby utworzyć szablon wielu projektów z istniejącego rozwiązania

1. Tworzenie rozwiązania, a następnie dodaj dwie lub więcej projektów.

1. Dostosowywanie projektów, dopóki gotowe do wyeksportowania do szablonu.

1. Na **projektu** menu, wybierz **Eksportuj szablon...** .

   **Kreatora eksportowania szablonu** otwiera.

1. Na **wybierz typ szablonu** wybierz pozycję **szablonu projektu**. Wybierz projekt, aby wyeksportować do szablonu, a następnie wybierz pozycję **dalej**.

1. Na **wybierz opcje szablonu** wprowadź nazwę i opcjonalny opis, ikonę i obrazu podglądu dla szablonu. Wybierz **Zakończ**.

   Projekt jest wyeksportowany do pliku zip i umieszczane w lokalizacji określonej w danych wyjściowych.

   > [!NOTE]
   > Każdy projekt musi być eksportowany do szablonu osobno, więc Powtórz te czynności dla każdego projektu w rozwiązaniu.

1. Utwórz katalog dla szablonu, w podkatalogu dla każdego projektu.

1. Wyodrębnij zawartość pliku .zip każdego projektu w podkatalogu odpowiedniego nowo utworzony.

1. W katalogu podstawowego, Utwórz plik XML z **.vstemplate** rozszerzenia pliku. Ten plik zawiera metadanych dla szablonów wielu projektów. Zobacz przykład poniżej dla struktury pliku. Należy określić ścieżkę względną do każdego projektu pliku .vstemplate.

1. Wybierz katalog podstawowy, a z menu kliknij prawym przyciskiem myszy lub kontekstu wybierz **przesyłają** > **skompresowanego folderu (zip)**.

   Pliki i foldery są kompresowane do pliku zip.

1. Skopiuj plik zip do katalogu szablonu projektu użytkownika. Domyślnie ten katalog jest %USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ProjectTemplates.

1. W programie Visual Studio Otwórz **nowy projekt** okna dialogowego i zweryfikować, czy szablon jest widoczny.

## <a name="two-project-example"></a>Przykład dwa projektu

Ten przykład przedstawia plik .vstemplate podstawowe głównego wielu projektów. W tym przykładzie szablon zawiera dwa projekty `My Windows Application` i `My Class Library`. `ProjectName` Atrybutu `ProjectTemplateLink` element Określa nazwę, która znajduje się w projekcie.

> [!TIP]
> Jeśli `ProjectName` atrybut nie jest określony, nazwa pliku .vstemplate jest używana jako nazwa projektu.

```xml
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

## <a name="example-with-solution-folders"></a>Przykład: foldery rozwiązania

W tym przykładzie użyto `SolutionFolder` elementu, aby podzielić na dwie grupy projektów `Math Classes` i `Graphics Classes`. Szablon zawiera cztery projektów, z których dwa są umieszczane w każdym folderze rozwiązania.

```xml
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

## <a name="see-also"></a>Zobacz także

[Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)  
[Porady: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)  
[Visual Studio odwołanie do schematu szablonu (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)  
[SolutionFolder — element (szablony Visual Studio)](../extensibility/solutionfolder-element-visual-studio-templates.md)  
[Projecttemplatelink — element (szablony Visual Studio)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
