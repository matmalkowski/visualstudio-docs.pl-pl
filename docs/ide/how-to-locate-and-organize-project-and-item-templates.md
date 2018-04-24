---
title: Organizowanie szablonów w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
- Visual Studio templates, organizing
- templates [Visual Studio], organizing
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 68ba015c1a1eb125f02e65c8a19c6f516e48f72a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Porady: lokalizowanie i organizowanie szablonów projektów i elementów

Pliki szablonów muszą znajdować się w lokalizacji, która rozpoznaje Visual Studio dla szablonów, które mają być widoczne w **nowy projekt** i **Dodaj nowy element** okien dialogowych. Można również utworzyć niestandardowe podkategorii w lokalizacji szablonu użytkownika i kategorie są wyświetlane w **nowy projekt** i **Dodaj nowy element** okien dialogowych.

## <a name="locate-templates"></a>Zlokalizuj szablonów

Zainstalowane szablony i użytkownika są przechowywane w dwóch różnych lokalizacjach.

### <a name="user-templates"></a>Szablony użytkownika

Jeśli dodasz skompresowany (*.zip*) pliku, który zawiera *.vstemplate* plik do katalogu użytkowników szablonu szablonu zostanie wyświetlony w **nowy projekt** lub  **Dodaj nowy element** okno dialogowe. Domyślnie szablony użytkownika znajdują się w:

- *%USERPROFILE%\Documents\Visual studio \<wersji\>\Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual studio \<wersji\>\Templates\ItemTemplates*

Na przykład następującego katalogu zawiera szablony projektów użytkownika dla C#:

- *C:\Users\UserName\Documents\Visual Studio 2017\Templates\ProjectTemplates\Visual C#*

> [!TIP]
> Można ustawić lokalizacji dla szablonów użytkownika w **narzędzia** > **opcje** > **projekty i rozwiązania**  >   **Lokalizacje**.

### <a name="installed-templates"></a>Zainstalowane szablony

Domyślnie szablony zainstalowane z programem Visual Studio znajdują się w:

- *\\< VisualStudioInstallationDirectory\>\Common7\IDE\ItemTemplates\\< język programowania\>\\<Locale ID>*

- *\\< VisualStudioInstallationDirectory\>\Common7\IDE\ProjectTemplates\\< język programowania\>\\<Locale ID>*

Na przykład następujący katalog zawiera szablony elementów Visual Basic dla języka angielskiego (LCID 1033):

- *C:\\< VisualStudioInstallationDirectory\>\Common7\IDE\ItemTemplates\VisualBasic\1033*

## <a name="organize-templates"></a>Organizowanie szablonów

Kategorie w **nowy projekt** i **Dodaj nowy element** okien dialogowych odzwierciedlić struktur katalogów, które istnieją w lokalizacjach zainstalowanych szablonu szablonu i użytkownika. Szablony użytkownika można można podzielić na ich własnych kategorii przez dodanie nowych folderów do katalogu szablonu użytkownika. **Nowy projekt** i **Dodaj nowy element** okien dialogowych wyświetlić wszelkie zmiany wprowadzone do kategorii szablonu użytkownika.

> [!NOTE]
> Nie można utworzyć nową kategorię na poziomie języka programowania. Nowych kategorii można tworzyć tylko w ramach każdego języka.

### <a name="to-create-new-user-project-template-categories"></a>Aby utworzyć nowego użytkownika kategorii szablonu projektu

1. Utwórz folder w folderze języka programowania, w katalogu szablonu projektu użytkownika. Na przykład, aby ustanowić **HelloWorld** kategorię dla C# szablony projektów, utworzyć następującego katalogu:

    - *\%USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ProjectTemplates\Visual C# \HelloWorld*

1. Umieść wszystkie szablony dla tej kategorii w nowym folderze.

1. Na **pliku** menu, wybierz **nowy** > **projektu**.

   **HelloWorld** kategorii jest wyświetlana w **nowy projekt** okna dialogowego, w obszarze **zainstalowana** > **Visual C#**.

### <a name="to-create-new-user-item-template-categories"></a>Aby utworzyć nowy użytkownik kategorie szablonów elementu

1. Utwórz folder w folderze języka programowania, w katalogu szablonu elementu użytkownika. Na przykład, aby ustanowić **HelloWorld** kategorię dla C# szablony elementów, utworzyć następującego katalogu:

    - *\%USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ItemTemplates\Visual C# \HelloWorld*

1. Umieść wszystkie szablony dla tej kategorii w nowym folderze.

1. Tworzenie projektu lub otworzyć istniejącego projektu. Następnie na **projektu** menu, wybierz **Dodaj nowy element**.

   **HelloWorld** kategorii jest wyświetlana w **Dodaj nowy element** okna dialogowego, w obszarze **zainstalowana** > **Visual C# elementów**.

### <a name="display-templates-in-parent-categories"></a>Wyświetl szablony w kategorii nadrzędnych

Można włączyć szablonów w podkategoriach mają być wyświetlane w ich kategorii nadrzędnych za pomocą `NumberOfParentCategoriesToRollUp` element *.vstemplate* pliku. Te kroki są takie same dla szablony projektów i elementów.

#### <a name="to-display-templates-in-parent-categories"></a>Aby wyświetlić szablony w kategorii nadrzędnych

1. Zlokalizuj *zip* plik, który zawiera szablon.

1. Wyodrębnij *.zip* pliku.

1. Otwórz *.vstemplate* pliku w programie Visual Studio.

1. W `TemplateData` elementu, Dodaj `NumberOfParentCategoriesToRollUp` elementu. Na przykład następujący kod sprawia, że szablon widoczne w kategorii nadrzędnej, ale nie jest wyższa.

    ```xml
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

1. Zapisz i Zamknij *.vstemplate* pliku.

1. Wybierz pliki do szablonu, kliknij prawym przyciskiem myszy zaznaczenie, a następnie wybierz pozycję **przesyłają** > **skompresowanego folderu (zip)**.

   Pliki są skompresowane w *.zip* pliku.

1. Usuń pliki szablonów wyodrębnionego i starego szablonu *.zip* pliku.

1. Umieść nowe *.zip* pliku w katalogu, który miał usuniętych *.zip* pliku.

## <a name="see-also"></a>Zobacz także

[Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)  
[Visual Studio odwołanie do schematu szablonu (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)  
[NumberOfParentCategoriesToRollUp (szablony Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)  
[Porady: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)  
[Porady: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
