---
title: "Jak używać CTest dla języka C++ w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 11/07/2017
ms.technology: vs-ide-test
ms.topic: article
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 602240df366d9ee978f632a8693bae3de21fcedf
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Jak używać CTest dla języka C++ w programie Visual Studio

CMake (w tym CTest) jest zintegrowany z programu Visual Studio IDE domyślnie jako składnik **Develoment pulpitu z C++** obciążenia. Jeśli musisz zainstalować go na komputerze, Otwórz program Instalator programu Visual Studio, kliknij pozycję **Modyfikuj** przycisk, a następnie sprawdź [CMake Tools dla Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) na liście składników obciążenia.

## <a name="to-write-tests"></a>Aby napisać testy

Obsługa CMake w programie Visual Studio nie może dotyczyć system projektu programu Visual Studio. W związku z tym zapisu i konfigurowanie CTest testów, tak samo jak w dowolnym środowisku CMake. Aby uzyskać więcej informacji o używaniu CMake w programie Visual Studio, zobacz [CMake Tools dla Visual C++](/cpp/ide/cmake-tools-for-visual-cpp).

## <a name="to-run-tests-visual-studio-2017-version-156"></a>Aby uruchomić testy (Visual Studio 2017 wersji 15,6)

W programie Visual Studio 2017 wersji 15,6, CTest jest w pełni zintegrowana z **Eksploratora testów** i również obsługuje zarówno Google i zwiększanie wyniku testowania struktury jednostek. Te struktury są domyślnie dołączone jako składników we **Develoment pulpitu z C++** obciążenia. Jednak w przypadku uaktualniania projektu ze starszej wersji programu Visual Studio, może być konieczne zainstalowania tych środowisk za pomocą programu Instalator programu Visual Studio.

Na poniższej ilustracji przedstawiono wyniki CTest, uruchomić przy użyciu struktury testowej Google:

![CTest z struktury testowej Google w VS2017 15,6](media/ctest-test-explorer.png "CTest i Google testu w teście Explorer")

Jeśli używasz CTest, ale nie kart Google lub zwiększenie wydajności, zobaczysz wyników na poziomie CTest zamiast poszczególnych testów poziom metody. Można debugować i krokowym CTest — tylko do plików wykonywalnych, ale śladów stosu na poszczególne testy nie są obsługiwane.

## <a name="to-run-tests-visual-studio-2017-version-155"></a>Aby uruchomić testy (Visual Studio 2017 wersji 15,5 cala)

W **programu Visual Studio 2017 wersji 15,5 cala**, CTest nie jest zintegrowany z **Eksploratora testów**. Można uruchomić testów z poziomu menu głównego CMake lub z menu kontekstowego **CMakeLists.txt** w pliku **Eksploratora rozwiązań**. Wyniki testu są kierowane do programu Visual Studio **okno danych wyjściowych**.

![Uruchom testy CTest w 15,5 cala VS2017](media/cpp-cmake-run-tests.png "CTest uruchamiania testów w 15,5 cala")

## <a name="see-also"></a>Zobacz także

[Pisanie testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md)