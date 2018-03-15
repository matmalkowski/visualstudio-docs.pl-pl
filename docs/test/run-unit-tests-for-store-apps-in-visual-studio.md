---
title: "Uruchom, organizować i debugowania testów jednostkowych programu Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d99b0ab4ce0b10a4a03f80c95a004df0a9facef5
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="run-organize-and-debug-unit-tests"></a>Uruchom, organizować i debugowania testów jednostkowych

W tym temacie opisano sposób uruchamiania testów jednostkowych za pomocą Eksploratora testów w programie Microsoft Visual Studio.

## <a name="unit-test-frameworks-and-test-projects"></a>Platform testów jednostkowych i projekty testowe

Visual Studio zawiera struktury testowania jednostki firmy Microsoft dla kodu zarządzanego i natywnego kodu C++. Eksplorator testów można uruchomić testy z wielu projektów testów w rozwiązaniu i klasy testowe, które należą do projektów kodu produkcyjnego. Projekty testowe może być dowolną kombinacją języka Visual C++ lub platform testów jednostkowych programu Visual C# i Visual Basic. Jeśli kod w ramach testu są zapisywane dla programu .NET Framework, w dowolnym języku .NET Framework, niezależnie od języka kodu docelowego można napisać projektu testowego. Natywny projektów kodu C/C++, należy sprawdzić za pomocą frameworka testów jednostkowych C++.

## <a name="run-tests-in-test-explorer"></a>Uruchom testy w narzędzia Eksplorator testów

Podczas kompilowania projektu testowego, testy są wyświetlane w Eksploratorze testów. Eksploratora testów nie jest widoczny, jeśli **testu** w menu programu Visual Studio, wybierz **systemu Windows**, a następnie wybierz pozycję **Eksploratora testów**.

![Eksplorator testów jednostkowych](../test/media/ute_failedpassednotrunsummary.png)

Jak uruchamiać, zapisu i ponownie uruchomić testy narzędzia Eksplorator testów wyświetla wyniki w domyślnych grup z **testy nie powiodło się**, **przekazany testy**, **pominięte testy** i  **Nie uruchamiać testów**. Możesz zmienić sposób Eksploratora testów grupy testów.

Można wykonać większość zadań znajdowanie, organizowanie i uruchamiania testów na pasku narzędzi Eksplorator testów.

![Uruchom testy na pasku narzędzi Eksplorator testów](../test/media/ute_toolbar.png)

### <a name="run-tests"></a>Uruchom testy

Można uruchomić wszystkie testy w rozwiązaniu, wszystkie testy z grupy lub zestawu testów, które można wybrać. Wykonaj jedną z następujących czynności:

- Aby uruchomić wszystkie testy w rozwiązaniu, wybierz pozycję **Uruchom wszystkie**.

- Aby uruchomić wszystkie testy w domyślnej grupy, wybierz pozycję **Uruchom...**  , a następnie wybierz grupę, w menu.

- Wybierz poszczególne testy, które chcesz uruchomić, otwórz menu skrótów dla wybranego testu, a następnie wybierz pozycję **uruchomić wybrane testy**.

Na pasku przebiegu/Niepowodzenie w górnej części okna Eksploratora testów jest animowany jako Uruchom testy. Po zakończeniu uruchomienia testu na pasku przebiegu/niepowodzenie włącza zielony wszystkie testy przekazany lub czerwony, jeśli żadnego testu nie powiodła się.

## <a name="view-test-results"></a>Wyświetlanie wyników testu

Jak uruchamiać, zapisu i ponownie uruchomić testy narzędzia Eksplorator testów wyświetla wyniki w grupach **testy nie powiodło się**, **przekazany testy**, **pominięte testy** i **nie działać Testy**. W okienku szczegółów w dolnej części Wyświetla Eksploratora testów Uruchom Podsumowanie testu.

### <a name="view-test-details"></a>Wyświetlanie szczegółów testu

Aby wyświetlić szczegółowe informacje o poszczególnych testów, wybierz testu.

W okienku szczegółów testu zawiera następujące informacje:

- Nazwa pliku źródłowego i numer wiersza metody testowej.

- Stan testu.

- Czas, który miał metody testowej do uruchomienia.

Jeśli test ma wynik negatywny, są wyświetlane również w okienku szczegółów:

- Komunikat zwrócony przez platformy testów jednostkowych dla testu.

- Ślad stosu w czasie testu nie powiodło się.

### <a name="view-the-source-code-of-a-test-method"></a>Wyświetlanie kodu źródłowego metody testowej

Aby wyświetlić kodu źródłowego metody testowej w edytorze programu Visual Studio, wybierz testu, a następnie wybierz **Otwórz Test** na pasku menu skrótów lub naciśnij **F12**.

## <a name="organize-the-test-list"></a>Organizowanie listy testów

### <a name="group-tests"></a>Grupa testów

Domyślnie narzędzia Eksplorator testów są wyświetlane jako węzły podrzędne testów **testy nie powiodło się**, **przekazany testy**, **pominięte testy** i **nie Uruchom testy**.

|||
|-|-|
|![Przycisk Eksploratora testów](../test/media/ute_groupby_btn.png "UTE_GroupBy_btn")|Do grupowania testów przez czas potrzebny na wykonanie ich, otwórz **Group By** listę i wybierz **czas trwania**. Wybierz **wynik testu** Aby przełączyć się do oryginalnej grupowania.|

### <a name="search-and-filter-the-test-list"></a>Wyszukiwanie i filtrowanie listy testów

Jeśli masz dużą liczbę testów, można wpisać w polu wyszukiwania Eksploratora testów, aby filtrować listę według określonego ciągu. Filtr można ograniczyć do określonych typów ciągów, wybierając z listy filtrów przed wprowadź ciąg wyszukiwania.

![Kategorie filtru wyszukiwania](../test/media/ute_searchfilter.png)

## <a name="debug-unit-tests"></a>Debuguj testy jednostkowe

Aby rozpocząć sesję debugowania dla testów, można użyć narzędzia Eksplorator testów. Krokowe wykonywanie kodu z debuger programu Visual Studio bezproblemowe przejście i z powrotem między testów jednostkowych i projektu w ramach testu. Można rozpocząć debugowania:

1. W edytorze programu Visual Studio należy ustawić punkt przerwania w metody testowe, które chcesz debugować.

    > [!NOTE]
    > Ponieważ metody testowe można uruchomić w dowolnej kolejności, ustaw punkty przerwania w wszystkie metody testowe, które chcesz debugować.

1. W Eksploratorze testów, wybierz metody testowe, a następnie wybierz **Debuguj zaznaczone testy** menu skrótów.

Aby uzyskać więcej informacji na temat debugera, zobacz [debugowania w programie Visual Studio](../debugger/debugging-in-visual-studio.md).
