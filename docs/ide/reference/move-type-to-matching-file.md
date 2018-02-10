---
title: "Typ przenoszenia do refaktoryzacji pasującego pliku w programie Visual Studio | Dokumentacja firmy Microsoft"
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
ms.openlocfilehash: 62187c88fa2d2cf7ecf1b358fa0c03416be449a8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Przenieś typu do refaktoryzacji pasującego pliku

Dotyczy to refaktoryzacji:

- C#

- Visual Basic

**Co:** umożliwia przenoszenie wybranego typu do osobnego pliku o tej samej nazwie.

**Kiedy:** ma wiele klasy, struktury, interfejsy, itp. w tym samym pliku, który chcesz oddzielić.

**Dlaczego:** umieszczenie wiele typów w tym samym pliku może utrudnić można znaleźć następujących typów. Przenosząc typy plików o takiej samej nazwie, kod będzie bardziej czytelny i łatwiej Przejdź.

## <a name="how-to"></a>Porada

1. Zaznacz lub umieść kursor tekst wewnątrz nazwę typu, aby przenieść:

   - C#:

    ![Wyróżniony kod - C#](media/movetype-highlight-cs.png)

   - Visual Basic:

    ![Wyróżniony kod - języka Visual Basic](media/movetype-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl +.** do wyzwalania **szybkie akcje i Refaktoryzacje** menu i wybierz **Przenieś typu *TypeName*.cs** z menu podręcznego okna podglądu gdzie *TypeName* to nazwa wybranego typu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **Przenieś typu *TypeName*.cs** z menu podręcznego okna podglądu gdzie  *Właściwość TypeName* to nazwa wybranego typu.

   Typ jest przenoszona do nowego pliku o tej samej nazwie, w ramach rozwiązania.

   - C#:

    ![Wbudowany wynik - C#](media/movetype-result-cs.png)

   - Visual Basic:

    ![Wynik wbudowanego - Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Zobacz także

[Refaktoryzacja](../refactoring-in-visual-studio.md)