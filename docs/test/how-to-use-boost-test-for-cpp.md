---
title: "Jak używać Boost.Test dla języka C++ w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0710a8-8e8a-4f6e-8415-5ab3eb830079
caps.latest.revision: "14"
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: af55f9f124b2ec609c4f0a590e7c2fab738624d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Jak używać Boost.Test dla języka C++ w programie Visual Studio
W **programu Visual Studio 2017 wersji 15,5 cala** i później, Boost.Test jest zintegrowana w środowisku IDE programu Visual Studio jako składnik **Develoment pulpitu z C++** obciążenia. Aby zainstalować go na komputerze, otwórz Instalator programu Visual Studio i Znajdź **karty Boost.Test** na liście składników obciążenia:

![Zainstaluj zwiększanie wyniku testu](media/cpp-boost-component.png "zainstalować Boost.Test dla języka C++")

## <a name="install-boost"></a>Zainstaluj zwiększanie wyniku

 Wymaga Boost.Test [zwiększanie wyniku](http://www.boost.org/)! Jeśli nie masz zwiększanie wyniku zainstalowane, zalecane jest użycie Vcpkg Menedżera pakietów. 

1. Postępuj zgodnie z instrukcjami w [Vcpkg: Menedżer pakietów C++ dla systemu Windows](/cpp/vcpkg) do zainstalowania vcpkg (Jeśli nie masz jeszcze go).
2. Uruchom `vcpkg install boost` do zainstalowania bibliotek zwiększanie wyniku.
3. Uruchom `vcpkg integrate install` polecenia do konfigurowania programu Visual Studio z biblioteki i dodać ścieżki do nagłówków zwiększenie wydajności i pliki binarne. 

## <a name="create-a-project-for-your-tests"></a>Utwórz projekt dla testów
W programie Visual Studio 2017 wersji 15,5 cala nie testu wstępnie skonfigurowane szablony projektów lub elementów są dostępne dla Boost.Test. W związku z tym należy utworzyć projekt aplikacji konsoli do przechowywania testów. Testowanie szablonów dla Boost.Test są planowane do uwzględnienia w przyszłych wersjach programu Visual Studio. 

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł rozwiązania i wybierz **Dodaj | Nowy projekt**. 
2. W okienku po lewej stronie wybierz **Windows Desktop** , a następnie wybierz **aplikacji konsoli systemu Windows** w środkowym okienku. 
3. Nadaj nazwę projektu, a następnie kliknij przycisk **OK**. 

## <a name="add-include-directives"></a>Dodaj dyrektyw
W pliku .cpp testowego, Dodaj wszelkie potrzebne `#include` dyrektywy, aby wyświetlić typy i funkcje programu kod testu. Zazwyczaj program działa jeden poziom w hierarchii folderów. W przypadku wpisania `#include "../"` są wyświetlane i umożliwia wybór pełną ścieżkę do pliku nagłówka okna IntelliSense.

![Dodaj # dyrektywy include](media/cpp-gtest-includes.png "Dodaj zawiera dyrektywy, które do pliku .cpp testu")

Co najmniej musisz uwzględniają [jeden nagłówek wariant Boost.Test](http://www.boost.org/doc/libs/1_48_0/libs/test/doc/html/utf/user-guide/usage-variants/single-header-variant.html) z `#include <path>/unit_test.hpp` i zdefiniuj `BOOST_TEST_MODULE`. Poniższy przykład jest wystarczająca dla testu być wykrywalny w **Eksploratora testów**:

```cpp
#include "stdafx.h"
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp>
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my_boost_test)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual();
    BOOST_CHECK(name == mc.GetName());
}
```

## <a name="write-and-run-tests"></a>Zapis i uruchamiania testów
Teraz można przystąpić do zapisu i uruchamiać testy zwiększanie wyniku. Zobacz [zwiększanie wyniku testu biblioteka dokumentacji](http://www.boost.org/doc/libs/1_38_0/libs/test/doc/html/index.html) informacji o makra testu. Zobacz [uruchamiania testów jednostkowych za pomocą narzędzia Eksplorator testów](run-unit-tests-with-test-explorer.md) informacji o odnajdywaniu, uruchamiania i grupowanie testów przy użyciu **Eksploratora testów**.

## <a name="see-also"></a>Zobacz też
[Pisanie testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md)


  







