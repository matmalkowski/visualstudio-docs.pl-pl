---
title: "Porady: aktualizowanie istniejących szablonów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0fffcc55953e394c5efd00b86949f04474a66111
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-update-existing-templates"></a>Porady: aktualizowanie istniejących szablonów
Po utworzeniu szablonu i kompresuje pliki do pliku zip, możesz zmodyfikować szablon. Można to zrobić przez ręczne zmienianie plików w szablonie lub przez wyeksportowanie szablonu z projektu, który jest oparty na szablonie.  
  
## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>Kreator eksportu szablonu do aktualizacji istniejącego szablonu  
Program Visual Studio udostępnia **Eksportuj szablon** kreatora, który może służyć do aktualizacji istniejącego szablonu.  
  
#### <a name="to-use-export-template-to-update-an-existing-template"></a>Aby wyeksportować szablon służy do aktualizacji istniejącego szablonu  
  
1.  Otwórz **nowy projekt** okno dialogowe, wybierając **pliku**, **nowy**, **projektu**.  
  
2.  Wybierz szablon, który chcesz zaktualizować, wprowadź nazwę i lokalizację projektu i wybierz **OK**.  
  
3.  Zmodyfikuj projektu programu Visual Studio.  
  
4.  Na **projektu** menu, wybierz **Eksportuj szablon**.  

    **Kreatora eksportowania szablonu** otwiera.  

5.  Postępuj zgodnie z monitami w kreatorze, aby wyeksportować szablon jako plik .zip.  

6.  Usuń stary plik zip szablonu.  
  
## <a name="manually-updating-an-existing-template"></a>Ręczne aktualizowanie istniejącego szablonu  
Należy zaktualizować istniejący szablon poza programem Visual Studio, modyfikując plików w pliku zip skompresowane.  
  
#### <a name="to-manually-update-an-existing-template"></a>Aby ręcznie zaktualizować istniejący szablon  
  
1.  Zlokalizuj plik zip, który zawiera szablon. Domyślnie ten plik znajduje się w %USERPROFILE%\Documents\Visual Studio \<wersji\>\My wyeksportowane szablony\.  
  
2.  Wyodrębnij plik zip.  
  
3.  Modyfikowanie Usuń bieżące pliki szablonu lub Dodaj nowe pliki do szablonu.  
  
4.  Otwierania, modyfikowania i Zapisz plik XML .vstemplate do obsługi zachowanie zaktualizowane lub nowych plików.  

    Aby uzyskać więcej informacji o schemacie .vstemplate, zobacz [odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md). Aby uzyskać więcej informacji o to, co może parametryzacja w plikach źródłowych, zobacz [parametrów szablonu](../ide/template-parameters.md).  
  
5.  Wybierz pliki do szablonu, kliknij prawym przyciskiem myszy, wybierz polecenie **Wyślij do**, a następnie wybierz pozycję **skompresowany Folder (zip)**.  

    Wybrane pliki są kompresowane do pliku zip.  
  
6.  Nowy plik zip należy umieścić w tym samym katalogu co stary plik zip.  
  
7.  Usuń pliki szablonów wyodrębnionego i stary plik zip szablonu.  
  
8.  Uruchom wiersz polecenia dla deweloperów wystąpienia z podwyższonym poziomem uprawnień:  

  1. W Start menu, przejdź do **programu Visual Studio \<wersji\>**, **wiersza polecenia dewelopera**.  

  2. Z menu kontekstowego (kliknij prawym przyciskiem myszy) wybierz **więcej**, **Uruchom jako administrator**.  
  
9. Uruchom następujące polecenie: `devenv /installvstemplates`.  
  
## <a name="see-also"></a>Zobacz także  
[Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)   
[Tworzenie szablony projektów i elementów](../ide/creating-project-and-item-templates.md)   
[Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
[Parametry szablonu](../ide/template-parameters.md)   
[Porady: tworzenie zestawów początkowych](../ide/how-to-create-starter-kits.md)