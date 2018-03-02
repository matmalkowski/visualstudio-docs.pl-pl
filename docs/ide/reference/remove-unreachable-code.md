---
title: "Usuń nieosiągalny kod Refaktoryzacja w programie Visual Studio | Dokumentacja firmy Microsoft"
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
ms.openlocfilehash: 90ea46079e318c09ab62e27f9a75ccdd2452887d
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="remove-unreachable-code-refactoring"></a>Usuń refaktoryzacji nieosiągalny kod

Dotyczy to refaktoryzacji:

- C#

**Co:** usuwa kod, który nigdy nie zostanie wykonana.

**Kiedy:** program nie ma ścieżki do fragment kodu, co ten fragment kodu niepotrzebne.

**Dlaczego:** poprawić czytelność i łatwości konserwacji przez usunięcie kodu, który jest zbędny i nigdy nie zostanie wykonana.

## <a name="how-to"></a>Porada

1. Umieść kursor w kodzie rozmyciem limit, który jest niedostępny:

![Pojawił nieosiągalny kod](media/unreachablecode-faded-cs.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **Usuń nieosiągalny kod** z menu podręcznego okna podglądu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **Usuń nieosiągalny kod** z menu podręcznego okna podglądu.

1. Po zakończeniu modyfikowania zmian, naciśnij klawisz **Enter** lub kliknij przycisk Usuń w menu, a zmiany zostaną zatwierdzone.

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