---
title: Aktualizowanie istniejących szablony projektów i elementów w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/02/2018
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 9465c098144f14db496bc1dbc382d6a30c8882cb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-update-existing-templates"></a>Porady: aktualizowanie istniejących szablonów

Po utworzeniu szablonu i kompresuje pliki do *zip* plik, można zmodyfikować szablon. Można to zrobić przez ręczne zmienianie plików w szablonie lub przez wyeksportowanie szablonu z projektu, który jest oparty na szablonie.

## <a name="using-the-export-template-wizard-to-update-an-existing-project-template"></a>Kreator eksportu szablonu do aktualizacji istniejącego szablonu projektu

Program Visual Studio udostępnia **Kreatora eksportowania szablonu** można zaktualizować istniejący szablon:

1. Otwórz **nowy projekt** okno dialogowe, wybierając **pliku** > **nowy** > **projektu**.

1. Wybierz szablon, który chcesz zaktualizować, wprowadź nazwę i lokalizację projektu i wybierz **OK**.

1. Zmodyfikuj projektu programu Visual Studio.

1. Na **projektu** menu, wybierz **Eksportuj szablon**.

    **Kreatora eksportowania szablonu** otwiera.

1. Postępuj zgodnie z monitami w kreatorze, aby wyeksportować szablon jako *.zip* pliku.

1. (Opcjonalnie) Aby dodać szablon do **nowy projekt** okno dialogowe, miejsce *.zip* pliku w następującym katalogu: *%USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ProjectTemplates*. Musisz wykonać ten krok, jeśli użytkownik nie wybrał opcji **automatycznie zaimportuj szablon do programu Visual Studio** w **Kreatora eksportowania szablonu**.

1. Usuwanie starego szablonu *.zip* pliku.

## <a name="manually-update-an-existing-template"></a>Ręcznie zaktualizować istniejący szablon

Możesz zaktualizować istniejący szablon bez użycia **Kreatora eksportowania szablonu**, modyfikując pliki skompresowane *.zip* pliku.

### <a name="to-manually-update-an-existing-template"></a>Aby ręcznie zaktualizować istniejący szablon

1. Zlokalizuj *zip* plik, który zawiera szablon. Szablony projektów użytkownika znajdują się w folderze *%USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ProjectTemplates*.

1. Wyodrębnij *.zip* pliku.

1. Modyfikowanie Usuń bieżące pliki szablonu lub Dodaj nowe pliki do szablonu.

1. Otwierać, modyfikować i zapisywać *.vstemplate* plik XML do obsługi zachowanie zaktualizowane lub nowych plików.

    Aby uzyskać więcej informacji na temat *.vstemplate* schematu, zobacz [odwołanie do schematu szablonu Visual Studio (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md). Aby uzyskać więcej informacji o to, co może parametryzacja w plikach źródłowych, zobacz [parametrów szablonu](../ide/template-parameters.md).

1. Wybierz pliki, w szablonie i w menu kliknij prawym przyciskiem myszy lub kontekstu, a następnie wybierz pozycję **przesyłają** > **skompresowanego folderu (zip)**.

    Wybrane pliki są skompresowane w *.zip* pliku.

1. Umieść nowe *.zip* pliku w tym samym katalogu co stary *.zip* pliku.

1. Usuń pliki szablonów wyodrębnionego i starego szablonu *.zip* pliku.

## <a name="see-also"></a>Zobacz także

[Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)  
[Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)  
[Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)  
[Parametry szablonu](../ide/template-parameters.md)  
[Porady: tworzenie zestawów początkowych](../ide/how-to-create-starter-kits.md)