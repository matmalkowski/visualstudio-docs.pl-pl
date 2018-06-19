---
title: Trwa znajdowanie odwołań w kodzie
ms.date: 09/26/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code editor, find all references
- find all references
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8ac09eace078ef60f36bd57e9a2c4a1e5f1c510c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942324"
---
# <a name="find-references-in-your-code"></a>Znajdowanie odwołań w kodzie

Można użyć **Znajdź wszystkie odwołania** polecenia można znaleźć, której elementy określonego kodu są przywoływane w całym baza kodu. **Znajdź wszystkie odwołania** polecenie jest dostępne w menu kontekstowym (kliknij prawym przyciskiem myszy) ma zostać odnaleziona odwołania do elementu. Lub, jeśli jesteś użytkownikiem klawiatury, naciśnij klawisz **Shift + F12**.

Wyniki są wyświetlane w oknie narzędzia o nazwie  **<element> odwołania**, gdzie *elementu* jest nazwa elementu, którego szukasz. Pasek narzędzi w **odwołania** okna umożliwia:
- Zmień zakres wyszukiwania w polu listy rozwijanej. Można wybrać do przeszukania tylko zmienione dokumenty do całego rozwiązania.
- Kopiuj wybrany element do którego istnieje odwołanie, wybierając **kopiowania** przycisku.
- Wybierz przycisk, aby przejść do następnej lub poprzedniej lokalizacji na liście lub naciśnij klawisz **F8** i **Shift + F8** kluczy, aby to zrobić.
- Usuń wszystkie filtry wyników zwróconych przez wybranie **wyczyść wszystkie filtry** przycisku.
- Zmień sposób zwracane elementy są pogrupowane według wybranie ustawienia w **Grupuj według:** pole listy rozwijanej.
- Zachowaj bieżące okno wyników wyszukiwania, wybierając **przechowywać wyniki** przycisku. Jeśli ten przycisk bieżące wyniki wyszukiwania pozostać w tym oknie, a nowe wyniki wyszukiwania są wyświetlane w nowym oknie narzędzia.
- Wyszukiwanie ciągów w wynikach wyszukiwania, wprowadzając tekst w **wyszukiwania Znajdź wszystkie odwołania** pola tekstowego.

Można również ustawić kursor myszy nad dowolny wynik wyszukiwania, aby zobaczyć podgląd odwołania.

![Znajdź wszystkie odwołania okna narzędzi](../ide/media/vside_findallreferences.png)

## <a name="navigate-to-references"></a>Przejdź do odwołania
Można użyć następujących metod można przejść do odwołań w **odwołania** okno:

- Naciśnij klawisz **F8** aby przejść do następnego odwołanie, lub **Shift + F8** aby przejść do poprzedniej odwołania.
- Naciśnij klawisz **Enter** klucza na odwołanie, lub kliknij dwukrotnie, aby przejść do niego w kodzie.
- W menu kontekstowym odwołanie, wybierz **przejdź do poprzedniej lokalizacji** lub **przejdź do następnej lokalizacji** poleceń.
- Wybierz **Strzałka w górę** i **Strzałka w dół** kluczy (jeśli są one włączone w **opcje** okno dialogowe). Aby włączyć tę funkcję na pasku menu wybierz **narzędzia** > **opcje** > **środowiska**  >   **Karty i okna** > **kartę Podgląd**, a następnie wybierz **Zezwalaj na nowe pliki w karcie podglądu** i **Podgląd zaznaczonych plików w Wyniki Znajdź** pola.

## <a name="change-reference-groupings"></a>Zmiana grupy odwołania
Domyślnie odwołania są pogrupowane według projektu, następnie przez definicję. Jednak to zamówienie grupowania można zmienić, zmieniając ustawienie w **Grupuj według:** pole listy rozwijanej na pasku narzędzi. Na przykład można zmienić go z ustawieniem domyślnym **następnie projektu definicji** do **definicji, a następnie projektu**, jak również do innych ustawień.

**Definicja** i **projektu** są używane dwa domyślne grupowania, ale można dodać inne, wybierając **grupowanie** polecenia w menu kontekstowym wybranego elementu. Dodanie więcej grup może być przydatne, jeśli rozwiązanie zawiera wiele plików i ścieżek.

## <a name="see-also"></a>Zobacz także

- [Nawigowanie po kodzie](../ide/navigating-code.md)