---
title: Dodawanie obsługi innych języków edytora programu Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax colorization
- IntelliSense
- IDE, navigation
- documents [Visual Studio], navigation
- TextMate bundle
- TextMate language grammar
- language support
ms.assetid: d78c43ee-4ef2-42e5-984e-d137de4e7e92
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: f3178738b707069fdf885c9821b7b7f1e17b246c
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>Dodaj obsługę innych języków w edytorze programu Visual Studio

Więcej informacji na temat sposobu edytorze programu Visual Studio obsługuje Odczyt i nawigować przez inny komputer języków i jak dodać obsługę innych języków w edytorze programu Visual Studio.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Kolorowanie składni, uzupełnianie i przejdź do pomocy technicznej

Funkcje w edytorze programu Visual Studio, takie jak kolorowanie składni, uzupełnianie i przejdź do można umożliwiają łatwe odczytywać, tworzyć i edytować swój kod. Poniższy zrzut ekranu przedstawia przykład edycję skryptu języka Perl w programie Visual Studio. Składnia jest automatycznie pokolorowane. Na przykład uwagi w kodzie mają kolor zielony, kod jest czarny ścieżki są oznaczone kolorem czerwonym i instrukcje są niebieski. Edytor programu Visual Studio automatycznie stosuje kolorowanie składni do dowolnego języka, który go obsługuje. Ponadto po rozpoczęciu wprowadzania słowem kluczowym języka znanych lub obiekt uzupełniania Wyświetla listę możliwych instrukcje i obiektów. Uzupełnianie mogą pomóc w bardziej szybkie i łatwe tworzenie kodu.

![Kolorowanie składni w skrypcie Perl](../ide/media/vside_perledit.png "VSIDE_PerlEdit")

Program Visual Studio udostępnia obecnie kolorowanie składni i podstawowe uzupełniania obsługę następujących języków przy użyciu [Gramatyk TextMate](https://manual.macromates.com/en/language_grammars). Jeśli Twoje ulubione język nie jest w tabeli, jednak nie martw się — można go dodać.

|||||||
|-|-|-|-|-|-|
|Bat|F#|Java|Język znaczników markdown|Rdzy|Visual Basic|
|Clojure|Przejdź|JavaDoc|Objective-C|ShaderLab|C#|
|CMake|Groovy|JSON|Perl|ShellScript|Visual C++|
|CoffeeScript|HTML|MNIEJ|Python|SQL|VBNet|
|CSS|INI|LUA|R|Swift|XML|
|Docker|Jade|Wprowadź|Ruby|TypeScript|YAML|

Oprócz kolorowanie składni i uzupełniania instrukcji podstawowych programu Visual Studio ma również funkcję [przejdź do](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/). Ta funkcja pozwala na szybkie wyszukiwanie plików kodu, ścieżki do plików i symbole kodu. Visual Studio udostępnia przejdź do pomocy technicznej dla następujących języków.

-   Przejdź

-   Java

-   JavaScript

-   PHP

-   TypeScript

-   Visual Basic

-   Visual C++

-   C#

Wszystkie typy plików mają funkcje opisane wcześniej nawet wtedy, gdy obsługa danego języka nie został jeszcze zainstalowany. Instalowanie obsługi specjalne w przypadku niektórych języków może zapewnić obsługę dodatkowych języków, takie jak IntelliSense lub innych funkcji języka zaawansowanych, takich jak żarówki.

## <a name="add-support-for-non-supported-languages"></a>Dodaj obsługę języków nieobsługiwanych

Visual Studio 2015 Update 1 lub nowszym zapewniają obsługę języka w edytorze przy użyciu [Gramatyk TextMate](https://manual.macromates.com/en/language_grammars). Jeśli Twoje ulubione język programowania nie jest aktualnie obsługiwana w edytorze programu Visual Studio, najpierw wyszukać w sieci web - już istnieje w pakiecie TextMate dla języka. Jeśli nie można odnaleźć jednego, jednak można dodać obsługę samodzielnie w Visual Studio 2015 Update 1 lub później, tworząc model pakietu TextMate gramatyki języka i fragmenty kodu.

Dodaj wszystkie nowe gramatyki TextMate dla programu Visual Studio w następującym folderze:

*% userprofile %\\. vs\Extensions*

W obszarze tej ścieżki podstawowej należy dodać do następujących folderów, jeśli mają one zastosowanie do sytuacji:

|Nazwa folderu|Opis|
|-----------------|-----------------|
|\\*\<Nazwa języka >*|Folder języka. Zastąp  *\<nazwy języka >* o nazwie języka. Na przykład *\Matlab*.|
|*\Syntaxes*|Folder gramatyki. Gramatyka zawiera *JSON* , takich jak pliki w języku *Matlab.json*.|
|*\Snippets*|Folder fragmentów. Zawiera fragmenty kodu dla języka.|

W systemie Windows *% userprofile %* jest rozpoznawane jako ścieżka: *c:\Users\\\<nazwa użytkownika >*. Jeśli folder rozszerzenia nie istnieje w systemie, należy go utworzyć. Jeśli folder już istnieje, zostanie ukryta.

Aby uzyskać więcej informacji o sposobie tworzenia TextMate gramatyki, zobacz [TextMate — wprowadzenie do języka gramatyki: osadzonych sposób dodawania wyróżnianie składni kodu źródłowego w formacie HTML](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) i [uwagi dotyczące tworzenia gramatyki języka i niestandardowe Motyw dla pakietu Textmate](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle).

## <a name="see-also"></a>Zobacz także

- [Wskazówki: Tworzenie wstawek kodu](../ide/walkthrough-creating-a-code-snippet.md)
- [Wskazówki: Wyświetlanie uzupełniania](../extensibility/walkthrough-displaying-statement-completion.md)