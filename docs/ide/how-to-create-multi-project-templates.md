---
title: Tworzenie szablonów wielu projektów dla programu Visual Studio
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-project
- project templates, multi-project
- multi-project templates
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8f28e451da90d9709eda1886a549819b4d46415f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-multi-project-templates"></a>Porady: Tworzenie szablonów wielu projektów

Szablony wieloprojektowe działają jak kontenery dla dwóch lub więcej projektów. Podczas tworzenia projektu jest oparty na szablonie wielu projektów z **nowy projekt** okno dialogowe, każdy projekt w szablonie zostanie dodany do rozwiązania.

Szablon projektu wielu ma co najmniej dwa szablony projektów i szablonu głównego typu `ProjectGroup`.

Szablony wielu projektów zachowywać się inaczej niż szablony pojedynczego projektu. Mają one unikatowe następujące właściwości:

- Poszczególnych projektów w szablonie wielu projektów nie można przypisać nazwy w **nowy projekt** okno dialogowe. Zamiast tego należy użyć `ProjectName` atrybutu `ProjectTemplateLink` element *vstemplate* plik, aby określić nazwę dla każdego projektu.

- Szablony wielu projektów mogą zawierać projektów dla różnych języków, ale cały szablonu mogą być przełączane tylko w jednej kategorii. Określ kategorię szablonu w `ProjectType` elementu *vstemplate* pliku.

Szablon wielu projektów musi zawierać następujące elementy skompresowane w *.zip* pliku:

- Katalog główny *vstemplate* dla całego szablonu wielu projektów. Ten katalog główny *vstemplate* zawierający metadane który **nowy projekt** okno dialogowe wyświetla i określa, gdzie można znaleźć *vstemplate* pliki projektów w szablon. Ten plik musi znajdować się w katalogu głównym *.zip* pliku.

- Co najmniej dwa foldery zawierające pliki, które są wymagane dla szablonu kompletnego projektu. Foldery obejmują wszystkie pliki kodu dla projektu, a także *vstemplate* w pliku projektu.

Na przykład szablonów wielu projektów *zip* plik, który zawiera dwa projekty mają następujące pliki i katalogi:

- *MultiProjectTemplate.vstemplate*
- *\Project1\Project1.vstemplate*
- *\Project1\Project1.vbproj*
- *\Project1\Class.VB*
- *\Project2\Project2.vstemplate*
- *\Project2\Project2.vbproj*
- *\Project2\Class.VB*

Katalog główny *vstemplate* plik szablonu wielu projektów różni się od szablonu pojedynczych projektów w następujący sposób:

- `Type` Atrybutu `VSTemplate` element ma wartość `ProjectGroup` zamiast `Project`. Na przykład:

    ```xml
    <VSTemplate Version="2.0.0" Type="ProjectGroup"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    ```

- `TemplateContent` Element zawiera `ProjectCollection` element, który ma co najmniej jeden `ProjectTemplateLink` elementów, które definiują ścieżki do *vstemplate* pliki uwzględnione projektów. Na przykład:

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

1. Na **projektu** menu, wybierz **Eksportuj szablon**.

   **Kreatora eksportowania szablonu** otwiera.

1. Na **wybierz typ szablonu** wybierz pozycję **szablonu projektu**. Wybierz projekt, aby wyeksportować do szablonu, a następnie wybierz pozycję **dalej**.

1. Na **wybierz opcje szablonu** wprowadź nazwę i opcjonalny opis, ikonę i obrazu podglądu dla szablonu. Wybierz **Zakończ**.

   Projekt został wyeksportowany do *.zip* plików i umieszczane w lokalizacji określonej w danych wyjściowych.

   > [!NOTE]
   > Każdy projekt musi być eksportowany do szablonu osobno, więc Powtórz te czynności dla każdego projektu w rozwiązaniu.

1. Utwórz katalog dla szablonu, w podkatalogu dla każdego projektu.

1. Wyodrębnij zawartość każdego projektu *.zip* pliku do podkatalogu odpowiedniego utworzony.

1. W katalogu podstawowego, Utwórz plik XML z *.vstemplate* rozszerzenia pliku. Ten plik zawiera metadanych dla szablonów wielu projektów. Zobacz przykład poniżej dla struktury pliku. Należy określić ścieżkę względną do każdego projektu *vstemplate* pliku.

1. Wybierz katalog podstawowy, a z menu kliknij prawym przyciskiem myszy lub kontekstu wybierz **przesyłają** > **skompresowanego folderu (zip)**.

   Pliki i foldery są skompresowane w *.zip* pliku.

1. Kopiuj *zip* plik do katalogu szablonu projektu użytkownika. Domyślnie ten katalog jest *%USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ProjectTemplates*.

1. W programie Visual Studio Otwórz **nowy projekt** okna dialogowego i zweryfikować, czy szablon jest widoczny.

## <a name="two-project-example"></a>Przykład dwa projektu

W tym przykładzie przedstawiono podstawowe głównego wielu projektów *vstemplate* pliku. W tym przykładzie szablon ma dwa projekty `My Windows Application` i `My Class Library`. `ProjectName` Atrybutu `ProjectTemplateLink` element Określa nazwę, która znajduje się w projekcie.

> [!TIP]
> Jeśli `ProjectName` atrybut nie jest określony, nazwa *vstemplate* plik jest używany jako nazwa projektu.

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

W tym przykładzie użyto `SolutionFolder` elementu, aby podzielić na dwie grupy projektów `Math Classes` i `Graphics Classes`. Szablon ma cztery projektów, z których dwa są umieszczane w każdym folderze rozwiązania.

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

- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Porady: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)
- [Visual Studio odwołanie do schematu szablonu (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)
- [SolutionFolder — element (szablony Visual Studio)](../extensibility/solutionfolder-element-visual-studio-templates.md)
- [Projecttemplatelink — element (szablony Visual Studio)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)