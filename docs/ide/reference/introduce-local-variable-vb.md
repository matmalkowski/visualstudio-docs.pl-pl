---
title: "Wprowadź zmienną lokalną - generowania kodu (Visual Basic) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1490d6ac-ed56-4d03-95db-c23f23cba70d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: abc0ef3ffdbada86a66bac9823894ee83d04047f
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2018
---
# <a name="introduce-a-local-variable-in-visual-basic"></a>Wprowadź zmienną lokalną w języku Visual Basic
**Co:** pozwala natychmiast wygenerować zmiennej lokalnej, aby zastąpić istniejącą wyrażenia.

**Kiedy:** kod, który można łatwo wykorzystywać później, jakby był w zmiennej lokalnej.  

**Dlaczego:** można skopiuj i Wklej kod wielokrotnie będzie używane w różnych lokalizacjach, jednak byłoby lepiej wykonać tę operację jeszcze raz, zapisz wynik w zmiennej lokalnej i używać lokalnego throughought zmiennej. 

**Jak:**

1. Zaznacz wyrażenie, które ma zostać przypisany do zmiennej lokalnej.

   ![Wyróżniony kod](media/local-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Keyboard**
     * Naciśnij klawisz **Ctrl +.** do wyzwalania **szybkie akcje i Refaktoryzacje** menu i wybierz **wprowadź element lokalny dla (wszystkie wystąpienia) "*wyrażenie*"** z menu podręczne okno podglądu, gdzie *wyrażenie* kodu zostały wyróżnione.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **wprowadź element lokalny dla (wszystkie wystąpienia) "*wyrażenie*"** z menu podręcznego okna podglądu gdzie *wyrażenie* kodu zostały wyróżnione.
     * Kliknij przycisk ![Żarówka](media/bulb-vb.png) ikonę, która jest wyświetlana na lewym marginesie, gdy kursor tekstu jest już w wierszu zawierającym czerwona falista.

   ![Wprowadzenie Podgląd lokalny](media/local-preview-vb.png)

   >[!TIP]
   >Użyj [ **podgląd zmian** ](../../ide/preview-changes.md) łącze umieszczone u dołu okna podglądu, aby zobaczyć wszystkie zmiany wprowadzone przed dokonaniem wyboru.

1. Zmienna lokalna zostaną utworzone automatycznie z typem wywnioskować na podstawie jej użycia.  Podaj nową nazwę Nowa zmienna lokalna, wpisując ją.

   ![Wprowadzenie wyniku lokalnej](media/local-result-vb.png)

   >[!NOTE]
   >Można użyć **.. wystąpień aplikacji...**  menu opcję, aby zastąpić wszystkie wystąpienia wybranego wyrażenia znaleziony, nie tylko jedną, specjalnie wyróżnioną pozycją.

## <a name="see-also"></a>Zobacz także

[Generowanie kodu](../code-generation-in-visual-studio.md)  
[Podgląd zmian](../../ide/preview-changes.md) 