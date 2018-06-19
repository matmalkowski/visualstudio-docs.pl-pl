---
title: Omówienie obsługi języka Python w programie Visual Studio w systemie Windows
description: Podsumowanie funkcji języka Python w programie Visual Studio, dzięki czemu najlepsze IDE języka Python w systemie Windows (znanej także jako narzędzi Python Tools for Visual Studio, PTVS).
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 587517bdeabf9755e2678b03206059ef5b403255
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34449172"
---
# <a name="working-with-python-in-visual-studio-on-windows"></a>Praca z języka Python w programie Visual Studio w systemie Windows

Python to niezawodne, elastyczne, łatwe dowiedzieć się, bez używania we wszystkich systemach operacyjnych i obsługiwanych przez społeczność deweloperów silne i wiele bibliotek wolnego popularnych język programowania. Python obsługuje wszystkie środki projektowanie, łącznie z aplikacji sieci web, usług sieci web, aplikacji klasycznych, skrypty i obliczanie naukowe i jest używany przez wiele uczelni, służące zwykłych deweloperzy i deweloperów podobne. Dodatkowe informacje na temat języka na [python.org](https://www.python.org) i [języka Python dla początkujących](https://www.python.org/about/gettingstarted/).

Program Visual Studio jest zaawansowanym IDE języka Python w systemie Windows. Program Visual Studio udostępnia [open source](https://github.com/Microsoft/ptvs) obsługę języka Python za pomocą obciążeń programowania Python i analizy danych (Visual Studio 2017 r) i wolnego narzędzi Python Tools for Visual Studio rozszerzenia (Visual Studio 2015 i wcześniej).

Python nie jest obecnie obsługiwany w programie Visual Studio dla komputerów Mac, ale jest dostępna w Mac i Linux za pomocą programu Visual Studio Code (zobacz [pytania i odpowiedzi](#questions-and-answers)).

Aby rozpocząć:

- Postępuj zgodnie z [instrukcje dotyczące instalacji](installing-python-support-in-visual-studio.md) do skonfigurowania obciążenia Python.
- Zapoznaj się z funkcjami języka Python programu Visual Studio przez sekcje w tym artykule. Możesz również [Obejrzyj seria filmów (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121) wprowadzenie do języka Python w programie Visual Studio (całkowita liczba minut 22).
- Przejdź do co najmniej jednego skróconych podręczników, aby utworzyć projekt. Jeśli masz pewności, Rozpocznij od [utworzona aplikacja sieci web za pomocą platformy Flask](../ide/quickstart-python.md?context=visualstudio/python/default).
- Postępuj zgodnie z [Praca z języka Python w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) samouczka środowisko pełnej end-to-end.

## <a name="support-for-multiple-interpreters"></a>Obsługa wielu tłumaczy

Visual Studio **środowiska Python** okna (w widoku szerokości, rozbudowane pokazana poniżej) zapewnia jedno miejsce do zarządzania wszystkimi globalnego środowiska Python, środowisk conda i środowisk wirtualnych. Visual Studio automatycznie wykrywa instalacji języka Python w lokalizacjach standardowe i pozwala na skonfigurowanie instalacje niestandardowe. Z każdego środowiska można łatwo Zarządzaj pakietami, Otwórz okno interaktywne dla tego środowiska i uzyskać dostęp do folderów środowiska.

![Widoku rozwiniętego okna środowiska Python](media/environments-expanded-view.png)

Informacje dodatkowe:

- Wideo (2m 35s): [Zarządzanie środowiska Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567)
- Dokumenty: [środowiska Python Zarządzanie](managing-python-environments-in-visual-studio.md)
- Dokumenty: [odwołanie okno środowiska Python](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>Edytowanie sformatowanego, IntelliSense i zrozumienia kodu

Program Visual Studio oferuje najwyższej jakości edytora języka Python, tym kolorowania składni, funkcja automatycznego uzupełniania kodu i bibliotek, formatowania kodu, podpis pomocy refaktoryzacji linting (pokazana poniżej) i wpisz wskazówek. Program Visual Studio oferuje również unikatowe funkcje, takie jak Widok klas, przejdź do definicji, Znajdź wszystkie odwołania i wstawki kodu. Bezpośrednia Integracja z [okna interaktywnego](#interactive-window) ułatwia szybkie tworzenie kodu języka Python, który jest już zapisana w pliku.

![Zakończeń kodu dla kodu języka Python w programie Visual Studio](media/code-editing-completions-simple.png)

Informacje dodatkowe:

- Wideo (2m 30s): [Python edytowanie kodu](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=r2iQH5LWE_4605918567)
- Dokumenty: [Python edytowanie kodu](editing-python-code-in-visual-studio.md)
- Dokumenty: [kodu, formatowanie](formatting-python-code.md)
- Dokumenty: [refaktoryzacji](refactoring-python-code.md)
- Dokumenty: [Linting](linting-python-code.md)
- Dokumentacja funkcji ogólne Visual Studio: [funkcje Edytor kodu](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>Okno interaktywne

Dla każdego środowiska Python znane dla programu Visual Studio możesz łatwo otworzyć tym samym środowisku interakcyjne (REPL) dla interpreter języka Python bezpośrednio z poziomu programu Visual Studio, a nie oddzielnych wiersza polecenia. Można łatwo przełączać się między środowiskami również.

![Okno interaktywne Python w programie Visual Studio](media/interactive-window.png)

Program Visual Studio oferuje również ścisła integracja między edytora kodu Python i okna interaktywnego. **Klawisze Ctrl + Enter** skrót klawiaturowy wygodnie bieżącego wiersza kodu (lub blok kodu) w edytorze do okna interaktywnego, a następnie przechodzi do następnego wiersza (lub blok). **Ctrl + Enter** pozwala łatwo kroków kodu bez konieczności uruchamiania debugera. Można również wysłać zaznaczony kod do interaktywnego okna z tego samego naciśnięcie klawisza i łatwo można wkleić do edytora kod z okna interaktywnego. Ze sobą te funkcje umożliwiają wyglądają szczegóły segment kodu w oknie interaktywnym i łatwo zapisane wyniki w pliku w edytorze.

Program Visual Studio obsługuje również IPython/Jupytr w REPL, w tym tekście powierzchni, .NET i Windows Presentation Foundation (WPF).

Informacje dodatkowe:

- Wideo (2m 22s: [okna interaktywnego Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=gJYKY5LWE_4605918567)
- Dokumenty: [okna interaktywnego](python-interactive-repl-in-visual-studio.md)
- Dokumenty: [IPython w programie Visual Studio](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>System projektu i szablonów projektów i elementów

Visual Studio ułatwia zarządzanie złożoności projektu w miarę zwiększania się wraz z upływem czasu. Projekt jest znacznie większa niż strukturę folderów: zawiera opis różnych plików są używane i jak są one powiązane ze sobą. Visual Studio pomaga odróżnić kodu aplikacji, przetestować kod, stron sieci web, JavaScript, skrypty kompilacji i tak dalej, które następnie umożliwiają odpowiednich plików funkcji. Rozwiązanie Visual Studio ułatwia ponadto zarządzanie wieloma projektami pokrewne, takie jak projektów języka Python i projekt rozszerzenia języka C++.

![Visual Studio rozwiązania zawierającego projekty zarówno Python i C++](media/projects-solution-explorer-two-projects.png)

Szablony projektów i elementów automatyzacji procesu konfigurowania różnych typów projektów i plików, co pozwala zaoszczędzić cenny czas i co uwalnia możesz Zarządzanie szczegóły skomplikowanych i podatne na błędy. Program Visual Studio udostępnia szablony sieci web, Azure, analizy danych, konsolę i innych typów projektów, wraz z szablonów dla plików takich jak klasy, testy jednostkowe, konfiguracji sieci web platformy Azure, HTML i nawet aplikacji Django Python.

[![Python szablonów projektów i elementów w programie Visual Studio](media/project-and-item-templates.png)](media/project-and-item-templates.png)

Informacje dodatkowe:

- Dokumenty: [projektów języka Python Zarządzanie](managing-python-projects-in-visual-studio.md)
- Dokumenty: [dotyczące szablonów elementu](python-item-templates.md)
- Dokumenty: [Python szablony projektu](managing-python-projects-in-visual-studio.md#project-templates)
- Dokumenty: [Praca z C++ i języku Python](working-with-c-cpp-python-in-visual-studio.md)
- Dokumentacja funkcji ogólne Visual Studio: [szablonów projektów i elementów](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- Dokumentacja funkcji ogólne Visual Studio: [rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>Oferujący wszystkie funkcje debugowania

Jednym z sile Visual Studio jest jego doskonałego debugera. Dla języka Python w szczególności Visual Studio zawiera Python/C++ debugowanie w trybie mieszanym, debugowanie zdalne w systemie Linux, zdalnego debugowania na platformie Azure, debugowania do interaktywnego okna i profilowanie testów jednostkowych Python.

![Debuger programu Visual Studio dla języka Python przedstawiający menu podręczne wyjątku](media/debugging-exception-popup.png)

Informacje dodatkowe:

- Wideo: [debugowania 3 m 32s Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=Ep5dp5LWE_3805918567)
- Dokumenty: [debugowania języka Python](debugging-python-in-visual-studio.md)
- Dokumenty: [debugowanie w trybie mieszanym Python/C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- Dokumenty: [debugowania zdalnego w systemie Linux](debugging-python-code-on-remote-linux-machines.md)
- Dokumenty: [zdalnego debugowania na platformie Azure](debugging-remote-python-code-on-azure.md)
- Dokumentacja funkcji ogólne Visual Studio: [Przewodnik po funkcji debuger programu Visual Studio](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>Narzędzia profilowania z raportowaniem kompleksowe

Profilowanie opisuje, jak jest zużywany czas w aplikacji. Visual Studio obsługuje profilowanie z na podstawie języka CPython tłumaczy i umożliwia porównanie wydajności między cyklów profilowania.

[![Visual Studio profilera wyniki dla projektów języka Python](media/profiling-results.png)](media/profiling-results.png)

Informacje dodatkowe:

- Wideo: [profilowania Python 3 m 00s](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=s6FoC6LWE_1005918567)
- Dokumenty: [Python narzędzia profilowania](profiling-python-code-in-visual-studio.md)
- Dokumentacja funkcji ogólne Visual Studio: [profilowania samouczek funkcji](../profiling/profiling-feature-tour.md). (Nie wszystkie funkcje profilowania programu Visual Studio są dostępne dla języka Python).

## <a name="unit-testing-tools"></a>Narzędzia do testowania jednostki

Odnajdywanie, uruchamianie, zarządzania testami w Visual Studio narzędzia Eksplorator testów i łatwe debugowanie testów jednostkowych.

![Debugowanie testu jednostkowego języka Python w programie Visual Studio](media/unit-test-debugging.png)

Informacje dodatkowe:

- Wideo: [testowanie 2 m 31s języka Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=hb46k6LWE_405918567)
- Dokumenty: [jednostki narzędzia do testowania dla języka Python](unit-testing-python-in-visual-studio.md)
- Dokumentacja funkcji ogólne Visual Studio: [kod testu jednostkowego](../test/unit-test-your-code.md).

## <a name="publishing-to-azure-and-azure-sdk-for-python"></a>Publikowanie na platformie Azure oraz Azure SDK dla języka Python

Visual Studio zapewnia zintegrowaną obsługę publikowania aplikacji sieci web i usługi w chmurze na platformie Azure. Visual Studio zawiera istotne `web.config` elementu szablony zarówno dynamicznej i statycznej zawartości. Obciążenie Python także zestaw Azure SDK dla języka Python, co upraszcza korzystanie z systemu Windows, Mac OS X i Linux aplikacji usług Azure.

![Publikowanie aplikacji Python do platformy Azure w programie Visual Studio](media/azure-publish-dialog.png)

Informacje dodatkowe:

- Dokumenty: [publikowania na platformie Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)
- Dokumenty: [Azure SDK dla języka Python](azure-sdk-for-python.md)

## <a name="python-training-on-microsoft-virtual-academy"></a>Python szkoleń w Microsoft Virtual Academy

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo") | <ul><li>[Wprowadzenie do programowania w języku Python](https://mva.microsoft.com/en-US/training-courses/introduction-to-programming-with-python-8360?l=lqhuMxFz_8904984382)</li><li>[Języka Python dla początkujących użytkowników: Ciągi i funkcje](https://mva.microsoft.com/en-US/training-courses/python-beginner-strings-and-functions-18015)</li><li>[Podstawy języka Python: Lista i pętle](https://mva.microsoft.com/en-US/training-courses/python-fundamentals-lists-and-loops-18019)</li><li>[Pytania TOP Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121)</li></ul> |

## <a name="questions-and-answers"></a>Pytania i odpowiedzi

**Q. Jest dostępna w programie Visual Studio for Mac obsługę języka Python?**

A. Nie w tej chwili, ale może nawet głosowania żądania w [UserVoice](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac/suggestions/18670291-python-tools-for-visual-studio-mac). [Programu Visual Studio for Mac](/visualstudio/mac/) dokumentacji identyfikuje bieżące typy programowanie, który go obsługuje. W międzyczasie, Visual Studio Code w systemie Windows, Mac i Linux [działa prawidłowo w przypadku języka Python za pomocą dostępnych rozszerzeń](https://code.visualstudio.com/docs/languages/python).

**Q. Co mogą wykorzystać do tworzenia interfejsu użytkownika z języka Python?**

A. Oferta głównego, w tym obszarze jest [Qt projektu](https://www.qt.io/qt-for-application-development/), z powiązaniami dla języka Python, znany jako [PySide (oficjalna powiązanie)](http://wiki.qt.io/PySide) (Zobacz też [pobiera PySide](https://download.qt.io/official_releases/pyside/.)) i [ PyQt](https://wiki.python.org/moin/PyQt). Obecnie obsługę języka Python w Visual Studio nie ma żadnych określonych narzędzi do tworzenia interfejsu użytkownika.

**Q. Projekt Python powodują autonomicznego pliku wykonywalnego?**

A. Python to zwykle interpretacji języka, z którym jest on uruchamiany na żądanie w odpowiednim środowisku obsługą języka Python, takie jak serwery sieci web i Visual Studio. Visual Studio, sam nie obecnie udostępnia środki do utworzenia autonomicznego pliku wykonywalnego, co oznacza zasadniczo program z osadzonych interpreter języka Python. Istnieją różne środków w obrębie społeczności Python do tworzenia plików wykonywalnych, zgodnie z opisem na [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). Języka CPython obsługuje również osadzona w aplikacji natywnych, zgodnie z opisem w blogu, [przy użyciu języka CPython w pliku Zip osadzenia](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/).

## <a name="features-matrix"></a>Funkcje macierzy

Funkcje języka Python można zainstalować w następujących wersjach programu Visual Studio zgodnie z opisem w [Przewodnik instalacji](installing-python-support-in-visual-studio.md):

- [Visual Studio 2017 (wszystkie wersje)](https://www.visualstudio.com/vs/)
- Visual Studio 2015 (wszystkie wersje)
- Visual Studio 2013 Community Edition
- Visual Studio Express 2013 for Web, aktualizacja 2 lub nowszy
- Visual Studio Express 2013 for pulpitu, aktualizacja 2 lub nowszy
- Visual Studio 2013 (Pro edition lub nowszy)
- Program Visual Studio 2012 (Pro edition lub nowszy)
- Visual Studio 2010 z dodatkiem SP1 (Pro edition lub nowszy; .NET 4.5 wymagana)

Visual Studio 2015 i starsze wersje są dostępne pod adresem [visualstudio.com/vs/older-downloads/](https://www.visualstudio.com/vs/older-downloads/).

> [!Important]
> Funkcje są w pełni obsługiwane i utrzymywana w najnowszej wersji programu Visual Studio. Funkcje są dostępne w starszych wersjach, ale nie są zachowywane aktywnie.

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

<a name="matrix-profiling"></a>

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

- [Mostek WFastCGI między usługami IIS a Python](https://pypi.org/p/wfastcgi) (pypi.org)
- [Bezpłatne kursy Python w Microsoft Virtual Academy](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Górny Python pytania wirtualna Akademia firmy Microsoft](https://aka.ms/mva-top-python-questions)
