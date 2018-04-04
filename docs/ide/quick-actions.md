---
title: Szybkie akcje | Dokumentacja firmy Microsoft
ms.date: 03/28/2018
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 30a3243b924032cd2501d42bb8aad37777e2f814
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2018
---
# <a name="quick-actions"></a>Szybkie akcje

Szybkie akcje pozwalają łatwo zrefaktoryzuj, generowanie lub modyfikację kodu za pomocą jednej akcji. Szybkie akcje są dostępne w języku C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp)i plików kodu programu Visual Basic. Niektóre akcje są specyficzne dla języka, a inne dotyczą wszystkich wersji językowych.

Szybkie akcje może służyć do:

- Zastosuj poprawkę kodu [analizator kodu](../code-quality/roslyn-analyzers-overview.md) naruszenia reguły
- [Pomiń](../code-quality/use-roslyn-analyzers.md) naruszeniem reguł analizatora kodu
- Zastosuj refaktoryzacji (na przykład [wbudowanej zmiennej tymczasowej](../ide/reference/inline-temporary-variable.md))
- Generowanie kodu (na przykład [wprowadzić zmienną lokalną](../ide/reference/introduce-local-variable.md))

Szybkie akcje można zastosować, korzystając z ikoną żarówki ![małych ikon żarówki](media/vs2015_lightbulbsmall.png), lub naciskając klawisz **Ctrl**+**.** gdy kursor jest w wierszu kodu, w którym akcja jest dostępna. Pojawi się, że żarówki, jeśli istnieje czerwona falista i Visual Studio ma sugestię jak rozwiązać problem. Na przykład jeśli masz wskazaniem czerwona falista błąd żarówka będą wyświetlane, gdy poprawki są dostępne dla tego błędu.

Dla żadnego języka stron trzecich mogą zapewnić diagnostyki niestandardowej i sugestie, na przykład jako część zestawu SDK i programu Visual Studio żarówki podświetlony, na podstawie tych reguł.

## <a name="to-see-a-light-bulb"></a>Aby wyświetlić żarówka

1. W wielu przypadkach żarówki samorzutnie są wyświetlane po wskaźnika myszy w punkcie błąd lub na lewym marginesie edytora przenoszenia karetkę do wiersza, który zawiera błąd. Gdy pojawi się czerwona falista, możesz go, aby wyświetlić żarówkę Aktywuj. Może również spowodować żarówka wyświetlany, gdy używasz myszy lub klawiatury można przejść do dowolnej lokalizacji w wierszu gdzie występuje problem.

1. Naciśnij klawisz **Ctrl**+**.** dowolne miejsce na linię, aby wywołać żarówkę i przejść bezpośrednio do listy potencjalnych poprawek.

   ![Żarówki z ustawiając kursor myszy](../ide/media/vs2015_lightbulb_hover.png)

## <a name="to-see-potential-fixes"></a>Aby wyświetlić potencjalne rozwiązania

Kliknij strzałkę w dół lub potencjalne Pokaż poprawki łącze, aby wyświetlić listę szybkie akcje wykonywane przez żarówkę dla Ciebie.

![Żarówki rozwinięty](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu w programie Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Typowe szybkie akcje](../ide/common-quick-actions.md)
- [Style kodu i szybkie akcje](../ide/code-styles-and-quick-actions.md)
- [Pisanie i refaktoryzacja kodu (C++)](/cpp/ide/writing-and-refactoring-code-cpp)