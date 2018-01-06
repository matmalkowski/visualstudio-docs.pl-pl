---
title: "Wprowadź zmienną lokalną - generowania kodu (C#) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1490d6ac-ed56-4d03-95db-c23f23cba70d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: c52a29cb3dd408dacb805479b9680873abb047d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="introduce-a-local-variable-in-c"></a>Wprowadź zmienną lokalną w języku C# #
**Co:** pozwala natychmiast wygenerować zmiennej lokalnej, aby zastąpić istniejącą wyrażenia.

**Kiedy:** kod, który można łatwo wykorzystywać później, jakby był w zmiennej lokalnej.  

**Dlaczego:** można skopiuj i Wklej kod wielokrotnie będzie używane w różnych lokalizacjach, jednak byłoby lepiej wykonać tę operację jeszcze raz, zapisz wynik w zmiennej lokalnej i używać lokalnego throughought zmiennej. 

**Jak:**

1. Zaznacz wyrażenie, które ma zostać przypisany do zmiennej lokalnej.

   ![Wyróżniony kod](media/local_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl +.** do wyzwalania **szybkie akcje i Refaktoryzacje** menu i wybierz  **wprowadź element lokalny dla (wszystkie wystąpienia) "*wyrażenie*" ** z menu podręczne okno podglądu, gdzie *wyrażenie* kodu zostały wyróżnione.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz  **wprowadź element lokalny dla (wszystkie wystąpienia) "*wyrażenie*" ** z menu podręcznego okna podglądu gdzie *wyrażenie* kodu zostały wyróżnione.
     * Kliknij przycisk ![Żarówka](media/bulb.png) ikonę, która jest wyświetlana na lewym marginesie, gdy kursor tekstu jest już w wierszu zawierającym czerwona falista.

   ![Wprowadzenie Podgląd lokalny](media/local_preview.png)

   >[!TIP]
   >Użyj [ **podgląd zmian** ](../../ide/preview-changes.md) łącze umieszczone u dołu okna podglądu, aby zobaczyć wszystkie zmiany wprowadzone przed dokonaniem wyboru.

1. Zmienna lokalna zostaną utworzone automatycznie z typem wywnioskować na podstawie jej użycia.  Podaj nową nazwę Nowa zmienna lokalna, wpisując ją.

   ![Wprowadzenie wyniku lokalnej](media/local_result.png)

   >[!NOTE]
   >Można użyć **.. wystąpień aplikacji...**  menu opcję, aby zastąpić wszystkie wystąpienia wybranego wyrażenia znaleziony, nie tylko jedną, specjalnie wyróżnioną pozycją.

## <a name="see-also"></a>Zobacz też  
[Generowanie kodu (C#)](../code-generation-csharp.md)  
[Podgląd zmian](../../ide/preview-changes.md) 
