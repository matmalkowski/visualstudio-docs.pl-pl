---
title: Visual Studio — Polecenia
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Visual Studio, commands
- commands, Visual Studio
- command syntax
ms.assetid: 76ffa394-ee89-4629-aba9-1a62b72e6cc1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f124ccc0a4eb7af470a9631bc2291dbeb089711e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31951794"
---
# <a name="visual-studio-commands"></a>Visual Studio — Polecenia
Visual Studio — polecenia umożliwiają Wywołaj polecenie z **polecenia** okna, **Immediate** okna, lub **Find/Command** pole. W każdym przypadku oznacza większe niż znak (`>`) służy do wskazywania polecenia, a nie operacji wyszukiwania lub debugowania do wykonania.

 Pełną listę poleceń i ich składni w można znaleźć **klawiatura, środowisko, opcje** okno dialogowe.

 Znak ucieczki dla programu Visual Studio — polecenia jest znakiem daszek (^), co oznacza, że znak natychmiast po jej jest interpretowany jako literału, a nie jako znak kontrolny. Może być używany do osadzania cudzysłowy proste ("), spacji, wiodącego ukośniki, daszka lub innych literał znaków w wartości parametru lub przełącznikiem, z wyjątkiem nazwy przełącznika. Na przykład

```
>Edit.Find ^^t /regex
```

 Daszek działa tak samo, czy wewnętrznej lub zewnętrznej znaki cudzysłowu. Jeśli daszek jest ostatni znak w wierszu, zostanie zignorowany.

 Zlokalizowane wersje środowiska IDE nazw poleceń można podać w języku macierzystym IDE lub w języku angielskim. Na przykład można wpisać albo `File.NewFile` lub `Fichier.NouveauFichier` w IDE francuskim, do wykonania tego samego polecenia.

 Wiele poleceń ma aliasów. Aby uzyskać listę aliasy poleceń, zobacz [programu Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md).

 Następujące polecenia zająć argumentów lub przełączników.

|Nazwa polecenia|Opis|
|------------------|-----------------|
|[Dodaj istniejący element](../../ide/reference/add-existing-item-command.md)|Dodaje istniejący plik do bieżącego rozwiązania, a następnie go otwiera.|
|[Dodaj istniejący projekt](../../ide/reference/add-existing-project-command.md)|Dodaje istniejący projekt do bieżącego rozwiązania.|
|[Dodaj nowy element](../../ide/reference/add-new-item-command.md)|Dodaje nowy element rozwiązania, takie jak htm, CSS, txt lub ramek do obecnego rozwiązania, a następnie go otwiera.|
|[Alias](../../ide/reference/alias-command.md)|Tworzy nowy alias pełne polecenie, pełny polecenia i argumentów lub nawet inny alias.|
|[Ocena — instrukcja](../../ide/reference/evaluate-statement-command.md)|Oblicza i wyświetla podanej instrukcji.|
|[Znajdź](../../ide/reference/find-command.md)|Wyszukuje pliki przy użyciu podzbiór opcje dostępne na **Znajdź i Zamień** formantu.|
|[Znajdź w plikach](../../ide/reference/find-in-files-command.md)|Wyszukuje pliki przy użyciu podzbiór opcje dostępne na [Znajdź w plikach](../../ide/find-in-files.md).|
|[Przejdź do](../../ide/reference/go-to-command.md)|Przesuwa kursor do określonego wiersza.|
|[Lista stosu wywołań](../../ide/reference/list-call-stack-command.md)|Wyświetla bieżący stos wywołań.|
|[Lista dezasemblacji](../../ide/reference/list-disassembly-command.md)|Rozpoczyna się proces debugowania i pozwala określić sposób obsługi błędów.|
|[Lista pamięci](../../ide/reference/list-memory-command.md)|Wyświetla zawartość z pamięci podanego zakresu.|
|[Lista modułów](../../ide/reference/list-modules-command.md)|Wyświetla listę modułów dla bieżącego procesu.|
|[Lista rejestrów](../../ide/reference/list-registers-command.md)|Zostanie wyświetlona lista rejestrów.|
|[Źródło listy](../../ide/reference/list-source-command.md)|Wyświetla określony wiersze kodu źródłowego.|
|[Lista wątków](../../ide/reference/list-threads-command.md)|Wyświetla listę wątki bieżącego programu.|
|[Dane wyjściowe okna polecenie dziennika](../../ide/reference/log-command-window-output-command.md)|Kopie wszystkich danych wejściowych i dane wyjściowe z okna wiersza polecenia do pliku.|
|[Nowy plik](../../ide/reference/new-file-command.md)|Tworzy nowy plik i dodaje go do aktualnie wybranego projektu.|
|[Otwórz plik](../../ide/reference/open-file-command.md)|Otwiera istniejący plik i umożliwia określenie edytora.|
|[Otwórz projekt](../../ide/reference/open-project-command.md)|Otwiera istniejący projekt i pozwala na dodawanie projektu do bieżącego rozwiązania.|
|[Otwórz rozwiązanie](../../ide/reference/open-solution-command.md)|Otwiera istniejącego rozwiązania.|
|[Drukuj](../../ide/reference/print-command.md)|Oblicza wyrażenie i wyświetla wyniki lub określony tekst.|
|[Szybka czujka, polecenie](../../ide/reference/quick-watch-command.md)|Wyświetla wybrany lub określony tekst w **wyrażenie** pole **Szybka czujka** okno dialogowe.|
|[Zamień](../../ide/reference/replace-command.md)|Zamienia tekst w plikach za pomocą podzbiór opcje dostępne na **Znajdź i Zamień** formantu.|
|[Zastąp w plikach](../../ide/reference/replace-in-files-command.md)|Zamienia tekst w plikach za pomocą podzbiór opcje dostępne w [Zastąp w plikach](../../ide/replace-in-files.md).|
|[Ustaw bieżącą ramkę stosu](../../ide/reference/set-current-stack-frame-command.md)|Umożliwia wyświetlenie ramki stosu w szczególności.|
|[Ustaw bieżący wątek](../../ide/reference/set-current-thread-command.md)|Umożliwia wyświetlenie określonego wątku.|
|[Ustaw radix —](../../ide/reference/set-radix-command.md)|Określa liczbę bajtów do wyświetlenia.|
|[powłoki](../../ide/reference/shell-command.md)|Uruchamia programy z poziomu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tak, jakby polecenie zostało wykonane w wierszu polecenia.|
|[ShowWebBrowser, polecenie](../../ide/reference/showwebbrowser-command.md)|Wyświetla adres URL, określ w oknie przeglądarki sieci Web albo w ramach zintegrowane środowisko programistyczne (IDE) lub zewnętrzne względem programu IDE.|
|[Start](../../ide/reference/start-command.md)|Rozpoczyna się proces debugowania i pozwala określić sposób obsługi błędów.|
|[Path](../../ide/reference/symbol-path-command.md)|Ustawia listę katalogów dla debugera do wyszukiwania symboli.|
|[Przełącz punkt przerwania](../../ide/reference/toggle-breakpoint-command.md)|Włącza punkt przerwania lub wyłączyć, w zależności od bieżącego stanu w bieżącej lokalizacji w pliku.|
|[Czujka, polecenie](../../ide/reference/watch-command.md)|Tworzy i otwiera określone wystąpienie programu **czujki** okna.|

## <a name="see-also"></a>Zobacz też

- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)