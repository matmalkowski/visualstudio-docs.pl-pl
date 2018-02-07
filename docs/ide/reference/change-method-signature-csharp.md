---
title: "Refaktoryzuj sygnatury metody w języku C# | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: 44aaf3f4a570600b715d6d54f5fd80da84611b94
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2018
---
# <a name="change-a-method-signature-in-c"></a>Zmień sygnatury metody w języku C# #

**Co:** umożliwia usuwanie lub zmiana kolejności parametrów metody.

**Kiedy:** chcesz przenieść lub usunąć parametr metody, który jest obecnie używana w różnych lokalizacjach.  

**Dlaczego:** możesz można ręcznie usunąć zmiany kolejności parametrów i Znajdź wszystkie wywołania tej metody i zmień je jeden po drugim, ale który może prowadzić do błędów.  To narzędzie refaktoryzacji będzie automatycznie wykonywać zadania.

**Jak:**

1. Zaznacz lub umieść kursor tekst wewnątrz nazwę metody, aby zmodyfikować lub jednego z jego użycia:

   ![Wyróżniony kod](media/changesignature-highlight-cs.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Keyboard**
     * Naciśnij klawisz **Ctrl + R**, następnie **klawisze Ctrl + V**.  (Należy pamiętać, że skrót klawiaturowy mogą być różne oparte na profil, który wybrano).
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **zmiany sygnatury** z menu podręcznego okna podglądu.
   * **Myszy**
     * Wybierz **Edytuj > Refaktoryzuj > Usuń parametry**.
     * Wybierz **Edytuj > Refaktoryzuj > zmiany kolejności parametrów**.
     * Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **zmiany sygnatury** z menu podręcznego okna podglądu.

1. W **Zmienianie podpisu** okna dialogowego, które pojawia się, umożliwia przycisków po prawej stronie Zmień podpis metody:

   ![Zmiana podpisu w oknie dialogowym](media/changesignature-dialog-cs.png)

   | Przycisk | Opis
   | ------ | ---
   | **Góra/dół** | Przenieś zaznaczony parametr w górę i w dół listy
   | **Usuń**  | Usuń zaznaczony parametr z listy
   | **Przywróć** | Przywróć wybrane, przekreślonym parametru do listy

   > [!TIP]
   > Użyj [ **podgląd zmian odwołanie** ](../../ide/preview-changes.md) pole wyboru, aby zobaczyć wynik będzie przed wykonaniem do niego.

1. Po zakończeniu naciśnij klawisz **OK** przycisk, aby wprowadzić zmiany.

   ![Zmiana wyniku podpisu](media/changesignature-result-cs.png)

## <a name="see-also"></a>Zobacz także

[Refaktoryzacja](../refactoring-in-visual-studio.md)  
[Podgląd zmian](../../ide/preview-changes.md)