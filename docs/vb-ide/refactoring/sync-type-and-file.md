---
title: Synchronizowanie typ i nazwa pliku - refaktoryzacji (Visual Basic) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff86d7bd-837b-4664-b0ea-d3ee0c52fe87
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs: VB
ms.openlocfilehash: da6f39dd3573d361c1da579eb3d84c2c8ceeb517
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-in-visual-basic"></a>Synchronizowanie typu na nazwę pliku lub nazwę pliku do typu w języku Visual Basic

<!-- VERSIONLESS -->
**Ta funkcja jest dostępna w programie Visual Studio 2017 lub nowszy.  Ponadto .NET Standard projekty nie są jeszcze obsługiwane dla tego refaktoryzacji.**

**Co:** pozwala zmienić typ do dopasowania nazwy pliku lub zmień nazwę pliku do dopasowania typu zawiera.

**Kiedy:** zmieniono nazwę pliku lub typu i nie zostały jeszcze zaktualizowane odpowiedniego pliku lub typ do dopasowania. 

**Dlaczego:** wprowadzania do typu w pliku z inną nazwę lub odwrotnie, jego trudne do znalezienia, czego szukasz.  Zmieniając typ lub nazwa pliku, kod będzie bardziej czytelny i łatwiej Przejdź.

**Jak:**

1. Zaznacz lub umieść kursor tekst wewnątrz nazwę typu do synchronizowania:

   ![Wyróżniony kod](media/synctype_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl +.** do wyzwalania **szybkie akcje i Refaktoryzacje** menu i wybierz **Zmień nazwę pliku do *TypeName*.vb** z menu podręczne okno podglądu, gdzie *TypeName* to nazwa wybranego typu.
     * Naciśnij klawisz **Ctrl +.** do wyzwalania **szybkie akcje i Refaktoryzacje** menu i wybierz **Zmień nazwę typu na _Filename_**  z menu podręczne okno podglądu, gdzie *Filename* jest nazwą bieżącego pliku.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Zmień nazwę pliku do *TypeName*.vb** z menu podręczne okno podglądu, gdzie *TypeName* to nazwa wybranego typu.
     * Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Zmień nazwę typu na _Filename_**  z menu podręczne okno podglądu, gdzie  *Nazwa pliku* jest nazwą bieżącego pliku.

   Typ lub pliku natychmiast zostanie zmieniona.  W przykładzie poniżej plik **Employee.vb** została zmieniona na **Person.vb** być zgodna z nazwą typu.

   ![Wynik wbudowany](media/synctype_result.png)

## <a name="see-also"></a>Zobacz też  
[Refaktoryzacji (Visual Basic)](../refactoring-vb.md)
