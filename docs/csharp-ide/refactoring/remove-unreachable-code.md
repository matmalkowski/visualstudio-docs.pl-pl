---
title: "Usuń nieosiągalny kod - Refaktoryzacja (C#) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: e57db74ea431d9090df1dc34fd3cff3cf03dd475
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="remove-unreachable-code-in-c"></a>Usuń nieosiągalny kod w języku C# #
**Co:** usuwa kod, który nigdy nie zostanie wykonana.

**Kiedy:** program nie ma ścieżki do fragment kodu, co ten fragment kodu niepotrzebne.

**Dlaczego:** poprawić czytelność i łatwości konserwacji przez usunięcie kodu, który jest zbędny i nigdy nie zostanie wykonana.

**Jak:**

1. Umieść kursor w kodzie rozmyciem limit, który jest niedostępny:

![Pojawił nieosiągalny kod](media/unreachablecode_faded.png)  

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
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

## <a name="see-also"></a>Zobacz też  
[Refaktoryzacja (C#)](../refactoring-csharp.md)  
[Podgląd zmian](../../ide/preview-changes.md)