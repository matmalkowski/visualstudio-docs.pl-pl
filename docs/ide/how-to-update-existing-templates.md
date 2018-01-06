---
title: "Aktualizowanie istniejących szablony projektów i elementów w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9401f8a9a07f7098575ff267825982a03024e968
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-update-existing-templates"></a>Porady: aktualizowanie istniejących szablonów

Po utworzeniu szablonu i kompresuje pliki do pliku zip, możesz zmodyfikować szablon. Można to zrobić przez ręczne zmienianie plików w szablonie lub przez wyeksportowanie szablonu z projektu, który jest oparty na szablonie.

## <a name="using-the-export-template-wizard-to-update-an-existing-project-template"></a>Kreator eksportu szablonu do aktualizacji istniejącego szablonu projektu

Program Visual Studio udostępnia **Kreatora eksportowania szablonu** można zaktualizować istniejący szablon:

1. Otwórz **nowy projekt** okno dialogowe, wybierając **pliku** > **nowy** > **projektu**.

1. Wybierz szablon, który chcesz zaktualizować, wprowadź nazwę i lokalizację projektu i wybierz **OK**.

1. Zmodyfikuj projektu programu Visual Studio.

1. Na **projektu** menu, wybierz **Eksportuj szablon...** .

    **Kreatora eksportowania szablonu** otwiera.

1. Postępuj zgodnie z monitami w kreatorze, aby wyeksportować szablon jako plik .zip.

1. (Opcjonalnie) Aby dodać szablon do **nowy projekt** okna dialogowego należy umieścić plik zip w następującym katalogu: %USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ProjectTemplates. Musisz wykonać ten krok, jeśli użytkownik nie wybrał opcji **automatycznie zaimportuj szablon do programu Visual Studio** w **Kreatora eksportowania szablonu**.

1. Usuń stary plik zip szablonu.

## <a name="manually-updating-an-existing-template"></a>Ręczne aktualizowanie istniejącego szablonu

Możesz zaktualizować istniejący szablon bez użycia **Kreatora eksportowania szablonu**, modyfikując plików w pliku zip skompresowane.

### <a name="to-manually-update-an-existing-template"></a>Aby ręcznie zaktualizować istniejący szablon

1. Zlokalizuj plik zip, który zawiera szablon. Szablony projektu użytkownika są zazwyczaj znajduje się w %USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ProjectTemplates.

1. Wyodrębnij plik zip.

1. Modyfikowanie Usuń bieżące pliki szablonu lub Dodaj nowe pliki do szablonu.

1. Otwierania, modyfikowania i Zapisz plik XML .vstemplate do obsługi zachowanie zaktualizowane lub nowych plików.

    Aby uzyskać więcej informacji o schemacie .vstemplate, zobacz [odwołanie do schematu szablonu Visual Studio (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md). Aby uzyskać więcej informacji o to, co może parametryzacja w plikach źródłowych, zobacz [parametrów szablonu](../ide/template-parameters.md).

1. Wybierz pliki, w szablonie i w menu kliknij prawym przyciskiem myszy lub kontekstu, a następnie wybierz pozycję **przesyłają** > **skompresowanego folderu (zip)**.

    Wybrane pliki są kompresowane do pliku zip.

1. Nowy plik zip należy umieścić w tym samym katalogu co stary plik zip.

1. Usuń pliki szablonów wyodrębnionego i stary plik zip szablonu.

## <a name="see-also"></a>Zobacz także

[Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)  
[Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)  
[Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)  
[Parametry szablonu](../ide/template-parameters.md)  
[Instrukcje: Tworzenie pakietów startowych](../ide/how-to-create-starter-kits.md)