---
title: Podpis metody zmiany - refaktoryzacji (Visual Basic) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: 64b37bca-92b8-4154-9d65-54073e5740fc
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: ac0b8394f71f2f7949cf21b4ea34eba733bf4d34
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="change-a-method-signature-in-visual-basic"></a>Zmień sygnatury metody w języku Visual Basic
**Co:** umożliwia usuwanie lub zmiana kolejności parametrów metody.

**Kiedy:** chcesz przenieść lub usunąć parametr metody, który jest obecnie używana w różnych lokalizacjach.  

**Dlaczego:** możesz można ręcznie usunąć zmiany kolejności parametrów i Znajdź wszystkie wywołania tej metody i zmień je jeden po drugim, ale który może prowadzić do błędów.  To narzędzie refaktoryzacji będzie automatycznie wykonywać zadania.

**Jak:**

1. Zaznacz lub umieść kursor tekst wewnątrz nazwę metody, aby zmodyfikować lub jednego z jego użycia:

   ![Wyróżniony kod](media/changesignature_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl + R**, następnie **klawisze Ctrl + V**.  (Należy pamiętać, że skrót klawiaturowy mogą być różne oparte na profil, który wybrano).
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **zmiany sygnatury** z menu podręcznego okna podglądu.
   * **Myszy**
     * Wybierz **Edytuj > Refaktoryzuj > Usuń parametry**.
     * Wybierz **Edytuj > Refaktoryzuj > zmiany kolejności parametrów**.
     * Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **zmiany sygnatury** z menu podręcznego okna podglądu.

1. W **Zmienianie podpisu** okna dialogowego, które pojawia się, umożliwia przycisków po prawej stronie Zmień podpis metody:

   ![Zmiana podpisu w oknie dialogowym](media/changesignature_dialog.png)

   | Przycisk | Opis
   | ------ | ---
   | **Góra/dół** | Przenieś zaznaczony parametr w górę i w dół listy
   | **Usuń**  | Usuń zaznaczony parametr z listy
   | **Przywróć** | Przywróć wybrane, przekreślonym parametru do listy

   > [!TIP]
   > Użyj [ **podgląd zmian odwołanie** ](../../ide/preview-changes.md) pole wyboru, aby zobaczyć wynik będzie przed wykonaniem do niego.

1. Po zakończeniu naciśnij klawisz **OK** przycisk, aby wprowadzić zmiany.

   ![Zmiana wyniku podpisu](media/changesignature_result.png)

## <a name="see-also"></a>Zobacz też  
[Refaktoryzacji (Visual Basic)](../refactoring-vb.md)  
[Podgląd zmian](../../ide/preview-changes.md)