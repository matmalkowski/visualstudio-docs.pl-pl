---
title: Jak używać Boost.Test dla języka C++ w programie Visual Studio
ms.date: 01/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: eadcc8f2a3e50f9a23da3e3bbc6689c643904470
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751627"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Jak używać Boost.Test dla języka C++ w programie Visual Studio

W **programu Visual Studio 2017 wersji 15,5 cala** i później, Boost.Test adapter testowy jest zintegrowany z programu Visual Studio IDE jako składnik **tworzenia klasycznych aplikacji w języku C++** obciążenia.

![Adapter testowy dla Boost.Test](media/cpp-boost-component.png)

Jeśli nie masz **tworzenia klasycznych aplikacji w języku C++** obciążenia zainstalowany, otwórz **Instalator programu Visual Studio** i wybierz **Modyfikuj**. Wybierz **tworzenia klasycznych aplikacji w języku C++** obciążenia, a następnie wybierz **Modyfikuj** przycisku.

## <a name="install-boost"></a>Zainstaluj zwiększanie wyniku

Wymaga Boost.Test [zwiększanie wyniku](http://www.boost.org/)! Jeśli nie masz zwiększanie wyniku zainstalowane, zalecane jest użycie Vcpkg Menedżera pakietów.

1. Postępuj zgodnie z instrukcjami w [Vcpkg: Menedżer pakietów C++ dla systemu Windows](/cpp/vcpkg) do zainstalowania vcpkg (Jeśli nie masz jeszcze go).

1. Zainstaluj biblioteki dynamicznej lub statycznej Boost.Test:

    - Uruchom **vcpkg zainstalować zwiększanie wyniku testu** zainstalować bibliotekę dynamiczną Boost.Test.

       -OR-

    - Uruchom **vcpkg zainstalować zwiększanie wyniku-testu: x 86 windows statycznej** do zainstalowania z biblioteką statyczną Boost.Test.

1. Uruchom **vcpkg integracji instalacji** do konfigurowania programu Visual Studio z biblioteki i dodać ścieżki do nagłówków zwiększenie wydajności i pliki binarne.

## <a name="add-the-item-template-visual-studio-2017-version-156-and-later"></a>Dodaj szablon elementu (Visual Studio 2017 wersji 15.6 i nowsze)

1. Aby utworzyć plik .cpp dla testów, kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj nowy element**.

   ![Szablon elementu Boost.Test](media/boost_test_item_template.png)

1. Nowy plik zawiera przykładowe metody testowej. Skompilowanie projektu Aby włączyć **Eksploratora testów** metody odnajdywania.

Szablon elementu używa wariant jeden nagłówek Boost.Test, ale można modyfikować #include ścieżkę do użycia autonomicznego variant biblioteki. Aby uzyskać więcej informacji, zobacz [Dodaj zawiera dyrektywy, które](#add_include_directives).

## <a name="create-a-test-project-visual-studio-2017-version-155"></a>Tworzenie projektu testu (Visual Studio 2017 wersji 15,5 cala)

W programie Visual Studio 2017 wersji 15,5 cala nie testu wstępnie skonfigurowane szablony projektów lub elementów są dostępne dla Boost.Test. W związku z tym należy utworzyć i skonfigurować projekt aplikacji konsoli do przechowywania testów.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł rozwiązania i wybierz **Dodaj** > **nowy projekt...** .

1. W okienku po lewej stronie wybierz **Visual C++** > **Windows Desktop**, a następnie wybierz pozycję **aplikacji konsoli systemu Windows** szablonu.

1. Nadaj nazwę projektu i wybierz polecenie **OK**.
1. Usuń `main` funkcji w pliku .cpp.

1. Jeśli używasz wersji nagłówka jednym lub dynamicznej biblioteki Boost.Test, przejdź do [Dodaj zawiera dyrektywy, które](#add_include_directives). Jeśli używasz wersji biblioteki statycznej, następnie należy wykonać pewne dodatkowe czynności konfiguracyjne:

   a. Aby edytować plik projektu, najpierw zwolnić ją. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Zwolnij projekt**. Następnie kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Edytuj < nazwa\>.vcxproj**.

   b. Dodaj dwa wiersze do **Globals** grupy właściwości, jak pokazano poniżej:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```
   c. Zapisz i Zamknij \*plik .vcxproj, a następnie ponownie Załaduj projekt.

   d. Aby otworzyć **strony właściwości**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **właściwości**.

   d. Rozwiń węzeł **C/C++** > **generowania kodu**, a następnie wybierz **biblioteki wykonawczej**. Wybierz **/MTd** dla bibliotek statycznych środowiska uruchomieniowego debugowania lub **/MT** wersji biblioteki statycznej środowiska wykonawczego.

   f. Rozwiń węzeł **konsolidatora > System**. Sprawdź, czy **podsystemu** ustawiono **konsoli**.

   g. Wybierz **OK** zamknąć strony właściwości.

## <a name="add-include-directives"></a>Dodaj dyrektyw

1. W pliku .cpp testowego, Dodaj wszelkie potrzebne `#include` dyrektywy, aby wyświetlić typy i funkcje programu kod testu. Zazwyczaj program działa jeden poziom w hierarchii folderów. W przypadku wpisania `#include "../"`, okno IntelliSense pojawia się i umożliwia wybranie pełną ścieżkę do pliku nagłówka.

   ![Dodaj # dyrektywy include](media/cpp-gtest-includes.png)

   Można użyć z biblioteki autonomicznej:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   Lub użyj wersji nagłówka jeden z:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Następnie zdefiniuj `BOOST_TEST_MODULE`.

Poniższy przykład jest wystarczająca dla testu być wykrywalny w **Eksploratora testów**:

```cpp
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp\> //single-header
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my\_boost_test)
{
    std::string expected_value = "Bill";

    // assume MyClass is defined in MyClass.h
    // and get_value() has public accessibility
    MyClass mc;
    BOOST_CHECK(expected_value == mc.get_value());
}
```

## <a name="write-and-run-tests"></a>Zapis i uruchamiania testów
Teraz można przystąpić do zapisu i uruchamiać testy zwiększanie wyniku. Zobacz [zwiększanie wyniku testu biblioteka dokumentacji](http://www.boost.org/doc/libs/release/libs/test/doc/html/index.html) informacji o makra testu. Zobacz [uruchamiania testów jednostkowych za pomocą narzędzia Eksplorator testów](run-unit-tests-with-test-explorer.md) informacji o odnajdywaniu, uruchamiania i grupowanie testów przy użyciu **Eksploratora testów**.

## <a name="see-also"></a>Zobacz także
[Pisanie testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md)
