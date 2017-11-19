---
title: "Użyj map kodu do debugowania aplikacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- Visual Studio Ultimate, visualizing code
- Visual Studio Ultimate, navigating code visually
- Visual Studio Ultimate, understanding code
- Visual Studio Ultimate, mapping code relationships
- Visual Studio Ultimate, code maps
- mapping code relationships
- code maps
- mapping relationships in code
ms.assetid: 9fd0c9a2-d351-40c8-be88-0749788264bf
caps.latest.revision: "49"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.openlocfilehash: d9d1f6ac733a0feccb3f2fa8175fb85ed035b35c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="use-code-maps-to-debug-your-applications"></a>Używanie map kodu do debugowania aplikacji
Mapy kodu mogą pomóc uniknąć poczucia zagubienia w dużych baz kodu, kod nieznane lub starszego kodu. Na przykład debugowanie, może być konieczne przeglądać kod pochodzące z wielu plików i projektów. Używanie map kodu do nawigację fragmentów kodu i zrozumieć ich relacje między nimi. Dzięki temu nie trzeba informacji o tym kodzie w nagłówek lub utworzyć oddzielne diagram. Dzięki pracy zostanie przerwany, kod mapy pomocy odświeżania pamięci dotyczące kodu, nad którymi pracuje.  
  
 ![&#45; mapy kodu Mapowanie relacji w kodzie](../modeling/media/codemapstoryboardpaint.png "CodeMapStoryboardPaint")  
  
 **Pokazuje zieloną strzałkę, gdy kursor zostanie wyświetlony w edytorze**  
  
 Szczegółowe poleceń i działań można używać podczas pracy z mapy kodu, patrz [przeglądania i zmieniać code map](../modeling/browse-and-rearrange-code-maps.md).  
  
## <a name="understand-the-problem"></a>Omówienie problemu  
 Przypuśćmy, że w programie graficznym, nad którym pracujesz, znajduje się błąd. Aby odtworzyć ten błąd, otwórz rozwiązanie w Visual Studio i naciśnij klawisz **F5** można rozpocząć debugowania.  
  
 Gdy Rysowanie linii i wybierz polecenie **Cofnij Moje ostatnie pociągnięcie**, aż do rysowania dalej nic się nie dzieje.  
  
 ![&#45; mapy kodu Błąd reprodukcja](../modeling/media/codemapstoryboardpaint0.png "CodeMapStoryboardPaint0")  
  
 Dzięki uruchamiania badanie, wyszukując `Undo` metody. Możesz znaleźć `PaintCanvas` klasy.  
  
 ![&#45; mapy kodu Znajdź kod](../modeling/media/codemapstoryboardpaint1.png "CodeMapStoryboardPaint1")  
  
## <a name="start-mapping-the-code"></a>Uruchamianie mapowania kodu  
 Teraz uruchomić mapowania `undo` — metoda i relacje. W edytorze kodu, możesz dodać `undo` — metoda i pola, które odwołuje się do nowej mapy kodu. Podczas tworzenia nowej mapy może trochę czasu może zająć indeksowanie kodu. Dzięki temu następne operacje działają szybciej.  
  
 ![&#45; mapy kodu Pokaż metody i powiązanych pól](../modeling/media/codemapstoryboardpaint3.png "CodeMapStoryboardPaint3")  
  
> [!TIP]
>  Zielone podświetlenie pokazuje ostatnie elementy dodane do mapy. Zieloną strzałkę pokazuje kursor w pozycji w kodzie. Strzałki między elementami reprezentują różne relacje. Aby uzyskać więcej informacji na temat elementów na mapie, należy przesuwanie wskaźnika myszy nad nimi i badanie etykietki.  
  
 ![&#45; mapy kodu Pokaż etykietki narzędzi](../modeling/media/codemapstoryboardpaint4.png "CodeMapStoryboardPaint4")  
  
## <a name="navigate-and-examine-code-from-the-map"></a>Nawigowanie i sprawdzanie kodu z mapy  
 Aby zobaczyć definicji kodu dla każdego pola, kliknij dwukrotnie pole na mapie lub wybierz pole i naciśnij klawisz **F12**. Zielona strzałka przesuwa się między elementami na mapie. Kursor w edytorze kodu również przesuwa się automatycznie.  
  
 ![&#45; mapy kodu Sprawdź definicję pola](../modeling/media/codemapstoryboardpaint5.png "CodeMapStoryboardPaint5")  
  
 ![&#45; mapy kodu Sprawdź definicję pola](../modeling/media/codemapstoryboardpaint5a.png "CodeMapStoryboardPaint5A")  
  
> [!TIP]
>  Zieloną strzałkę na mapie możesz również przesunąć, przesuwając kursor w edytorze kodu.  
  
## <a name="understand-relationships-between-pieces-of-code"></a>Omówienie relacji między fragmentami kodu  
 Teraz chcesz wiedzieć, który inny kod współdziała z `history` i `paintObjects` pól. Możesz dodać do mapy wszystkie metody odwołujące się do tych pól. Można to zrobić z mapy lub edytora kodu.  
  
 ![&#45; mapy kodu Znajdź wszystkie odwołania](../modeling/media/codemapstoryboardpaint6.png "CodeMapStoryboardPaint6")  
  
 ![Otwórz mapy kodu w edytorze kodu](../modeling/media/codemapstoryboardpaint6a.PNG "CodeMapStoryboardPaint6A")  
  
> [!NOTE]
>  Po dodaniu elementów z projektu, który jest współużytkowany przez wiele aplikacji, takich jak Windows Phone lub Sklepu Windows, a następnie te elementy są umieszczane w projekcie aplikacji aktualnie aktywny na mapie. Tak Jeśli Zmienianie kontekstu do innego projektu aplikacji, a następnie zmienia także kontekstu na mapie dla dowolnej nowo dodanych elementów z projektu udostępnionego. Operacje wykonywane za pomocą elementu na mapie dotyczą tylko tych elementów, które współużytkują ten sam kontekst.  
  
 Zmień układ, aby przeorganizować przepływ relacji i poprawić czytelność mapy. Elementy na mapie możesz również przesuwać, przeciągając je.  
  
 ![&#45; mapy kodu Zmiana układu](../modeling/media/codemapstoryboardpaint7a.png "CodeMapStoryboardPaint7A")  
  
> [!TIP]
>  Domyślnie **przyrostową układu** jest włączona. Dzięki temu mapa jest reorganizowana w możliwie najmniejszym stopniu przy dodawaniu nowych elementów. Aby zmienić kolejność całego mapy za każdym razem, gdy dodawania nowych elementów, wyłącz **przyrostową układu**.  
  
 ![&#45; mapy kodu Zmiana układu](../modeling/media/codemapstoryboardpaint7.png "CodeMapStoryboardPaint7")  
  
 Zbadajmy te metody. Na mapie, kliknij dwukrotnie **PaintCanvas** metody, lub wybierz ta metoda i naciśnij klawisz **F12**. Dowiedz się, że ta metoda tworzy `history` i `paintObjects` jako pusty listy.  
  
 ![&#45; mapy kodu Sprawdź definicję metody](../modeling/media/codemapstoryboardpaint8.png "CodeMapStoryboardPaint8")  
  
 Teraz Powtórz te same kroki, aby sprawdzić `clear` definicję metody. Dowiesz się, że `clear` wykonuje pewne zadania związane z `paintObjects` i `history`. Następnie wywołuje `Repaint` metody.  
  
 ![&#45; mapy kodu Sprawdź definicję metody](../modeling/media/codemapstoryboardpaint9.png "CodeMapStoryboardPaint9")  
  
 Teraz zbadać `addPaintObject` definicję metody. Wykonuje także niektóre zadania związane z `history` i `paintObjects`. Wywołuje również `Repaint`.  
  
 ![&#45; mapy kodu Sprawdź definicję metody](../modeling/media/codemapstoryboardpaint10.png "CodeMapStoryboardPaint10")  
  
## <a name="find-the-problem-by-examining-the-map"></a>Znajdowanie problemu poprzez analizowanie mapy  
 Wydaje się, że wszystkie metody które modyfikują `history` i `paintObjects` wywołania `Repaint`. Jeszcze `undo` nie wywołanie metody `Repaint`, mimo że `undo` modyfikuje tych samych polach. Dlatego uważasz, że może rozwiązać ten problem, wywołując `Repaint` z `undo`.  
  
 ![&#45; mapy kodu Znajdź brakujące wywołanie metody](../modeling/media/codemapstoryboardpaint11.png "CodeMapStoryboardPaint11")  
  
 Nie mając mapy, z której wynika, że brak tego wywołania, znalezienie problemu mogłoby być trudniejszy, zwłaszcza przy bardziej skomplikowanym kodzie.  
  
## <a name="share-your-discovery-and-next-steps"></a>Przekazanie ustaleń innym osobom i następne kroki  
 Zanim Ty lub ktokolwiek inny rozwiąże ten problem, można robić na mapie notatki dotyczące problemu i sposobach jego rozwiązania.  
  
 ![&#45; mapy kodu Elementy komentarz i flaga monitującą](../modeling/media/codemapstoryboardpaint12.png "CodeMapStoryboardPaint12")  
  
 Na przykład możesz dodać komentarze do mapy i flagować elementy przy użyciu kolorów.  
  
 ![&#45; mapy kodu Komentarz i elementów oflagowanych](../modeling/media/codemapstoryboardpaint12a.png "CodeMapStoryboardPaint12A")  
  
 Jeśli masz zainstalowany program Microsoft Outlook, możesz wysłać mapę do innych osób pocztą e-mail. Mapę możesz również wyeksportować jako obraz lub w innym formacie.  
  
 ![&#45; mapy kodu Udostępnianie, eksportowanie, poczty](../modeling/media/codemapstoryboardpaint13.png "CodeMapStoryboardPaint13")  
  
## <a name="fix-the-problem-and-show-what-you-did"></a>Rozwiązanie problemu i pokazanie innym, co zostało zrobione  
 Aby rozwiązać ten problem, dodaj wywołanie do `Repaint` do `undo`.  
  
 ![&#45; mapy kodu Dodaj brakujące wywołanie metody](../modeling/media/codemapstoryboardpaint14.png "CodeMapStoryboardPaint14")  
  
 Aby potwierdzić rozwiązanie problemu, ponownie uruchom sesję debugowania i spróbuj odtworzyć błąd. Teraz wybranie **Cofnij Moje ostatnie pociągnięcie** działa zgodnie z oczekiwaniami i potwierdza wprowadzone prawidłowe poprawki.  
  
 ![&#45; mapy kodu Potwierdź kod poprawka](../modeling/media/codemapstoryboardpaint15.png "CodeMapStoryboardPaint15")  
  
 Możesz zaktualizować mapę, aby pokazać wprowadzoną poprawkę.  
  
 ![&#45; mapy kodu Mapa aktualizacji z brakującymi wywołania metody](../modeling/media/codemapstoryboardpaint16.png "CodeMapStoryboardPaint16")  
  
 Mapy zawiera teraz łącze między **Cofnij** i **odświeżenia**.  
  
 ![&#45; mapy kodu Mapa zaktualizowane z wywołania metody](../modeling/media/codemapstoryboardpaint17.png "CodeMapStoryboardPaint17")  
  
> [!NOTE]
>  Po zaktualizowaniu mapy, może pojawić się komunikat o zaktualizowaniu indeksu kodu użytego do utworzenia mapy. Oznacza to, że ktoś zmienił kod, co powoduje, że mapa nie pasuje do bieżącego kodu. Nie zatrzymuje to aktualizowania mapy, ale może być konieczne ponowne utworzenie mapy w celu potwierdzenia, że pasuje do kodu.  
  
 Po zakończeniu badania. Problem został znaleziony i rozwiązany pomyślnie dzięki mapowaniu kodu. Istnieje również mapa pomagająca w nawigowaniu po kodzie, zapamiętaniu nowych informacji, a także pokazująca kroki, które zostały podjęte w celu rozwiązania problemu.  
  
## <a name="see-also"></a>Zobacz też  
 [Metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)   
 [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)