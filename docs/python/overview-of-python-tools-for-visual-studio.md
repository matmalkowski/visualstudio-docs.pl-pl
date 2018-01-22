---
title: "Omówienie obsługi języka Python w programie Visual Studio (z systemem Windows) | Dokumentacja firmy Microsoft"
description: "Podsumowanie funkcji dostępnych dla języka Python w programie Visual Studio (znanej także jako narzędzia Python Tools for Visual Studio i narzędzi PTVS), w tym pytania i odpowiedzi (FAQ) macierz obsługi funkcji w wersjach programu Visual Studio."
ms.custom: 
ms.date: 01/09/2018
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: hero-article
caps.latest.revision: "11"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 067684c7b5064e096849afe69d2f0db1bcc75ea6
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2018
---
# <a name="working-with-python-in-visual-studio-windows"></a>Praca z języka Python w programie Visual Studio (z systemem Windows)

Python to niezawodne, elastyczne, łatwe dowiedzieć się, bez używania we wszystkich systemach operacyjnych i obsługiwanych przez społeczność deweloperów silne i wiele bibliotek wolnego popularnych język programowania. Python obsługuje wszystkie środki projektowanie, łącznie z aplikacji sieci web, usług sieci web, aplikacji klasycznych, skrypty i obliczanie naukowe i jest używany przez wiele uczelni, służące zwykłych deweloperzy i deweloperów podobne. Dodatkowe informacje na temat języka na [python.org](https://www.python.org) i [języka Python dla początkujących](https://www.python.org/about/gettingstarted/).

Program Visual Studio w systemie Windows udostępnia [open source](https://github.com/Microsoft/ptvs) obsługę języka Python za pomocą programowania Python i obciążeń nauki danych (Visual Studio 2017 r) i bezpłatne narzędzia Python Tools for Visual Studio rozszerzenia (Visual Studio 2015 i starszych). Python nie jest obecnie obsługiwany w programie Visual Studio dla komputerów Mac, ale jest dostępna w Mac i Linux za pomocą programu Visual Studio Code (zobacz [pytania i odpowiedzi](#questions-and-answers)).

Aby rozpocząć:

- Postępuj zgodnie z [instrukcje dotyczące instalacji](installing-python-support-in-visual-studio.md) do skonfigurowania obciążenia Python
- Przejdź do co najmniej jednego skróconych podręczników, aby utworzyć projekt. Jeśli masz pewności, Rozpocznij od [utworzyć projekt z szablonu](quickstart-02-project-from-template.md).
- Postępuj zgodnie z [Praca z języka Python w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) samouczka środowisko pełnej end-to-end.
- Następnie użyć łącza w poniższej tabeli, aby poznać funkcje związane z języka Python oraz możliwości programu Visual Studio, sam.

| Funkcja | Opis | Dokumentacja ogólna Visual Studio |
| --- | --- | --- |
| [Program Visual Studio system projektu](managing-python-projects-in-visual-studio.md) | Niejawnie wybiera się strukturę folderów kodu Python, umożliwiając jawne formantu do identyfikacji kodu aplikacji, kodu testowego stron sieci web, JavaScript, tworzenia skryptów, itp. | [Rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Szablony projektu](managing-python-projects-in-visual-studio.md#project-templates) | Szybko tworzy struktury projektu dla konsoli sieci web, Azure, analizy danych i innych typów projektów | [Szablony programu Visual Studio](../ide/creating-project-and-item-templates.md#visual-studio-templates) |
| Obsługa wielu interpretera | Obsługuje różne wersje języka CPython i IronPython. | n/d |
| Obsługa IPython | Obsługuje IPython/Jupyter w REPL dla powierzchni wbudowany, .NET i Windows Presentation Foundation (WPF). | n/d |
| [Edytowanie sformatowanego, IntelliSense i zrozumienia kodu](code-editing.md) | Obejmuje kolorowania składni, funkcja automatycznego uzupełniania kodu i bibliotek, [kod formatowania](code-formatting.md), pomocy podpisu, Widok klas, przejdź do definicji, Znajdź wszystkie odwołania, fragmentów kodu [refaktoryzacji](code-refactoring.md), [ PyLint](code-pylint.md)itd. | [Pisanie kodu w edytorze kodu i tekstu](../ide/writing-code-in-the-code-and-text-editor.md) |
| [Okno interaktywne](interactive-repl.md) | Zapewnia szybkie REPL dla języka Python umożliwia łatwe wyróżnianie fragment kodu i wysyłania go do okna interaktywnego. | n/d |
| [Oferujący wszystkie funkcje debugowania](debugging.md) | Debugowanie może odbywać się z lub bez projektu programu Visual Studio, w tym możliwość debugowania istniejącego pliku wykonywalnego, [debugowanie w trybie mieszanym Python/C++](debugging-mixed-mode.md), [zdalnego debugowania](debugging-cross-platform-remote.md) do systemu Windows/Linux/Mac [zdalnego debugowania na platformie Azure](debugging-azure-remote.md)i debugowanie okna interaktywnego. | [Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md) |
| [Narzędzia profilowania z raportowaniem kompleksowe](profiling.md) | Opisuje, jak jest zużywany czas w aplikacji, łącznie z możliwością porównania wydajności między cyklów profilowania. | [Narzędzia profilowania](../profiling/profiling-tools.md) (nie wszystkie funkcje profilowania programu Visual Studio są dostępne dla języka Python) |
| [Narzędzia do testowania jednostki](unit-testing.md) | Odnajdywanie, uruchamianie, zarządzania testami w Visual Studio narzędzia Eksplorator testów i łatwe debugowanie testów jednostkowych. | [Kod testu jednostkowego](../test/unit-test-your-code.md) |

Zawiera również obciążenia Python [zestaw Azure SDK for Python](azure-sdk-for-python.md), który upraszcza korzystanie z aplikacji systemu Windows, Mac OS X i Linux usług Azure.

Wprowadzenie wideo, zobacz krótkim [narzędzi Python Tools for Visual Studio](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121) kursu na Microsoft Virtual Academy (około 22 minut całkowita). 

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Installing-Visual-Studio-Python-Support-go1id3LWE_1705918567]

## <a name="questions-and-answers"></a>Pytania i odpowiedzi

**Q. Jest dostępna w programie Visual Studio for Mac obsługę języka Python?**

A. Nie w tej chwili, mimo że żądanie na [UserVoice](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac/suggestions/18670291-python-tools-for-visual-studio-mac). [Programu Visual Studio for Mac](/visualstudio/mac/) dokumentacji identyfikuje bieżące typy programowanie, który go obsługuje. W międzyczasie, Visual Studio Code w systemie Windows, Mac i Linux [działa prawidłowo w przypadku języka Python za pomocą dostępnych rozszerzeń](https://code.visualstudio.com/docs/languages/python).

**Q. Co mogą wykorzystać do tworzenia interfejsu użytkownika z języka Python?**

A. Oferta głównego, w tym obszarze jest [Qt projektu](https://www.qt.io/qt-for-application-development/), z powiązaniami dla języka Python, znany jako [PySide (oficjalna powiązanie)](http://wiki.qt.io/PySide) (Zobacz też [pobiera PySide](https://download.qt.io/official_releases/pyside/.)) i [ PyQt](https://wiki.python.org/moin/PyQt). Obecnie obsługę języka Python w Visual Studio nie ma żadnych określonych narzędzi do tworzenia interfejsu użytkownika.

**Q. Projekt Python powodują autonomicznego pliku wykonywalnego?**

A. Python to zwykle interpretacji języka, z którym jest on uruchamiany na żądanie w odpowiednim środowisku obsługą języka Python, takie jak serwery sieci web i Visual Studio. Visual Studio, sam nie obecnie udostępnia środki do utworzenia autonomicznego pliku wykonywalnego, co oznacza zasadniczo program z osadzonych interpreter języka Python. Istnieją różne środków w obrębie społeczności Python do tworzenia plików wykonywalnych, zgodnie z opisem na [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). Języka CPython obsługuje również osadzona w aplikacji natywnych, zgodnie z opisem w blogu, [przy użyciu języka CPython w pliku Zip osadzenia](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/).

## <a name="features-matrix"></a>Funkcje macierzy

Obsługa języka Python można zainstalować w następujących wersjach programu Visual Studio zgodnie z opisem w [Przewodnik instalacji](installing-python-support-in-visual-studio.md):

- [Visual Studio 2017 (wszystkie wersje)](https://www.visualstudio.com/vs/)
- [Visual Studio 2015 (wszystkie wersje)] (https://www.visualstudio.com/en-us/downloads/visual-studio-2015-downloads-vs)
- Visual Studio 2013 Community Edition
- Visual Studio Express 2013 for Web, aktualizacja 2 lub nowszy
- Visual Studio Express 2013 for pulpitu, aktualizacja 2 lub nowszy
- Visual Studio 2013 (Pro edition lub nowszy)
- Program Visual Studio 2012 (Pro edition lub nowszy)
- Visual Studio 2010 z dodatkiem SP1 (Pro edition lub nowszy; .NET 4.5 wymagana)

Obsługiwane funkcje w wersji programu Visual Studio i wersji:

| Obsługa języka Python | 2017 | 2015 | 2013 Comm | Pulpit 2013 | Sieci web 2013 | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Zarządzanie wieloma tłumaczy | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Autowykrywanie popularnych tłumaczy | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Dodaj niestandardowy tłumaczy | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Środowiska wirtualne | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Zainstaluj narzędzie PIP/łatwe | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| System projektu | 2017 | 2015 | 2013 Comm | Pulpit 2013 | Sieci web 2013 | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Nowy projekt z istniejących źródeł | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Pokaż wszystkie pliki | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Kontrola źródła | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Integracja z usługą Git | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004;<sup>1</sup> | &#10007; |
<br/>

| Edytowanie | 2017 | 2015 | 2013 Comm | Pulpit 2013 | Sieci web 2013 | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| wyróżnianie składni | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Funkcja automatycznego uzupełniania | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Podpis pomocy | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Szybkie informacje | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Widok klas przeglądarki obiektu | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Pasek nawigacyjny | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Przejdź do definicji | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Przejdź do | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Znajdź wszystkie odwołania | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Wcięcie automatycznie | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Formatowanie kodu | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Refaktoryzuj — Zmień nazwę | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Zrefaktoryzuj - extract — metoda | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Refaktoryzuj — Dodawanie/usuwanie importu | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| PyLint | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Okno interaktywne | 2017 | 2015 | 2013 Comm | Pulpit 2013 | Sieci web 2013 | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Okno interaktywne | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| IPython wykresami wbudowany | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Pulpitu | 2017 | 2015 | 2013 Comm | Pulpit 2013 | Sieci web 2013 | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Aplikacja konsoli/Windows | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| WPF IronPython (za pomocą projektanta XAML) | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Formularze systemu Windows IronPython | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| sieć Web | 2017 | 2015 | 2013 Comm | Pulpit 2013 | Sieci web 2013 | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Projekt sieci web Django | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Projekt sieci web bottle | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Projekt sieci web platformy flask | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Projekt sieci web ogólny | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Azure | 2017 | 2015 | 2013 Comm | Pulpit 2013 | Sieci web 2013 | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Wdrażanie w witrynie sieci web | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004;<sup>2</sup> |
| Wdrażanie w roli sieci web | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Wdrażanie w roli procesu roboczego | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Uruchamianie w emulatorze platformy Azure | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Debugowanie zdalne | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> | &#10007; |
| Dołącz Eksploratora serwera | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> | &#10007; | &#10007; |
<br/>

| Szablony Django | 2017 | 2015 | 2013 Comm | Pulpit 2013 | Sieci web 2013 | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Debugowanie | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Funkcja automatycznego uzupełniania | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004; | &#10004; |
| Funkcja automatycznego uzupełniania CSS i JavaScript | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007; | &#10007; |
<br/>

| Debugowanie | 2017 | 2015 | 2013 Comm | Pulpit 2013 | Sieci web 2013 | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Debugowanie | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Debugowanie bez projektu | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Debugowanie — dołączenie do edycji | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| Debugowanie w trybie mieszanym | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Zdalne debugowanie (z systemem Windows, Mac OS X, Linux) | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| Okno interaktywne debugowania | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Profilowanie | 2017 | 2015 | 2013 Comm | Pulpit 2013 | Sieci web 2013 | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Profilowanie | &#10004; | &#10004; | &#10004; | &#10007; | &#10007; | &#10004; | &#10004; | &#10004; |
<br/>

| Test | 2017 | 2015 | 2013 Comm | Pulpit 2013 | Sieci web 2013 | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Eksplorator testów | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Uruchamianie testu | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Debuguj test | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
<br/>

1. Obsługa Git dla programu Visual Studio 2012 jest dostępna w Visual Studio Tools for Git rozszerzenia, dostępne w [galerii programu Visual Studio](http://visualstudiogallery.msdn.microsoft.com/abafc7d6-dcaa-40f4-8a5e-d6724bdb980c).

1. Wymaga wdrożenia do witryny sieci Web Azure [zestaw Azure SDK for .NET 2.1 — Visual Studio 2010 z dodatkiem SP1](http://go.microsoft.com/fwlink/?LinkId=313855). Nowsze wersje nie obsługują programu Visual Studio 2010.

1. Obsługa roli proces roboczy i rolą sieć Web Azure wymaga [zestaw Azure SDK for .NET 2.3 - VS 2012](http://go.microsoft.com/fwlink/?LinkId=323511) lub nowszym.

1. Obsługa roli proces roboczy i rolą sieć Web Azure wymaga [zestaw Azure SDK for .NET 2.3 - VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) lub nowszym.

1. Edytor szablonu Django w programie Visual Studio 2013 ma znane problemy, które są rozpoznawane przez zainstalowanie aktualizacji 2.

1. Wymaga systemu Windows 8 lub nowszy. Visual Studio Express 2013 for Web nie ma dołączanie do procesu w oknie dialogowym, ale zdalne debugowanie witryny sieci Web Azure jest nadal możliwe, w Eksploratorze serwera za pomocą polecenia dołączanie debugera (Python). Zdalne debugowanie wymaga [zestaw Azure SDK for .NET 2.3 — Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkId=323510) lub nowszym.

1. Wymaga systemu Windows 8 lub nowszy. Dołączanie debugera (Python) wymaga polecenia w Eksploratorze serwera [zestaw Azure SDK for .NET 2.3 — Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkId=323510) lub nowszym.

1. Wymaga systemu Windows 8 lub nowszy.

## <a name="additional-resources"></a>Dodatkowe zasoby

- [Mostek WFastCGI między usługami IIS a Python](https://pypi.python.org/pypi/wfastcgi) (python.org)
- [Bezpłatne kursy Python w Microsoft Virtual Academy](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Górny Python pytania wirtualna Akademia firmy Microsoft](https://aka.ms/mva-top-python-questions)
