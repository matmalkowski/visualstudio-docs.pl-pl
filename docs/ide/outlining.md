---
title: Zwijać i rozwijać regionów kodu w programie Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f6c8102eb2bc94785d36256fc0c5653146cc5c76
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="outlining"></a>Tworzenie konspektu

Można ukryć kodu z widoku, zwijając region kodu, aby był on wyświetlany w obszarze znak plus (**+**). Możesz rozwinąć zwinięty region, klikając znak plus. Jeśli jesteś użytkownikiem klawiatury, możesz wybrać **Ctrl**+**M**+**M** można zwijać i rozwijać. Region zwijania można zwinąć również przez dwukrotne kliknięcie każdego wiersza w regionie na marginesie zwijania pojawia się po lewej kodu. Po umieszczeniu na zwinięty region, mogą wyświetlać zawartość obszaru zwinięte jako etykietka narzędzia.

Regiony zwijania marginesie są wyróżnione po umieszczeniu na marginesie przy użyciu myszy. Domyślnie wyróżnianie kolor może wydawać się raczej Blade w niektórych konfiguracjach kolorów. Możesz je zmienić w **narzędzia** > **opcje** > **środowiska** > **czcionki i kolory**  >  **Zwijanej Region**.

Podczas pracy w kodzie obramowane można rozwinąć sekcje, które chcesz pracować nad, zwijając, gdy są wykonywane, a następnie przenieść pozostałe sekcje zasad. Jeśli nie chcesz, aby mieć obramowanie wyświetlane, można użyć **zatrzymać zwijania** polecenie, aby usunąć informacje konspektu bez zakłócania kodu źródłowego.

**Cofnij** i **wykonaj ponownie** polecenia w **Edytuj** menu wpływać na te akcje. **Kopiowania**, **Wytnij**, **Wklej**, i Zachowaj operacji przeciągania i upuszczania zwijania informacji, ale nie zwijanej regionu. Na przykład przy kopiowaniu region, który jest zwinięte, **Wklej** operacji będzie Wklej skopiowany tekst jako rozwinięte region.

> [!CAUTION]
> Jeśli zmienisz obramowane region zwijania mogą zostać utracone. Na przykład usunięcia lub znajdowanie i zamienianie operacji może spowodować usunięcie koniec regionu.

Następujące polecenia można znaleźć w **Edytuj** > **Tworzenie konspektu** podmenu.

|||
|-|-|
|Ukryj zaznaczenia|(**Ctrl**+**M**, **Ctrl**+**H**)-zwija wybranego bloku kodu, który zwykle nie jest dostępne dla zwijania, na przykład `if` bloku. Aby usunąć regionu niestandardowego, użyj **zatrzymać ukrywanie bieżącego** (lub **Ctrl**+**M**, **Ctrl** + **U**). Nie jest dostępna w języku Visual Basic.|
|Przełącz Tworzenie konspektu rozszerzenia|-Odwraca bieżący stan ukryte lub rozszerzonych najbardziej wewnętrzną funkcją zwijania sekcji, gdy kursor znajduje się w zagnieżdżonych zwiniętą sekcję.|
|Przełącz wszystkie Tworzenie konspektu|(**Ctrl**+**M**, **Ctrl**+**L**) — zestawy wszystkie regiony do tej samej zwinięte lub rozszerzyć stanu. Jeśli niektóre regiony są rozwinięte, a niektóre zwinięte, następnie zwinięte regiony są rozwinięte.|
|Zatrzymaj, obramowanie|(**Ctrl**+**M**, **Ctrl**+**P**)-usuwa wszystkie informacje zwijania w całym dokumencie.|
|Przestań ukrywać bieżący|(**Ctrl**+**M**, **Ctrl**+**U**)-usuwa zwijania informacje dotyczące aktualnie wybranego region zdefiniowany przez użytkownika. Nie jest dostępna w języku Visual Basic.|
|Zwiń do definicji|(**Ctrl**+**M**, **Ctrl**+**O**)-Zwija wszystkie typy elementów członkowskich.|
|Zwiń blok:\<granic logiczna >|(Visual C++) Zwija regionu w funkcji znajduje się punkt wstawiania. Na przykład jeśli punkt wstawiania znajduje się wewnątrz pętli, pętli jest ukryty.|
|Zwiń wszystkie w: \<struktury logicznej >|(Visual C++) Zwija wszystkie struktury wewnątrz funkcji.|

Aby zdefiniować regionów tekst, który chcesz rozwiń lub Zwiń umożliwia także programu Visual Studio SDK. Zobacz [wskazówki: Tworzenie konspektu](../extensibility/walkthrough-outlining.md).

## <a name="see-also"></a>Zobacz także

- [Funkcje Edytor kodu](../ide/writing-code-in-the-code-and-text-editor.md)
