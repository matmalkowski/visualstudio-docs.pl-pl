---
title: Generowanie konstruktora w programie Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 091caf9db4152b7c349fdf717d97639b360bb602
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513027"
---
# <a name="generate-a-constructor-in-visual-studio"></a>Generowanie konstruktora w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

- Visual Basic

**Co:** pozwala natychmiast generowania kodu dla nowego konstruktora klasy.

**Kiedy:** wprowadzenie nowego konstruktora, aby poprawnie Zadeklaruj go automatycznie lub zmodyfikuj istniejące konstruktora.

**Dlaczego:** można zadeklarować konstruktora przed użyciem, ale tej funkcji będzie generowana, za pomocą odpowiednich parametrów, automatycznie. Ponadto modyfikowania istniejących Konstruktor wymaga aktualizacji wszystkich callsites, chyba, że ta funkcja umożliwia automatyczne aktualizowanie.

**Jak:** istnieje kilka sposobów, aby wygenerować Konstruktor:

   - [Generuj Konstruktor i wybierz elementy członkowskie](#pick)
   - [Generuj Konstruktor z wybranych pól](#selection)
   - [Generuj Konstruktor podczas korzystania z nowego](#usage)
   - [Dodaj parametr do konstruktora istniejące](#addparameter)
   - [Tworzenie i Inicjowanie pola/właściwości z parametru konstruktora](#create)

## <a id = "pick"></a> Generuj Konstruktor i wybierz elementy członkowskie (tylko język C#)

1. Umieść kursor w dowolnym pustym wierszu w klasie:

   ![Kursor w pustym wierszu](media/constructor1-highlight-cs.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
     - Kliknij ikonę ![Żarówka](media/bulb-cs.png) ikona, który pojawia się na lewym marginesie, jeśli kursor tekstu jest już w pustym wierszu w klasie.

   ![Generowanie konstruktora (wersja zapoznawcza)](media/constructor1-preview-cs.png)

1. Wybierz **Generuj Konstruktor** z menu rozwijanego.

   **Wybierz składowe** zostanie otwarte okno dialogowe.

1. Wybierz składowe, które mają zostać uwzględnione jako parametry konstruktora. Można uporządkować je przy użyciu w górę i strzałki w dół. Wybierz **OK**.

   ![Wybierz elementy członkowskie w oknie dialogowym](media/constructor1-dialog-cs.png)

   > [!TIP]
   > Możesz sprawdzić **Dodaj sprawdzenia wartości null** pole wyboru, aby automatycznie wygenerować sprawdzanie wartości null dla parametry konstruktora.

   Konstruktor jest tworzony przy użyciu określonych parametrów.

   ![Generuj Konstruktor wynik](media/constructor1-result-cs.png)

## <a id="selection"></a> Generuj Konstruktor z wybranych pól (tylko język C#)

1. Wyróżnij elementy członkowskie, których chcesz użyć w wygenerowanych konstruktora:

   ![Wyróżnij elementy członkowskie](media/constructor2-highlight-cs.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
     - Kliknij ikonę ![Żarówka](media/bulb-cs.png) ikonę, która pojawia się na lewym marginesie, gdy kursor tekstu znajduje się już na wiersz z zaznaczenia.

     ![Generowanie konstruktora (wersja zapoznawcza)](media/constructor2-preview-cs.png)

1. Wybierz **Generuj Konstruktor "TypeName(...)"**  z menu rozwijanego.

   Konstruktor jest tworzony przy użyciu wybranych parametrów.

   ![Generuj Konstruktor wynik](media/constructor2-result-cs.png)

## <a id="usage"></a> Generuj Konstruktor podczas korzystania z nowego (C# i Visual Basic)

1. Umieść kursor w wierszu gdzie znajduje się czerwona fala. Czerwona fala wskazuje wywołanie konstruktora, który jeszcze nie istnieje.

   - C#:

    ![Wyróżniony kod C#](media/constructor-highlight-cs.png)

   - Visual Basic:

    ![Wyróżniony Kod VB](media/constructor-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
     - Umieść kursor nad czerwona fala, a następnie kliknij przycisk ![Żarówka](media/bulb-cs.png) ikona, który jest wyświetlany.
     - Kliknij ikonę ![Żarówka](media/bulb-cs.png) ikona, który pojawia się na lewym marginesie, jeśli kursor tekstu jest już w wierszu zawierającym czerwona fala.

    ![Generowanie konstruktora (wersja zapoznawcza)](media/constructor-preview-cs.png)

1. Wybierz **Generowanie konstruktora w "*TypeName*"** z menu rozwijanego.

   > [!TIP]
   > Użyj **podgląd zmian** link w dolnej części okna podglądu [Aby wyświetlić wszystkie zmiany](../../ide/preview-changes.md) , zostaną wprowadzone przed dokonaniem wyboru.

   Konstruktor jest tworzony, parametrami wywnioskować na podstawie jej użycie.

   - C#:

      ![Generowanie metody powodują C#](media/constructor-result-cs.png)

   - Visual Basic:

      ![Generowanie metody powodują VB](media/constructor-result-vb.png)

## <a id="addparameter"></a> Dodaj parametr do konstruktora istniejących (tylko język C#)

1. Dodaj parametr do istniejących wywołanie konstruktora.

1. Umieść kursor w wierszu gdzie znajduje się czerwona fala wskazujący użyty Konstruktor, który jeszcze nie istnieje.

    ![Generuj Konstruktor wyróżnienia](media/constructor4-highlight-cs.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
     - Umieść kursor nad czerwona fala, a następnie kliknij przycisk ![Żarówka](media/bulb-cs.png) ikona, który jest wyświetlany.
     - Kliknij ikonę ![Żarówka](media/bulb-cs.png) ikona, który pojawia się na lewym marginesie, jeśli kursor tekstu jest już w wierszu zawierającym czerwona fala.

    ![Generowanie konstruktora (wersja zapoznawcza)](media/constructor4-preview-cs.png)

1. Wybierz **dodać parametr "TypeName(...)"**  z menu rozwijanego.

   Parametr zostanie dodany do konstruktora z typem wywnioskować na podstawie jej użycie.

   ![Generuj Konstruktor wynik](media/constructor4-result-cs.png)

## <a id="create"></a> Utwórz i zainicjuj pole lub właściwość z parametru konstruktora (tylko język C#)

1. Znajdź istniejący konstruktora, a następnie dodaj parametr:

   ![Generuj Konstruktor wyróżnienia](media/constructor5-highlight-cs.png)

1. Umieść kursor wewnątrz nowo dodany parametr.

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
     - Kliknij ikonę ![Żarówka](media/bulb-cs.png) ikona, który pojawia się na lewym marginesie, jeśli kursor tekstu jest już w wierszu zawierającym dodano parametr.

   ![Generowanie konstruktora (wersja zapoznawcza)](media/constructor5-preview-cs.png)

1. Wybierz **tworzenie i Inicjowanie właściwości** lub **tworzenie i Inicjowanie pola** z menu rozwijanego.

   Pole lub właściwość jest zadeklarowana i automatycznie nadawaną nazwę, aby dopasować swoje typy. Wiersz kodu jest także dodawane do zainicjowania pole lub właściwość w treści konstruktora.

   ![Generuj Konstruktor wynik](media/constructor5-result-cs.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)