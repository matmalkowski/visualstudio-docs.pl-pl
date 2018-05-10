---
title: Okno polecenia
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.CommandWindow
helpviewer_keywords:
- IDE, Command window
- Mark mode in Command window
- Command window
- Command mode in Command window
- IDE Command window
ms.assetid: 48711628-1909-4713-a73e-d7b714c77f8a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6594b87ad313b7f452f579059af377e6128a887a
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="command-window"></a>Okno polecenia
**Polecenia** okna jest używany do wykonywania poleceń ani aliasów bezpośrednio w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE). W żadnym menu mogą wykonywać zarówno poleceń menu i poleceń, które nie są wyświetlane. Aby wyświetlić **polecenia** okna, wybierz **inne okna** z **widoku** menu, a następnie wybierz **okno polecenia**.

## <a name="displaying-the-values-of-variables"></a>Wyświetlanie wartości zmiennych
 Aby sprawdzić wartość zmiennej `varA`, użyj [polecenia Drukuj](../../ide/reference/print-command.md):

```cmd
>Debug.Print varA
```

 Znak zapytania (?) jest aliasem `Debug.Print`, dlatego to polecenie może być także zapisane:

```cmd
>? varA
```

 Obie wersje to polecenie zwróci wartość zmiennej `varA`.

## <a name="entering-commands"></a>Wprowadzanie polecenia
 Im większa niż symbol (`>`) jest wyświetlany przy lewej krawędzi okna wiersza polecenia, jako wiersz dla nowych wierszy. Użyj klawiszy Strzałka w górę i Strzałka w dół, aby przewijać wcześniej wydanych poleceń.

|Zadanie|Rozwiązanie|Przykład|
|----------|--------------|-------------|
|Obliczyć wyrażenia.|Należy poprzedzić wyrażenia znakiem zapytania (`?`).|`? myvar`|
|Przełącz do okna bezpośredniego.|Wprowadź `immed` do okna bez oznacza większe znak większości (>)|`immed`|
|Przejdź do okna poleceń w oknie bezpośrednim.|Wprowadź `cmd` do okna.|`>cmd`|

 Następujące skróty pomóc Przejdź w trybie polecenia.

|Akcja|Lokalizacja kursora|Keybinding|
|------------|---------------------|----------------|
|Przełączanie po kolei listę poleceń, wprowadzony wcześniej.|Wierszu danych wejściowych|&AMP; STRZAŁKA W DÓŁ STRZAŁKA W GÓRĘ|
|Przewiń w górę okna.|Zawartość okna polecenia|CTRL + STRZAŁKA W GÓRĘ|
|Przewiń w dół okna.|Zawartość okna polecenia|Strzałka w dół lub CTRL + Strzałka w dół|

> [!TIP]
> Całość lub część poprzednie polecenie można skopiować do wierszu danych wejściowych przewijanie do niego, wyróżnianie całości lub części, a następnie naciskając klawisz ENTER.


## <a name="mark-mode"></a>Tryb oznaczania
 Po kliknięciu dowolnej poprzedniego wiersza w **polecenia** okna, następuje przejście automatycznie w trybie znaku. Dzięki temu można wybrać, edytowania i skopiować tekst powyższych poleceń w edytorze tekstu i wklej je do bieżącego wiersza.

## <a name="the-equals--sign"></a>Znak równości (=)
 Okno służy do wprowadzania `EvaluateStatement` polecenie Określa, czy znak równości (=) jest interpretowany jako operator porównania lub operator przypisania.

 W **polecenia** okna, znak równości (=) jest interpretowana jako operator porównania. Nie można używać operatorów przypisania w **polecenia** okna. Na przykład, jeśli wartości zmiennych `varA` i `varB` są różne, a następnie polecenie `>Debug.EvaluateStatement(varA=varB)` zwróci wartość `False`.

 W **Immediate** okna, natomiast znak równości (=) jest interpretowana jako operatora przypisania. Tak, na przykład polecenie `>Debug.EvaluateStatement(varA=varB)` przypisze do zmiennej `varA` wartość zmiennej `varB`.

## <a name="parameters-switches-and-values"></a>Parametry, przełączniki i wartości
 Niektóre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] polecenia mają odpowiednie polecenia i argumentów opcjonalnych, przełączniki i wartości. Niektóre zasady mają zastosowanie podczas pracy z tych poleceń. Oto przykład poleceniu sformatowanego wyjaśnienie terminologii.

```cmd
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar
```

 W tym przykładzie

-   `Edit.ReplaceInFiles` to polecenie

-   `/case` i `/pattern:regex` parametry (poprzedzone znakiem ukośnika [/])

-   `regex` jest to wartość `/pattern` przełączyć; `/case` przełącznik nie ma wartości

-   `var[1-3]+` i `oldpar` parametrów

    > [!NOTE]
    >  Polecenie, parametr, przełącznika lub wartość zawierająca spacje musi mieć podwójny cudzysłów po obu stronach.

Pozycja przełączników i parametry mogą być stosowane zamiennie za darmo w wierszu polecenia, z wyjątkiem produktów [powłoki](../../ide/reference/shell-command.md) polecenia, które wymaga jego przełączników i parametrów w określonej kolejności.

Niemal każdy przełącznik obsługiwane przez polecenie ma dwie formy: formularza (jeden znak) krótkich i długich fragmentów. W grupie można łączyć wielu przełącznikach krótkiej postaci. Na przykład `/p /g /m` mogą być również wyrażone jako `/pgm`.

Jeśli przełączniki skróconej są łączone w grupy i określoną wartość tej wartości ma zastosowanie do każdego przełącznika. Na przykład `/pgm:123` jest równa `/p:123 /g:123 /m:123`. Błąd występuje, gdy dowolne przełączników w grupie nie akceptuje wartości.

## <a name="escape-characters"></a>Znaki specjalne
 Daszek (^) znaku w wierszu polecenia oznacza, że znak natychmiast po jej jest interpretowany jako literału, a nie jako znak kontrolny. Może być używany do osadzania cudzysłowy proste ("), spacji, wiodącego ukośniki, daszka lub innych literał znaków w wartości parametru lub przełącznikiem, z wyjątkiem nazwy przełącznika. Na przykład

```cmd
>Edit.Find ^^t /regex
```

 Daszek działa tak samo, czy wewnętrznej lub zewnętrznej znaki cudzysłowu. Jeśli daszek jest ostatni znak w wierszu, zostanie zignorowany. Tu przykładzie pokazano, jak wyszukać wzorzec "^ t".

## <a name="use-quotes-for-path-names-with-spaces"></a>Użycie cudzysłowu dla nazwy ścieżki zawierające spacje
 Jeśli na przykład chcesz otworzyć plik, który ma ścieżkę zawierających spacje, możesz umieścić cudzysłowów wokół ścieżki lub segment ścieżki, która zawiera spacje: **C:\\"Program Files"** lub **"C:\Program Files"**.

## <a name="see-also"></a>Zobacz też

- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)