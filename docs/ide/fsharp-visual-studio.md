---
title: 'Narzędzia języka F #'
description: 'Dowiedz się, które funkcje programu Visual Studio są obsługiwane w F #.'
ms.date: 07/11/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- F# features [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 938beef8676901c385ef7cc7c07b9ce0d52067c3
ms.sourcegitcommit: c87b0d9f65dc7ebe95071f66ea8da4d4bc52d360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2018
ms.locfileid: "38993905"
---
# <a name="develop-with-visual-f-in-visual-studio"></a>Programowanie za pomocą programu Visual F # w programie Visual Studio

Ten artykuł zawiera informacje o funkcjach programu Visual Studio do tworzenia aplikacji F #.

## <a name="install-f-support"></a>Instalowanie obsługi języka F #

Aby opracować z F # w programie Visual Studio, należy najpierw zainstalować **programowanie aplikacji klasycznych dla platformy .NET** obciążenia, jeśli jeszcze go. Instalowanie programu Visual Studio obciążeń za pośrednictwem Instalator programu Visual Studio, który można otworzyć, wybierając **narzędzia** > **Pobierz narzędzia i funkcje**.

![Obciążenie programowanie aplikacji klasycznych dla platformy .NET w programie Visual Studio](media/dotnet-desktop-development-workload.png)

## <a name="f-project-features"></a>Funkcje projektu F #

Różnych szablonów projektów i elementów są dostępne w języku F # w programie Visual Studio. Na poniższej ilustracji przedstawiono niektóre szablony projektu języka F # dla platformy .NET Core i .NET Standard:

![Szablony projektu języka F # w programie Visual Studio](media/fsharp-project-templates.png)

Na poniższej ilustracji przedstawiono niektóre szablony elementów języka F #:

![Szablony elementów języka F # w programie Visual Studio](media/fsharp-item-templates.png)

Aby uzyskać więcej informacji na temat szablonów elementów, aby uzyskać dostęp do danych, zobacz [dostawcy typów F #](/dotnet/fsharp/tutorials/type-providers/index).

W poniższej tabeli podsumowano funkcje we właściwościach projektu dla języka F #:

|Ustawienia projektu|Obsługiwane w F #?|Uwagi|
|---------------|----------------|-----|
|Pliki zasobów|Tak||
|Odwołanie do ustawienia, debugowania i kompilacji|Tak||
|Wielowersyjność kodu|Tak||
|Ikony i manifestu|Nie|Dostępne opcje wiersza polecenia kompilatora.|
|Usługi klienta programu ASP.NET|Nie||
|ClickOnce|Nie|W innym języku .NET Framework, należy użyć projektu klienta, jeśli ma to zastosowanie.|
|Silne nazewnictwo|Nie|Dostępne opcje wiersza polecenia kompilatora.|
|Zestaw publikowania i przechowywania wersji|Nie||
|Analiza kodu|Nie|Narzędzia do analizy kodu można uruchomić ręcznie lub jako część polecenia po kompilacji.|
|Zabezpieczenia (zmiana poziomów zaufania)|Nie||

## <a name="project-designer"></a>Projektant projektu

**Projektant projektu** składa się z kilku stron właściwości projektu, pogrupowane według pokrewne funkcje. Stron, które są dostępne dla projektów języka F # są głównie podzbiór tych, które są dostępne dla innych języków i są opisane w poniższej tabeli. Linki zostały podane dla odpowiedniego języka C# **projektanta projektu** strony.

|Strona projektanta projektu|Linki pokrewne|Opis|
|---------------------|-------------|-----------|
|Aplikacja|[Strona aplikacji, Projektant projektu](reference/application-page-project-designer-csharp.md)|Umożliwia określenie ustawień na poziomie aplikacji i właściwości, takie jak tego, czy tworzysz bibliotekę lub plik wykonywalny, jakiej wersji programu .NET Framework jest przeznaczony dla aplikacji i informacje o którym zasobu pliki aplikacji zastosowań są przechowywane.|
|Kompilacja|[Strona, Projektant projektu kompilacji](reference/build-page-project-designer-csharp.md)|Umożliwia kontrolowanie sposobu kompilowania kodu.|
|Zdarzenia kompilacji|[Strona zdarzenia, Projektant projektu kompilacji](reference/build-events-page-project-designer-csharp.md)|Pozwala określić polecenie do uruchomienia przed lub po kompilacji.|
|Debugowanie|[Strona debugowania, Projektant projektu](reference/debug-page-project-designer.md)|Można kontrolować, jak aplikacja zostanie uruchomiona podczas debugowania. Obejmuje to, co polecenia i co na uruchamianie aplikacji, że katalog jest i wszelkie specjalne trybów debugowania, który chcesz włączyć, takich jak SQL i kodu natywnego.|
|Pakiet (tylko zestaw SDK platformy .NET)|Brak|Umożliwia zdefiniowanie metadanych pakietu NuGet, podczas publikowania jako pakiet NuGet.|
|Ścieżki odwołania|[Zarządzanie odwołaniami w projekcie](managing-references-in-a-project.md)|Pozwala określić, gdzie do przeszukania pod kątem zestawów, który zależy od kodu.|
|Zasoby (tylko zestaw SDK platformy .NET)|Brak|Umożliwia generowanie i zarządzanie nimi domyślnego pliku zasobów.|

### <a name="f-specific-settings"></a>F #-konkretne ustawienia

Poniższa tabela zawiera podsumowanie ustawień, które są specyficzne dla języka F #:

|Strona projektanta projektu|Ustawienie|Opis|
|---------------------|-------|-----------|
|Kompilacja|Generuj wywołania zakończenia|Jeśli zaznaczone, umożliwia korzystanie z fragmentarycznej instrukcji Microsoft Intermediate Language (MSIL). Powoduje to ramek stosu, można użyć ponownie dla funkcji cyklicznych. Odpowiednikiem `--tailcalls` — opcja kompilatora.|
|Kompilacja|Inne flagi|Pozwala określić opcje wiersza polecenia kompilatora dodatkowe.|

## <a name="code-and-text-editor-features"></a>Funkcje edytora kodu i tekstu

Następujące funkcje edytory kodu i tekstu programu Visual Studio są obsługiwane w F #:

|Funkcja|Opis|Obsługiwane w F #?|
|-------|-----------|----------------|
|Automatycznie komentarz|Można dodać komentarz lub usuń znaczniki komentarza sekcje kodu.|Tak|
|Automatycznie Formatuj|Formatuje kodu za pomocą standardowych wcięcia i stylu.|Nie|
|Zakładki|Umożliwia zapisanie miejsc w edytorze.|Tak|
|Zmiana wcięcia|Wcięcia lub usuwa wcięcia w zaznaczonych wierszach.|Tak|
|Inteligentne wcięcie|Automatycznie wcięcia i cofnąć wcięcia kursora zgodnie z regułami zakresu F #.|Tak|
|[Znajdowanie i zastępowanie tekstu](finding-and-replacing-text.md)|Umożliwia wyszukiwanie w pliku, projekt lub rozwiązanie i potencjalnie zmiana tekstu.|Tak|
|Przejdź do definicji interfejsu API programu .NET Framework|Gdy kursor znajduje się na interfejs API programu .NET Framework, zawiera kod generowany z .NET Framework — metadane.|Nie|
|Przejdź do definicji dla użytkownika z interfejsu API|Gdy kursor znajduje się w jednostce program, który zdefiniowano, przenosi kursor do lokalizacji w kodzie, w której jednostka została zdefiniowana.|Tak|
|Przejdź do wiersza|Umożliwia przejście do określonego wiersza w pliku przez numer wiersza.|Tak|
|Paski nawigacji u góry pliku|Można przejść do lokalizacji w kodzie, na przykład nazwę funkcji.|Tak|
|Wskazówki dotyczące struktury bloku|Zawiera wskazówki, które wskazują F # zakresy, które mogą być najechania kursorem dla wersji zapoznawczej.|Tak|
|[Obramowanie](outlining.md)|Umożliwia zwijanie sekcji kodu, aby utworzyć bardziej zwarty.|Tak|
|Zmień spacje na tabulatory|Konwertuje spacje na znaki tabulacji.|Tak|
|Kolorowanie typów|Pokazuje zdefiniowane nazwy typów w kolorze specjalne.|Tak|
|Szybkie wyszukiwanie. Zobacz Szybkie szukanie, znajdowanie i zamienianie okna.|Umożliwia wyszukiwanie pliku lub projektu.|Tak|
|**CTRL**+**kliknij** do przejdź do definicji|Służy do przechowywania **Ctrl** i kliknij symbol F # do wywołania, przejdź do definicji.|Tak|
|Przejdź do definicji z sekcji szybkich informacji|Możesz klikać symbole wewnątrz etykietki narzędzi, które wywoływać przejdź do definicji.|Tak|
|Przejdź do wszystkich|Umożliwia globalny, dopasowywania rozmytego nawigacji dla wszystkich konstrukcji F # za pomocą **Ctrl**+**T**.|Tak|
|Zmiany nazwy wstawionego elementu|Zmienia nazwę wszystkich wystąpień elementu wbudowanego symboli.|Tak|
|Znajdź wszystkie odwołania|Umożliwia znalezienie wszystkich wystąpień symbolu w bazie kodu.|Tak|
|Uprość nazwy poprawki kodu|Usuwa niepotrzebne kwalifikatory dla symboli, F #.|Tak|
|Usuń nieużywane `open` poprawki kodu — instrukcja|Usuwa wszystkie zbędne `open` instrukcje w dokumencie.|Tak|
|Poprawka kodu nieużywanych wartości|Sugeruje, zmiana nazwy nieużywany identyfikator, aby znaku podkreślenia.|Tak|

Aby uzyskać ogólne informacje na temat edytowania kodu w programie Visual Studio i funkcje edytora tekstu, zobacz [pisanie kodu w edytorze](writing-code-in-the-code-and-text-editor.md).

## <a name="intellisense-features"></a>Funkcje IntelliSense

W poniższej tabeli podsumowano funkcje IntelliSense obsługiwane i nieobsługiwane w języku F #:

|Funkcja|Opis|Obsługiwane w F #?|
|-------|-----------|----------------|
|Automatycznie implementować interfejsów|Generuje kod wycinków dla metod interfejsu.|Tak|
|Fragmenty kodu|Wprowadza kod z biblioteki typowe konstrukcje programowania na tematy.|Nie|
|Dokończ wyraz|Zapisuje wpisywanie, wykonując słów i nazwy podczas wpisywania.|Tak|
|Automatyczne uzupełnianie|Po włączeniu powoduje, że uzupełnianie wyrazów, zaznacz pierwsze dopasowanie, podczas wpisywania, zamiast czekać, aż można wybrać jedną lub naciśnij **Ctrl**+**miejsca**.|Tak|
|Zakończenie oferty dla symboli w nieotwartych przestrzeniach nazw|Za pomocą automatycznego uzupełniania pasującego symbol, który znajduje się w przestrzeni nazw usługi nieotwarte jest zalecane, oferty, można wykonać przy użyciu odpowiednich `open` instrukcji po wybraniu.|Tak|
|Generuj elementy kodu|Umożliwia generowanie kodu klasy zastępczej dla różnych konstrukcji.|Nie|
|Lista składników|Podczas wpisywania tekstu operator dostępu do elementów członkowskich (.), zawiera elementy członkowskie typu.|Tak|
|Organizowanie deklaracje Using/Otwórz|Organizuje przestrzenie nazw odwołuje się **przy użyciu** instrukcji w języku C# lub **Otwórz** dyrektywy w języku F #.|Nie|
|Informacje o parametrach|Zawiera przydatne informacje dotyczące parametrów podczas wpisywania wywołania funkcji.|Tak|
|Szybkie informacje|Wyświetla pełną deklarację dla każdego identyfikatora w kodzie.|Tak|
|Automatyczne uzupełnianie nawiasów|W sposób transakcyjny, automatycznie wypełnia F # w nawias klamrowy składni konstrukcji.|Tak|

Aby uzyskać ogólne informacje na temat technologii IntelliSense, zobacz [IntelliSense użyj](using-intellisense.md).

## <a name="debugging-features"></a>Funkcje debugowania

W poniższej tabeli podsumowano funkcje, które są dostępne podczas debugowania kodu F #:

|Funkcja|Opis|Obsługiwane w F #?|
|-------|-----------|----------------|
|okno zmiennych automatycznych|Pokazuje zmienne automatyczne lub tymczasowego.|Nie|
|Punkty przerwania|Można wstrzymać wykonanie kodu w określonych punktach podczas debugowania.|Tak|
|Warunkowe punkty przerwania|Umożliwia punktów przerwania, warunek, który określa, czy należy wstrzymać wykonywania testu.|Tak|
|Edytuj i kontynuuj|Umożliwia kodu można modyfikować i skompilowany podczas debugowania uruchomiony program bez zatrzymywania i ponownego uruchamiania debugera.|Nie|
|Ewaluator wyrażeń|Oblicza i wykonuje kod w czasie wykonywania.|Nie, ale języka C# Ewaluator wyrażeń mogą być używane, ale należy użyć składni języka C#.|
|Debugowanie historyczne|Można przejść do wcześniej wykonywany kod.|Tak|
|okno zmiennych lokalnych|Pokazuje lokalnie zdefiniowane wartości oraz zmienne.|Tak|
|Uruchom do kursora|Umożliwia wykonanie kodu, aż do osiągnięcia wiersz zawierający kursor.|Tak|
|Wkrocz|Pozwala na wcześniejsze wykonanie i Przenieś do dowolnej wywołania funkcji.|Tak|
|Przekrocz nad|Pozwala na wcześniejsze wykonanie w bieżącej ramki stosu i przejścia za każde wywołanie funkcji.|Tak|

Aby uzyskać ogólne informacje o debugerze programu Visual Studio, zobacz [debugowania w programie Visual Studio](../debugger/index.md).

## <a name="additional-tools"></a>Dodatkowe narzędzia

Poniższa tabela zawiera podsumowanie obsługi F # w programie Visual Studio tools.

|Narzędzie|Opis|Obsługiwane w F #?|
|----|-----------|----------------|
|Hierarchia wywołań|Wyświetla struktury zagnieżdżonej funkcji wywołania w kodzie.|Nie|
|Metryki kodów|Zbiera informacje o swoim kodzie, takie jak liczba linii.|Nie|
|Widok klas|Zapewnia widok na podstawie typu kodu w projekcie.|Nie|
|[Okno listy błędów](reference/error-list-window.md)|Zawiera listę błędów w kodzie.|Tak|
|[F# Interactive](/dotnet/fsharp/tutorials/fsharp-interactive/)|Umożliwia typu (lub skopiować i wkleić) F # kodu i natychmiastowe jego uruchomienie, niezależnie od tworzenia projektu. Okno F # Interactive jest Odczyt, oceń, drukowania pętli (REPL).|Tak|
|Przeglądarka obiektów|Umożliwia wyświetlanie typów w zestawie.|Typy F # w jakiej występują w skompilowanych zestawach nie są wyświetlane dokładnie tak, jak je tworzyć. Możesz przeglądać skompilowanych reprezentacja typów F #, ale nie można wyświetlić typy, w jakiej występują w F #.|
|[Okno danych wyjściowych](reference/output-window.md)|Wyświetla dane wyjściowe kompilacji.|Tak|
|Analiza wydajności|Udostępnia narzędzia do pomiaru wydajności kodu.|Tak|
|Okno właściwości|Wyświetla i umożliwia edytowanie właściwości obiektu w środowisku programistycznym, który ma fokus.|Tak|
|Server Explorer|Zapewnia sposoby interakcji z różnych zasobów serwera.|Tak|
|Eksplorator rozwiązań|Umożliwia wyświetlanie i zarządzanie nimi, projektów i plików.|Tak|
|Lista zadań|Umożliwia zarządzanie elementami roboczymi odnoszących się do kodu.|Nie|
|Projekty testowe|Oferuje funkcje, które pomagają testować kod.|Nie|
|Przybornik|Wyświetla karty zawierające przeciąganego obiekty, takie jak formanty i części tekstu lub kodu.|Tak|

## <a name="see-also"></a>Zobacz także

- [Podręcznik języka F # (.NET Framework)](/dotnet/fsharp/)
- [Wprowadzenie do F # w programie Visual Studio](/dotnet/fsharp/get-started/get-started-visual-studio)