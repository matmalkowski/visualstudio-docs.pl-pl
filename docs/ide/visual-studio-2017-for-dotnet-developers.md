---
title: Visual Studio 2017 dla deweloperów platformy .NET | Dokumentacja firmy Microsoft
description: Omówienie funkcji programu Visual Studio 2017 ułatwia pisanie szybciej lepsze kodu platformy .NET.
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.technology: vs-ide-general
ms.date: 01/16/2018
ms.topic: article
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 78e9245df26a2de747414a91b9024fde9325ef22
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="visual-studio-2017-productivity-guide-for-net-developers"></a>Visual Studio 2017 wydajność przewodnik dla deweloperów platformy .NET

[Visual Studio 2017](https://www.visualstudio.com/downloads/) zwiększa wydajność niż kiedykolwiek deweloperów! Firma Microsoft poprawia wydajność i niezawodność dla uruchomienia rozwiązania i obciążenia, wykrywania testów i wpisując opóźnienia. Firma Microsoft również został dodany i ulepszone funkcje umożliwiające szybsze pisanie kodu lepsze. Oto niektóre z tych funkcji: Nawigacja do zestawów decompiled, zmiennej nazwy sugestie podczas wpisywania, widok hierarchii w Eksploratorze testów, przejdź do wszystkich (**Ctrl + T**) można przejść do deklaracji pliku/typu/elementu członkowskiego/symbol inteligentnego pomocnika wyjątków, konfiguracja styl kodu i wymuszanie i wiele poprawek refaktoryzacje i kod. 

Postępuj zgodnie z tego przewodnika, aby zoptymalizować wydajność.

##  <a name="im-used-to-my-keyboard-shortcuts-from-a-different-extensioneditoride"></a>Używany jest skróty klawiaturowe z różnych rozszerzenia/Edytor/IDE.

Jeśli pochodzących z innego środowiska IDE lub środowisko programistyczne, może się okazać, instalowania jednego z następujących rozszerzeń, które są pomocne:

- [Emacs: emulacji](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [Klawisze dostępu dla programu Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

![Galerii rozszerzeń programu Visual Studio](../ide/media/VSIDE_Productivity_Extensibility.png)

Poniżej przedstawiono popularne skróty programu Visual Studio. 

> [!NOTE]
> Niektóre rozszerzenia usunięcia powiązania powiązań kluczy programu Visual Studio domyślne, należy przywrócić je, aby użyć następujących poleceń. Przywróć domyślne Visual Studio z powiązań kluczy, przechodząc do: **Narzędzia > Import i eksport ustawień > zresetować wszystkie ustawienia** lub **Narzędzia > Opcje > klawiatury > Resetuj**.

| Skrót (wszystkie profile) | Polecenie | Opis |
|-|-|-|
| **Ctrl+T** | Przejdź do wszystkich | Przejdź do dowolnego pliku/typu/elementu członkowskiego/symbol deklaracji |
| **F12** (również **kliknij z wciśniętym**) | Przejdź do definicji | Przejdź do których jest zdefiniowany symbol |
| **Ctrl+F12** | Przejdź do implementacji | Przejdź z podstawowego typu lub elementu członkowskiego do jej różnych implementacji |
| **Shift+F12** | Znajdź wszystkie odwołania | Zobacz wszystkie symbolu lub literału odwołań |
| **Ctrl**+**.** (również **Alt + wprowadź** w profilu C#) | Szybkie akcje i operacje refaktoryzacji | Zobacz, jaki kod poprawki, akcje generowania kodu, refaktoryzacje lub innych szybkie akcje są dostępne pod adresem wybór pozycji lub kod kursora |
| **Ctrl**+**D** | Zduplikowany wiersz | Duplikaty wiersz kodu, w którym znajduje się kursor (dostępne w **programu Visual Studio 2017 wersji 15,6** i nowsze) |
| **Shift**+**Alt**+**+**/**-** | Rozwiń/kontraktu zaznaczenia | Rozwija lub umów bieżące zaznaczenie w edytorze (dostępne w **programu Visual Studio 2017 wersji 15,5 cala** i nowsze) |
| **Ctrl+Q** | Szybkie uruchamianie | Wyszukaj wszystkie ustawienia programu Visual Studio |
| **F5** | Rozpocznij debugowanie | Rozpocznij debugowanie aplikacji |
| **Ctrl+F5** | Uruchom bez debugowania | Uruchamianie aplikacji lokalnie bez debugowania |
| **CTRL + K, D** (profil domyślny) lub **Ctrl + E, D** (profil C#) | Format dokumentu | Czyści formatowanie naruszeń w pliku są oparte na nowym wierszem, odstępy i ustawienia wcięć |
| **CTRL +\\, E** (profil domyślny) lub **Ctrl + W, E** (profil C#) | Widok listy błędów | Zobacz wszystkie błędy w dokumencie, projektu lub rozwiązania |

## <a name="i-need-a-way-to-quickly-navigate-to-files-or-types"></a>I muszą mieć możliwość szybkiego przechodzenia do plików lub typów.
Visual Studio 2017 ma funkcję _przejdź do wszystkich_ (**Ctrl + T**). Przejdź do wszystkich umożliwia szybkie przejście do pliku, typu, elementu członkowskiego lub deklaracji symbolu.
- Zmień lokalizację ten pasek wyszukiwania lub Wyłącz na podglądzie nawigacji na żywo z **narzędzi** ikony
- Filtrowanie wyników przy użyciu naszego składni zapytania (na przykład "mojtyp t"). Można również ograniczyć wyszukiwanie do bieżącego dokumentu.
- Dopasowywanie (camelcase) jest obsługiwany!

![Przejdź do wszystkich w programie Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="my-team-enforces-code-style-rules-on-our-codebase"></a>Mojego zespołu wymusza stosowanie reguł stylu kodu na naszych codebase.
Plik .editorconfig umożliwia skodyfikować Konwencji kodowania. Zaleca się zainstalowanie [rozszerzenia usług języka EditorConfig](https://aka.ms/editorconfig) do dodawania i edytowania pliku .editorconfig. Firma Microsoft zaleca, zapoznaj się [dokumentacji](https://aka.ms/editorconfigDocs) dla programu .NET wszystkie opcje Konwencji kodowania.

Zapoznaj się z [tego gist](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8) dla .editorconfig przykład.

![Wymuszanie stylu kodu w programie Visual Studio](../ide/media/VSGuide_CodeStyle.png)

## <a name="i-need-more-refactorings-and-code-fixes"></a>Potrzebuję więcej poprawki refaktoryzacje i kod.
Visual Studio 2017 pochodzi z dużą refaktoryzacje kodu generowania akcji i kodu poprawki, które widać w naszym [dokumentacji](https://aka.ms/refactorings). Czerwone zygzaki reprezentuje błędy, zygzaki zielony reprezentują ostrzeżenia i wielokropek szarego reprezentują sugestie kodu.

Możesz poprawki kodu dostępu, klikając ikonę żarówka/śrubokręt lub naciskając klawisz **Ctrl +.** lub **Alt + wprowadź**. Każda poprawka jest dostarczany z okna podglądu, pokazujący różnicowego kodu na żywo, działania poprawkę.

Oto niektóre szybkie popularne rozwiązania i refaktoryzacje: *zmienić*, *Wyodrębnij metodę*, *podpis metody zmiany*, *Generuj Konstruktor*, *Wygenerować metody*, *Przenieś typu do pliku*, *dodania sprawdzenia wartości Null*, *Dodaj parametr*, *Usuń Deklaracje Using niepotrzebnych*.

Refaktoryzacje i Kod poprawki, które mogą być łatwo zapisywane z [analizatorów Roslyn](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix). Kilka członków społeczności, musieli napisać *wolnego* rozszerzeń, których dodanie dodatkowych kodu inspekcji: [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017), [SonarLint dla programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017), i [ StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/). 

![Refaktoryzacje w programie Visual Studio](../ide/media/VSGuide_CodeAnalysis.png "VSGuide_CodeAnalysis")

## <a name="i-need-find-usages-go-to-implementation-navigate-to-decompiled-assemblies"></a>Należy znaleźć użycia, przejdź do implementacji, przejdź do Decompiled zestawów
Visual Studio 2017 oferuje wiele funkcji, które ułatwiają wyszukiwanie i przejdź baza kodu — tym Znajdź wszystkie odwołania (**Shift + F12**), przejdź do implementacji (**Ctrl + F12**), przejdź do definicji ( **F12** lub **kliknij z wciśniętym**). Wprowadziliśmy wiele ulepszeń te funkcje w VS2017, na przykład Znajdź wszystkie odwołania teraz jest pokolorowane i pozwala na grupowanie niestandardowe. *Przejdź do Decompiled zestawy* na Przejdź do definicji został dodany w wersji 15,6. Aby włączyć tę funkcję, przejdź do **Narzędzia > Opcje > Edytor tekstu > C# > Zaawansowane > Włącz nawigacji do źródeł decompiled**.

Inne typowe narzędzia nawigacji obejmują: definicji wglądu (**Alt + F12**), wizualizatora struktury (hoverable kropkami wierszy nawiasach), i [więcej](../ide/navigating-code.md).

![Przejdź do wszystkich i Znajdź wszystkie odwołania](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="i-want-to-run-and-see-my-unit-tests"></a>I chcesz uruchomić, a następnie zobacz Moje testów jednostkowych.
Mamy dwa ofert dla jednostki testowania w programie Visual Studio 2017: Eksplorator testów i _Live testów jednostkowych_ (zarówno obsługiwać MSTest v1, MSTest v2 NUnit i XUnit). Firma Microsoft znacznie ulepszona szybkości wykrywania testów w Eksploratorze testów w wersji 15,6 (Aby uzyskać najlepsze wyniki, uaktualnienia do najnowszej wersji karty testu). Możemy również przeprojektowano interfejsu użytkownika do obsługi hierarchicznych sortowania.

Visual Studio 2017 Enterprise ma również jednostki testujące wywołuje funkcję [Live testów jednostkowych](../test/live-unit-testing.md). Stale testów jednostkowych na żywo działa w tle, uruchamia testy wpływ zmiany kodu i aktualizuje wbudowanego edytora ikon informujący stan testów.

![Widok hierarchii Explorer tekstu w programie Visual Studio](../ide/media/VSGuide_Testing.png)

## <a name="i-want-to-debug-my-code"></a>Chcę Debuguj kod.
Dodano wiele możliwości nowe funkcje debugowania w programie Visual Studio 2017 r. *Uruchom, aby kliknij* służy do aktywowania obok wiersza kodu, kliknij zieloną ikonę "play", który pojawia się i uruchomić program, dopóki nie osiągnie tego wiersza. Nowy *pomocnika wyjątków* naraża najważniejsze informacje, takie jak zmienna, która jest wartość "null" w NullReferenceException na najwyższym poziomie w oknie dialogowym. I [wróć do kroku](../debugger/how-to-use-intellitrace-step-back.md) debugowanie umożliwia wróć na poprzednich punktów przerwania lub kroków i wyświetlić stan aplikacji, ponieważ był w przeszłości.

Jeśli masz zasobów na platformie Azure, użyj [debugowania migawki](/azure/application-insights/app-insights-snapshot-debugger) do sprawdzania, czy stan aplikacji sieci web, w tej chwili Wystąpił wyjątek.

![Nowy Pomocnik wyjątków w VS2017](../ide/media/VSGuide_Debugging.png "VSGuide_Debugging")

## <a name="i-want-to-use-version-control-with-my-projects"></a>Chcę użyć kontroli wersji z projektami.
Git lub TFVC służy do przechowywania i zaktualizuj kod w programie Visual Studio. W edytorze organizowanie lokalne zmiany z programu Team Explorer i użyj paska stanu do śledzenia oczekujących zatwierdzeń i zmiany. Konfigurowanie ciągłej integracji i dostarczania dla projektów w programie Visual Studio z naszych [ciągłego dostarczania Tools for Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) rozszerzenia i przyjmuje przepływu pracy agile developer.

![Kontroli źródła w programie Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-do-i-need-to-know-about"></a>Jakie inne funkcje należy znać?
Oto lista edytora i produktywność funkcje ułatwiające efektywniejsze pisanie kodu. Niektóre funkcje mogą muszą być włączone, ponieważ są one wyłączone domyślnie (może indeksie czynności na komputerze, są kontrowersyjna lub są obecnie eksperymentalne).
- *Zlokalizuj plik w Eksploratorze rozwiązań* wyróżnia aktywnego pliku w Eksploratorze rozwiązań.
  - **Narzędzia > Opcje > projektów i rozwiązań > Śledzenie aktywnego elementu w Eksploratorze rozwiązań**
- *Dodaj użycie typów w zestawy referencyjne i pakiety NuGet* pokazuje żarówka z poprawkę kodu można zainstalować pakietu NuGet, dla której nie istniały odwołania typu.
  - **Narzędzia > Opcje > Edytor tekstu > C# > Zaawansowane > Sugeruj użycie typów w zestawach odwołanie** i **Sugeruj użycie typów w pakietach NuGet**
- *Włącz pełną analizę rozwiązania* aby zobaczyć wszystkie błędy w rozwiązaniu na liście błędów.
  - **Narzędzia > Opcje > Edytor tekstu > C# > Zaawansowane > Włącz pełną analizę rozwiązania**
- *Włączanie nawigacji w źródłach decompiled* Włącz przejdź do definicji typów/elementów członkowskich z zewnętrznych źródeł i umożliwia wyświetlanie treści metody ILSpy decompiler.
  - **Narzędzia > Opcje > Edytor tekstu > C# > Zaawansowane > Włącz nawigacji do decompiled źródeł**
- *Tryb uzupełniania/sugestii* w IntelliSense zmienia zachowanie uzupełniania. Deweloperom tła IntelliJ często Zmień ustawienie tutaj wartości domyślnej.
  - **Menu > Edytuj > IntelliSense > Przełącz tryb uzupełniania**
- *[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)*  Wyświetla informacje o odwołaniu kodu i zmień historii w edytorze.
  - **Narzędzia > Opcje > Edytor tekstu > wszystkie języki > CodeLens**
- Mamy *wstawki kodu* ułatwiające stub limit wspólne elementy standardowe (dwa razy klawisz "Karta"). Zobacz [pełną listę](../ide/visual-csharp-code-snippets.md).

![Wstawki kodu programu Visual Studio](../ide/media/VSGuide_SmartEditor.png)

## <a name="missing-a-feature-that-makes-you-productive-or-experiencing-poor-performance"></a>Brak funkcja, która zwiększa produktywność lub obciążony pogorszenie wydajności?
Istnieje kilka sposobów Wystaw nam opinię:
- Żądania funkcji .NET można złożyć na naszych [repozytorium GitHub](https://github.com/dotnet/roslyn/issues).
- Żądania funkcji w usłudze Visual Studio, błędy i problemy z wydajnością można złożyć za pomocą **Prześlij opinię** ikonę w prawym górnym rogu okna programu Visual Studio.
