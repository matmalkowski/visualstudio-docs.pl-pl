---
title: "Trwa znajdowanie odwołań w kodzie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code editor, find all references
- find all references
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 92c12e4d51255849843f938c032ca17b611eeeab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="finding-references-in-your-code"></a>Trwa znajdowanie odwołań w kodzie  
Można użyć **Znajdź wszystkie odwołania** polecenia można znaleźć, której elementy określonego kodu są przywoływane w całym baza kodu. **Znajdź wszystkie odwołania** polecenie jest dostępne w menu kontekstowym (kliknij prawym przyciskiem myszy) ma zostać odnaleziona odwołania do elementu. Lub, jeśli jesteś użytkownikiem klawiatury, naciśnij klawisz **Shift + F12**.  

Wyniki są wyświetlane w oknie narzędzia o nazwie  **"*elementu*" odwołania **, gdzie *elementu* jest nazwa elementu, którego szukasz. Pasek narzędzi w **odwołania** okna umożliwia:  
- Zmień zakres wyszukiwania w polu listy rozwijanej. Można wybrać do przeszukania tylko zmienione dokumenty do całego rozwiązania.  
- Kopiuj wybrany element do którego istnieje odwołanie, wybierając **kopiowania** przycisku.  
- Wybierz przycisk, aby przejść do następnej lub poprzedniej lokalizacji na liście lub naciśnij klawisz **F8** i **Shift + F8** kluczy, aby to zrobić.  
- Usuń wszystkie filtry wyników zwróconych przez wybranie **wyczyść wszystkie filtry** przycisku.  
- Zmień sposób zwracane elementy są pogrupowane według wybranie ustawienia w **Grupuj według:** pole listy rozwijanej.  
- Zachowaj bieżące okno wyników wyszukiwania, wybierając **przechowywać wyniki** przycisku. Jeśli ten przycisk bieżące wyniki wyszukiwania pozostać w tym oknie, a nowe wyniki wyszukiwania są wyświetlane w nowym oknie narzędzia.  
- Wyszukiwanie ciągów w wynikach wyszukiwania, wprowadzając tekst w **wyszukiwania Znajdź wszystkie odwołania** pola tekstowego.  

Można również ustawić kursor myszy nad dowolny wynik wyszukiwania, aby zobaczyć podgląd odwołania.  

![Znajdź wszystkie odwołania okna narzędzi](../ide/media/vside_findallreferences.png)  

### <a name="navigate-to-references"></a>Przejdź do odwołania
Można użyć następujących metod można przejść do odwołań w **odwołania** okno:  

- Naciśnij klawisz **F8** aby przejść do następnego odwołanie, lub **Shift + F8** aby przejść do poprzedniej odwołania.  
- Naciśnij klawisz **Enter** klucza na odwołanie, lub kliknij dwukrotnie, aby przejść do niego w kodzie.  
- W menu kontekstowym odwołanie, wybierz **przejdź do poprzedniej lokalizacji** lub **przejdź do następnej lokalizacji** poleceń.  
- Wybierz **Strzałka w górę** i **Strzałka w dół** kluczy (jeśli są one włączone w oknie dialogowym Opcje). Aby włączyć tę funkcję na pasku menu wybierz **narzędzia**, **opcje**, **środowiska**, **zakładek i okien**,  **Karta Podgląd**, a następnie wybierz **Zezwalaj na nowe pliki w karcie podglądu** i **Podgląd zaznaczonych plików w wynikach Znajdź** pola.  

### <a name="change-reference-groupings"></a>Zmiana grupy odwołania  
Domyślnie odwołania są pogrupowane według projektu, następnie przez definicję. Jednak to zamówienie grupowania można zmienić, zmieniając ustawienie w **Grupuj według:** pole listy rozwijanej na pasku narzędzi. Na przykład można zmienić go z ustawieniem domyślnym **następnie projektu definicji** do **definicji, a następnie projektu**, jak również do innych ustawień.  

**Definicja** i **projektu** są używane dwa domyślne grupowania, ale można dodać inne, wybierając **grupowanie** polecenia w menu kontekstowym wybranego elementu. Dodanie więcej grup może być przydatne, jeśli rozwiązanie zawiera wiele plików i ścieżek.  

## <a name="see-also"></a>Zobacz także  
[Nawigowanie po kodzie](../ide/navigating-code.md)  