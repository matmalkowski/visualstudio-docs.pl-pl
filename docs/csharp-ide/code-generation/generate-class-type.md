---
title: Generuj klasy lub typu - generowania kodu (C#) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: ebc361fe-d9b1-4c7a-ae28-5e71b5775460
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vsl.GenerateFromUsage
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: c72b9e898bd150e0d4ec1cc6a7a91d1eb7e6b7a8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="generate-a-class-or-type-in-c"></a>Generuj klasy lub typu w języku C# #
**Co:** umożliwia natychmiast generowania kodu dla klasy lub typu. 

**Kiedy:** wprowadzenie nowej klasy lub typu i chcesz poprawnie zadeklarować, automatycznie.  

**Dlaczego:** przed użyciem, jednak ta funkcja będzie generowania klasy lub typu automatycznie można zadeklarować klasy lub typu. 

**Jak:**

1. Umieść kursor w wierszu przypadku czerwona falista wskazujący używano klasę, która jeszcze nie istnieje.

   ![Wyróżniony kod](media/class_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz jedną z opcji z menu podręcznego okna podglądu.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz jedną z opcji z menu podręcznego okna podglądu.
     * Umieść kursor nad czerwona falista, a następnie kliknij przycisk ![Żarówka](media/bulb.png) ikonę, która jest wyświetlana.
     * Kliknij przycisk ![Żarówka](media/bulb.png) ikonę, która jest wyświetlana na lewym marginesie, gdy kursor tekstu jest już w wierszu zawierającym czerwona falista.

   ![Generowanie podglądu — klasa](media/class_preview.png)

   Wybór | Opis
   --- | ---
   Generuj klasy*TypeName*"w nowym pliku | Tworzy klasę o nazwie *TypeName* w pliku o nazwie *TypeName*.cs/.vb
   Generuj klasy*TypeName*" | Tworzy klasę o nazwie *TypeName* w bieżącym pliku.
   Generuj klasy zagnieżdżonej*TypeName*" | Tworzy klasę o nazwie *TypeName* zagnieżdżone wewnątrz klasy.
   Generowanie nowego typu... | Tworzy nową klasą lub strukturą z wszystkich właściwości, które określisz.

   >[!TIP]
   >Użyj [ **podgląd zmian** ](../../ide/preview-changes.md) łącze umieszczone u dołu okna podglądu, aby zobaczyć wszystkie zmiany wprowadzone przed dokonaniem wyboru.

1. W przypadku wybrania **wygenerować nowy typ...**  elementu, okno dialogowe będzie wyskakujące umożliwiający niektóre dodatkowe akcje.

   ![Generowanie typu](media/class_newtype.png)

   Wybór | Opis
   --- | ---
   Access | Ustaw typ ma *domyślne*, *wewnętrzne* lub *publicznego* dostępu.
   rodzaj | To może być ustawiona jako *klasy* lub *struktury*.
   Nazwa | Nie można zmienić i będzie można już wpisana nazwa.
   Projekt | Jeśli istnieje wiele projektów w rozwiązaniu, są dostępne miejsce klasie/strukturze wygaśnięcia.
   Nazwa pliku | Można utworzyć nowego pliku lub typu można dodać do istniejącego pliku.

1. Klasa/struktura zostaną utworzone automatycznie przy użyciu konstruktora wywnioskować na podstawie jej użycia.

   ![Generowanie wyników — klasa](media/class_result.png)

## <a name="see-also"></a>Zobacz też  
[Generowanie kodu (C#)](../code-generation-csharp.md)  
[Podgląd zmian](../../ide/preview-changes.md)