---
title: "Visual Studio 2017 dla deweloperów platformy .NET | Dokumentacja firmy Microsoft"
description: "Omówienie funkcji programu Visual Studio 2017 ułatwia pisanie szybciej lepsze kodu platformy .NET."
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
ms.openlocfilehash: 7e910c50682d45d209d993cb883ca01d1ea436f2
ms.sourcegitcommit: 236c250bb97abdab99d00c6525d106fc0035d7d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2018
---
# <a name="visual-studio-2017-productivity-guide-for-net-developers"></a>Visual Studio 2017 wydajność przewodnik dla deweloperów platformy .NET

- [Przewodnik wydajności](#guide)
- [Visual Studio 2017 — omówienie](#overview)

## <a name="a-idguide-productivity-guide"></a><a id="guide"/> Przewodnik wydajności
[Visual Studio 2017](https://www.visualstudio.com/downloads/) zwiększa wydajność niż kiedykolwiek deweloperów! Firma Microsoft poprawia wydajność i niezawodność dla uruchomienia rozwiązania i obciążenia, wykrywania testów i wpisując opóźnienia. Firma Microsoft również został dodany i ulepszone funkcje umożliwiające szybsze pisanie kodu lepsze. Oto niektóre z tych funkcji: Nawigacja do zestawów decompiled, zmiennej nazwy sugestie podczas wpisywania, widok hierarchii w Eksploratorze testów, przejdź do wszystkich (**Ctrl + T**) można przejść do deklaracji pliku/typu/elementu członkowskiego/symbol inteligentnego pomocnika wyjątków, konfiguracja styl kodu i wymuszanie i wiele poprawek refaktoryzacje i kod. 

Postępuj zgodnie z tego przewodnika, aby zoptymalizować wydajność.

###  <a name="im-used-to-my-keyboard-shortcuts-from-a-different-extensioneditoride"></a>Używany jest skróty klawiaturowe z różnych rozszerzenia/Edytor/IDE.

Jeśli pochodzących z innego środowiska IDE lub środowisko programistyczne, może się okazać, instalowania jednego z następujących rozszerzeń, które są pomocne:

- [Emacs: emulacji](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [Klawisze dostępu dla programu Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

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

### <a name="i-need-a-way-to-quickly-navigate-to-files-or-types"></a>I muszą mieć możliwość szybkiego przechodzenia do plików lub typów.
Visual Studio 2017 ma funkcję _przejdź do wszystkich_ (**Ctrl + T**). Przejdź do wszystkich umożliwia szybkie przejście do pliku, typu, elementu członkowskiego lub deklaracji symbolu.
- Zmień lokalizację ten pasek wyszukiwania lub Wyłącz na podglądzie nawigacji na żywo z **narzędzi** ikony
- Filtrowanie wyników przy użyciu naszego składni zapytania (na przykład "mojtyp t"). Można również ograniczyć wyszukiwanie do bieżącego dokumentu.
- Dopasowywanie (camelcase) jest obsługiwany!

![Przejdź do wszystkich w programie Visual Studio](../ide/media/VS2017Guide-go-to-all.png "VS2017Guide przejdź do wszystkich")

### <a name="my-team-enforces-code-style-rules-on-our-codebase"></a>Mojego zespołu wymusza stosowanie reguł stylu kodu na naszych codebase.
Plik .editorconfig umożliwia skodyfikować Konwencji kodowania. Zaleca się zainstalowanie [rozszerzenia usług języka EditorConfig](https://aka.ms/editorconfig) do dodawania i edytowania pliku .editorconfig. Firma Microsoft zaleca, zapoznaj się [dokumentacji](https://aka.ms/editorconfigDocs) dla programu .NET wszystkie opcje Konwencji kodowania.

Chck limit [tego gist](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8) dla .editorconfig przykład.

![Styl wymuszania w programie Visual Studio Code](../ide/media/VS2017Guide-code-style.png "VS2017Guide kodu stylu")

### <a name="i-need-more-refactorings-and-code-fixes"></a>Potrzebuję więcej poprawki refaktoryzacje i kod.
Visual Studio 2017 pochodzi z dużą refaktoryzacje kodu generowania akcji i kodu poprawki, które widać w naszym [dokumentacji](https://aka.ms/refactorings). Czerwone zygzaki reprezentuje błędy, zygzaki zielony reprezentują ostrzeżenia i wielokropek szarego reprezentują sugestie kodu.

Możesz poprawki kodu dostępu, klikając ikonę żarówka/śrubokręt lub naciskając klawisz **Ctrl +.** lub **Alt + wprowadź**. Każda poprawka jest dostarczany z okna podglądu, pokazujący różnicowego kodu na żywo, działania poprawkę.

Oto niektóre szybkie popularne rozwiązania i refaktoryzacje: zmienić nazwę, Wyodrębnij metodę, Zmień podpis metody, Generuj Konstruktor, generowanie — metoda, typ przenoszenia do pliku, Dodaj Null sprawdzania, Dodaj parametr, usuń zbędne deklaracje Using.

Refaktoryzacje i Kod poprawki, które mogą być łatwo zapisywane z [analizatorów Roslyn](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix). Kilka członków społeczności, musieli napisać *wolnego* rozszerzeń zwiększających dodatkowe kodu inspekcji: Roslynator i SonarLint dla programu Visual Studio. 

![Refaktoryzacje w programie Visual Studio](../ide/media/VS2017Guide-refactoring.png "refaktoryzacji VS2017Guide")

### <a name="i-need-find-usages-go-to-implementation-navigate-to-decompiled-assemblies"></a>Należy znaleźć użycia, przejdź do implementacji, przejdź do Decompiled zestawów
Visual Studio 2017 oferuje wiele funkcji, które ułatwiają wyszukiwanie i przejdź baza kodu — tym Znajdź wszystkie odwołania (**Shift + F12**), przejdź do implementacji (**Ctrl + F12**), przejdź do definicji ( **F12** lub **kliknij z wciśniętym**). Przejdź do Decompiled zestawy został dodany w wersji 15,6. Aby włączyć tę funkcję, przejdź do **Narzędzia > Opcje > Edytor tekstu > C# > Zaawansowane > Włącz nawigacji do źródeł decompiled**.

![Przejdź do źródła decompiled w programie Visual Studio](../ide/media/VS2017Guide-navigate-to-source.png "VS2017Guide przejdź do source")

### <a name="i-want-to-run-and-see-my-unit-tests"></a>I chcesz uruchomić, a następnie zobacz Moje testów jednostkowych.
Mamy dwa ofert dla jednostki testowania w programie Visual Studio 2017: Eksplorator testów i _Live testów jednostkowych_. Szybkość wykrywania testów w Eksploratorze testów w wersji 15,6 możemy znacznie ulepszona. Możemy również przeprojektowano interfejsu użytkownika do obsługi hierarchicznych sortowania.

Visual Studio ma również jednostki testujące wywołuje funkcję [Live testów jednostkowych](/test/live-unit-testing). Stale testów jednostkowych na żywo działa w tle, uruchamia testy wpływ zmiany kodu i aktualizuje wbudowanego edytora ikon informujący stan testów.

![Widok hierarchii Explorer tekstu w programie Visual Studio](../ide/media/VS2017Guide-hiearchy-test-explorer.png "VS2017Guide-hiearchy--Eksplorator testów")

### <a name="what-other-features-do-i-need-to-know-about"></a>Jakie inne funkcje należy znać?
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
  - **Menu > Edytuj > IntelliSense -> Przełącz tryb uzupełniania**
- Mamy *wstawki kodu* ułatwiające stub limit wspólne elementy standardowe (dwa razy klawisz "Karta"). Zobacz [pełną listę](/ide/visual-csharp-code-snippets).

![Fragmenty kodu w programie Visual Studio Code](../ide/media/VS2017Guide-code-snippet.png "VS2017Guide wstawki")

### <a name="missing-a-feature-that-makes-you-productive-or-experiencing-poor-performance"></a>Brak funkcja, która zwiększa produktywność lub obciążony pogorszenie wydajności?
Istnieje kilka sposobów Wystaw nam opinię:
- Żądania funkcji .NET można złożyć na naszych [repozytorium GitHub](https://github.com/dotnet/roslyn/issues).
- Żądania funkcji w usłudze Visual Studio, błędy i problemy z wydajnością można złożyć za pomocą **Prześlij opinię** ikonę w górnej części okna programu Visual Studio.


## <a name="a-idoverview-overview-of-visual-studio-2017-for-net-developers"></a><a id="overview"/> Omówienie programu Visual Studio 2017 dla deweloperów platformy .NET

### <a name="smart-code-editor"></a>Edytor kodu inteligentne

- [Dokumentacja: Korzystanie z IntelliSense](using-intellisense.md)
- [Dokumentacji: Funkcje edycji inteligentne](writing-code-in-the-code-and-text-editor.md)

Visual Studio ma bezpośrednich opis kodu przez kompilator .NET ("Roslyn"), aby umożliwiają edytowanie Inteligentne funkcje, takie jak kolorowanie składni, kod zakończenia, sprawdzanie pisowni błędnie wpisane zmienne, rozpoznawania typu niezaimportowanych zwijania — struktura wizualizatory, [CodeLens](find-code-changes-and-other-history-with-codelens.md), wywołaj hierarchii, stanie hover szybka podpowiedź, parametr pomocy, a także narzędzia do refaktoryzacji, szybkie akcje stosowania i generowanie kodu.

![Edytor kodu inteligentne w usłudze Visual Studio](../ide/media/VSIDE_Productivity_SmartCodeEditor.png "VSIDE_Productivity_SmartCodeEditor")

### <a name="navigate-and-search-your-codebase"></a>Nawigowanie i wyszukiwania baza kodu

[Dokumentacja: Nawigowanie po kodzie](navigating-code.md)

Szybko przejść przez przejście do pliku, typu, elementu członkowskiego lub deklaracja symboli z kodu .NET *przejdź do wszystkich* skrótów (**Ctrl + T**). Znajdź wszystkie odwołania symbolu lub literał w kodzie, w tym odwołania między językami .NET (**Shift + F12**). I skorzystaj naszych poleceń docelowe nawigacji, aby przejść bezpośrednio do definicji symbolu (**F12**) lub implementacji (**Ctrl + F12**).

![Przejdź do wszystkich i Znajdź wszystkie odwołania](../ide/media/VSIDE_Productivity_Navigation.png "VSIDE_Productivity_Navigation")

### <a name="live-code-analysis-for-code-quality"></a>Analiza kodu na żywo dla jakości kodu

[Dokumentacji: Refaktoryzacje i szybkie akcje](refactoring-code-generation-quick-actions.md)

Visual Studio ma diagnostyki kodu na żywo, aby pomóc w poprawie jakości kodu przez wykrywanie błędów i kod potencjalnie powodować problemy. Firma Microsoft udostępnia szybkie akcje (**Ctrl**+**.**) do rozwiązywania problemów wykrytych przez dokument, projektu lub rozwiązania. Włącz *analizy rozwiązania pełnej* Aby znaleźć problemy dla całego rozwiązania, nawet jeśli nie są one otwarte pliki w edytorze.

Ponadto przy użyciu kodu sugestie Dowiedz się, najlepsze rozwiązania w zakresie, wejściowy lub generowanie kodu refaktoryzacji kodu, a przyjmuje nowe funkcje językowe z **Ctrl**+**.** Skrót.

![Zastosuj Szybkie rozwiązania i refaktoryzacje za pomocą menu żarówka](../ide/media/VSIDE_Productivity_CodeAnalysis.png "VSIDE_Productivity_CodeAnalysis")

### <a name="unit-testing"></a>Testy jednostkowe

[Dokumentacji: Testowania w programie Visual Studio jednostek](../test/improve-code-quality.md)

Uruchom i debugowanie testy jednostkowe na podstawie MSTest, NUnit lub XUnit testowania struktur dla dowolnej aplikacji przeznaczonych dla platformy .NET Framework, .NET Standard lub .NET Core. Eksploruj i przejrzyj testów w *Eksploratora testów* lub natychmiast zobaczyć wpływ zmian kodu w edytorze z testy jednostkowe *Live testów jednostkowych* (tylko w wersji Enterprise).

![Na żywo testowania w programie Visual Studio jednostek](../ide/media/VSIDE_Productivity_LiveUnitTesting.png "VSIDE_Productivity_LiveUnitTesting")

### <a name="code-consistency-and-style"></a>Kod spójności i stylu

- [Dokumentacji: Opcje przenośne niestandardowego edytora](create-portable-custom-editor-options.md)
- [Dokumentacja: EditorConfig kodu stylu ustawień dla platformy .NET](editorconfig-code-style-settings-reference.md)

Program Visual Studio umożliwia konfigurację Konwencji kodowania, wykrywa naruszeń styl kodowania i zapewnia szybkie — poprawki, aby rozwiązać problemy stylu z **Ctrl**+**.** Skrót. Konfigurowanie i wymuszać formatowania zespołu, nazw i kodu konwencje stylu w repozytorium — umożliwiając zastępowania wartości na poziomie projektu i pliku — za pomocą *EditorConfig*.

![Konfigurowanie i wymuszaniu Konwencji kodowania z EditorConfig](../ide/media/VSIDE_Productivity_CodeStyle.png "VSIDE_Productivity_CodeStyle")

### <a name="debugging"></a>Debugowanie

[Dokumentacja: Debugowanie w programie Visual Studio](../debugger/index.md)

Visual Studio zawiera top-notch debuger, który służy do debugowania aplikacji .NET przeznaczonych dla platformy .NET Framework, .NET Standard i .NET Core. Przełącz i ustawić warunkowe punkty przerwania (**F9**), wkroczyć do wywołania metody, oceny wyrażenia LINQ i lambda, ustawienie zmiennej obserwowanie, ponownie dołączyć do procesów, przejrzyj stos wywołań lub wprowadzać zmiany kodu podczas debugowania za pomocą nażywo *Edytuj i Kontynuuj*.

Jeśli usługa jest uruchomiona na platformie Azure, użyj *debugowania migawki* do diagnozowania problemów w aplikacji w chmurze na żywo, wdrożonych w Visual Studio Enterprise 2017 r.

![Debugowanie w programie Visual Studio](../ide/media/VSIDE_Productivity_Debugging.png "VSIDE_Productivity_Debugging")

### <a name="version-control"></a>Kontrola wersji

[Dokumentacja: Kontroli wersji w programie Visual Studio](/vsts/index)

Użyj narzędzia git lub TFVC do przechowywania i zaktualizuj kod w programie Visual Studio. W edytorze organizowanie lokalnych zmian z Team Explorer i użyj paska stanu do śledzenia oczekujących zatwierdzeń i zmiany. Konfigurowanie ciągłej integracji i dostarczania w programie Visual Studio z naszych [ciągłego dostarczania Tools for Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) rozszerzenia podjęcie przepływu pracy agile developer.

![Formant w programie Visual Studio źródła](../ide/media/VSIDE_Productivity_SourceControl.png "VSIDE_Productivity_SourceControl")

### <a name="extensibility"></a>Rozszerzalność

[Dokumentacja: Rozszerzenie programu Visual Studio](../extensibility/index.md)

Visual Studio ma rozbudowany ekosystem rozszerzeń, które można zainstalować lub utworzyć w miarę potrzeby. Zainstaluj rozszerzenia z *galerii rozszerzeń* lub *Visual Studio Marketplace*, tworzenie własnych wtyczka edytora z *zestawu VS SDK*, lub utworzyć własne analizator kodu na żywo lub refaktoryzacji przy użyciu *zestawu SDK platformy kompilatora .NET*. Dodatkowy kod poprawki i sugestie można znaleźć pobierając [analizy kodu Microsoft](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) rozszerzenia.

![Galerii rozszerzeń programu Visual Studio](../ide/media/VSIDE_Productivity_Extensibility.png "VSIDE_Productivity_Extensibility")
