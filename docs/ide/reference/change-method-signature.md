---
title: Refaktoryzuj sygnatury metody w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/26/2018
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ce920d11d7f29f166bf551d8ce95df11f5abf9d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="change-a-method-signature-refactoring"></a>Zmień refaktoryzacji podpisu — metoda

Dotyczy to refaktoryzacji:

- C#

- Visual Basic

**Co:** umożliwia usuwanie lub zmiana kolejności parametrów metody.

**Kiedy:** chcesz przenieść lub usunąć parametr metody, który jest obecnie używana w różnych lokalizacjach.

**Dlaczego:** możesz można ręcznie usunąć zmiany kolejności parametrów i Znajdź wszystkie wywołania tej metody i zmień je jeden po drugim, ale który może prowadzić do błędów.  To narzędzie refaktoryzacji będzie automatycznie wykonywać zadania.

## <a name="how-to"></a>Porada

1. Zaznacz lub umieść kursor tekst wewnątrz nazwę metody, aby zmodyfikować lub jednego z jego użycia:

   - C#:

    ![Wyróżniony kod C#](media/changesignature-highlight-cs.png)

   - VB:

    ![Wyróżniony kod Visual Basic](media/changesignature-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl + R**, następnie **klawisze Ctrl + V**.  (Należy pamiętać, że skrót klawiaturowy mogą być różne oparte na profil, który wybrano).
     - Naciśnij klawisz **Ctrl**+**.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **zmiany sygnatury** z menu podręcznego okna podglądu.
   - **Myszy**
     - Wybierz **Edytuj > Refaktoryzuj > Usuń parametry**.
     - Wybierz **Edytuj > Refaktoryzuj > zmiany kolejności parametrów**.
     - Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **zmiany sygnatury** z menu podręcznego okna podglądu.

1. W **Zmienianie podpisu** okna dialogowego, które pojawia się, umożliwia przycisków po prawej stronie Zmień podpis metody:

   ![Zmiana podpisu w oknie dialogowym](media/changesignature-dialog-cs.png)

   | Przycisk | Opis
   | ------ | ---
   | **Góra/dół** | Przenieś zaznaczony parametr w górę i w dół listy
   | **Usuń**  | Usuń zaznaczony parametr z listy
   | **Przywróć** | Przywróć wybrane, przekreślonym parametru do listy

   > [!TIP]
   > Użyj **podgląd zmian odwołanie** pole wyboru, aby [Zobacz, czego wynikiem będzie](../../ide/preview-changes.md) przed zatwierdzeniem do niego.

1. Po zakończeniu naciśnij klawisz **OK** przycisk, aby wprowadzić zmiany.

   - C#:

    ![Zmienianie podpisu wynik - C#](media/changesignature-result-cs.png)

   - Visual Basic:

    ![Zmienianie podpisu wynik - Visual Basic](media/changesignature-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)