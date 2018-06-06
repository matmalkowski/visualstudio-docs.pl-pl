---
title: Używanie map kodu do debugowania aplikacji
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, visualizing code
- Visual Studio Ultimate, navigating code visually
- Visual Studio Ultimate, understanding code
- Visual Studio Ultimate, mapping code relationships
- Visual Studio Ultimate, code maps
- mapping code relationships
- code maps
- mapping relationships in code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 006db4f3fd820a25b0c413deabce3da5faa70cec
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750275"
---
# <a name="use-code-maps-to-debug-your-applications"></a>Używanie map kodu do debugowania aplikacji
Mapy kodu mogą pomóc uniknąć poczucia zagubienia w dużych baz kodu, kod nieznane lub starszego kodu. Na przykład debugowanie, może być konieczne przeglądać kod pochodzące z wielu plików i projektów. Używanie map kodu do nawigację fragmentów kodu i zrozumieć ich relacje między nimi. Dzięki temu nie trzeba informacji o tym kodzie w nagłówek lub utworzyć oddzielne diagram. Dzięki pracy zostanie przerwany, kod mapy pomocy odświeżania pamięci dotyczące kodu, nad którymi pracuje.

 ![Mapy kodu &#45; Mapowanie relacji w kodzie](../modeling/media/codemapstoryboardpaint.png)

 **Pokazuje zieloną strzałkę, gdy kursor zostanie wyświetlony w edytorze**

 Szczegółowe poleceń i działań można używać podczas pracy z mapy kodu, patrz [przeglądania i zmieniać code map](../modeling/browse-and-rearrange-code-maps.md).

## <a name="understand-the-problem"></a>Omówienie problemu
 Przypuśćmy, że w programie graficznym, nad którym pracujesz, znajduje się błąd. Aby odtworzyć ten błąd, otwórz rozwiązanie w Visual Studio i naciśnij klawisz **F5** można rozpocząć debugowania.

 Gdy Rysowanie linii i wybierz polecenie **Cofnij Moje ostatnie pociągnięcie**, aż do rysowania dalej nic się nie dzieje.

 ![Mapy kodu &#45; reprodukcja usterki](../modeling/media/codemapstoryboardpaint0.png)

 Dzięki uruchamiania badanie, wyszukując `Undo` metody. Możesz znaleźć `PaintCanvas` klasy.

 ![Mapy kodu &#45; znaleźć kodu](../modeling/media/codemapstoryboardpaint1.png)

## <a name="start-mapping-the-code"></a>Uruchamianie mapowania kodu
 Teraz uruchomić mapowania `undo` — metoda i relacje. W edytorze kodu, możesz dodać `undo` — metoda i pola, które odwołuje się do nowej mapy kodu. Podczas tworzenia nowej mapy może trochę czasu może zająć indeksowanie kodu. Dzięki temu następne operacje działają szybciej.

 ![Mapy kodu &#45; Pokaż pola powiązane i — metoda](../modeling/media/codemapstoryboardpaint3.png)

> [!TIP]
>  Zielone podświetlenie pokazuje ostatnie elementy dodane do mapy. Zieloną strzałkę pokazuje kursor w pozycji w kodzie. Strzałki między elementami reprezentują różne relacje. Aby uzyskać więcej informacji na temat elementów na mapie, należy przesuwanie wskaźnika myszy nad nimi i badanie etykietki.

 ![Mapy kodu &#45; Pokaż etykietki narzędzi](../modeling/media/codemapstoryboardpaint4.png)

## <a name="navigate-and-examine-code-from-the-map"></a>Nawigowanie i sprawdzanie kodu z mapy
 Aby zobaczyć definicji kodu dla każdego pola, kliknij dwukrotnie pole na mapie lub wybierz pole i naciśnij klawisz **F12**. Zielona strzałka przesuwa się między elementami na mapie. Kursor w edytorze kodu również przesuwa się automatycznie.

 ![Mapy kodu &#45; Sprawdź definicję pola](../modeling/media/codemapstoryboardpaint5.png)

 ![Mapy kodu &#45; Sprawdź definicję pola](../modeling/media/codemapstoryboardpaint5a.png)

> [!TIP]
>  Zieloną strzałkę na mapie możesz również przesunąć, przesuwając kursor w edytorze kodu.

## <a name="understand-relationships-between-pieces-of-code"></a>Omówienie relacji między fragmentami kodu
 Teraz chcesz wiedzieć, który inny kod współdziała z `history` i `paintObjects` pól. Możesz dodać do mapy wszystkie metody odwołujące się do tych pól. Można to zrobić z mapy lub edytora kodu.

 ![Mapy kodu &#45; Znajdź wszystkie odwołania](../modeling/media/codemapstoryboardpaint6.png)

 ![Otwórz mapy kodu w edytorze kodu](../modeling/media/codemapstoryboardpaint6a.png)

> [!NOTE]
>  Po dodaniu elementów z projektu, który jest współużytkowany przez wiele aplikacji, takich jak Windows Phone lub Sklepu Windows, a następnie te elementy są umieszczane w projekcie aplikacji aktualnie aktywny na mapie. Tak Jeśli Zmienianie kontekstu do innego projektu aplikacji, a następnie zmienia także kontekstu na mapie dla dowolnej nowo dodanych elementów z projektu udostępnionego. Operacje wykonywane za pomocą elementu na mapie dotyczą tylko tych elementów, które współużytkują ten sam kontekst.

 Zmień układ, aby przeorganizować przepływ relacji i poprawić czytelność mapy. Elementy na mapie możesz również przesuwać, przeciągając je.

 ![Mapy kodu &#45; zmiany układu](../modeling/media/codemapstoryboardpaint7a.png)

> [!TIP]
>  Domyślnie **przyrostową układu** jest włączona. Dzięki temu mapa jest reorganizowana w możliwie najmniejszym stopniu przy dodawaniu nowych elementów. Aby zmienić kolejność całego mapy za każdym razem, gdy dodawania nowych elementów, wyłącz **przyrostową układu**.

 ![Mapy kodu &#45; zmiany układu](../modeling/media/codemapstoryboardpaint7.png)

 Zbadajmy te metody. Na mapie, kliknij dwukrotnie **PaintCanvas** metody, lub wybierz ta metoda i naciśnij klawisz **F12**. Dowiedz się, że ta metoda tworzy `history` i `paintObjects` jako pusty listy.

 ![Mapy kodu &#45; Sprawdź definicję — metoda](../modeling/media/codemapstoryboardpaint8.png)

 Teraz Powtórz te same kroki, aby sprawdzić `clear` definicję metody. Dowiesz się, że `clear` wykonuje pewne zadania związane z `paintObjects` i `history`. Następnie wywołuje `Repaint` metody.

 ![Mapy kodu &#45; Sprawdź definicję — metoda](../modeling/media/codemapstoryboardpaint9.png)

 Teraz zbadać `addPaintObject` definicję metody. Wykonuje także niektóre zadania związane z `history` i `paintObjects`. Wywołuje również `Repaint`.

 ![Mapy kodu &#45; Sprawdź definicję — metoda](../modeling/media/codemapstoryboardpaint10.png)

## <a name="find-the-problem-by-examining-the-map"></a>Znajdowanie problemu poprzez analizowanie mapy
 Wydaje się, że wszystkie metody które modyfikują `history` i `paintObjects` wywołania `Repaint`. Jeszcze `undo` nie wywołanie metody `Repaint`, mimo że `undo` modyfikuje tych samych polach. Dlatego uważasz, że może rozwiązać ten problem, wywołując `Repaint` z `undo`.

 ![Mapy kodu &#45; Znajdź brakujące wywołanie metody](../modeling/media/codemapstoryboardpaint11.png)

 Nie mając mapy, z której wynika, że brak tego wywołania, znalezienie problemu mogłoby być trudniejszy, zwłaszcza przy bardziej skomplikowanym kodzie.

## <a name="share-your-discovery-and-next-steps"></a>Przekazanie ustaleń innym osobom i następne kroki
 Zanim Ty lub ktokolwiek inny rozwiąże ten problem, można robić na mapie notatki dotyczące problemu i sposobach jego rozwiązania.

 ![Mapy kodu &#45; elementy komentarz i flaga monitującą](../modeling/media/codemapstoryboardpaint12.png)

 Na przykład możesz dodać komentarze do mapy i flagować elementy przy użyciu kolorów.

 ![Mapy kodu &#45; komentarzem i oflagowane elementy](../modeling/media/codemapstoryboardpaint12a.png)

 Jeśli masz zainstalowany program Microsoft Outlook, możesz wysłać mapę do innych osób pocztą e-mail. Mapę możesz również wyeksportować jako obraz lub w innym formacie.

 ![Mapy kodu &#45; udziału eksportu, poczty](../modeling/media/codemapstoryboardpaint13.png)

## <a name="fix-the-problem-and-show-what-you-did"></a>Rozwiązanie problemu i pokazanie innym, co zostało zrobione
 Aby rozwiązać ten problem, dodaj wywołanie do `Repaint` do `undo`.

 ![Mapy kodu &#45; Dodaj brakujące wywołanie — metoda](../modeling/media/codemapstoryboardpaint14.png)

 Aby potwierdzić rozwiązanie problemu, ponownie uruchom sesję debugowania i spróbuj odtworzyć błąd. Teraz wybranie **Cofnij Moje ostatnie pociągnięcie** działa zgodnie z oczekiwaniami i potwierdza wprowadzone prawidłowe poprawki.

 ![Mapy kodu &#45; Potwierdź kod poprawka](../modeling/media/codemapstoryboardpaint15.png)

 Możesz zaktualizować mapę, aby pokazać wprowadzoną poprawkę.

 ![Mapy kodu &#45; mapy aktualizacji z brakującymi wywołanie metody](../modeling/media/codemapstoryboardpaint16.png)

 Mapy zawiera teraz łącze między **Cofnij** i **odświeżenia**.

 ![Mapy kodu &#45; Mapa zaktualizowane z wywołania metody](../modeling/media/codemapstoryboardpaint17.png)

> [!NOTE]
>  Po zaktualizowaniu mapy, może pojawić się komunikat o zaktualizowaniu indeksu kodu użytego do utworzenia mapy. Oznacza to, że ktoś zmienił kod, co powoduje, że mapa nie pasuje do bieżącego kodu. Nie zatrzymuje to aktualizowania mapy, ale może być konieczne ponowne utworzenie mapy w celu potwierdzenia, że pasuje do kodu.

 Po zakończeniu badania. Problem został znaleziony i rozwiązany pomyślnie dzięki mapowaniu kodu. Istnieje również mapa pomagająca w nawigowaniu po kodzie, zapamiętaniu nowych informacji, a także pokazująca kroki, które zostały podjęte w celu rozwiązania problemu.

## <a name="see-also"></a>Zobacz też

- [Metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)
