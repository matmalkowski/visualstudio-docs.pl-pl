---
title: "Jak używać CTest dla języka C++ w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
author: mikeblome
ms.openlocfilehash: 989f2b06df55fd0927863fe7e5603d3d0ec90b06
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Jak używać CTest dla języka C++ w programie Visual Studio
CMake (w tym CTest) jest zintegrowany jako część programu Visual Studio IDE **Develoment pulpitu z C++** obciążenia. Aby zainstalować go na komputerze, otwórz Instalator programu Visual Studio i Znajdź [CMake Tools dla Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) na liście składników obciążenia.

Obsługa CMake w programie Visual Studio nie wiąże się z systemu projektu programu Visual Studio. W związku z tym zapisu i konfigurowanie CTest testów, tak samo jak w dowolnym środowisku CMake. Zobacz [CMake Tools dla Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) uzyskać więcej informacji o użyciu CMake programu Visual Studio.

**Visual Studio 2017 wersji 15,5 cala** CTest nie jest zintegrowany z **Eksploratora testów**. Można uruchomić testów z poziomu menu głównego CMake lub z menu kontekstowego **CMakeLists.txt** w pliku **Eksploratora rozwiązań**. Wyniki testu są kierowane do programu Visual Studio **okno danych wyjściowych**.

![Uruchom testy CTest](media/cpp-cmake-run-tests.png "CTest uruchomienia testów")


## <a name="see-also"></a>Zobacz też
[Pisanie testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md)


  







