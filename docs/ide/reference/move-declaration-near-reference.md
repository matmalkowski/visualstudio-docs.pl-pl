---
title: "Przenieś zmiennej deklarację blisko odwołania w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: a76e6024a2b61bcae08fb8db169483bcee6e5d19
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
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