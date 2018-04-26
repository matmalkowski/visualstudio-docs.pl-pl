---
title: Generowanie C# Equals i GetHashCode — metoda zastępuje w programie Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: cdbb5273d046be8f11cc2fbc4a03ed6767a31e00
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Generowanie Equals i GetHashCode — metoda zastępuje w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

**Co:** umożliwia wygenerowanie **jest równe** i **GetHashCode** metody.

**Kiedy:** generowania te zastąpienia mieć typ, który powinien być porównywane przez jeden lub więcej pól, zamiast według lokalizacji obiektu w pamięci.

**Dlaczego:**

- W przypadku wdrażania typu wartości, należy rozważyć zastępowanie **jest równe** metodę, aby uzyskać większą wydajność przez domyślną implementację metody Equals na ValueType.

- W przypadku wdrażania Typ referencyjny, należy rozważyć zastępowanie **jest równe** metodę, jeśli z danym typem wygląda typu podstawowego, takie jak punkt, String, BigNumber i tak dalej.

- Zastąpienie **GetHashCode** metodę umożliwiającą typu działać poprawnie w tablicy skrótów. Przeczytaj więcej pomocy na [Operatory równości](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Porada

1. Umieść kursor w Twojej deklaracji typu.

   ![Wyróżniony kod](media/overrides-highlight-cs.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
     - Kliknij ikonę ![Żarówka](media/bulb-cs.png) ikonę, która jest wyświetlana na lewym marginesie, jeśli kursor tekstu znajduje się już na wiersz z deklaracji typu.

   ![Generowanie podglądu zastąpień](media/overrides-preview-cs.png)

1. Wybierz **Generowanie Equals(object)** lub **Generowanie metodę Equals i GetHashCode** z menu rozwijanego.

1. W **wybierz elementy członkowskie** okno dialogowe, wybierz elementy członkowskie, aby wygenerować metody:

    ![Generowanie okna dialogowego zastąpień](media/overrides-dialog-cs.png)

    > [!TIP]
    > Można także wygenerować operatory z tego okna dialogowego za pomocą pola wyboru poniżej listy członków.

   Equals i GetHashCode zastąpienia są generowane z domyślnej implementacji.

   ![Generowanie wyników — metoda](media/overrides-result-cs.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)