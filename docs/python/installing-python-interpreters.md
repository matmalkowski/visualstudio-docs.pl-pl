---
title: "Wybieranie i instalowanie tłumaczy Python | Dokumentacja firmy Microsoft"
description: "Pełna lista tłumaczy Python, które są obsługiwane w programie Visual Studio z krótkie instrukcje o tym, gdzie można znaleźć instalatorów ich."
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
ms.openlocfilehash: 1bdec69c45cbd6ebb7943ce38853fd2207000a0f
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="installing-python-interpreters"></a>Instalowanie tłumaczy Python

Domyślnie instalowanie Python obciążenia Programowanie w Visual Studio 2017 instaluje Python 3 (64-bitowe). Opcjonalnie można zainstalować 32-bitowe i 64-bitowe wersje Python 2, Python 3, Anaconda 2 i Anaconda 3, zgodnie z opisem w [instalacji](installing-python-support-in-visual-studio.md).

Można też ręcznie zainstalują dowolną z tłumaczy wymienione w poniższej tabeli poza Instalator programu Visual Studio. Na przykład jeśli zainstalowano Anaconda 3 przed zainstalowaniem programu Visual Studio, nie trzeba ponownie zainstalować za pomocą Instalatora programu Visual Studio.

Dla programu Visual Studio 2015 i starszych należy ręcznie zainstalować jedną tłumaczy.

Visual Studio (wszystkie wersje) automatycznie wykrywa każdego zainstalowana interpreter języka Python i jego środowiska, sprawdzając rejestru (następujące [514 program ten - Python rejestracji w rejestrze systemu Windows](https://www.python.org/dev/peps/pep-0514/)).

Jeśli program Visual Studio nie wykrywa zainstalowane środowisko, zobacz [ręczne identyfikowanie istniejącego środowiska](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment).

Visual Studio zawiera wszystkie znane środowiska w [okno środowiska Python](managing-python-environments-in-visual-studio.md)i automatycznie wykrywa aktualizacje do istniejących tłumaczy.

| Interpreter | Opis |
| --- | --- |
| [CPython](https://www.python.org/) | "Natywny" i najbardziej często używanych interpretera dostępne w wersjach 32-bitowych i 64-bitowych (32-bitowy zalecane). Zawiera najnowsze funkcje językowe, maksymalną zgodność pakiet języka Python, pełną obsługę debugowania i współdziałanie z [IPython](http://ipython.org/). Zobacz też: [użyć Python 2 lub Python 3?](http://wiki.python.org/moin/Python2orPython3). Należy pamiętać, że Visual Studio 2015 i starsze nie obsługują 3,6 Python i zapewnić błąd "Nieobsługiwana wersja języka python 3,6". Użyj języka Python w wersji 3.5 lub starszej zamiast tego. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | .NET stosowania Python, dostępne w wersjach 32-bitowych i 64-bitowych, podając podstawowe interop /F #/ Visual C dostęp do interfejsów API architektury .NET, Python standardowe debugowania (ale nie C++ debugowanie w trybie mieszanym) oraz mieszany IronPython / C# debugowania. IronPython, jednak nie obsługuje środowisk wirtualnych. |
| [Anaconda](https://www.continuum.io) | Danych otwartych nauki platformy obsługiwane przez Python i zawiera najnowszą wersję języka CPython i większość pakietów trudne do zainstalowania. Firma Microsoft zaleca, jeśli nie zdecydujesz inaczej. |
| [PyPy](http://www.pypy.org/) | Implementacja JIT śledzenie wysokiej wydajności, języka Python, który ułatwia programy długotrwałe i sytuacji możesz określić wydajności problemów, ale nie można znaleźć inne rozwiązania. Działa z programem Visual Studio, ale z ograniczoną obsługę zaawansowanych funkcji debugowania. |
| [Jython](http://www.jython.org/) | Implementacja Python na maszynie wirtualnej Java (JVM). Podobny do IronPython, kodu uruchamianego w Jython mogą prowadzić interakcję z klas Java i bibliotek, ale może nie móc korzystać z wielu bibliotek przeznaczonych do języka CPython. Działa z programem Visual Studio, ale z ograniczoną obsługę zaawansowanych funkcji debugowania. |

Deweloperzy, które chcą udostępniać nowych metod wykrywania dla środowiska Python, zobacz [wykrywania środowiska PTVS](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (witryną github.com).

## <a name="moving-an-interpreter"></a>Przenoszenie interpretera

Interpreter istniejących zostanie przeniesiony do nowej lokalizacji w systemie plików, Visual Studio nie automatycznie wykryć zmiany.

- Jeśli określona pierwotnie lokalizację interpreter za pośrednictwem **środowiska Python** okna, Edycja jego przy użyciu środowiska **Konfiguruj** karcie tego okna, aby zidentyfikować nową lokalizację. Zobacz [ręczne identyfikowanie istniejącego środowiska](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment).

- Jeśli zainstalowano interpreter za pomocą programu instalacyjnego, użyj następujące kroki ponownie zainstalować interpreter w nowej lokalizacji:

  1. Przywróć interpreter języka Python do jej oryginalnej lokalizacji.
  2. Odinstaluj interpreter przy użyciu jego Instalatora, który usuwa wpisy rejestru.
  3. Zainstaluj ponownie interpreter w wybranej lokalizacji.
  4. Uruchom ponownie program Visual Studio, które powinien automatycznie wykrywa nowej lokalizacji zamiast poprzedniej lokalizacji.

Następujące ten proces zapewnia wpisy rejestru, które identyfikują interpreter lokalizacji, która korzysta z programu Visual Studio, są poprawnie aktualizowanie. Za pomocą Instalatora obsługuje także inne efekty uboczne, które mogą wystąpić.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie środowiska Python](managing-python-environments-in-visual-studio.md)
- [Wybierz interpreter dla projektu](selecting-a-python-environment-for-a-project.md)
- [Używanie pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Odwołanie do okna środowiska Python](python-environments-window-tab-reference.md)