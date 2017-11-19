---
title: "Jak używać CTest dla języka C++ w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8b30934-5f38-4a18-8819-263e0733cdbe
caps.latest.revision: "14"
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7e1d00460a4acf26f23c256f8eb0180360315a98
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Jak używać CTest dla języka C++ w programie Visual Studio
CMake (w tym CTest) jest zintegrowany jako część programu Visual Studio IDE **Develoment pulpitu z C++** obciążenia. Aby zainstalować go na komputerze, otwórz Instalator programu Visual Studio i Znajdź [CMake Tools dla Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) na liście składników obciążenia.

Obsługa CMake w programie Visual Studio nie wiąże się z systemu projektu programu Visual Studio. W związku z tym zapisu i konfigurowanie CTest testów, tak samo jak w dowolnym środowisku CMake. Zobacz [CMake Tools dla Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) uzyskać więcej informacji o użyciu CMake programu Visual Studio.

**Visual Studio 2017 wersji 15,5 cala** CTest nie jest zintegrowany z **Eksploratora testów**. Można uruchomić testów z poziomu menu głównego CMake lub z menu kontekstowego **CMakeLists.txt** w pliku **Eksploratora rozwiązań**. Wyniki testu są kierowane do programu Visual Studio **okno danych wyjściowych**.

![Uruchom testy CTest](media/cpp-cmake-run-tests.png "CTest uruchomienia testów")


## <a name="see-also"></a>Zobacz też
[Pisanie testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md)


  







