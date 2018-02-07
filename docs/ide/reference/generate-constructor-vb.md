---
title: Generuj Konstruktor - generowania kodu (Visual Basic) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 891a33b74927d45434c4614dc4c5d7f1533ba4c0
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2018
---
# <a name="generate-a-constructor-in-visual-basic"></a>Generuj Konstruktor w języku Visual Basic
**Co:** umożliwia natychmiast generowania kodu dla nowego konstruktora dla klasy. 

**Kiedy:** wprowadzenie nowego konstruktora i aby poprawnie zadeklarować, automatycznie.  

**Dlaczego:** można zadeklarować konstruktora przed użyciem go, jednak ta funkcja spowoduje wygenerowanie, z użyciem odpowiednich parametrów, automatycznie. 

**Jak:**

1. Umieść kursor w wierszu przypadku czerwona falista wskazujący używano konstruktora, który jeszcze nie istnieje.

   ![Wyróżniony kod](media/constructor-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Keyboard**
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **Generuj Konstruktor w "*TypeName*"** z menu podręcznego okna podglądu.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **Generuj Konstruktor w "*TypeName*"** z menu podręcznego okna podglądu.
     * Umieść kursor nad czerwona falista, a następnie kliknij przycisk ![Żarówka](media/bulb-vb.png) ikonę, która jest wyświetlana.
     * Kliknij przycisk ![Żarówka](media/bulb-vb.png) ikonę, która jest wyświetlana na lewym marginesie, gdy kursor tekstu jest już w wierszu zawierającym czerwona falista.

   ![Generowanie podglądu — Konstruktor](media/constructor-preview-vb.png)

   >[!TIP]
   >Użyj [ **podgląd zmian** ](../../ide/preview-changes.md) łącze umieszczone u dołu okna podglądu, aby zobaczyć wszystkie zmiany wprowadzone przed dokonaniem wyboru.

1. Konstruktor zostaną utworzone automatycznie, wszystkie parametry wywnioskować na podstawie jej użycia.

   ![Generowanie wyników — Konstruktor](media/constructor-result-vb.png)
 
## <a name="see-also"></a>Zobacz także

[Generowanie kodu](../code-generation-in-visual-studio.md)  
[Podgląd zmian](../../ide/preview-changes.md)