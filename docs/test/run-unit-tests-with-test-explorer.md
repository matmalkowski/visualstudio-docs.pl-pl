---
title: "Uruchom testy jednostkowe za pomocą narzędzia Eksplorator testów | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: article
f1_keywords:
- vs.unittesting.testexplorer.overview
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: ff1f101ba9c4335ca694d8bc13f6f17701d0974c
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="run-unit-tests-with-test-explorer"></a>Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów

Użyj **Eksploratora testów** do uruchamiania testów jednostkowych programu Visual Studio lub projektów testów jednostkowych innych firm. Można również użyć **Eksploratora testów** do grupowania testów w kategorie, filtrowanie listy testów i tworzenia, zapisywania i uruchom listy odtwarzania testów. Można debugować testy i Analizuj pokrycie testu wydajności i kod.

Visual Studio zawiera struktury testowania jednostki firmy Microsoft dla kodu zarządzane i natywne. Jednak **Eksploratora testów** można również uruchomić wszystkie jednostki struktury testowej, który zaimplementowała karty Eksploratora testów. Aby uzyskać więcej informacji na temat Instalowanie platform testów jednostkowych innych firm, zobacz [instalowanie platform testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md)

**Testowanie Explorer** można uruchomić testy z wielu projektów testów w rozwiązaniu i klasy testowe, które należą do projektów kodu produkcyjnego. Projekty testowe można używać platform testów jednostkowych inny. Jeśli kod w ramach testu są zapisywane dla programu .NET Framework, w dowolnym języku również przeznaczonego dla programu .NET Framework, niezależnie od języka kodu docelowego można napisać projektu testowego. Natywny projektów kodu C/C++, należy sprawdzić za pomocą frameworka testów jednostkowych C++. Aby uzyskać więcej informacji, zobacz [pisania testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="run-tests-in-test-explorer"></a>Uruchom testy w narzędzia Eksplorator testów

Podczas kompilowania projektu testowego, testy są wyświetlane w Eksploratorze testów. Eksploratora testów nie jest widoczny, jeśli **testu** w menu programu Visual Studio, wybierz **systemu Windows**, a następnie wybierz pozycję **Eksploratora testów**.

![Eksplorator testów jednostkowych](../test/media/ute_failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

Jak uruchamiać, zapisu i ponownie uruchomić testy narzędzia Eksplorator testów wyświetla wyniki w domyślnych grup z **testy nie powiodło się**, **przekazany testy**, **pominięte testy** i  **Nie uruchamiać testów**. Możesz zmienić sposób Eksploratora testów grupy testów.

Można wykonać większość zadań znajdowanie, organizowanie i uruchamiania testów na pasku narzędzi Eksplorator testów.

![Uruchamianie testów za pomocą narzędzi Eksploratora testów](../test/media/ute_toolbar.png "UTE_ToolBar")

### <a name="run-tests"></a>Uruchom testy

Można uruchomić wszystkie testy w rozwiązaniu, wszystkie testy z grupy lub zestawu testów, które można wybrać. Wykonaj jedną z następujących czynności:

- Aby uruchomić wszystkie testy w rozwiązaniu, wybierz pozycję **Uruchom wszystkie**.

- Aby uruchomić wszystkie testy w domyślnej grupy, wybierz pozycję **Uruchom...**  , a następnie wybierz grupę, w menu.

- Wybierz poszczególne testy, które chcesz uruchomić, otwórz menu kontekstowe dla wybranego testu, a następnie wybierz pozycję **uruchomić wybrane testy**.

- Jeśli poszczególne testy nie ma żadnych zależności, które uniemożliwiają uruchomione w dowolnej kolejności, włącz wykonywanie równoległe testu z ![UTE&#95;parallelicon&#45;małych](../test/media/ute_parallelicon-small.png "małych UTE_parallelicon") przycisk przełączania na pasku narzędzi. To znacznie ograniczyć czas potrzebny na uruchamianie wszystkich testów.

Na pasku przebiegu/Niepowodzenie w górnej części okna Eksploratora testów jest animowany jako Uruchom testy. Po zakończeniu uruchomienia testu na pasku przebiegu/niepowodzenie włącza zielony wszystkie testy przekazany lub czerwony, jeśli żadnego testu nie powiodła się.

### <a name="run-tests-after-every-build"></a>Uruchom testy po każdej kompilacji

|||
|-|-|
|![Uruchom po kompilacji](../test/media/ute_runafterbuild_btn.png)|Aby uruchomić testy jednostkowe po każdym lokalnej kompilacji, wybierz pozycję **testu** w standardowe menu, a następnie wybierz **Uruchom testy po kompilacji** na pasku narzędzi Eksplorator testów.|

## <a name="view-test-results"></a>Wyświetlanie wyników testu

Jak uruchamiać, zapisu i ponownie uruchomić testy narzędzia Eksplorator testów wyświetla wyniki w grupach **testy nie powiodło się**, **przekazany testy**, **pominięte testy** i **nie działać Testy**. W okienku szczegółów w dolnej części Wyświetla Eksploratora testów Uruchom Podsumowanie testu.

### <a name="view-test-details"></a>Wyświetlanie szczegółów testu

Aby wyświetlić szczegółowe informacje o poszczególnych testów, wybierz testu.

![Szczegóły wykonywania testów](../test/media/ute_testdetails.png "UTE_TestDetails")

W okienku szczegółów testu zawiera następujące informacje:

- Nazwa pliku źródłowego i numer wiersza metody testowej.

- Stan testu.

- Czas, który miał metody testowej do uruchomienia.

Jeśli test ma wynik negatywny, są wyświetlane również w okienku szczegółów:

- Komunikat zwrócony przez platformy testów jednostkowych dla testu.

- Ślad stosu w czasie testu nie powiodło się.

### <a name="view-the-source-code-of-a-test-method"></a>Wyświetlanie kodu źródłowego metody testowej

 Aby wyświetlić kodu źródłowego metody testowej w edytorze programu Visual Studio, wybierz testu, a następnie wybierz **Otwórz Test** w menu kontekstowym (klawiatury: **F12**).

## <a name="group-and-filter-the-test-list"></a>Grupowanie i filtrowanie listy testów

Eksplorator testów umożliwia grupowanie testów do wstępnie zdefiniowanych kategorii. Większość platform testów jednostkowych, które Uruchom Eksploratora testów let definiować własne kategorie i pary wartości/kategorii do grupowania testów. Lista testów można również filtrować według dopasowywanie ciągów dla właściwości testu.

### <a name="group-tests-in-the-test-list"></a>Grupa testów na liście testu

 Aby zmienić sposób, że testy są zorganizowane, wybierz strzałkę w dół **Group By** przycisk ![przycisk Eksploratora testów](../test/media/ute_groupby_btn.png "UTE_GroupBy_btn") i wybierz nowy grupowania kryteria.

 ![Grupuj testy według kategorii w Eksploratorze testów](../test/media/ute_groupbycategory.png "UTE_GroupByCategory")

### <a name="test-explorer-groups"></a>Grupy Eksploratora testów

|Grupa|Opis|
|-----------|-----------------|
|**Czas trwania**|Grupy test przez czas wykonywania: **Fast**, **średni**, i **wolno**.|
|**Wynik**|Grupy testów przez wyniki wykonania: **testy nie powiodło się**, **pominięte testy**, **przekazany testy**.|
|**Cechy**|Grupy przetestować par kategorii i wartości należy zdefiniować. Składnia służąca do określenia kategorii cechy i wartości jest zdefiniowana przez platformy testów jednostkowych.|
|**Project**|Test grupy według nazwy projektów.|

### <a name="group-by-traits"></a>Grupuj według cech

 Cechy jest zazwyczaj pary nazwa/wartość kategorii, ale można też jednej kategorii. Cechy można przypisywać do metod, które są identyfikowane jako metody testowej za pomocą frameworka testów jednostkowych. Framework testów jednostkowych można zdefiniować cechy kategorii. Do kategorii cechy do zdefiniowania własnych pary nazwa/wartość kategorii można dodać wartości. Składnia służąca do określenia kategorii cechy i wartości jest zdefiniowana przez platformy testów jednostkowych.

 **Cech w jednostce Microsoft testowania Framework dla kodu zarządzanego**

 W Microsoft platformy testów jednostkowych dla aplikacji zarządzanych, należy zdefiniować nazwę cechy-wartość pary w <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> atrybutu. Struktura testowa zawiera także tych wstępnie zdefiniowanych cech:

|Cechy|Opis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Kategoria właściciela jest definiowana za pomocą frameworka testów jednostkowych i musisz podać wartość ciągu właściciela.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Kategoria priorytet jest definiowana za pomocą frameworka testów jednostkowych i musisz podać wartość priorytetu.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|Atrybut TestCategory umożliwia podanie kategorii bez wartości. Kategorię zdefiniowanych w atrybucie TestCategory można także kategorii atrybut TestProperty.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|Atrybut TestProperty umożliwia zdefiniowanie cechy para kategorii i wartości.|

 **Cech w Framework testów jednostkowych Microsoft dla języka C++** zobacz [sposób użycia Framework testów jednostkowych Microsoft dla języka C++](how-to-use-microsoft-test-framework-for-cpp.md).

### <a name="search-and-filter-the-test-list"></a>Wyszukiwanie i filtrowanie listy testów

Filtry Eksploratora testów służy do ograniczania metody testowe w projektach, które możesz wyświetlać i uruchamiać.

Wpisz ciąg w Eksploratora testów w polu wyszukiwania, a następnie wybierz polecenie ENTER, listy testów są filtrowane do wyświetlenia tylko te testy, których nazwy FQDN zawierają ciąg znaków.

Aby filtrować według różnych kryteriów:

1. Otwarcie listy rozwijanej z prawej strony pola wyszukiwania.

2. Wybierz nowe kryteria.

3. Wprowadź wartość filtru między znakami cudzysłowu.

![Filtruje testy w Eksploratorze testów](../test/media/ute_filtertestlist.png "UTE_FilterTestList")

> [!NOTE]
> Wyszukiwanie uwzględniana jest wielkość liter i zgodny z określonym ciągiem żadnej części wartości kryteriów.

|Kwalifikator|Opis|
|---------------|-----------------|
|**Cechy**|Wyszukiwana cechy kategorii i wartość do dopasowania. Składnia służąca do określenia kategorii cechy i wartości są definiowane przez platformy testów jednostkowych.|
|**Project**|Wyszukuje nazwy projektu testowego do dopasowania.|
|**Komunikat o błędzie**|Wyszukiwanie wiadomości zdefiniowane przez użytkownika błędu zwrócony przez nie powiodło się potwierdzeń do dopasowania.|
|**Ścieżka pliku**|Przeszukuje dopasowań w pełni kwalifikowanej nazwy pliku plików źródłowych testu.|
|**W pełni kwalifikowana nazwa**|Wyszukuje w pełni kwalifikowanej nazwy pliku testu przestrzeni nazw, klasy i metody do dopasowania.|
|**Output**|Wyszukuje użytkownika komunikaty o błędach są zapisywane do wyjścia standardowego (stdout) lub błąd standardowy (stderr). Składnia służąca do określenia komunikaty wyjściowe są definiowane przez platformy testów jednostkowych.|
|**Wynik**|Wyszukuje nazwy kategorii Eksploratora testów dopasowań: **testy nie powiodło się**, **pominięte testy**, **przekazany testy**.|

Aby wykluczyć podzbiór wyników filtru, należy użyć następującej składni:

```
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

Na przykład `FullName:"MyClass" - FullName:"PerfTest"` zwraca wszystkie testy, które obejmują "MyClass" w nazwie, z wyjątkiem testów, które również obejmować "PerfTest" w nazwie.

## <a name="create-custom-playlists"></a>Utwórz własne listy odtwarzania

 Można tworzyć i zapisywać listy testów, które chcesz zobaczyć jako grupa. Po wybraniu listy odtwarzania testów na liście są wyświetlane Eksploratora testów. Można dodać testu do więcej niż jedną listę odtwarzania i wszystkich testów w projekcie są dostępne po wybraniu domyślnie **wszystkie testy** listy odtwarzania.

 ![Wybierz listę odtwarzania](../test/media/ute_playlist.png "UTE_Playlist")

 **Aby utworzyć listę odtwarzania**, wybierz jeden lub więcej testów w Eksploratorze testów. W menu kontekstowego wybierz polecenie **Dodaj do listy odtwarzania**, **NewPlaylist**. Zapisz plik z nazwy i lokalizacji określonej w **Utwórz nową listę odtwarzania** okno dialogowe.

 **Aby dodać do listy odtwarzania testów**, wybierz jeden lub więcej testów w Eksploratorze testów. W menu kontekstowego wybierz polecenie **Dodaj do listy odtwarzania**, a następnie wybierz pozycję listy odtwarzania, które chcesz dodać testów do.

 **Aby otworzyć listę odtwarzania**, wybierz Test, odtwarzania z menu programu Visual Studio i wybierz z listy ostatnio używanych listy odtwarzania, lub wybierz Otwórz listę, aby określić nazwę i lokalizację listy odtwarzania.

 Jeśli poszczególne testy nie ma żadnych zależności, które uniemożliwiają uruchomione w dowolnej kolejności, włącz wykonywanie równoległe testu z ![UTE&#95;parallelicon&#45;małych](../test/media/ute_parallelicon-small.png "małych UTE_parallelicon") przycisk przełączania na pasku narzędzi. To znacznie ograniczyć czas potrzebny na uruchamianie wszystkich testów.

## <a name="debug-and-analyze-unit-tests"></a>Debugowania i analizowania testy jednostkowe

### <a name="debug-unit-tests"></a>Debuguj testy jednostkowe

Aby rozpocząć sesję debugowania dla testów, można użyć narzędzia Eksplorator testów. Krokowe wykonywanie kodu z debuger programu Visual Studio bezproblemowe przejście i z powrotem między testów jednostkowych i projektu w ramach testu. Można rozpocząć debugowania:

1. W edytorze programu Visual Studio należy ustawić punkt przerwania w metody testowe, które chcesz debugować.

    > [!NOTE]
    > Ponieważ metody testowe można uruchomić w dowolnej kolejności, ustaw punkty przerwania w wszystkie metody testowe, które chcesz debugować.

2. W Eksploratorze testów, wybierz metody testowe, a następnie wybierz **Debuguj zaznaczone testy** w menu kontekstowym.

 Aby uzyskać więcej informacji o debugera, zobacz [debugowania w programie Visual Studio](../debugger/debugging-in-visual-studio.md).

### <a name="diagnose-test-method-performance-issues"></a>Diagnozowanie problemów z wydajnością test — metoda

 Aby Sprawdź, dlaczego metody testowej trwa zbyt długo, wybierz metodę w Eksploratorze testów, a następnie wybierz profil w menu kontekstowym. Zobacz [Eksplorator wydajności](../profiling/performance-explorer.md).

### <a name="analyze-unit-test-code-coverage"></a>Analizuj pokrycie kodu testu jednostki

Można określić ilość swój kod produktu, który jest rzeczywiście testowane przez testy jednostkowe za pomocą narzędzia pokrycia kodu programu Visual Studio. Pokrycie kodu można uruchomić wybranych testów lub wszystkie testy w rozwiązaniu.

Aby uruchomić pokrycie kodu dla metody testowe w rozwiązaniu:

1. Wybierz **testy** w menu programu Visual Studio, a następnie wybierz **Analizuj pokrycie kodu**.

2. Wybierz jedną z poniższych poleceń podmenu:

    - **Wybrane testy** uruchamia metody testowe, które wybrano w Eksploratorze testów.

    - **Wszystkie testy** uruchamia wszystkie metody testowe w rozwiązaniu.

Okno wyników pokrycia kodu przedstawia wartość procentową bloków kodu produktu, które były wykonywane przez wiersz, funkcji, klasy, przestrzeń nazw i moduł.

Aby uzyskać więcej informacji, zobacz [przy użyciu pokrycia kodu do określenia, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="test-shortcuts"></a>Skróty testu

Testy można uruchomić z **Eksploratora testów**, klikając prawym przyciskiem myszy w edytorze kodu dla testu i wybierając **testu**, lub przy użyciu domyślnej [skróty Eksploratora testów](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL) w Program Visual Studio. Niektóre skróty są oparte na kontekstu. Oznacza to, czy uruchamiania lub debugowania testów bazujących na gdy kursor jest w edytorze kodu. Jeśli kursor znajduje się wewnątrz metody testowej, następnie która metoda uruchomień testów. Jeśli kursor znajduje się na poziomie klasy, a następnie uruchom wszystkie testy w tej klasie. Jest to ten sam, jak również poziomu przestrzeni nazw.

|Częste poleceń| Skróty klawiaturowe|
|--------------|------------------------|
|TestExplorer.DebugAllTestsInContext|Ctrl+R, Ctrl+T|
|TestExplorer.RunAllTestsInContext|Ctrl+R, T|

> [!NOTE]
> Nie można uruchomić testu w klasie abstrakcyjnej, ponieważ testy są tylko określone w klasy abstrakcyjne i nie wystąpienia. Aby uruchomić testy w klas abstrakcyjnych, Utwórz klasę, która pochodzi z klasy abstrakcyjnej.

## <a name="see-also"></a>Zobacz także

- [Testowanie jednostek kodu](../test/unit-test-your-code.md)
- [Uruchamianie testu jednostkowego jako procesu 64-bitowego](../test/run-a-unit-test-as-a-64-bit-process.md)
