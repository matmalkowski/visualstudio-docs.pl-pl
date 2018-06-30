---
title: Sposób stosowania ścieżki wyszukiwania Python
description: Przegląd używaniu Python ścieżki wyszukiwania w środowiskach i projektów programu Visual Studio.
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: d1d05670192630e0bc4903988770c52840a5e347
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118242"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Jak Visual Studio używa języka Python, ścieżki wyszukiwania

Typowy Usage Python `PYTHONPATH` zmiennej środowiskowej (lub `IRONPYTHONPATH`, itd.) zapewnia domyślnej ścieżki wyszukiwania plików modułu. Oznacza to, że jeśli używasz `from <name> import...` lub `import <name>` instrukcji, Python wyszukuje następujące lokalizacje w kolejności zgodnej nazwie:

1. Wbudowane moduły języka Python.
1. Folder zawierający kod języka Python, który jest uruchomiony.
1. "Moduł ścieżki wyszukiwania" jako zdefiniowanej przez zmienną środowiskową zastosowania. (Zobacz [ścieżki wyszukiwania modułu](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) i [zmiennych środowiskowych](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) w podstawowej dokumentacji języka Python.)

Visual Studio ignoruje zmiennej środowiskowej ścieżki wyszukiwania, jednak nawet wtedy, gdy zmienna jest ustawiana dla całego systemu. Jest on ignorowany, w rzeczywistości, dokładnie *ponieważ* ustawiono dla całego systemu i w związku z tym zgłasza niektóre kwestie, które nie mogą być odbierane automatycznie: moduły do którego istnieje odwołanie, przeznaczone dla języka Python 2.7 lub 3,6 Python? Są one będą zastąpienie modułów standardowa biblioteka? Zna dewelopera tego zachowania, czy jest próba złośliwego przejęcie kontroli?

Program Visual Studio udostępnia w związku z tym określenie ścieżki wyszukiwania bezpośrednio w środowiskach i projektów. Kod, który uruchamiania lub debugowania w programie Visual Studio odbiera ścieżki wyszukiwania w wartości `PYTHONPATH` (i inne zmienne równoważne). Dodanie ścieżki wyszukiwania, Visual Studio bada bibliotek w tych lokalizacjach i kompilacji IntelliSense baz danych w ramach je w razie potrzeby (Visual Studio 2017 wersji 15.5 i starszych; konstruowanie bazy danych może potrwać pewien czas w zależności od liczby bibliotek).

Aby dodać ścieżkę wyszukiwania, kliknij prawym przyciskiem myszy **ścieżki wyszukiwania** elementu w Eksploratorze rozwiązań wybierz **Dodaj Folder do ścieżki wyszukiwania...** i wybierz folder do dołączenia. Ta ścieżka jest używana w każdym środowisku skojarzony z projektem. (Mogą zostać wyświetlone błędy Jeśli środowisko jest oparta na Python 3 i użytkownik podejmie próbę dodania ścieżki wyszukiwania w modułach Python 2.7.)

Pliki z `.zip` lub `.egg` rozszerzenia również mogą być dodawane jako ścieżki wyszukiwania, wybierając **dodać archiwum Zip do ścieżki wyszukiwania...** . Podobnie jak w przypadku folderów, zawartość te pliki są skanowane i udostępnione IntelliSense.

Jeśli zawartość nie należy zmieniać często są regularnie przy użyciu tej samej ścieżki wyszukiwania, może być bardziej wydajne, aby zainstalować go do folderu pakietów lokacji. Ścieżki wyszukiwania następnie są analizowane i przechowywane w bazie danych IntelliSense, jest zawsze być skojarzony z danego środowiska i nie wymaga ścieżkę wyszukiwania do dodania do każdego projektu.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie środowiska Python w programie Visual Studio](managing-python-environments-in-visual-studio.md)
- [Wybierz interpreter dla projektu](selecting-a-python-environment-for-a-project.md)
- [Używanie pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Odwołanie do okna środowiska Python](python-environments-window-tab-reference.md)