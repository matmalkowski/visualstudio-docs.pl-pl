---
title: Generuj klasy lub typu w programie Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vsl.GenerateFromUsage
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 25e56d77ef9094338455b3a3f576fe8bc58387b2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947365"
---
# <a name="generate-a-class-or-type-in-visual-studio"></a>Generuj klasy lub typu w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

- Visual Basic

**Co:** umożliwia natychmiast generowania kodu dla klasy lub typu.

**Kiedy:** wprowadzenie nowej klasy lub typu i chcesz poprawnie zadeklarować, automatycznie.

**Dlaczego:** przed użyciem, jednak ta funkcja będzie generowania klasy lub typu automatycznie można zadeklarować klasy lub typu.

## <a name="how-to"></a>Porada

1. Umieść kursor w wierszu przypadku czerwona falista. Czerwona falista wskazuje klasę, która jeszcze nie istnieje.

   - C#:

    ![Wyróżniony kod C#](media/class-highlight-cs.png)

   - Visual Basic:

    ![Wyróżniony Kod VB](media/class-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
     - Umieść kursor nad czerwona falista, a następnie kliknij przycisk ![Żarówka](media/bulb-cs.png) ikonę, która jest wyświetlana.
     - Kliknij ikonę ![Żarówka](media/bulb-cs.png) ikonę, która jest wyświetlana na lewym marginesie, gdy kursor tekstu jest już w wierszu zawierającym czerwona falista.

    ![Generowanie podglądu — klasa](media/class-preview-cs.png)

1. Z menu rozwijanego wybierz jedną z opcji:

   - Generuj klasy*TypeName*"w nowym pliku&mdash;tworzy klasę o nazwie *TypeName* w pliku o nazwie *TypeName*.cs/.vb
   - Generuj klasy*TypeName*"&mdash;tworzy klasę o nazwie *TypeName* w bieżącym pliku.
   - Generuj klasy zagnieżdżonej*TypeName*"&mdash;tworzy klasę o nazwie *TypeName* zagnieżdżone wewnątrz klasy.
   - Generowanie nowego typu... &mdash;Tworzy nową klasą lub strukturą z wszystkich właściwości, należy określić.

   > [!TIP]
   > Użyj **podgląd zmian** łącze umieszczone u dołu okna podglądu [aby zobaczyć wszystkie zmiany](../../ide/preview-changes.md) która zostanie podjęta przed dokonaniem wyboru.

1. W przypadku wybrania **wygenerować nowy typ...**  elementu **Generowanie typu** zostanie otwarte okno dialogowe. Skonfiguruj dostępność, typu i lokalizacji, nowego typu.

   ![Generowanie typu](media/class-newtype-cs.png)

   Wybór | Opis
   --- | ---
   Access | Ustaw typ ma *domyślne*, *wewnętrzne* lub *publicznego* dostępu.
   rodzaj | To może być ustawiona jako *klasy* lub *struktury*.
   Nazwa | Nie można zmienić i będzie można już wpisana nazwa.
   Projekt | Jeśli istnieje wiele projektów w rozwiązaniu, są dostępne miejsce klasie/strukturze wygaśnięcia.
   Nazwa pliku | Można utworzyć nowego pliku lub typu można dodać do istniejącego pliku.

Utworzono klasy lub struktury. Język C# tworzona jest również konstruktora.

- C#

   ![Generowanie wyników klasy C#](media/class-result-cs.png)

- Visual Basic

   ![Generowanie wyników klasy VB](media/class-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)