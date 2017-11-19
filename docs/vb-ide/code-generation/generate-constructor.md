---
title: Generuj Konstruktor - generowania kodu (Visual Basic) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0380076319a80ba85aa59c388959baece9008e94
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-constructor-in-visual-basic"></a>Generuj Konstruktor w języku Visual Basic
**Co:** umożliwia natychmiast generowania kodu dla nowego konstruktora dla klasy. 

**Kiedy:** wprowadzenie nowego konstruktora i aby poprawnie zadeklarować, automatycznie.  

**Dlaczego:** można zadeklarować konstruktora przed użyciem go, jednak ta funkcja spowoduje wygenerowanie, z użyciem odpowiednich parametrów, automatycznie. 

**Jak:**

1. Umieść kursor w wierszu przypadku czerwona falista wskazujący używano konstruktora, który jeszcze nie istnieje.

   ![Wyróżniony kod](media/constructor_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz  **Generuj Konstruktor w "*TypeName*" ** z menu podręcznego okna podglądu.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz  **Generuj Konstruktor w "*TypeName*" ** z menu podręcznego okna podglądu.
     * Umieść kursor nad czerwona falista, a następnie kliknij przycisk ![Żarówka](media/bulb.png) ikonę, która jest wyświetlana.
     * Kliknij przycisk ![Żarówka](media/bulb.png) ikonę, która jest wyświetlana na lewym marginesie, gdy kursor tekstu jest już w wierszu zawierającym czerwona falista.

   ![Generowanie podglądu — Konstruktor](media/constructor_preview.png)

   >[!TIP]
   >Użyj [ **podgląd zmian** ](../../ide/preview-changes.md) łącze umieszczone u dołu okna podglądu, aby zobaczyć wszystkie zmiany wprowadzone przed dokonaniem wyboru.

1. Konstruktor zostaną utworzone automatycznie, wszystkie parametry wywnioskować na podstawie jej użycia.

   ![Generowanie wyników — Konstruktor](media/constructor_result.png)
  
## <a name="see-also"></a>Zobacz też  
[Generowanie kodu (Visual Basic)](../code-generation-vb.md)  
[Podgląd zmian](../../ide/preview-changes.md)