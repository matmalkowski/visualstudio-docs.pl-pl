---
title: "Pisanie testów jednostkowych dla C/C++ w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 11/04/2017
ms.technology: vs-ide-test
ms.topic: article
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: ecb611d7ab816ed99e4bcce954466309f7436f76
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Pisanie testów jednostkowych dla C/C++ w programie Visual Studio

Możesz wpisać i uruchom testy jednostkowe C++ za pomocą **Eksploratora testów** okna, podobnie jak w przypadku innych języków. Aby uzyskać więcej informacji o korzystaniu z **Eksploratora testów**, zobacz [uruchamiania testów jednostkowych za pomocą narzędzia Eksplorator testów](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> Niektóre funkcje, takie jak Live testów jednostkowych, kodowanych testów interfejsu użytkownika i IntelliTest nie są obsługiwane dla języka C++.

Visual Studio zawiera tych platform testów C++ z nie dodatkowe pliki do pobrania wymagane:

- Microsoft testu jednostkowego Framework dla języka C++
- Google Test
- Boost.Test
- CTest

Oprócz zainstalowanych struktur można napisać własny adapter testowy dla dowolnego framework chcesz użyć w programie Visual Studio. Adapter testowy można zintegrować testów jednostkowych z **Eksploratora testów** okna. Kilka kart innych firm są dostępne na [Visual Studio Marketplace](https://marketplace.visualstudio.com). Aby uzyskać więcej informacji, zobacz [instalowanie platform testów jednostkowych innych firm](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 wersji 15,5 cala**

- **Adapter testowy Google** jest uwzględniana jako część domyślnego **tworzenia klasycznych aplikacji w języku C++** obciążenia. Wybrano szablon projektu, które można dodać do rozwiązania za pomocą **Dodawanie nowego projektu** menu kontekstowego w węźle rozwiązania w **Eksploratora rozwiązań**i można skonfigurować za pomocą opcji **narzędzia | Opcje**. Aby uzyskać więcej informacji, zobacz [porady: Użyj Google testu w programie Visual Studio](how-to-use-google-test-for-cpp.md).

- **Boost.Test** jest uwzględniana jako część domyślnego **tworzenia klasycznych aplikacji w języku C++** obciążenia. Jest zintegrowany z **Eksploratora testów** , ale obecnie nie ma szablonu projektu, dlatego należy go ręcznie skonfigurować. Aby uzyskać więcej informacji, zobacz [porady: Użyj Boost.Test w programie Visual Studio](how-to-use-boost-test-for-cpp.md).

- **CTest** pomocy technicznej jest dołączana do [CMake Tools for Visual Studio](/cpp/ide/cmake-tools-for-cpp) składnika, który jest częścią programu **tworzenia klasycznych aplikacji w języku C++** obciążenia. Jednak CTest nie jest jeszcze pełni zintegrowana z **Eksploratora testów**. Aby uzyskać więcej informacji, zobacz [porady: Użyj CTest w programie Visual Studio](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 i starsze wersje**

Możesz pobrać adapter testowy Google i Boost.Test karty rozszerzeń dla programu Visual Studio Marketplace w [Adapter testowy dla Boost.Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) i [karty testu dla testu Google](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest).

## <a name="basic-test-workflow"></a>Podstawowy test przepływu pracy

W poniższych sekcjach przedstawiono podstawowe czynności ułatwiających rozpoczęcie pracy z testy jednostkowe C++. Podstawowa konfiguracja jest bardzo podobny dla platform firmy Microsoft i testowania Google. Boost.Test wymaga ręcznie utworzyć projektu testowego.

### <a name="create-a-test-project"></a>Tworzenie projektu testu

Definiowanie i uruchom testy wewnątrz projekty testowe, które znajdują się w tym samym rozwiązaniu jako kod, który ma zostać przetestowana. Aby dodać nowy projekt testowy do istniejącego rozwiązania, kliknij prawym przyciskiem myszy węzeł rozwiązania w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj | Nowy projekt**. Następnie w okienku po lewej stronie wybierz **Visual C++ Test** i wybierz jeden z typów projektów w środkowym okienku. Na poniższej ilustracji przedstawiono projekty testowe, które są dostępne podczas obliczania **projektowania aplikacji w języku C++** obciążenie jest zainstalowany:

![Testowanie projektów C++](media/cpp-new-test-project.png "C++ przetestować nowe szablony projektu")

### <a name="create-references-to-other-projects-in-the-solution"></a>Tworzenie odwołań do innych projektów w rozwiązaniu

Aby włączyć swój kod testu, aby uzyskać dostęp do funkcji w projekcie, który ma zostać przetestowana, Dodaj odwołanie do projektu w projekcie testowym. Kliknij prawym przyciskiem myszy węzeł projektu testu w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj | Odwołanie**. Następnie w oknie dialogowym Wybierz projekty, które mają zostać przetestowane.

![Dodaj odwołanie](media/cpp-add-ref-test-project.png "testu C++ Dodaj odwołanie do projektów ma zostać przetestowana")

### <a name="add-include-directives-for-header-files"></a>Dodaj #include dyrektywy pliki nagłówka

Następnie w pliku .cpp testu jednostki, Dodaj `#include` dyrektywy dla nagłówka pliki, które deklaruje typy i funkcje, która ma zostać przetestowana. Typ `#include "` i IntelliSense będzie aktywować ułatwiające wybór. Powtórz dla dowolnych dodatkowych nagłówków.

![Dodaj zawiera dyrektywy, które](media/cpp-add-includes-test-project.png "testu C++ dodać zawiera pliki nagłówka")

### <a name="write-test-methods"></a>Zapis metody testowe

> [!NOTE]
> W tej sekcji przedstawiono składnię dla Framework testów jednostkowych firmy Microsoft do C/C++. Jest opisanych tutaj: [dokumentacja interfejsu API z Microsoft.VisualStudio.TestTools.CppUnitTestFramework](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Google Test dokumentację można znaleźć [Elementarz testu Google](https://github.com/google/googletest/blob/master/googletest/docs/Primer.md). Aby uzyskać Boost.Test, zobacz [zwiększanie wyniku testu biblioteki: Frameworka testów jednostkowych](http://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

Plik .cpp w projekcie testowym ma Klasa zastępcza i metody zdefiniowane dla użytkownika, na przykład dotyczących tworzenia, testowania kodu. Należy pamiętać, że podpisy makra TEST_CLASS i TEST_METHOD, które metody wykrywalny z okna narzędzia Eksplorator testów.

![Dodaj zawiera dyrektywy, które](media/cpp-write-test-methods.png "testu C++ dodać zawiera pliki nagłówka")

TEST_CLASS i TEST_METHOD należą [Microsoft natywnych testów Framework]((microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). **Testowanie Explorer** odnajduje metody testowe w innych obsługiwanych platform, w podobny sposób.

TEST_METHOD zwraca typ void. Aby uzyskać wynik testu, użyj metody statyczne w `Assert` klasy do przetestowania rzeczywiste wyniki oczekiwano. W poniższym przykładzie założono `MyClass` zawiera konstruktora przyjmującego który `std::string`. Można sprawdzić, czy Konstruktor inicjuje klasy zgodnie z oczekiwaniami w następujący sposób:

```cpp
        TEST_METHOD(TestClassInit)
        {
            std::string name = "Bill";
            MyClass mc(name);
            Assert::AreEqual(name, mc.GetName());
        }
```
W poprzednim przykładzie, wynik `Assert::AreEqual` wywołania Określa, czy test przekazuje lub kończy się niepowodzeniem. Klasa Assert zawiera wiele innych metod do porównywania oczekiwano a rzeczywiste wyniki.

Możesz dodać *cech* do testowania metod do określenia badanie właścicieli, priorytet i inne informacje. Te wartości można następnie użyć, sortować i grupować testów w **Eksploratora testów**. Aby uzyskać więcej informacji, zobacz [uruchamiania testów jednostkowych za pomocą narzędzia Eksplorator testów](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Uruchom testy

1. Na **testu** menu, wybierz **Windows** > **Eksploratora testów**. Na poniższej ilustracji przedstawiono projektu testowego, w których testów nie został jeszcze uruchomiony.

   ![Testowanie Explorer przed uruchomieniem testów](media/cpp-test-explorer.png "C++ narzędzia Eksplorator testów")

   > [!NOTE]
   > Integracja CTest z **Eksploratora testów** nie jest jeszcze dostępna. Uruchom testy CTest z poziomu menu głównego CMake.

1. Jeśli wszystkie testy nie są widoczne w oknie, klikając prawym przyciskiem myszy jego węzła w kompilacji projektu testowego **Eksploratora rozwiązań** i wybierając polecenie **kompilacji** lub **odbudować**.

1. W Eksploratorze testów, wybierz **Uruchom wszystkie**, lub wybierz określonych testów, który chcesz uruchomić. Kliknij prawym przyciskiem myszy na test na inne opcje, w tym, uruchomienie jej w trybie debugowania punkty włączone. Po uruchomieniu wszystkich testów, okno zawiera testy, które przekazane i te, które nie powiodło się:

![Testowanie Explorer po uruchomieniu testów](media/cpp-test-explorer-passed.png "C++ Eksploratora testów po uruchomieniu testów")

Testy nie powiodły się komunikat oferuje szczegółowe informacje, które pomogą zdiagnozować przyczynę. Możesz kliknij prawym przyciskiem myszy na niepowodzenie testu i **Debuguj zaznaczone testy** do kroku przy użyciu funkcji, w którym wystąpił błąd.

Aby uzyskać więcej informacji o korzystaniu z **Eksploratora testów**, zobacz [uruchamiania testów jednostkowych za pomocą narzędzia Eksplorator testów](run-unit-tests-with-test-explorer.md).

Aby uzyskać najlepsze rozwiązania dotyczące przeprowadzania testów jednostkowych, zobacz [teście jednostkowym](unit-test-basics.md)

## <a name="see-also"></a>Zobacz także

[Testowanie jednostek kodu](unit-test-your-code.md)