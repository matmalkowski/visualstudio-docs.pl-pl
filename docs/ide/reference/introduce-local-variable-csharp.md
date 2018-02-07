---
title: "Wprowadź zmienną lokalną - generowania kodu (C#) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 6ba9478c09e55df54f94ed93c7a694f798ae76b4
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2018
---
# <a name="introduce-a-local-variable-in-c"></a>Wprowadź zmienną lokalną w języku C# #

**Co:** pozwala natychmiast wygenerować zmiennej lokalnej, aby zastąpić istniejącą wyrażenia.

**Kiedy:** kod, który można łatwo wykorzystywać później, jakby był w zmiennej lokalnej.

**Dlaczego:** można skopiuj i Wklej kod wielokrotnie będzie używane w różnych lokalizacjach, jednak byłoby lepiej wykonać tę operację jeszcze raz, zapisz wynik w zmiennej lokalnej i używać lokalnego throughought zmiennej.

**Jak:**

1. Zaznacz wyrażenie, które ma zostać przypisany do zmiennej lokalnej.

   ![Wyróżniony kod](media/local-highlight-cs.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Keyboard**
     * Naciśnij klawisz **Ctrl +.** do wyzwalania **szybkie akcje i Refaktoryzacje** menu i wybierz **wprowadź element lokalny dla (wszystkie wystąpienia) "*wyrażenie*"** z menu podręczne okno podglądu, gdzie *wyrażenie* kodu zostały wyróżnione.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **wprowadź element lokalny dla (wszystkie wystąpienia) "*wyrażenie*"** z menu podręcznego okna podglądu gdzie *wyrażenie* kodu zostały wyróżnione.
     * Kliknij przycisk ![Żarówka](media/bulb-cs.png) ikonę, która jest wyświetlana na lewym marginesie, gdy kursor tekstu jest już w wierszu zawierającym czerwona falista.

   ![Wprowadzenie Podgląd lokalny](media/local-preview-cs.png)

   > [!TIP]
   > Użyj [ **podgląd zmian** ](../../ide/preview-changes.md) łącze umieszczone u dołu okna podglądu, aby zobaczyć wszystkie zmiany wprowadzone przed dokonaniem wyboru.

1. Zmienna lokalna zostaną utworzone automatycznie z typem wywnioskować na podstawie jej użycia.  Podaj nową nazwę Nowa zmienna lokalna, wpisując ją.

   ![Wprowadzenie wyniku lokalnej](media/local-result-cs.png)

   > [!NOTE]
   > Można użyć **.. wystąpień aplikacji...**  menu opcję, aby zastąpić wszystkie wystąpienia wybranego wyrażenia znaleziony, nie tylko jedną, specjalnie wyróżnioną pozycją.

## <a name="see-also"></a>Zobacz także

[Generowanie kodu](../code-generation-in-visual-studio.md)  
[Podgląd zmian](../../ide/preview-changes.md)
