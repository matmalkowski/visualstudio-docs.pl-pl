---
title: Typ przenoszenia do refaktoryzacji pasującego pliku w programie Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 00fab87a8fed4d1dcd9b4899551d68eaab28d46a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945340"
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
     - Naciśnij klawisz **Ctrl**+**.** do wyzwalania **szybkie akcje i Refaktoryzacje** menu i wybierz **Przenieś typu *TypeName*.cs** z menu podręcznego okna podglądu gdzie *TypeName* to nazwa wybranego typu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **Przenieś typu *TypeName*.cs** z menu podręcznego okna podglądu gdzie  *Właściwość TypeName* to nazwa wybranego typu.

   Typ jest przenoszona do nowego pliku o tej samej nazwie, w ramach rozwiązania.

   - C#:

    ![Wbudowany wynik - C#](media/movetype-result-cs.png)

   - Visual Basic:

    ![Wynik wbudowanego - Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)