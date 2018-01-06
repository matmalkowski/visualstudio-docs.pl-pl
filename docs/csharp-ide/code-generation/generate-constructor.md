---
title: Generuj Konstruktor - generowania kodu (C#) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 9ffa85d768939522935199edde6d0f19b3f2b7a2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="generate-a-constructor-in-c"></a>Generuj Konstruktor w języku C# #
**Co:** umożliwia natychmiast generowania kodu dla nowego konstruktora dla klasy. 

**Kiedy:** wprowadzenie nowego konstruktora, aby poprawnie zadeklarować automatycznie lub zmodyfikuj istniejące konstruktora. 

**Dlaczego:** można zadeklarować konstruktora przed użyciem go, jednak ta funkcja spowoduje wygenerowanie, z użyciem odpowiednich parametrów, automatycznie. Ponadto modyfikowanie istniejącego Konstruktor wymaga aktualizacji wszystkich callsites, chyba że korzystania z tej funkcji automatycznej aktualizacji.

**Jak:** kilka sposobów, aby wygenerować Konstruktor:
- [Generuj Konstruktor i wybierz elementy członkowskie](#pick)
- [Generuj Konstruktor z wybranych pól](#selection)
- [Generuj Konstruktor z użycia nowego](#usage)
- [Dodaj parametr do istniejących konstruktora](#addparameter)
- [Utwórz i zainicjuj pola/właściwości z parametru konstruktora](#create)

## <a id = "pick"></a>Generuj Konstruktor i wybierz elementy członkowskie
1. Umieść kursor w dowolnym pustym wierszu w klasie:

   ![Kursor w pustym wierszu](media/constructor1_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **Generuj Konstruktor...**  z menu podręcznego okna podglądu.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **Generuj Konstruktor...**  z menu podręcznego okna podglądu.
     * Kliknij przycisk ![Żarówka](media/bulb.png) ikonę, która jest wyświetlana na lewym marginesie, jeśli kursor tekstu znajduje się już na pusty wiersz w klasie.

   ![Generowanie podglądu — Konstruktor](media/constructor1_preview.png)

1. Wyświetli się okno dialogowe pozwala wybrać składniki, które mają być używane jako parametry konstruktora, jak również kolejność ich (z up i strzałki w dół). Naciśnij klawisz **Ok** aby zatwierdzić zmiany.
  
   ![Wybierz elementy członkowskie w oknie dialogowym](media/constructor1_dialog.png)

   >[!TIP] 
   >Możesz sprawdzić **dodać sprawdzenia wartości null** pole wyboru, aby automatycznie wygenerować sprawdzenia wartości null dla parametry konstruktora.

1. Konstruktor zostanie utworzony z wybranych parametrów w określonej kolejności.
   ![Generowanie wyników — Konstruktor](media/constructor1_result.png)

## <a id="selection"></a>Generuj Konstruktor z wybranych pól
1. Wyróżnij elementy członkowskie chcesz mieć w Twojej wygenerowany Konstruktor: ![Wyróżnij elementy członkowskie](media/constructor2_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **Generuj Konstruktor "TypeName(...)"**  z menu podręcznego okna podglądu.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **Generuj Konstruktor "TypeName(...)"**  z menu podręcznego okna podglądu.
     * Kliknij przycisk ![Żarówka](media/bulb.png) ikonę, która pojawia się na lewym marginesie, gdy kursor tekstu znajduje się już na wiersz z zaznaczenia.

     ![Generowanie podglądu — Konstruktor](media/constructor2_preview.png)

1. Konstruktor zostanie utworzony z wybranych parametrów.
     ![Generowanie wyników — Konstruktor](media/constructor2_result.png)

## <a id="usage"></a>Generuj Konstruktor z użycia nowego
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

## <a id="selection"></a>Dodaj parametr do istniejących konstruktora
1. Dodawanie parametru do istniejącego wystąpienia obiektu.

1. Umieść kursor w wierszu przypadku czerwona falista wskazujący używano konstruktora, który jeszcze nie istnieje.
    
    ![Generuj Konstruktor wyróżnienia](media/constructor4_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **dodać parametr "TypeName(...)"**  z menu podręcznego okna podglądu.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **dodać parametr "TypeName(...)"**  z menu podręcznego okna podglądu.
     * Umieść kursor nad czerwona falista, a następnie kliknij przycisk ![Żarówka](media/bulb.png) ikonę, która jest wyświetlana.
     * Kliknij przycisk ![Żarówka](media/bulb.png) ikonę, która jest wyświetlana na lewym marginesie, gdy kursor tekstu jest już w wierszu zawierającym czerwona falista.

    ![Generowanie podglądu — Konstruktor](media/constructor4_preview.png)

1. Parametr zostaną dodane automatycznie z typem wywnioskować na podstawie jej użycia.
   
   ![Generowanie wyników — Konstruktor](media/constructor4_result.png)

## <a id="create"></a>Utwórz i zainicjuj pola/właściwości z parametru konstruktora
1. Z istniejących konstruktora Dodaj parametr:

   ![Generuj Konstruktor wyróżnienia](media/constructor5_highlight.png)

1. Umieść kursor w nowo dodanym parametrze.

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl +.** do wyzwalania **szybkie akcje i Refaktoryzacje** menu i wybierz **tworzenie i zainicjować właściwości "YourProperty"** lub **tworzenie i zainicjować pola "YourField"** z Podręcznego okna podglądu.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **tworzenie i zainicjować właściwości "YourProperty"** lub **tworzenie i zainicjować pola "YourField"**z menu podręcznego okna podglądu.
     * Kliknij przycisk ![Żarówka](media/bulb.png) ikonę, która pojawia się na lewym marginesie, gdy kursor tekstu znajduje się już na wiersz za pomocą parametru dodany.

   ![Generowanie podglądu — Konstruktor](media/constructor5_preview.png)

1. Pola lub właściwości zostanie utworzona i automatycznie o nazwie zgodne z typami.

   ![Generowanie wyników — Konstruktor](media/constructor5_result.png)
  
## <a name="see-also"></a>Zobacz też  
[Generowanie kodu (C#)](../code-generation-csharp.md)  
[Podgląd zmian](../../ide/preview-changes.md)