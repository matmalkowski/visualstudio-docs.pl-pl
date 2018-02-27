---
title: "Jak Python ścieżki wyszukiwania są stosowane w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/20/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 43e42bf246af0ea5df69a2960d9f13ae97784f6a
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Jak Visual Studio używa języka Python, ścieżki wyszukiwania

Typowy Usage Python `PYTHONPATH` zmiennej środowiskowej (lub `IRONPYTHONPATH`, itd.) zapewnia domyślnej ścieżki wyszukiwania plików modułu. Oznacza to, że jeśli używasz `from <name> import...` lub `import <name>` instrukcji, Python wyszukuje następujące lokalizacje w kolejności zgodnej nazwie:

1. Wbudowane moduły języka Python.
1. Folder zawierający kod języka Python, który jest uruchomiony.
1. "Moduł ścieżki wyszukiwania" jako zdefiniowanej przez zmienną środowiskową zastosowania. (Zobacz [ścieżki wyszukiwania modułu](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) i [zmiennych środowiskowych](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) w podstawowej dokumentacji języka Python.)

Visual Studio ignoruje zmiennej środowiskowej ścieżki wyszukiwania, jednak nawet wtedy, gdy zmienna jest ustawiana dla całego systemu. Jest on ignorowany, w rzeczywistości, dokładnie *ponieważ* ustawiono dla całego systemu i w związku z tym zgłasza niektóre kwestie, które nie mogą być odbierane automatycznie: moduły do którego istnieje odwołanie, przeznaczone dla języka Python 2.7 lub Python 3.3? Są one będą zastąpienie modułów standardowa biblioteka? Zna dewelopera tego zachowania, czy jest próba złośliwego przejęcie kontroli?

Program Visual Studio udostępnia w związku z tym określenie ścieżki wyszukiwania bezpośrednio w środowiskach i projektów. Kod, który uruchamiania lub debugowania w programie Visual Studio odbiera ścieżki wyszukiwania w wartości `PYTHONPATH` (i inne zmienne równoważne). Dodając ścieżki wyszukiwania, Visual Studio przeprowadzający bibliotek w tych lokalizacjach i kompilacje baz danych IntelliSense dla nich (utworzenie bazy danych może zająć trochę czasu w zależności od liczby bibliotek).

Aby dodać ścieżkę wyszukiwania, kliknij prawym przyciskiem myszy **ścieżki wyszukiwania** elementu w Eksploratorze rozwiązań wybierz **Dodaj Folder do ścieżki wyszukiwania...** i wybierz folder do dołączenia. Ta ścieżka jest używana w każdym środowisku skojarzony z projektem. (Mogą zostać wyświetlone błędy Jeśli środowisko jest oparta na Python 3 i użytkownik podejmie próbę dodania ścieżki wyszukiwania w modułach Python 2.7.)

Pliki z `.zip` lub `.egg` rozszerzenia również mogą być dodawane jako ścieżki wyszukiwania, wybierając **dodać archiwum Zip do ścieżki wyszukiwania...** . Podobnie jak w przypadku folderów, zawartość te pliki są skanowane i udostępnione IntelliSense.

Jeśli zawartość nie należy zmieniać często są regularnie przy użyciu tej samej ścieżki wyszukiwania, może być bardziej wydajne, aby zainstalować go do folderu pakietów lokacji. Ścieżki wyszukiwania następnie są analizowane i przechowywane w bazie danych IntelliSense, jest zawsze być skojarzony z danego środowiska i nie wymaga ścieżkę wyszukiwania do dodania do każdego projektu.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie środowiska Python w programie Visual Studio](managing-python-environments-in-visual-studio.md)
- [Wybierz interpreter dla projektu](selecting-a-python-environment-for-a-project.md)
- [Używanie pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Odwołanie do okna środowiska Python](python-environments-window-tab-reference.md)