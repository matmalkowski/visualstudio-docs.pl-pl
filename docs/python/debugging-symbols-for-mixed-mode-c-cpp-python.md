---
title: "Symbole dla języka Python/C++ debugowanie w trybie mieszanym w programie Visual Studio | Dokumentacja firmy Microsoft"
description: "Jak Visual Studio pozwala, aby załadować symbole dla pełnej C++ trybu mieszanego i Python debugowania."
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 2f309e50337195dc0e4057ce34f56e2575ec1b61
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="installing-debugging-symbols-for-python-interpreters"></a>Instalowanie symbole debugowania dla języka Python tłumaczy

Aby zapewnić pełne środowisko debugowania, [debugera Python trybu mieszanego](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) w programie Visual Studio wymaga debugowania symbole dla interpreter języka Python, używany do analizowania wielu struktur danych wewnętrznych. Na przykład w przypadku python27.dll, odpowiedniego pliku symboli jest python27.pdb; w przypadku python36.dll pliku symboli jest python36.pdb. Każda wersja programu interpretera udostępnia również pliki symboli w różnych modułach.

Z programu Visual Studio 2017 r "Python 3" i "Anaconda 3" tłumaczy automatycznie zainstalować ich odpowiednich symboli i program Visual Studio automatycznie znaleźć symbole. Dla programu Visual Studio 2015 lub starszym, lub w przypadku używania innych tłumaczy, musisz pobrać osobno symbole, a następnie wskaż Visual Studio do nich za pośrednictwem **Narzędzia > Opcje** okno dialogowe w **debugowanie > symbole**  kartę. Te kroki są szczegółowo opisane w poniższych sekcjach.

Visual Studio może monitować podczas zwykle wymaga symbole, podczas uruchamiania sesji debugowania w trybie mieszanym. W takim przypadku wyświetla okno dialogowe z dwóch opcji:

- **Symbol Otwórz okno dialogowe Ustawienia** otwiera **opcje** okna dialogowego, aby **debugowanie > symbole** kartę.
- **Pobieranie symboli dla moich interpreter** otwiera niniejszej dokumentacji strony, w takim przypadku wybierz **Narzędzia > Opcje** i przejdź do **debugowanie > symbole** kartę, aby kontynuować.

    ![Tryb mieszany debugera symbole wiersza](media/mixed-mode-debugging-symbols-required.png)

## <a name="downloading-symbols"></a>Pobieranie symboli

- Python w wersji 3.5 lub nowszej: uzyskanie symboli debugowania za pomocą Instalatora języka Python. Wybierz **Instalacja niestandardowa**, wybierz pozycję **dalej** na uzyskanie dostępu do **zaawansowane opcje**, następnie zaznacz pola **Pobierz symbole debugowania** i **pliki binarne debugowania pobierania**:

    ![Python 3.x Instalatora, łącznie z symboli debugowania](media/mixed-mode-debugging-symbols-installer35.png)

    Pliki symboli (`.pdb`) następnie znajdują się w folderze głównym instalacji (pliki symboli dla poszczególnych modułów są `DLLs` również folder). W związku z tym Visual Studio umożliwia znalezienie je automatycznie i nie są wymagane żadne dodatkowe czynności.

- Python 3.4.x i starszych wersji: symboli są dostępne jako pliki zip do pobrania z [oficjalnego dystrybucje](#official-distributions) lub [korony Enthought](#enthought-canopy). Po pobraniu, Wyodrębnij pliki do folderu lokalnego, aby kontynuować, takich jak `Symbols` folder w folderze Python.

    > [!Important]
    > Symbole różnią się między kompilacjami pomocniczych języka Python i między 32-bitowe i 64-bitowych wersjach, dlatego należy dokładnie zgodne z wersjami. Aby sprawdzić interpreter używany, rozwiń węzeł **środowiska Python** *węzła* w obszarze Projekt w Eksploratorze rozwiązań i zanotuj nazwę środowiska. Następnie przejdź do **środowiska Python** *okna* i zanotuj lokalizację instalacji. Następnie otwórz okno polecenia w tej lokalizacji i uruchom `python.exe`, które powoduje wyświetlenie dokładnej wersji i czy jest 32-bitowy lub 64-bitowej.

- Dla żadnych innych firm Python dystrybucji, takie jak ActiveState Python: Skontaktuj się z autorów dystrybucji i zażądać ich dostarczają symboli. WinPython, ze swojej strony zawiera standardowe interpreter języka Python bez zmian, należy więc symbole z oficjalnego dystrybucji dla jej numer wersji.

## <a name="pointing-visual-studio-to-the-symbols"></a>Wskazuje Visual Studio do symboli

Jeśli pobrano symbole oddzielnie, wykonaj poniższe kroki, aby uświadomić Visual Studio z nich. Jeśli zainstalowano symboli za pomocą języka Python w wersji 3.5 lub nowszej Instalator Visual Studio znajduje się automatycznie.

1. Wybierz **Narzędzia > Opcje** menu i przejdź do **debugowanie > symbole**.
    
1. Wybierz **Dodaj** znajdującego się na pasku narzędzi (opisanych poniżej), wprowadź folder, gdzie rozwinięty pobranych symboli (czyli gdzie `python.pdb` znajduje się, takich jak `c:\python34\Symbols`, przedstawiono poniżej) i wybierz **OK**. 

    ![Opcje symbole debugowania w trybie mieszanym](media/mixed-mode-debugging-symbols.png)

1. Podczas sesji debugowania programu Visual Studio może również monit o lokalizację pliku źródłowego interpreter języka Python. Jeśli pobrano pliki źródłowe (z [python.org/downloads](https://www.python.org/downloads), na przykład), a następnie oczywiście można wskazać je również.

> [!Note]
> Symbol funkcji buforowania pokazać w oknie dialogowym są używane do tworzenia lokalnej pamięci podręcznej symboli uzyskanych ze źródła danych w trybie online. Te funkcje nie są potrzebne przy użyciu symboli interpreter języka Python, jak symbole są już lokalnie. W każdym przypadku dotyczą [plików źródłowych w debugerze programu Visual Studio i określ symbole](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) szczegółowe informacje.

## <a name="official-distributions"></a>Dystrybucje urzędowego

| Wersja języka Python | Pliki do pobrania | 
| --- | --- | 
| 3.5 i nowsze | Instalowanie symboli za pomocą Instalatora języka Python. | 
| 3.4.4 | [32-bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32-bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32-bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32-bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32-bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32-bit](http://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip) - [64-bit](http://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32-bit](http://python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip) - [64-bit](http://python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32-bit](http://python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip) - [64-bit](http://python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32-bit](http://python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip) - [64-bit](http://python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32-bit](http://python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip) - [64-bit](http://python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32-bit](http://python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip) - [64-bit](http://python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.11 | [32-bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32-bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32-bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32-bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32-bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32-bit](http://python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip) - [64-bit](http://python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32-bit](http://python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip) - [64-bit](http://python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32-bit](http://python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip) - [64-bit](http://python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32-bit](http://python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip) - [64-bit](http://python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32-bit](http://python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip) - [64-bit](http://python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32-bit](http://python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip) - [64-bit](http://python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |


## <a name="enthought-canopy"></a>Korony Enthought

Korony Enthought zawiera symbole dla jego danych binarnych, począwszy od wersji 1.2. Są one instalowane automatycznie razem z rozkładem, ale nadal musisz ręcznie dodać folderu zawierającego je do ścieżki symboli zgodnie z wcześniejszym opisem. W przypadku instalacji użytkownika typowe korony symbole znajdują się w `%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts` w 64-bitowej wersji i `%UserProfile%\AppData\Local\Enthought\Canopy32\User\Scripts` w 32-bitowej wersji.

Korony Enthought 1.1 lub starszym, a także Enthought Python dystrybucji (EPD), nie udostępniają interpreter symbole i dlatego nie są zgodne z debugowanie w trybie mieszanym.