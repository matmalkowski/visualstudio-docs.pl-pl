---
title: Generuj Konstruktor w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 0767b47fcf4456e1ac198674ece6c9de31850279
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="generate-a-constructor-in-visual-studio"></a>Generuj Konstruktor w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

- Visual Basic

**Co:** umożliwia natychmiast generowania kodu dla nowego konstruktora dla klasy.

**Kiedy:** wprowadzenie nowego konstruktora, aby poprawnie zadeklarować automatycznie lub zmodyfikuj istniejące konstruktora.

**Dlaczego:** można zadeklarować konstruktora przed użyciem go, jednak ta funkcja spowoduje wygenerowanie, z użyciem odpowiednich parametrów, automatycznie. Ponadto modyfikowanie istniejącego Konstruktor wymaga aktualizacji wszystkich callsites, chyba że korzystania z tej funkcji automatycznej aktualizacji.

**Jak:** kilka sposobów, aby wygenerować Konstruktor:

   - [Generuj Konstruktor i wybierz elementy członkowskie](#pick)
   - [Generuj Konstruktor z wybranych pól](#selection)
   - [Generuj Konstruktor z użycia nowego](#usage)
   - [Dodaj parametr do istniejących konstruktora](#addparameter)
   - [Utwórz i zainicjuj pola/właściwości z parametru konstruktora](#create)

## <a id = "pick"></a> Generuj Konstruktor i wybierz elementy członkowskie (C# tylko)

1. Umieść kursor w dowolnym pustym wierszu w klasie:

   ![Kursor w pustym wierszu](media/constructor1-highlight-cs.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
     - Kliknij przycisk ![Żarówka](media/bulb-cs.png) ikonę, która jest wyświetlana na lewym marginesie, jeśli kursor tekstu znajduje się już na pusty wiersz w klasie.

   ![Generowanie podglądu — Konstruktor](media/constructor1-preview-cs.png)

1. Wybierz **Generuj Konstruktor...**  z menu rozwijanego.

   **Wybierz memebers** zostanie otwarte okno dialogowe.

1. Wybierz elementy członkowskie, które chcesz dołączyć jako parametry konstruktora. Można je za pomocą w górę kolejności i strzałki w dół. Wybierz **OK**.

   ![Wybierz elementy członkowskie w oknie dialogowym](media/constructor1-dialog-cs.png)

   > [!TIP]
   > Możesz sprawdzić **dodać sprawdzenia wartości null** pole wyboru, aby automatycznie wygenerować sprawdzenia wartości null dla parametry konstruktora.

   Konstruktor jest tworzony z określonymi parametrami.

   ![Generowanie wyników — Konstruktor](media/constructor1-result-cs.png)

## <a id="selection"></a> Generuj Konstruktor z wybranego pola (C# tylko)

1. Wyróżnij elementy członkowskie, które chcesz mieć w Twojej wygenerowany Konstruktor:

   ![Wyróżnij elementy członkowskie](media/constructor2-highlight-cs.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
     - Kliknij przycisk ![Żarówka](media/bulb-cs.png) ikonę, która pojawia się na lewym marginesie, gdy kursor tekstu znajduje się już na wiersz z zaznaczenia.

     ![Generowanie podglądu — Konstruktor](media/constructor2-preview-cs.png)

1. Wybierz **Generuj Konstruktor "TypeName(...)"**  z menu rozwijanego.

   Konstruktor jest tworzony z wybranych parametrów.

   ![Generowanie wyników — Konstruktor](media/constructor2-result-cs.png)

## <a id="usage"></a> Generuj Konstruktor z użycia nowego (C# i Visual Basic)

1. Umieść kursor w wierszu przypadku czerwona falista. Czerwona falista wskazuje wywołanie konstruktora, który jeszcze nie istnieje.

   - C#:

    ![Wyróżniony kod C#](media/constructor-highlight-cs.png)

   - Visual Basic:

    ![Wyróżniony Kod VB](media/constructor-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
     - Umieść kursor nad czerwona falista, a następnie kliknij przycisk ![Żarówka](media/bulb-cs.png) ikonę, która jest wyświetlana.
     - Kliknij przycisk ![Żarówka](media/bulb-cs.png) ikonę, która jest wyświetlana na lewym marginesie, gdy kursor tekstu jest już w wierszu zawierającym czerwona falista.

    ![Generowanie podglądu — Konstruktor](media/constructor-preview-cs.png)

1. Wybierz **Generuj Konstruktor w "*TypeName*"** z menu rozwijanego.

   > [!TIP]
   > Użyj **podgląd zmian** łącze umieszczone u dołu okna podglądu [aby zobaczyć wszystkie zmiany](../../ide/preview-changes.md) która zostanie podjęta przed dokonaniem wyboru.

   Konstruktor jest tworzony, wszystkie parametry wywnioskować na podstawie jego użycia.

   - C#:

      ![Generowanie wynik metody C#](media/constructor-result-cs.png)

   - Visual Basic:

      ![Generowanie wynik metody VB](media/constructor-result-vb.png)

## <a id="addparameter"></a> Dodawanie parametru do istniejących — Konstruktor (C# tylko)

1. Dodawanie parametru do istniejących wywołania konstruktora.

1. Umieść kursor w wierszu przypadku czerwona falista wskazujący używano konstruktora, który jeszcze nie istnieje.

    ![Generuj Konstruktor wyróżnienia](media/constructor4-highlight-cs.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
     - Umieść kursor nad czerwona falista, a następnie kliknij przycisk ![Żarówka](media/bulb-cs.png) ikonę, która jest wyświetlana.
     - Kliknij przycisk ![Żarówka](media/bulb-cs.png) ikonę, która jest wyświetlana na lewym marginesie, gdy kursor tekstu jest już w wierszu zawierającym czerwona falista.

    ![Generowanie podglądu — Konstruktor](media/constructor4-preview-cs.png)

1. Wybierz **dodać parametr "TypeName(...)"**  z menu rozwijanego.

   Parametr jest dodawana do konstruktora z typem wywnioskować na podstawie jej użycia.

   ![Generowanie wyników — Konstruktor](media/constructor4-result-cs.png)

## <a id="create"></a> Utwórz i zainicjuj pola lub właściwości w parametrze — Konstruktor (C# tylko)

1. Znajdź istniejący Konstruktor i dodać parametr:

   ![Generuj Konstruktor wyróżnienia](media/constructor5-highlight-cs.png)

1. Umieść kursor w nowo dodanym parametrze.

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
     - Kliknij przycisk ![Żarówka](media/bulb-cs.png) ikonę, która pojawia się na lewym marginesie, gdy kursor tekstu znajduje się już na wiersz za pomocą parametru dodany.

   ![Generowanie podglądu — Konstruktor](media/constructor5-preview-cs.png)

1. Wybierz **tworzenie i Inicjowanie właściwości** lub **tworzenie i Inicjowanie pola** z menu rozwijanego.

   Pole lub właściwość został zadeklarowany i automatycznie o nazwie zgodne z typami. Wiersz kodu jest także dodawane do zainicjowania pola lub właściwości w treści konstruktora.

   ![Generowanie wyników — Konstruktor](media/constructor5-result-cs.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)