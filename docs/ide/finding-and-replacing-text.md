---
title: Znajdź i Zamień tekst
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- Find in Files dialog box
- text searches, finding and replacing text
- text, finding and replacing
- find and replace
- find text
- replace text
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c8e0ec78153f7b6fdf0a9f673938a361619f2c2
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="find-and-replace-text"></a>Znajdź i Zamień tekst

Można znaleźć i zastępowanie tekstu w edytorze programu Visual Studio przy użyciu [Znajdź i Zamień](#find-and-replace-control) lub [Znajdź/Zamień w plikach](#find-replace-in-files).

> [!TIP]
> Jeśli zmieniasz kod symbole, na przykład zmienne i metody, lepiej jest *[zrefaktoryzuj](../ide/reference/rename.md)* ich niż korzystać Znajdź i Zamień. Refaktoryzacja jest inteligentnego i rozumie zakresu, Znajdź i Zamień ślepo zastępuje wszystkie wystąpienia.

Funkcje Znajdź i zamień są dostępne w edytorze, w niektórych tekstowych windows takich jak **znaleźć wyników** systemu windows w projektanta systemu windows, takich jak projektanta XAML i Projektant formularzy systemu Windows i okien narzędzi.

Można określić zakres wyszukiwania do bieżącego dokumentu, bieżące rozwiązanie lub niestandardowy zestaw folderów. Można również określić zestaw rozszerzeń nazw plików do wyszukiwania wielu plików. Dostosowywanie składni wyszukiwania przy użyciu programu .NET [wyrażeń regularnych](../ide/using-regular-expressions-in-visual-studio.md).

> [!TIP]
> [Find/Command](../ide/find-command-box.md) pole jest dostępna jako formantu paska narzędzi, ale nie jest wyświetlany domyślnie. Aby wyświetlić **Find/Command** wybierz opcję **Dodaj lub usuń przyciski** na **standardowe** narzędzi, a następnie wybierz **znaleźć**.

## <a name="find-and-replace-control"></a>Znajdź i Zamień formantu

**Znajdź i Zamień** formant jest widoczny w prawym górnym rogu okna edytora kodu. **Znajdź i Zamień** kontroli natychmiast prezentuje wszystkie wystąpienia podanego ciągu w bieżącym dokumencie. Można przechodzić z jednego wystąpienia na inny, wybierając **Znajdź następny** przycisk lub **Znajdź poprzednie** przycisku kontrolki wyszukiwania.

![Znajdź i Zamień formantu](media/find-and-replace-box.png)

Dostępne opcje zastępowania wybierając przycisk Dalej, aby **znaleźć** pola tekstowego. Aby jedno zastąpienie w czasie, wybierz polecenie **Zastąp dalej** znajdujący się obok **Zastąp** pola tekstowego. Aby zastąpić wszystkie dopasowania, wybierz **Zamień wszystkie** przycisku.

Aby zmienić kolor wyróżnienia dopasowań, wybierz **narzędzia** menu, wybierz opcję **opcje**, a następnie wybierz pozycję **środowiska**i wybierz **czcionki i kolory** . W **Pokaż ustawienia dla** listy, wybierz **Edytor tekstu**, a następnie w **wyświetlania elementów** listy, wybierz **znaleźć Wyróżnij (rozszerzenie)**.

### <a name="search-tool-windows"></a>Okna narzędzi wyszukiwania

Można użyć **znaleźć** kontroli kodu lub tekstu systemu Windows, takich jak **dane wyjściowe** systemu windows i **znaleźć wyników** systemu windows, wybierając **Edytuj**  >  **Znajdź i Zamień** lub naciskając klawisz **Ctrl + F**.

Wersja **znaleźć** kontroli jest również dostępna w niektórych okien narzędzi. Na przykład można filtrować na liście kontrolek w **przybornika** okna, wpisując tekst w polu wyszukiwania. Inne okna narzędzi, które umożliwiają wyszukiwanie ich zawartość obejmują **Eksploratora rozwiązań**, **właściwości** okno i **Team Explorer**.

## <a name="find-in-files-and-replace-in-files"></a>Znajdź w plikach i Zamień w plikach

**Znajdź/Zamień w plikach** działa, takich jak **Znajdź i Zamień** kontrolować, z wyjątkiem tego, że można zdefiniować zakres wyszukiwania. Nie można wyszukać bieżący plik otwarty w edytorze, tylko również otwarte dokumenty, całe rozwiązanie, bieżącego projektu i wybrać folder zestawów. Można także przeszukać przez rozszerzenie nazwy pliku. Aby uzyskać dostęp do **Znajdź/Zamień w plikach** okno dialogowe, wybierz opcję **Znajdź i Zamień** na **Edytuj** menu lub naciśnij klawisz **Ctrl + Shift + F**.

![Znajdź w plikach — Okno dialogowe](media/find-in-files-box.png)

### <a name="find-results"></a>Wyniki Znajdź

Po wybraniu **Znajdź wszystkie**, **znaleźć wyników** okno otwiera i lista pasujących do wyszukiwania. Wybieranie wynik na liście Wyświetla plik skojarzony i zaznacza dopasowania. Jeśli plik nie jest już otwarty do edycji, jest otwierany na karcie podglądu po prawej stronie karty oraz. Można użyć **znaleźć** formantu do przeszukiwania **znaleźć wyników** listy.

### <a name="create-custom-search-folder-sets"></a>Utwórz zestawy folder wyszukiwania niestandardowego

Można zdefiniować zakres wyszukiwania, wybierając **wybierz foldery wyszukiwania** przycisk (prawdopodobnie **...** ) obok pozycji **Szukaj w** pole. W **wybierz foldery wyszukiwania** okno dialogowe, można określić zestaw folderów wyszukiwania i można zapisać specyfikację, dzięki czemu można używać go później.

> [!TIP]
> Jeśli zamapowany dysk na maszynie zdalnej na komputerze lokalnym, można określić folderów do wyszukiwania na komputerze zdalnym.

### <a name="create-custom-component-sets"></a>Tworzenie zestawów niestandardowych składników

Ustawia składnika można zdefiniować jako zakres wyszukiwania, wybierając **edytowanie zestawu składnika niestandardowe** znajdujący się obok **Szukaj w** pole. Można określić zainstalowanych .NET lub COM składników, projektów programu Visual Studio, które znajdują się w rozwiązaniu lub żadnej biblioteki zestawu lub typu (*.dll*, *.tlb*, *.olb*, *.exe*, lub *.ocx*). Aby przeszukać odwołania, zaznacz **Szukaj w odwołaniach** pole.

## <a name="see-also"></a>Zobacz także

- [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
- [Zrefaktoryzuj kod w programie Visual Studio](../ide/refactoring-in-visual-studio.md)