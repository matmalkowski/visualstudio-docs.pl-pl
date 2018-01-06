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
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b469ee739ebdc4f3cf61e8b5e578c676b5af5e24
ms.sourcegitcommit: 0614bdb0895b6e6f5b84ba4e1d9327802eca3a6b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/06/2018
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Jak używać Boost.Test dla języka C++ w programie Visual Studio

W **programu Visual Studio 2017 wersji 15,5 cala** i później, Boost.Test adapter testowy jest zintegrowany z programu Visual Studio IDE jako składnik **tworzenia klasycznych aplikacji w języku C++** obciążenia.

![Adapter testowy dla Boost.Test](media/cpp-boost-component.png "Adapter testowy dla składnika Boost.Test")

Jeśli nie masz **tworzenia klasycznych aplikacji w języku C++** obciążenia zainstalowany, otwórz **Instalator programu Visual Studio** i wybierz **Modyfikuj**. Wybierz **tworzenia klasycznych aplikacji w języku C++** obciążenia, a następnie wybierz **Modyfikuj** przycisku.

## <a name="install-boost"></a>Zainstaluj zwiększanie wyniku

Wymaga Boost.Test [zwiększanie wyniku](http://www.boost.org/)! Jeśli nie masz zwiększanie wyniku zainstalowane, zalecane jest użycie Vcpkg Menedżera pakietów.

1. Postępuj zgodnie z instrukcjami w [Vcpkg: Menedżer pakietów C++ dla systemu Windows](/cpp/vcpkg) do zainstalowania vcpkg (Jeśli nie masz jeszcze go).

1. Uruchom `vcpkg install boost:x86-windows-static` do zainstalowania z biblioteką statyczną zwiększanie wyniku.

1. Uruchom `vcpkg integrate install` polecenia do konfigurowania programu Visual Studio z biblioteki i dodać ścieżki do nagłówków zwiększenie wydajności i pliki binarne.

## <a name="create-a-project-for-your-tests"></a>Utwórz projekt dla testów

> [!NOTE]
> W programie Visual Studio 2017 wersji 15,5 cala nie testu wstępnie skonfigurowane szablony projektów lub elementów są dostępne dla Boost.Test. W związku z tym należy utworzyć projekt aplikacji konsoli do przechowywania testów. Testowanie szablonów dla Boost.Test są planowane do uwzględnienia w przyszłych wersjach programu Visual Studio.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł rozwiązania i wybierz **Dodaj** > **nowy projekt...** .

1. W okienku po lewej stronie wybierz **Visual C++** > **Windows Desktop**, a następnie wybierz pozycję **aplikacji konsoli systemu Windows** szablonu.

1. Nadaj nazwę projektu i wybierz polecenie **OK**.

## <a name="link-and-configuration-boost-static-library-only"></a>Łącze i konfiguracji (zwiększanie wyniku biblioteki statyczne tylko)

Skonfiguruj projekt w celu uruchomienia testów Boost.Test.

1. Aby edytować plik projektu, najpierw zwolnić ją. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Zwolnij projekt**. Następnie kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Edytuj < nazwa\>.vcxproj**.

1. Dodaj dwa wiersze do **Globals** grupy właściwości, jak pokazano poniżej:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```
1. Zapisz i Zamknij \*plik .vcxproj, a następnie ponownie Załaduj projekt.

1. Aby otworzyć **strony właściwości**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **właściwości**.

1. Rozwiń węzeł **C/C++** > **generowania kodu**, a następnie wybierz **biblioteki wykonawczej**. Wybierz `/MTd` dla bibliotek statycznych środowiska uruchomieniowego debugowania lub `/MT` wersji biblioteki statycznej środowiska wykonawczego.

1. Rozwiń węzeł **konsolidatora > System**. Sprawdź, czy **podsystemu** ustawiono **konsoli**.

1. Wybierz **OK** zamknąć strony właściwości.

## <a name="add-include-directives"></a>Dodaj dyrektyw

1. W przypadku `main` funkcji w pliku .cpp testu, usuń go.

1. W pliku .cpp testowego, Dodaj wszelkie potrzebne `#include` dyrektywy, aby wyświetlić typy i funkcje programu kod testu. Zazwyczaj program działa jeden poziom w hierarchii folderów. W przypadku wpisania `#include "../"`, okno IntelliSense pojawia się i umożliwia wybranie pełną ścieżkę do pliku nagłówka.

   ![Dodaj # dyrektywy include](media/cpp-gtest-includes.png "Dodaj zawiera dyrektywy, które do pliku .cpp testu")

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
Teraz można przystąpić do zapisu i uruchamiać testy zwiększanie wyniku. Zobacz [zwiększanie wyniku testu biblioteka dokumentacji](http://www.boost.org/doc/libs/1_38_0/libs/test/doc/html/index.html) informacji o makra testu. Zobacz [uruchamiania testów jednostkowych za pomocą narzędzia Eksplorator testów](run-unit-tests-with-test-explorer.md) informacji o odnajdywaniu, uruchamiania i grupowanie testów przy użyciu **Eksploratora testów**.

## <a name="see-also"></a>Zobacz także
[Pisanie testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md)