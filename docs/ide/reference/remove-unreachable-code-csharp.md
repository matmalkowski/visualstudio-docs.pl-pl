---
title: "Usuń refaktoryzacji nieosiągalnego kodu dla C# w programie Visual Studio | Dokumentacja firmy Microsoft"
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
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: 12b6910aad6399b72b3e4bc10e6b857cc98c09bb
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2018
---
# <a name="remove-unreachable-code-in-c"></a>Usuń nieosiągalny kod w języku C# #

**Co:** usuwa kod, który nigdy nie zostanie wykonana.

**Kiedy:** program nie ma ścieżki do fragment kodu, co ten fragment kodu niepotrzebne.

**Dlaczego:** poprawić czytelność i łatwości konserwacji przez usunięcie kodu, który jest zbędny i nigdy nie zostanie wykonana.

**Jak:**

1. Umieść kursor w kodzie rozmyciem limit, który jest niedostępny:

![Pojawił nieosiągalny kod](media/unreachablecode-faded-cs.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Keyboard**
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **Usuń nieosiągalny kod** z menu podręcznego okna podglądu.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **Usuń nieosiągalny kod** z menu podręcznego okna podglądu.

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

[Refaktoryzacja](../refactoring-in-visual-studio.md)  
[Podgląd zmian](../../ide/preview-changes.md)