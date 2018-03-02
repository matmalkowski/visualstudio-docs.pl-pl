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
ms.openlocfilehash: f15239ed045185449735ec3b5e0bcdc514fa786d
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="visual-studio-2017-for-net-developers"></a>Visual Studio 2017 dla deweloperów platformy .NET

## <a name="smart-code-editor"></a>Edytor kodu inteligentne

- [Dokumentacja: Korzystanie z IntelliSense](using-intellisense.md)
- [Dokumentacji: Funkcje edycji inteligentne](writing-code-in-the-code-and-text-editor.md)

Visual Studio ma bezpośrednich opis kodu przez kompilator .NET ("Roslyn"), aby umożliwiają edytowanie Inteligentne funkcje, takie jak kolorowanie składni, kod zakończenia, sprawdzanie pisowni błędnie wpisane zmienne, rozpoznawania typu niezaimportowanych zwijania — struktura wizualizatory, [CodeLens](find-code-changes-and-other-history-with-codelens.md), wywołaj hierarchii, stanie hover szybka podpowiedź, parametr pomocy, a także narzędzia do refaktoryzacji, szybkie akcje stosowania i generowanie kodu.

![Edytor kodu inteligentne w usłudze Visual Studio](../ide/media/VSIDE_Productivity_SmartCodeEditor.png "VSIDE_Productivity_SmartCodeEditor")

## <a name="navigate-and-search-your-codebase"></a>Nawigowanie i wyszukiwania baza kodu

[Dokumentacja: Nawigowanie po kodzie](navigating-code.md)

Szybko przejść przez przejście do pliku, typu, elementu członkowskiego lub deklaracja symboli z kodu .NET *przejdź do wszystkich* skrótów (**Ctrl + T**). Znajdź wszystkie odwołania symbolu lub literał w kodzie, w tym odwołania między językami .NET (**Shift + F12**). I skorzystaj naszych poleceń docelowe nawigacji, aby przejść bezpośrednio do definicji symbolu (**F12**) lub implementacji (**Ctrl + F12**).

![Przejdź do wszystkich i Znajdź wszystkie odwołania](../ide/media/VSIDE_Productivity_Navigation.png "VSIDE_Productivity_Navigation")

## <a name="live-code-analysis-for-code-quality"></a>Analiza kodu na żywo dla jakości kodu

[Dokumentacji: Refaktoryzacje i szybkie akcje](refactoring-code-generation-quick-actions.md)

Visual Studio ma diagnostyki kodu na żywo, aby pomóc w poprawie jakości kodu przez wykrywanie błędów i kod potencjalnie powodować problemy. Firma Microsoft udostępnia szybkie akcje (**Ctrl**+**.**) do rozwiązywania problemów wykrytych przez dokument, projektu lub rozwiązania. Włącz *analizy rozwiązania pełnej* Aby znaleźć problemy dla całego rozwiązania, nawet jeśli nie są one otwarte pliki w edytorze.

Ponadto przy użyciu kodu sugestie Dowiedz się, najlepsze rozwiązania w zakresie, wejściowy lub generowanie kodu refaktoryzacji kodu, a przyjmuje nowe funkcje językowe z **Ctrl**+**.** Skrót.

![Zastosuj Szybkie rozwiązania i refaktoryzacje za pomocą menu żarówka](../ide/media/VSIDE_Productivity_CodeAnalysis.png "VSIDE_Productivity_CodeAnalysis")

## <a name="unit-testing"></a>Testy jednostkowe

[Dokumentacji: Testowania w programie Visual Studio jednostek](../test/improve-code-quality.md)

Uruchom i debugowanie testy jednostkowe na podstawie MSTest, NUnit lub XUnit testowania struktur dla dowolnej aplikacji przeznaczonych dla platformy .NET Framework, .NET Standard lub .NET Core. Eksploruj i przejrzyj testów w *Eksploratora testów* lub natychmiast zobaczyć wpływ zmian kodu w edytorze z testy jednostkowe *Live testów jednostkowych* (tylko w wersji Enterprise).

![Na żywo testowania w programie Visual Studio jednostek](../ide/media/VSIDE_Productivity_LiveUnitTesting.png "VSIDE_Productivity_LiveUnitTesting")

## <a name="code-consistency-and-style"></a>Kod spójności i stylu

- [Dokumentacji: Opcje przenośne niestandardowego edytora](create-portable-custom-editor-options.md)
- [Dokumentacja: EditorConfig kodu stylu ustawień dla platformy .NET](editorconfig-code-style-settings-reference.md)

Program Visual Studio umożliwia konfigurację Konwencji kodowania, wykrywa naruszeń styl kodowania i zapewnia szybkie — poprawki, aby rozwiązać problemy stylu z **Ctrl**+**.** Skrót. Konfigurowanie i wymuszać formatowania zespołu, nazw i kodu konwencje stylu w repozytorium — umożliwiając zastępowania wartości na poziomie projektu i pliku — za pomocą *EditorConfig*.

![Konfigurowanie i wymuszaniu Konwencji kodowania z EditorConfig](../ide/media/VSIDE_Productivity_CodeStyle.png "VSIDE_Productivity_CodeStyle")

## <a name="debugging"></a>Debugowanie

[Dokumentacja: Debugowanie w programie Visual Studio](../debugger/index.md)

Visual Studio zawiera top-notch debuger, który służy do debugowania aplikacji .NET przeznaczonych dla platformy .NET Framework, .NET Standard i .NET Core. Przełącz i ustawić warunkowe punkty przerwania (**F9**), wkroczyć do wywołania metody, oceny wyrażenia LINQ i lambda, ustawienie zmiennej obserwowanie, ponownie dołączyć do procesów, przejrzyj stos wywołań lub wprowadzać zmiany kodu podczas debugowania za pomocą nażywo *Edytuj i Kontynuuj*.

Jeśli usługa jest uruchomiona na platformie Azure, użyj *debugowania migawki* do diagnozowania problemów w aplikacji w chmurze na żywo, wdrożonych w Visual Studio Enterprise 2017 r.

![Debugowanie w programie Visual Studio](../ide/media/VSIDE_Productivity_Debugging.png "VSIDE_Productivity_Debugging")

## <a name="version-control"></a>Kontrola wersji

[Dokumentacja: Kontroli wersji w programie Visual Studio](/vsts/index)

Użyj narzędzia git lub TFVC do przechowywania i zaktualizuj kod w programie Visual Studio. W edytorze organizowanie lokalnych zmian z Team Explorer i użyj paska stanu do śledzenia oczekujących zatwierdzeń i zmiany. Konfigurowanie ciągłej integracji i dostarczania w programie Visual Studio z naszych [ciągłego dostarczania Tools for Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) rozszerzenia podjęcie przepływu pracy agile developer.

![Formant w programie Visual Studio źródła](../ide/media/VSIDE_Productivity_SourceControl.png "VSIDE_Productivity_SourceControl")

## <a name="extensibility"></a>Rozszerzalność

[Dokumentacja: Rozszerzenie programu Visual Studio](../extensibility/index.md)

Visual Studio ma rozbudowany ekosystem rozszerzeń, które można zainstalować lub utworzyć w miarę potrzeby. Zainstaluj rozszerzenia z *galerii rozszerzeń* lub *Visual Studio Marketplace*, tworzenie własnych wtyczka edytora z *zestawu VS SDK*, lub utworzyć własne analizator kodu na żywo lub refaktoryzacji przy użyciu *zestawu SDK platformy kompilatora .NET*. Dodatkowy kod poprawki i sugestie można znaleźć pobierając [analizy kodu Microsoft](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) rozszerzenia.

![Galerii rozszerzeń programu Visual Studio](../ide/media/VSIDE_Productivity_Extensibility.png "VSIDE_Productivity_Extensibility")

## <a name="popular-extensions--shortcuts"></a>Popularne rozszerzenia & skrótów

Jeśli pochodzących z innego środowiska IDE lub środowisko programistyczne, może się okazać, instalowania jednego z następujących rozszerzeń, które są pomocne:

- [Emacs: emulacji](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation )
- [Klawisze dostępu dla programu Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Poniżej przedstawiono popularne skróty programu Visual Studio. Zauważ, że niektóre rozszerzenia usunięcia powiązania powiązań kluczy programu Visual Studio domyślne i należy przywrócić powiązania klawiszy użycie poniższych poleceń. Aby przywrócić ustawienia domyślne programu Visual Studio z powiązań kluczy, przejdź do **Narzędzia > Import i eksport ustawień > zresetować wszystkie ustawienia**.

| Skrót (wszystkie profile) | Polecenie | Opis |
|-|-|-|
| **Ctrl+T** | Przejdź do wszystkich | Przejdź do dowolnego pliku/typu/elementu członkowskiego/symbol deklaracji |
| **F12** (również **kliknij z wciśniętym**) | Przejdź do definicji | Przejdź do których jest zdefiniowany symbol |
| **Ctrl+F12** | Przejdź do implementacji | Przejdź z podstawowego typu lub elementu członkowskiego do jej różnych implementacji |
| **Shift+F12** | Znajdź wszystkie odwołania | Zobacz wszystkie symbolu lub literału odwołań |
| **Ctrl**+**.** (również **Alt + wprowadź** w profilu C#) | Szybkie akcje i operacje refaktoryzacji | Zobacz, jaki kod poprawki, akcje generowania kodu, refaktoryzacje lub innych szybkie akcje są dostępne pod adresem wybór pozycji lub kod kursora |
| **CTRL**+**E**,**V** | Zduplikowany wiersz | Duplikaty wiersz kodu, w którym znajduje się kursor (dostępne w **programu Visual Studio 2017 wersji 15,6 preview 2** i nowsze) |
| **Ctrl+Q** | Szybkie uruchamianie | Wyszukaj wszystkie ustawienia programu Visual Studio |
| **F5** | Rozpocznij debugowanie | Rozpocznij debugowanie aplikacji |
| **Ctrl+F5** | Uruchom bez debugowania | Uruchamianie aplikacji lokalnie bez debugowania |
| **CTRL + K, D** (profil domyślny) lub **Ctrl + E, D** (profil C#) | Format dokumentu | Czyści formatowanie naruszeń w pliku są oparte na nowym wierszem, odstępy i ustawienia wcięć |
| **CTRL +\\, E** (profil domyślny) lub **Ctrl + W, E** (profil C#) | Widok listy błędów | Zobacz wszystkie błędy w dokumencie, projektu lub rozwiązania |