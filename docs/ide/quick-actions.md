---
title: Szybkie akcje, żarówki i śrubokręty
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d413d5b440c39c3603e1e909fb0c4645719f188b
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
ms.locfileid: "34064853"
---
# <a name="quick-actions"></a>Szybkie akcje

Szybkie akcje pozwalają łatwo zrefaktoryzuj, generowanie lub modyfikację kodu za pomocą jednej akcji. Szybkie akcje są dostępne w języku C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp)i plików kodu programu Visual Basic. Niektóre akcje są specyficzne dla języka, a inne dotyczą wszystkich wersji językowych.

Szybkie akcje może służyć do:

- Zastosuj poprawkę kodu [analizator kodu](../code-quality/roslyn-analyzers-overview.md) naruszenia reguły
- [Pomiń](../code-quality/use-roslyn-analyzers.md) naruszeniem reguł analizatora kodu
- Zastosuj refaktoryzacji (na przykład [wbudowanej zmiennej tymczasowej](../ide/reference/inline-temporary-variable.md))
- Generowanie kodu (na przykład [wprowadzić zmienną lokalną](../ide/reference/introduce-local-variable.md))

Szybkie akcje może zostać zastosowana za pomocą żarówkę ![ikoną żarówki](media/light-bulb-icon.png) lub śrubokręt ![ikona śrubokręt](media/screwdriver-icon.png) ikony lub naciskając klawisz **Ctrl** + **.** gdy kursor jest w wierszu kodu, w którym akcja jest dostępna. Zostanie wyświetlony błąd żarówki ![ikoną żarówki błąd](media/error-light-bulb-icon.png) Jeśli istnieje czerwona falista, co wskazuje na błąd i Visual Studio ma Poprawka dostępna dla tego błędu.

Dla żadnego języka stron trzecich mogą zapewnić diagnostyki niestandardowej i sugestie, na przykład jako część zestawu SDK i programu Visual Studio żarówki podświetlony, na podstawie tych reguł.

## <a name="icons"></a>Ikony

Ikona wyświetlana podczas szybkiego akcja jest dostępna oznacza wskazanie typu poprawkę lub refaktoryzacji, który jest dostępny. *Śrubokręt* ![ikona śrubokręt](media/screwdriver-icon.png) ikona tylko wskazuje brak dostępnych akcji do zmiany kodu, że nie należy zawsze używać ich. *Żółta żarówka* ![ikoną żarówki](media/light-bulb-icon.png) ikona wskazuje brak dostępnych akcji które *powinien* zrobić, aby poprawić kod. *Błąd żarówki* ![ikoną żarówki błąd](media/error-light-bulb-icon.png) ikona wskazuje brak dostępnych akcji, która rozwiązuje wystąpił błąd w kodzie.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>Aby wyświetlić żarówkę lub śrubokręt

- Jeśli dostępna jest poprawka żarówki samorzutnie są wyświetlane, gdy wskaźnik myszy w lokalizacji wystąpił błąd.

   ![Żarówki z ustawiając kursor myszy](../ide/media/vs2015_lightbulb_hover.png)

- Żarówki i śrubokręty są wyświetlane na lewym marginesie edytora po Przesuń karetkę do wiersza kodu, dla którego szybkie akcja jest dostępna.

- Naciśnij klawisz **Ctrl**+**.** dowolne miejsce na linię, aby wyświetlić listę dostępnych szybkie akcje i refaktoryzacje.

## <a name="to-see-potential-fixes"></a>Aby wyświetlić potencjalne rozwiązania

Wybierz albo strzałkę w dół obok żarówkę lub **Pokaż potencjalne rozwiązania** łącze, aby wyświetlić listę szybkie akcje, które są dostępne.

![Żarówki rozwinięty](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu w programie Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Typowe szybkie akcje](../ide/common-quick-actions.md)
- [Style kodu i szybkie akcje](../ide/code-styles-and-quick-actions.md)
- [Zapis i refaktoryzacji kodu (C++)](/cpp/ide/writing-and-refactoring-code-cpp)