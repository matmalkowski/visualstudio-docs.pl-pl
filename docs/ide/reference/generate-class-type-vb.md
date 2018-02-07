---
title: Generuj klasy lub typu - generowania kodu (Visual Basic) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: ebc361fe-d9b1-4c7a-ae28-5e71b5775460
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vsl.GenerateFromUsage
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4a4ff45a59fb53964a365f31cc4d5f48a5b159dc
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2018
---
# <a name="generate-a-class-or-type-in-visual-basic"></a>Generuj klasy lub typu w języku Visual Basic
**Co:** umożliwia natychmiast generowania kodu dla klasy lub typu. 

**Kiedy:** wprowadzenie nowej klasy lub typu i chcesz poprawnie zadeklarować, automatycznie.  

**Dlaczego:** przed użyciem, jednak ta funkcja będzie generowania klasy lub typu automatycznie można zadeklarować klasy lub typu. 

**Jak:**

1. Umieść kursor w wierszu przypadku czerwona falista wskazujący używano klasę, która jeszcze nie istnieje.

   ![Wyróżniony kod](media/class-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Keyboard**
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz jedną z opcji z menu podręcznego okna podglądu.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz jedną z opcji z menu podręcznego okna podglądu.
     * Umieść kursor nad czerwona falista, a następnie kliknij przycisk ![Żarówka](media/bulb-vb.png) ikonę, która jest wyświetlana.
     * Kliknij przycisk ![Żarówka](media/bulb-vb.png) ikonę, która jest wyświetlana na lewym marginesie, gdy kursor tekstu jest już w wierszu zawierającym czerwona falista.

   ![Generowanie podglądu — klasa](media/class-preview-vb.png)

   Wybór | Opis
   --- | ---
   Generuj klasy*TypeName*"w nowym pliku | Tworzy klasę o nazwie *TypeName* w pliku o nazwie *TypeName*.cs/.vb
   Generuj klasy*TypeName*" | Tworzy klasę o nazwie *TypeName* w bieżącym pliku.
   Generuj klasy zagnieżdżonej*TypeName*" | Tworzy klasę o nazwie *TypeName* zagnieżdżone wewnątrz klasy.
   Generowanie nowego typu... | Tworzy nową klasą lub strukturą z wszystkich właściwości, które określisz.

   >[!TIP]
   >Użyj [ **podgląd zmian** ](../../ide/preview-changes.md) łącze umieszczone u dołu okna podglądu, aby zobaczyć wszystkie zmiany wprowadzone przed dokonaniem wyboru.

1. W przypadku wybrania **wygenerować nowy typ...**  elementu, okno dialogowe będzie wyskakujące umożliwiający niektóre dodatkowe akcje.

   ![Generowanie typu](media/class-newtype-vb.png)

   Wybór | Opis
   --- | ---
   Access | Ustaw typ ma *domyślne*, *wewnętrzne* lub *publicznego* dostępu.
   rodzaj | To może być ustawiona jako *klasy* lub *struktury*.
   Nazwa | Nie można zmienić i będzie można już wpisana nazwa.
   Projekt | Jeśli istnieje wiele projektów w rozwiązaniu, są dostępne miejsce klasie/strukturze wygaśnięcia.
   Nazwa pliku | Można utworzyć nowego pliku lub typu można dodać do istniejącego pliku.

1. Klasa/struktura zostaną utworzone automatycznie przy użyciu konstruktora wywnioskować na podstawie jej użycia.

   ![Generowanie wyników — klasa](media/class-result-vb.png)

## <a name="see-also"></a>Zobacz także

[Generowanie kodu](../code-generation-in-visual-studio.md)  
[Podgląd zmian](../../ide/preview-changes.md)