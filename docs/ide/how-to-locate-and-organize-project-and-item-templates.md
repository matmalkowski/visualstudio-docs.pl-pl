---
title: "Organizowanie szablonów w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
- Visual Studio templates, organizing
- templates [Visual Studio], organizing
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 167ffa269ea8051a4791000d96a86cb5788af60d
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Porady: lokalizowanie i organizowanie szablonów projektów i elementów

Pliki szablonów muszą znajdować się w lokalizacji, która rozpoznaje programu Visual Studio, szablonów, które mają być widoczne w **nowy projekt** i **Dodaj nowy element** okien dialogowych. Można tworzyć niestandardowe podkategorie szablonów, które pojawiają się w oknach dialogowych.

## <a name="locating-templates"></a>Lokalizowanie szablonów

Zainstalowane szablony i użytkownika są przechowywane w dwóch różnych lokalizacjach. Jeśli istnieje skompresowany plik, który zawiera plik .vstemplate w tych lokalizacjach, szablon pojawi się w **nowy projekt** lub **Dodaj nowy element** okno dialogowe.

> [!TIP]
> Można ustawić lokalizacji dla szablonów użytkownika w **narzędzia** > **opcje** > **projekty i rozwiązania**  >   **Lokalizacje**.

### <a name="installed-templates"></a>Zainstalowane szablony

Domyślnie szablony zainstalowane z programem Visual Studio znajdują się w:

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\\*język programowania*\\*identyfikator ustawień regionalnych*

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\\*język programowania*\\*identyfikator ustawień regionalnych*

Na przykład następujący katalog zawiera szablony elementów Visual Basic dla języka angielskiego (LCID 1033):

   C:\\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\VisualBasic\1033\

### <a name="user-templates"></a>Szablony użytkownika

Domyślnie szablony użytkownika znajdują się w:

- %USERPROFILE%\Documents\Visual studio \<wersji\>\Templates\ProjectTemplates

- %USERPROFILE%\Documents\Visual studio \<wersji\>\Templates\ItemTemplates

Na przykład następujący katalog zawiera szablony projektów użytkownika dla C#:

   C:\Users\UserName\Documents\Visual Studio 2017\Templates\ProjectTemplates\Visual C# \

> [!NOTE]
> Lokalizacja szablonów użytkownika nie obejmuje podkatalogi ustawień regionalnych zlokalizowanej szablonów.

Można zmienić domyślny katalog dla szablonów użytkownika w **opcje** okna dialogowego, w obszarze **projekty i rozwiązania** > **lokalizacje**.

## <a name="organizing-templates"></a>Organizowanie szablonów

Kategorie w **nowy projekt** i **Dodaj nowy element** okien dialogowych odzwierciedlić struktur katalogów, które istnieją w lokalizacjach zainstalowanych szablonu szablonu i użytkownika. Można zmodyfikować te struktury katalogu tak, aby uporządkować w taki sposób, który ma sens dla Ciebie.

> [!NOTE]
> Nie można utworzyć nową kategorię na poziomie języka programowania. Nowych kategorii można tworzyć tylko w ramach każdego języka.

> [!NOTE]
> Jeśli zainstalowana struktur katalogów dla szablonów użytkownika dla określonego języka nie są takie same (to znaczy istnieją katalogi w ramach jednego folderu, ale nie drugiej), wszystkie kategorie są wyświetlane w **nowy projekt** okno dialogowe.

### <a name="organizing-user-templates"></a>Organizowanie szablonów użytkownika

Szablony użytkownika można można podzielić na ich własnych kategorii, dodając nowe foldery w lokalizacji szablonu użytkownika. **Nowy projekt** okno dialogowe odzwierciedla wszystkie zmiany wprowadzone do kategorii szablonu.

#### <a name="to-create-new-user-project-template-categories"></a>Aby utworzyć nowego użytkownika kategorii szablonu projektu

1. Utwórz folder w folderze języka programowania, w katalogu szablonu projektu użytkownika. Na przykład, aby ustanowić **HelloWorld** kategorię dla C# szablony projektów, utworzyć następującego katalogu:

    \%USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ProjectTemplates\Visual C# \HelloWorld\

1. Umieść wszystkie szablony dla tej kategorii w nowym folderze.

1. Na **pliku** menu, wybierz **nowy** > **projektu**.

   **HelloWorld** kategorii jest wyświetlana w **nowy projekt** okna dialogowego, w obszarze **zainstalowana** > **Visual C#**.

#### <a name="to-create-new-user-item-template-categories"></a>Aby utworzyć nowy użytkownik kategorie szablonów elementu

1. Utwórz folder w folderze języka programowania, w katalogu szablonu elementu użytkownika. Na przykład, aby ustanowić **HelloWorld** kategorię dla C# szablony elementów, utworzyć następującego katalogu:

    \%USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ItemTemplates\Visual C# \HelloWorld\

1. Umieść wszystkie szablony dla tej kategorii w nowym folderze.

1. Tworzenie projektu lub otworzyć istniejącego projektu. Następnie na **projektu** menu, wybierz **Dodaj nowy element**.

   **HelloWorld** kategorii jest wyświetlana w **Dodaj nowy element** okna dialogowego, w obszarze **zainstalowana** > **Visual C# elementów**.

### <a name="displaying-templates-in-parent-categories"></a>Wyświetlanie szablonów w kategorii nadrzędnych

Można włączyć szablonów w podkategoriach mają być wyświetlane w ich kategorii nadrzędnych za pomocą `NumberOfParentCategoriesToRollUp` elementu w pliku .vstemplate. Te kroki są identyczne, szablony projektów i elementów.

#### <a name="to-display-templates-in-parent-categories"></a>Aby wyświetlić szablony w kategorii nadrzędnych

1. Zlokalizuj plik zip, który zawiera szablon.

1. Wyodrębnij plik zip.

1. Otwórz plik .vstemplate w programie Visual Studio.

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

1. Zapisz i zamknij plik .vstemplate.

1. Wybierz pliki do szablonu, kliknij prawym przyciskiem myszy zaznaczenie, a następnie wybierz pozycję **przesyłają** > **skompresowanego folderu (zip)**.

   Pliki są kompresowane do pliku zip.

1. Usuń pliki szablonów wyodrębnionego i stary plik zip szablonu.

1. Umieść nowy plik zip w katalogu, który miał plik zip usunięte.

## <a name="see-also"></a>Zobacz także

[Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)  
[Odwołanie do schematu szablonu Visual Studio (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)  
[NumberOfParentCategoriesToRollUp (szablony Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)  
[Instrukcje: Tworzenie szablonów projektu](../ide/how-to-create-project-templates.md)  
[Instrukcje: Tworzenie szablonów elementu](../ide/how-to-create-item-templates.md)
