---
title: Usuwanie nieosiągalnego kodu jest Refaktoryzacja w programie Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: fcd402398e8669eb84d1ee23cd128e2d7eb04031
ms.sourcegitcommit: aea5cdb76fbc7eb31d1e5cc3c8d6adb0c743220f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44124882"
---
# <a name="remove-unreachable-code-refactoring"></a>Usuwanie nieosiągalnego kodu refaktoryzacji

Ta Refaktoryzacja mają zastosowanie do:

- C#

**Co:** usunięcie kodu, która nigdy nie zostanie wykonana.

**Kiedy:** program nie ma ścieżki do fragmentu kodu, co ten fragment kodu jest niepotrzebne.

**Dlaczego:** zwiększyć czytelność i łatwość konserwacji przez usunięcie kodu, który jest zbędny i nigdy nie zostanie wykonana.

## <a name="how-to"></a>Instrukcje

1. Umieść kursor w dowolnym miejscu w rozmytą się kod, który jest niedostępny:

![Rozmytą nieosiągalnego kodu](media/unreachablecode-faded-cs.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **usuwanie nieosiągalnego kodu** z menu podręcznego okna podglądu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy ten kod, wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **usuwanie nieosiągalnego kodu** z menu podręcznego okna podglądu.

1. Po zakończeniu zmiany, naciśnij klawisz **Enter** lub kliknij poprawki w menu, a zmiany zostaną zatwierdzone.

Przykład:

```csharp
// Before
private void Method()
{
    throw new Exception(nameof(Method));
    Console.WriteLine($"Exception for method {nameof(Method)}");
}

// Remove unreachable code

// After
private void Method()
{
    throw new Exception(nameof(Method));
}
```

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)