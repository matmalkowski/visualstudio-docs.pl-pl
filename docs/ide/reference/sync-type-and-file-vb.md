---
title: "Synchronizowanie typu i nazwę pliku w Visual Basic | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: 93e1b1f446dc330b2c2c1c1e5b36e6a21e64f521
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-in-visual-basic"></a>Synchronizowanie typu na nazwę pliku lub nazwę pliku do typu w języku Visual Basic

<!-- VERSIONLESS -->
**Ta funkcja jest dostępna w programie Visual Studio 2017 lub nowszy.  Ponadto .NET Standard projekty nie są jeszcze obsługiwane dla tego refaktoryzacji.**

**Co:** pozwala zmienić typ do dopasowania nazwy pliku lub zmień nazwę pliku do dopasowania typu zawiera.

**Kiedy:** zmieniono nazwę pliku lub typu i nie zostały jeszcze zaktualizowane odpowiedniego pliku lub typ do dopasowania. 

**Dlaczego:** wprowadzania do typu w pliku z inną nazwę lub odwrotnie, jego trudne do znalezienia, czego szukasz.  Zmieniając typ lub nazwa pliku, kod będzie bardziej czytelny i łatwiej Przejdź.

**Jak:**

1. Zaznacz lub umieść kursor tekst wewnątrz nazwę typu do synchronizowania:

   ![Wyróżniony kod](media/synctype-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl +.** do wyzwalania **szybkie akcje i Refaktoryzacje** menu i wybierz **Zmień nazwę pliku do *TypeName*.vb** z menu podręczne okno podglądu, gdzie *TypeName* to nazwa wybranego typu.
     * Naciśnij klawisz **Ctrl +.** do wyzwalania **szybkie akcje i Refaktoryzacje** menu i wybierz **Zmień nazwę typu na _Filename_**  z menu podręczne okno podglądu, gdzie *Filename* jest nazwą bieżącego pliku.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Zmień nazwę pliku do *TypeName*.vb** z menu podręczne okno podglądu, gdzie *TypeName* to nazwa wybranego typu.
     * Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Zmień nazwę typu na _Filename_**  z menu podręczne okno podglądu, gdzie  *Nazwa pliku* jest nazwą bieżącego pliku.

   Typ lub pliku natychmiast zostanie zmieniona.  W przykładzie poniżej plik **Employee.vb** została zmieniona na **Person.vb** być zgodna z nazwą typu.

   ![Wynik wbudowany](media/synctype-result-vb.png)

## <a name="see-also"></a>Zobacz także

[Refaktoryzacja](../refactoring-in-visual-studio.md)
