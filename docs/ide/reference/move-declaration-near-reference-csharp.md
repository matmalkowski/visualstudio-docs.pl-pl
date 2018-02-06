---
title: "Przenieś zmiennej deklarację blisko odwołania w języku C# | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: f61fbdc8dd24bb07082081557c875e9149c1c398
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="move-declaration-near-reference-in-c"></a>Przenieś deklarację blisko odwołania w języku C# #

**Co:** pozwala przesunąć bliżej deklaracji zmiennych do ich użycia.

**Kiedy:** masz deklaracji zmiennych, które mogą być w zakresie mniejszą niż.

**Dlaczego:** można pozostanie ona jest, ale mogą powodować problemy z czytelność lub ukrywanie informacji. Jest to możliwość zrefaktoryzuj w celu zwiększenia czytelności.

**Jak:**

1. Umieść kursor w deklaracji zmiennej.

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **Przenieś deklarację blisko odwołania** z menu podręcznego okna podglądu.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **Przenieś deklarację blisko odwołania** z menu podręcznego okna podglądu.

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

[Refaktoryzacja](../refactoring-in-visual-studio.md)  
[Podgląd zmian](../../ide/preview-changes.md)