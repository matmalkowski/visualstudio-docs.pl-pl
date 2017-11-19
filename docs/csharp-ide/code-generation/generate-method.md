---
title: "Generate — metoda - generowania kodu (C#) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683790b4-b68b-42d7-8dc4-a68eca05aa01
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 626db0d9c62fc606539fc9d72fc14c3651dca7ff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-method-in-c"></a>Generowanie metody w języku C# #
**Co:** można bezpośrednio dodać metodę do klasy. 

**Kiedy:** wprowadzenie nowej metody i aby poprawnie zadeklarować, automatycznie.  

**Dlaczego:** można deklarowaniu — metoda i parametry przed użyciem go, jednak funkcja ta automatycznie wygeneruje deklaracji. 

**Jak:**

1. Umieść kursor w wierszu przypadku czerwona falista wskazujący użyto metody, która jeszcze nie istnieje.

   ![Wyróżniony kod](media/method_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl +.** do wyzwalania **szybkie akcje i Refaktoryzacje** menu i wybierz **wygenerować metody** z menu podręcznego okna podglądu.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **wygenerować metody** z menu podręcznego okna podglądu.
     * Umieść kursor nad czerwona falista, a następnie kliknij przycisk ![Żarówka](media/bulb.png) ikonę, która jest wyświetlana.
     * Kliknij przycisk ![Żarówka](media/bulb.png) ikonę, która jest wyświetlana na lewym marginesie, gdy kursor tekstu jest już w wierszu zawierającym czerwona falista.

   ![Generowanie podglądu — metoda](media/method_preview.png)

   >[!TIP]
   >Użyj [ **podgląd zmian** ](../../ide/preview-changes.md) łącze umieszczone u dołu okna podglądu, aby zobaczyć wszystkie zmiany wprowadzone przed dokonaniem wyboru.

1. Metoda zostaną utworzone automatycznie, wszystkie parametry wywnioskować na podstawie jej użycia.

   ![Generowanie wyników — metoda](media/method_result.png)

## <a name="see-also"></a>Zobacz też  
[Generowanie kodu (C#)](../code-generation-csharp.md)  
[Podgląd zmian](../../ide/preview-changes.md)
