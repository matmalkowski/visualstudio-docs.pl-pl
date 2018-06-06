---
title: Visual Studio 2017 dla deweloperów platformy .NET
description: Omówienie funkcji programu Visual Studio 2017 ułatwia pisanie szybciej lepsze kodu platformy .NET.
author: kuhlenh
ms.author: kaseyu
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.date: 01/16/2018
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 9c4577b1d04b74bdc351927603604d2f92d31eb9
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748754"
---
# <a name="visual-studio-2017-productivity-guide-for-net-developers"></a>Visual Studio 2017 wydajność przewodnik dla deweloperów platformy .NET

[Visual Studio 2017](https://www.visualstudio.com/downloads/) zwiększa wydajność niż kiedykolwiek deweloperów! Firma Microsoft poprawia wydajność i niezawodność dla uruchomienia rozwiązania i obciążenia, wykrywania testów i wpisując opóźnienia. Firma Microsoft również został dodany i ulepszone funkcje umożliwiające szybsze pisanie kodu lepsze. Oto niektóre z tych funkcji: Nawigacja do zestawów decompiled, zmiennej nazwy sugestie podczas wpisywania, widok hierarchii w **Eksploratora testów**, przejdź do wszystkich (**Ctrl** +  **T**) można przejść do pliku/typu/elementu członkowskiego/symbol deklaracji, inteligentnego **pomocnika wyjątków**, styl konfiguracji i wymuszania i refaktoryzacje wiele kodu i kodu poprawki.

Postępuj zgodnie z tego przewodnika, aby zoptymalizować wydajność.

##  <a name="im-used-to-my-keyboard-shortcuts-from-a-different-extensioneditoride"></a>Używany jest skróty klawiaturowe z różnych rozszerzenia/Edytor/IDE.

Jeśli pochodzących z innego środowiska IDE lub środowisko programistyczne, może się okazać, instalowania jednego z następujących rozszerzeń, które są pomocne:

- [Emacs: emulacji](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [Klawisze dostępu dla programu Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Poniżej przedstawiono popularne skróty programu Visual Studio:

| Skrót (wszystkie profile) | Polecenie | Opis |
|-|-|-|
| **CTRL**+**T** | Przejdź do wszystkich | Przejdź do dowolnego pliku/typu/elementu członkowskiego/symbol deklaracji |
| **F12** (również **Ctrl**+**kliknij**) | Przejdź do definicji | Przejdź do których jest zdefiniowany symbol |
| **CTRL**+**F12** | Przejdź do implementacji | Przejdź z podstawowego typu lub elementu członkowskiego do jej różnych implementacji |
| **SHIFT**+**F12** | Znajdź wszystkie odwołania | Zobacz wszystkie symbolu lub literału odwołań |
| **Ctrl**+**.** (również **Alt**+**wprowadź** w profilu C#) | Szybkie akcje i operacje refaktoryzacji | Zobacz, jaki kod poprawki, akcje generowania kodu, refaktoryzacje lub innych szybkie akcje są dostępne pod adresem wybór pozycji lub kod kursora |
| **Ctrl**+**D** | Zduplikowany wiersz | Duplikaty wiersz kodu, w którym znajduje się kursor (dostępne w **programu Visual Studio 2017 wersji 15,6** i nowsze) |
| **Shift**+**Alt**+**+**/**-** | Rozwiń/kontraktu zaznaczenia | Rozwija lub umów bieżące zaznaczenie w edytorze (dostępne w **programu Visual Studio 2017 wersji 15,5 cala** i nowsze) |
| **CTRL**+**Q** | Szybkie uruchamianie | Wyszukaj wszystkie ustawienia programu Visual Studio |
| **F5** | Rozpocznij debugowanie | Rozpocznij debugowanie aplikacji |
| **CTRL**+**F5** | Uruchom bez debugowania | Uruchamianie aplikacji lokalnie bez debugowania |
| **CTRL**+**K**,**D** (profil domyślny) lub **Ctrl**+**E**,**D**  (Profil C#) | Format dokumentu | Czyści formatowanie naruszeń w pliku są oparte na nowym wierszem, odstępy i ustawienia wcięć |
| **CTRL**+**\\**,**E** (profil domyślny) lub **Ctrl**+**W**, **E** (profil C#) | Widok listy błędów | Zobacz wszystkie błędy w dokumencie, projektu lub rozwiązania |

> [!NOTE]
> Niektóre rozszerzenia usunięcia powiązania powiązań kluczy programu Visual Studio domyślne. Aby użyć następujących poleceń, Przywróć z powiązań kluczy programu Visual Studio domyślne, przechodząc do **narzędzia** > **Import i eksport ustawień** > **Resetuj wszystkie ustawienia** lub **narzędzia** > **opcje** > **klawiatury** > **resetowania** .

## <a name="i-need-a-way-to-quickly-navigate-to-files-or-types"></a>I muszą mieć możliwość szybkiego przechodzenia do plików lub typów.
Visual Studio 2017 ma funkcję **przejdź do wszystkich** (**Ctrl**+**T**). Przejdź do wszystkich umożliwia szybkie przejście do pliku, typu, elementu członkowskiego lub deklaracji symbolu.
- Zmień lokalizację ten pasek wyszukiwania lub Wyłącz na podglądzie nawigacji na żywo z **narzędzi** ikony
- Filtrowanie wyników przy użyciu naszego składni zapytania (na przykład "mojtyp t"). Można również ograniczyć wyszukiwanie do bieżącego dokumentu.
- Dopasowywanie (camelcase) jest obsługiwany!

![Przejdź do wszystkich w programie Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="my-team-enforces-code-style-rules-on-our-codebase"></a>Mojego zespołu wymusza stosowanie reguł stylu kodu na naszych codebase.
Można użyć *.editorconfig* pliku skodyfikować Konwencji kodowania i ich działają podczas podróży z źródła.
- Zaleca się zainstalowanie [rozszerzenie usługi języka EditorConfig](https://aka.ms/editorconfig) umożliwiających dodawanie i edytowanie *.editorconfig* pliku w programie Visual Studio.
- Zapoznaj się z [dokumentacji](https://aka.ms/editorconfigDocs) dla programu .NET wszystkie opcje Konwencji kodowania.
- Zobacz [tego gist](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8) przykład *.editorconfig*.

![Wymuszanie stylu kodu w programie Visual Studio](../ide/media/VSGuide_CodeStyle.png)

## <a name="i-need-more-refactorings-and-code-fixes"></a>Potrzebuję więcej poprawki refaktoryzacje i kod.
Visual Studio 2017 pochodzi z dużą refaktoryzacje kodu generowania akcji i kodu poprawki. Czerwone zygzaki reprezentuje błędy, zygzaki zielony reprezentują ostrzeżenia i wielokropek szarego reprezentują sugestie kodu. Możesz poprawki kodu dostępu, klikając ikonę żarówka/śrubokręt lub naciskając klawisz **Ctrl**+**.** lub **Alt**+**wprowadź**. Każda poprawka jest dostarczany z okna podglądu, pokazujący różnicowego kodu na żywo, działania poprawkę.

- Popularne Szybkie rozwiązania i refaktoryzacje obejmują:
  - *Zmiana nazwy*
  - *Wyodrębnianie metody*
  - *Zmiana sygnatury metody*
  - *Generowanie konstruktora*
  - *Generowanie metody*
  - *Typ przenoszenia pliku*
  - *Dodawanie sprawdzania wartości Null*
  - *Dodaj parametr*
  - *Usuń zbędne deklaracji Using*
  - Więcej informacji, zobacz Zobacz nasze [dokumentacji](https://aka.ms/refactorings)
- Pisanie własnych poprawka refaktoryzacji lub kod z [analizatorów Roslyn](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix).
- Kilka członków społeczności napisano wolnego rozszerzenia, które dodać dodatkowy kod inspekcji:
  - [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
  - [SonarLint dla programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
  - [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)

![Refaktoryzacje w programie Visual Studio](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="i-need-find-usages-go-to-implementation-navigate-to-decompiled-assemblies"></a>Należy znaleźć użycia, przejdź do implementacji, przejdź do Decompiled zestawów
Visual Studio 2017 ma wiele funkcji, które ułatwiają wyszukiwanie i przejdź baza kodu. Przeczytaj więcej na temat [kodu funkcji nawigacji](../ide/navigating-code.md)

| Funkcja | Skrót | Szczegóły/ulepszenia |
|- | - | -|
| Znajdź wszystkie odwołania | **SHIFT**+**F12**| Wyniki są kolorowane i można grupować według projektu, definicji itp. Można również "zablokować" wyników. |
| Przejdź do implementacji | **CTRL**+**F12** | Możesz użyć przejdź do definicji w `override` — słowo kluczowe, aby przejść do zastąpionym elementem członkowskim |
| Przejdź do definicji | **F12** lub **Ctrl**+**kliknij**| Naciśnij i przytrzymaj **Ctrl** podczas klikania do navgiate do definicji |
| Definicji wglądu | **ALT**+**F12** | Widok wbudowanej definicji |
| Struktura wizualizatora | Szary, kropkami linie między nawiasy klamrowe | Aktywowanie Zobacz struktury kodu |
| Nawigacja do decompiled zestawów | **F12** lub **Ctrl**+**kliknij** | Przejdź do źródła zewnętrznego (decompiled z ILSpy), należy włączyć funkcję: **narzędzia** > **opcje** > **Edytor tekstu**  >  **C#** > **zaawansowane** > **umożliwiają nawigowanie do źródeł decompiled**. |

![Przejdź do wszystkich i Znajdź wszystkie odwołania](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="i-want-to-run-and-see-my-unit-tests"></a>I chcesz uruchomić, a następnie zobacz Moje testów jednostkowych.
Wprowadziliśmy wiele ulepszeń testowania czynności w programie Visual Studio 2017 r. Użyj jednej z naszych testowania przy użyciu przełącznika MSTest v1, MSTest v2, NUnit lub XUnit jednostek testów struktur.
- **Testowanie Explorer** wykrywania testów jest szybkie w wersji 15,6 (Aby uzyskać najlepsze wyniki, uaktualnienia do najnowszej wersji karty testu).
- Organizowanie testów w Eksploratorze testów z naszej nowej *hierarchiczna sortowanie* w wersji 15,6.
- [Testy jednostkowe na żywo](../test/live-unit-testing.md) stale uruchamia testy wpływ zmiany kodu i aktualizuje wbudowanego edytora ikon informujący stan testów. Dołączyć lub wykluczyć określonych testów lub testowanie projektów z Twojej *aktywnego testu ustawić*.

![Widok hierarchii Explorer tekstu w programie Visual Studio](../ide/media/VSGuide_Testing.png)

## <a name="i-want-to-debug-my-code"></a>Chcę Debuguj kod.
Dodano wiele możliwości nowe funkcje debugowania w programie Visual Studio 2017 r.
- *Uruchom, aby kliknij* służy do aktywowania obok wiersza kodu, kliknij zieloną ikonę "play", który pojawia się i uruchomić program, dopóki nie osiągnie tego wiersza.
- Nowy **pomocnika wyjątków** naraża najważniejsze informacje, takie jak zmienna, która jest wartość "null" w NullReferenceException na najwyższym poziomie w oknie dialogowym.
- [Krok wstecz](../debugger/how-to-use-intellitrace-step-back.md) debugowanie umożliwia wróć na poprzednich punktów przerwania lub kroków i wyświetlić stan aplikacji, ponieważ był w przeszłości.
- [Debugowanie migawki](/azure/application-insights/app-insights-snapshot-debugger) umożliwia badanie stanu aplikacji sieci web w tej chwili Wystąpił wyjątek (musi być na platformie Azure).

![Nowy Pomocnik wyjątków w VS2017](../ide/media/VSGuide_Debugging.png)

## <a name="i-want-to-use-version-control-with-my-projects"></a>Chcę użyć kontroli wersji z projektami.
Git lub TFVC służy do przechowywania i zaktualizuj kod w programie Visual Studio.
- Organizowanie lokalne zmiany z **Team Explorer** i używać na pasku stanu do śledzenia oczekujących zatwierdzeń i zmiany.
- Konfigurowanie ciągłej integracji i dostarczania dla projektów w programie Visual Studio z naszych [ciągłego dostarczania narzędzi dla programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) rozszerzenia i przyjmuje przepływu pracy agile developer.

![Kontroli źródła w programie Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-do-i-need-to-know-about"></a>Jakie inne funkcje należy znać?
Oto lista edytora i produktywność funkcje ułatwiające efektywniejsze pisanie kodu. Niektóre funkcje mogą muszą być włączone, ponieważ są one wyłączone domyślnie (może indeksie czynności na komputerze, są kontrowersyjna lub są obecnie eksperymentalne).

| Funkcja | Szczegóły | Jak włączyć |
|-|-|-|
| Zlokalizuj plik w Eksploratorze rozwiązań | Wyróżnia aktywnego pliku w Eksploratorze rozwiązań | **Narzędzia** > **opcje** > **projekty i rozwiązania** > **śledzenie aktywnego elementu w Eksploratorze rozwiązań** |
| Dodaj użycie typów w zestawy referencyjne i pakiety NuGet | Pokazuje żarówka z poprawkę kodu można zainstalować pakietu NuGet, dla której nie istniały odwołania typu | **Narzędzia** > **opcje** > **Edytor tekstu** > **C#** > **zaawansowane**   >  **Sugeruj użycie typów w zestawach odwołanie** i **Sugeruj użycie typów w pakietach NuGet** |
| Włącz pełną analizę rozwiązania | Zobacz wszystkie błędy w rozwiązaniu w **listy błędów** | **Narzędzia** > **opcje** > **Edytor tekstu** > **C#** > **zaawansowane**   >  **Włącz pełną analizę rozwiązania** |
| Włączanie nawigacji do decompiled źródeł | Zezwalaj na Przejdź do definicji dla typów/elementów członkowskich z zewnętrznych źródeł i umożliwia wyświetlanie treści metody ILSpy decompiler | **Narzędzia** > **opcje** > **Edytor tekstu** > **C#** > **zaawansowane**   >  **Umożliwiają nawigowanie do decompiled źródeł** |
| Tryb uzupełniania/sugestii | Zmiany zachowanie uzupełniania IntelliSense — deweloperom tła IntelliJ często Zmień ustawienie tutaj wartości domyślnej | **Menu** > **Edytuj** > **IntelliSense** > **Przełącz tryb uzupełniania** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Wyświetla informacje o odwołaniu kodu i zmień historii w edytorze | **Narzędzia** > **opcje** > **Edytor tekstu** > **wszystkie języki**  >   **CodeLens** |
| [Fragmenty kodu](../ide/visual-csharp-code-snippets.md) | Pomoc stub limitu wspólnej standardowego |  Wpisz nazwę fragment kodu i naciśnij klawisz **kartę** dwa razy. |

![Wstawki kodu programu Visual Studio](../ide/media/VSGuide_SmartEditor.png)

## <a name="missing-a-feature-that-makes-you-productive-or-experiencing-poor-performance"></a>Brak funkcja, która zwiększa produktywność lub obciążony pogorszenie wydajności?
Istnieje kilka sposobów Wystaw nam opinię:
- Żądania funkcji .NET można złożyć na naszych [repozytorium GitHub](https://github.com/dotnet/roslyn/issues).
- Żądania funkcji w usłudze Visual Studio, błędy i problemy z wydajnością można złożyć za pomocą **Prześlij opinię** ikonę w prawym górnym rogu okna programu Visual Studio.