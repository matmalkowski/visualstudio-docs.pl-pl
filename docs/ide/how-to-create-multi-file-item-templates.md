---
title: "Tworzenie szablonów elementów wielu plików dla programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f1d5b11c97b7f214a13225b5605f47e3d3a45966
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-create-multi-file-item-templates"></a>Porady: Tworzenie szablonów elementów wielu plików

Szablony elementów może określać tylko jeden element, ale czasami element składa się z wielu plików. Szablon elementu formularzy systemu Windows wymaga na przykład trzy następujące pliki:

- Plik zawierający kod dla formularza

- Plik zawierający informacje projektanta formularza

- Plik zawierający zasoby osadzone w formularzu

Szablony elementów wielu plików wymagane parametry, aby upewnić się, że właściwy plik rozszerzenia są używane podczas tworzenia elementu. W przypadku utworzenia szablonów elementów wielu plików za pomocą **Kreatora eksportowania szablonu**, te parametry są generowane automatycznie i żadne dodatkowe edycji jest wymagana.

## <a name="to-create-a-multi-file-item-template-by-using-the-export-template-wizard"></a>Aby utworzyć szablon elementów wielu plików za pomocą Kreatora eksportowania szablonu

Można utworzyć szablon elementów wielu plików tak samo, jak szablon elementu pojedynczego pliku. Zobacz [porady: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md). Na **wybierz element do eksportowania** strony kreatora, wybierz plik, który zawiera pliki zależne (na przykład plik formularza formularzy systemu Windows). Kreator automatycznie uwzględnia pliki zależne, takie jak projektanta i pliki zasobów w szablonie.

## <a name="to-manually-create-a-multi-file-item-template"></a>Ręczne tworzenie szablonów elementów wielu plików

1. Utwórz szablon elementu po czy ręcznie utworzyć szablon elementu pojedynczego pliku, ale zawierają każdego pliku, który stanowi elementów wielu plików.

1. W pliku .vstemplate XML, Dodaj `ProjectItem` elementu dla poszczególnych plików, a następnie dodaj `TargetFileName` atrybutu do tego elementu. Ustaw wartość `TargetFileName` atrybutu $fileinputname$. *FileExtension*, gdzie *FileExtension* jest rozszerzeniem pliku jest zawarta w szablonie. Na przykład:

    ```xml
    <ProjectItem TargetFileName="$fileinputname$.vb">
        Form1.vb
    </ProjectItem>
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">
        Form1.Designer.vb
    </ProjectItem>
    <ProjectItem TargetFileName="$fileinputname$.resx">
        Form1.resx
    </ProjectItem>
    ```

     > [!NOTE]
     > Gdy element uzyskanych z tego szablonu zostanie dodany do projektu, nazwy plików będzie pochodzić od nazwy, wprowadzonych przez użytkownika w **Dodaj nowy element** okno dialogowe.

1. Wybierz pliki do uwzględnienia w szablonie, kliknij prawym przyciskiem myszy zaznaczenie, a następnie wybierz pozycję **przesyłają** > **skompresowanego folderu (zip)**.

   Wybrane pliki są kompresowane do pliku zip.

1. Skopiuj plik zip do lokalizacji szablonu elementu użytkownika. Domyślnie, katalog jest %USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ItemTemplates. Aby uzyskać więcej informacji, zobacz [porady: Znajdź i organizowanie szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

1. Zamknij program Visual Studio, a następnie otwórz go ponownie.

1. Utwórz nowy projekt, ani otworzyć istniejącego projektu, a następnie wybierz **projektu** > **Dodaj nowy element...**  lub naciśnij klawisz **Ctrl** + **Shift** + **A**.

   Szablon elementów wielu plików jest wyświetlany w **Dodaj nowy element** okno dialogowe.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono szablon formularzy systemu Windows. Gdy element jest tworzony na podstawie tego szablonu, nazwy trzy pliki tworzone będzie zgodna z nazwą, wprowadzona w **Dodaj nowy element** okno dialogowe.

```xml
<VSTemplate Version="2.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-file Item Template</Name>
        <Icon>Icon.ico</Icon>
        <Description>An example of a multi-file item template</Description>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">
            Form1.vb
        </ProjectItem>
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">
            Form1.Designer.vb
        </ProjectItem>
        <ProjectItem TargetFileName="$fileinputname$.resx">
            Form1.resx
        </ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Zobacz także

[Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)  
[Instrukcje: Tworzenie szablonów elementu](../ide/how-to-create-item-templates.md)  
[Parametry szablonu](../ide/template-parameters.md)  
[Instrukcje: Zastępowanie parametrów w szablonie](../ide/how-to-substitute-parameters-in-a-template.md)