---
title: "Zmień nazwę pliku do dopasowania do typu w Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 29260d2f33c9debfe698cb6af30f711e9617cdd1
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-refactoring"></a>Synchronizowanie typu na nazwę pliku lub nazwę pliku do refaktoryzacji typu

Dotyczy to refaktoryzacji:

- C#

- Visual Basic

**Co:** pozwala zmienić typ do dopasowania nazwy pliku lub zmień nazwę pliku do dopasowania typu zawiera.

**Kiedy:** zmieniono nazwę pliku lub typu i nie zostały jeszcze zaktualizowane odpowiedniego pliku lub typ do dopasowania.

**Dlaczego:** wprowadzania do typu w pliku z inną nazwę lub odwrotnie, jego trudne do znalezienia, czego szukasz. Zmieniając typ lub nazwa pliku, kod będzie bardziej czytelny i łatwiej Przejdź.

## <a name="how-to"></a>Porada

1. Zaznacz lub umieść kursor tekst wewnątrz nazwę typu do synchronizowania:

   - C#:

    ![Wyróżniony kod - C#](media/synctype-highlight-cs.png)

   - Visual Basic:

    ![Wyróżniony kod - języka Visual Basic](media/synctype-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** do wyzwalania **szybkie akcje i Refaktoryzacje** menu i wybierz **Zmień nazwę pliku do *TypeName*.cs** z menu podręczne okno podglądu, gdzie *TypeName* to nazwa wybranego typu.
     - Naciśnij klawisz **Ctrl**+**.** do wyzwalania **szybkie akcje i Refaktoryzacje** menu i wybierz **Zmień nazwę typu na _Filename_**  z menu podręczne okno podglądu, gdzie *Filename* jest nazwą bieżącego pliku.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Zmień nazwę pliku do *TypeName*.cs** z menu podręczne okno podglądu, gdzie *TypeName* to nazwa wybranego typu.
     - Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Zmień nazwę typu na _Filename_**  z menu podręczne okno podglądu, gdzie  *Nazwa pliku* jest nazwą bieżącego pliku.

   Typ lub pliku zostanie zmieniona.

   - C#: W przykładzie poniżej plik **MyClass.cs** została zmieniona na **MyNewClass.cs** być zgodna z nazwą typu.

      ![Wynik wbudowane C#](media/synctype-result-cs.png)

   - Visual Basic: W przykładzie poniżej plik **Employee.vb** została zmieniona na **Person.vb** być zgodna z nazwą typu.

      ![Wynik wbudowanego języka Visual Basic](media/synctype-result-vb.png)

> ! [UWAGA] Ta refaktoryzacji nie jest jeszcze dostępne dla projektów .NET Standard i .NET Core.

## <a name="see-also"></a>Zobacz także

[Refaktoryzacja](../refactoring-in-visual-studio.md)
