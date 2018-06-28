---
title: Formatowanie kodu języka Python
description: Jak automatycznie sformatować kodu języka Python w programie Visual Studio, w tym odstępów, instrukcji, zawijania i komentarze.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 91a3651dcc7fd16bec2e094fd152242e67fa2d70
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056914"
---
# <a name="formatting-python-code"></a>Formatowanie kodu języka Python

Visual Studio umożliwia sformatowanie szybki kod do dopasowania wstępnie skonfigurowane opcje formatowania.

- Aby sformatować zaznaczenia: Wybierz **Edytuj > Zaawansowane > Wybieranie formatu** lub naciśnij klawisze Ctrl + E, F.
- Aby sformatować cały plik: Wybierz **Edytuj > Zaawansowane > dokumentu w formacie** lub naciśnij klawisze Ctrl + E, D.

Opcje są ustawiane za pomocą **Narzędzia > Opcje > Edytor tekstu > Python > Formatowanie** i jego zagnieżdżonych karty. Musisz wybrać **Pokaż wszystkie ustawienia** opcje te są wyświetlane:

![Opcje programu Visual Studio formatowania języka Python](media/options-editor-formatting.png)

Opcje formatowania domyślnie są ustawione na zgodne z rozszerzeniem [8 program ten przewodnik po stylu](http://www.python.org/dev/peps/pep-0008/). **Ogólne** kartę Określa, kiedy stosowane jest formatowanie; ustawienia trzy karty są opisane w tym artykule.

[Python obsługi w programie Visual Studio](installing-python-support-in-visual-studio.md) dodaje również przydatne [wypełnienia akapitu komentarz](#fill-comment-paragraph-command) polecenie **Edytuj > Zaawansowane** menu zgodnie z opisem w dalszej części artykułu.

## <a name="spacing"></a>Odstępy

**Odstępy** kontrolki, w którym spacje są wstawiane lub usunąć wokół różnych konstrukcji języka. Każda opcja charakteryzuje się trzema możliwymi wartościami:

- Zaznaczony: gwarantuje, że zastosowano odstępów.
- Wyczyszczone: usuwa wszystkie odstęp.
- Nieokreślony: pozostawia oryginalne formatowanie miejscowej.

W poniższych tabelach znajdują się przykłady dla różnych opcji:

| Opcja definicji klasy | Zaznaczone | Wyczyszczone |
| --- | --- | --- | 
| Wstaw odstęp między nazwy deklaracji klasy oraz listę typów podstawowych | `class X (object): pass` | `class X(object): pass` | 
| Wstaw spację wewnątrz nawiasów listy zasad | `class X( object ): pass` | `class X(object): pass` |
| Wstaw spację wewnątrz nawiasów listy baz pusty | `class X( ): pass` | `class X(): pass` |

<br/>

| Definicje funkcji-opcja | Zaznaczone | Wyczyszczone |
| --- | --- | --- |
| Wstaw spację między nazwę deklaracji funkcji i listy parametrów | `def X (): pass` | `def X(): pass` | 
| Wstaw spację wewnątrz nawiasów listy parametrów | `def X( a, b ): pass` | `def X(a, b): pass` |
| Wstaw spację wewnątrz nawiasów pustej listy parametrów | `def X( ): pass` | `def X(): pass` |
| Wstawiaj odstępy dookoła "=" w wartości domyślne parametrów | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| Wstaw spację przed i po operatorach adnotacji zwracanego | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| Opcja operatory | Zaznaczone | Wyczyszczone |
| --- | --- | --- |
| Wstawiaj odstępy dookoła operatorów dwuargumentowych | `a + b` | `a+b` |
| Wstawiaj odstępy dookoła przypisania | `a = b` | `a=b` |

<br/>

| Opcja Odstępy wyrażenia | Zaznaczone | Wyczyszczone |
| --- | --- | --- |
| Wstaw spację między nazwę wywołanie funkcji i listy argumentów | `X ()` | `X()` |
| Wstaw spację wewnątrz nawiasów pustej listy argumentów | `X( )` | `X()` |
| Wstaw spację wewnątrz nawiasów listy argumentów | `X( a, b )` | `X(a, b)` |
| Wstaw spację wewnątrz nawiasów wyrażenia | `( a )` | `(a)` |
| Wstaw spację wewnątrz nawiasów pusty spójnej kolekcji. | `( )` | `()` |
| Wstaw spację wewnątrz nawiasów spójnej kolekcji | `( a, b )` | `(a, b)` |
| Wstaw spację wewnątrz pustych nawiasów kwadratowych | `[ ]` | `[]` |
| Wstaw spacje wewnątrz nawiasów kwadratowych list | `[ a, b ]` | `[a, b]` |
| Wstaw spację przed otwierającym nawiasem kwadratowym | `x [i]` | `x[i]` |
| Wstaw spację wewnątrz nawiasów kwadratowych | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>Instrukcje

**Instrukcje** opcje umożliwiają kontrolowanie automatyczne ponowne zapisywanie różnych instrukcji w formularzach Pythonic więcej.

| Opcja | Przed formatowania | Po sformatowaniu |
| --- | --- | --- |
| Umieść zaimportowanych modułów w nowym wierszu | `import sys, pickle` | `import sys`<br/>`import pickle` |
| Usuń zbędne średnikami | `x = 42;` | `x = 42` |
| Umieść użycie wielu instrukcji w nowych wierszy | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |

## <a name="wrapping"></a>Zawijanie

**Zawijanie** umożliwia ustawisz **maksymalna szerokość komentarz** (wartość domyślna to 80). Jeśli **zawijać komentarze, które są zbyt szerokie** opcja jest ustawiona, komentarze, aby nie przekroczyć tego maksymalną szerokość formatuje Visual Studio.

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```

## <a name="fill-comment-paragraph-command"></a>Wypełnij polecenie Akapit komentarza

**Edytuj > Zaawansowane > wypełnienia akapitu komentarz** (Ctrl + E, P) i który formatów komentarz tekstu, łączenie krótkich wierszy ze sobą i podzielenie długo z nich.

Na przykład:

```python
# foo
# bar
# baz
```

zmiany:

```python
# foo bar baz
```

```python
# This is a very long long long long long long long long long long long long long long long long long long long comment
```

zmiany:

```python
# This is a very long long long long long long long long long long long long
# long long long long long long long comment
```
