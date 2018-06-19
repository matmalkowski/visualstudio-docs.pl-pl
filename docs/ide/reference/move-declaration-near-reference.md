---
title: Przenieś zmiennej deklarację blisko odwołania w programie Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: douge
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: e98f7b7e9df0a1df3482257c70a661aa22d5980a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31949270"
---
# <a name="move-declaration-near-reference-refactoring"></a>Przenieś deklarację blisko odwołania refaktoryzacji

Dotyczy to refaktoryzacji:

- C#

**Co:** pozwala przesunąć bliżej deklaracji zmiennych do ich użycia.

**Kiedy:** masz deklaracji zmiennych, które mogą być w zakresie mniejszą niż.

**Dlaczego:** można pozostanie ona jest, ale mogą powodować problemy z czytelność lub ukrywanie informacji. Jest to możliwość zrefaktoryzuj w celu zwiększenia czytelności.

## <a name="how-to"></a>Porada

1. Umieść kursor w deklaracji zmiennej.

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **Przenieś deklarację blisko odwołania** z menu podręcznego okna podglądu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **Przenieś deklarację blisko odwołania** z menu podręcznego okna podglądu.

1. Po zakończeniu modyfikowania zmian, naciśnij klawisz **Enter** lub kliknij przycisk Usuń w menu, a zmiany zostaną zatwierdzone.

Przykład:

```csharp
// Before
int x;
if (condition)
{
    x = 1;
    Console.WriteLine(x);
}

// Move declaration near reference

// After
if (condition)
{
    int x = 1;
    Console.WriteLine(x);
}
```

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)