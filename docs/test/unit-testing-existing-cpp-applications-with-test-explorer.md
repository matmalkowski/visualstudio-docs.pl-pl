---
redirect_url: /visualstudio/test/how-to-use-microsoft-test-framework-for-cpp
ms.openlocfilehash: 7ab917a55d9a2d00a8d4635e2de45cd43cbe02f2
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="how-to-use-the-microsoft-unit-testing-framework-for-c"></a>Jak używać Framework testów jednostkowych Microsoft dla języka C++
Zaleca się, że przed wprowadzeniem zmian w istniejącej aplikacji, należy upewnić się, że ma dobrej pokrycia przy użyciu testów jednostkowych. Daje to pewność, że zmiany nie zostały wprowadzone usterki. Jeśli aplikacja nie ma testów jednostkowych, możesz dodać je przy użyciu techniki przedstawiona w tym temacie. W tym temacie opisano sposób dodawania testów jednostkowych dla istniejącego kodu Visual C++, począwszy od o wyborze sposobu testu z kodu, a następnie tworzenie zapisu, a na koniec testów.  
  
## <a name="deciding-how-to-test-your-code"></a>Podejmowania decyzji o sposobie do testowania kodu  
 Otwórz istniejący projekt C++ i sprawdzić, aby zdecydować, jak dodać testów jednostkowych. Można używać niektórych narzędzi modelowania, które pomocy, zobacz zależności w kodzie i pomóc zrozumieć sposób interakcji części. Aby uzyskać więcej informacji, zobacz [tworzenie wizualizacji kodu](../modeling/visualize-code.md).  
  
 Firma Microsoft zaleca, aby oddzielić zmiany na małych zadania. Przed każdym mała zmiana, zapis testów jednostkowych dla aspekty zachowania, która jest taka sama. Te testy będą w dalszym ciągu przekazać po dokonaniu zmiany. Na przykład jeśli zamierzasz zmienić funkcji sortowania, tak aby sortuje listę osób przez nazwisko zamiast według imienia, następnie napisać testu jednostkowego, która sprawdza, czy wszystkie nazwy wejściowe są wyświetlane w danych wyjściowych. Po wprowadzeniu zmiany można dodać nowego testów jednostkowych dla nowe zachowanie.  
  
 Jeśli jest to możliwe, część lub wszystkie testy jednostkowe należy używać tylko funkcje, które zostaną wyeksportowane. Jednak w przypadku zmiany tylko niewielką częścią całej aplikacji, a następnie można użyć funkcji, które nie są eksportowane. Można na przykład testy, które wywołują funkcje wewnętrznej lub testy, które Ustawianie i pobieranie wartości zmiennych wewnętrznych.  
  
 Istnieje kilka sposobów do testowania kodu produktu, w zależności od tego, czy eksponuje interfejsów, które mają zostać przetestowane. Wybierz jedną z następujących sposobów:  
  
 **Testy jednostkowe można wywołać tylko funkcje, które są eksportowane z kodu w ramach testu:**  
 Dodaj projekt testowy oddzielne. W projekcie testowym Dodaj odwołanie do projektu w ramach testu.  
  
 Przejdź do procedury [odwołanie z projektu testowego eksportowane funkcje do](#projectRef).  
  
 **Kod w ramach testu jest tworzone w postaci pliku .exe:**  
 Dodaj projekt testowy oddzielne. Umieść Link do pliku wyjściowego obiektu.  
  
 Przejdź do procedury [Aby połączyć testy z plików obiektu lub biblioteki](#objectRef).  
  
 **Testy jednostkowe musi używać funkcji prywatnych i danych, a testowanego kodu mogą być wbudowane jako bibliotekę statyczną:**  
 Zmienić projekt w ramach testu, dzięki czemu jest on skompilowany do pliku lib. Dodaj projekt testowy oddzielne, który odwołuje się do projektu w ramach testu.  
  
 Takie podejście charakteryzuje się korzyści wynikające z umożliwienia testów używać prywatne elementy członkowskie, ale nadal zachować testy w oddzielnych projektu. Jednak może nie być odpowiednie dla pewnych aplikacji gdzie musi mieć biblioteki dołączanej dynamicznie (dll).  
  
 Przejdź do procedury [Aby zmienić kod w ramach testu do biblioteki statycznej](#staticLink).  
  
 **Testy jednostkowe musi używać funkcji prywatnego elementu członkowskiego i danych, a kod muszą zostać skompilowane jako biblioteki dołączanej dynamicznie (DLL):**  
 Dodawanie testów jednostkowych w tym samym projekcie jako kod produktu.  
  
 Przejdź do procedury [dodać testów jednostkowych w tym samym projekcie](#sameProject).  
  
## <a name="creating-the-tests"></a>Tworzenie testów  
  
###  <a name="staticLink"></a>Aby zmienić kod w ramach testu do biblioteki statycznej  
  
-   Jeśli testy muszą używać elementów członkowskich, które nie są eksportowane przez projekt w ramach testu, a projekt w ramach testu jest skompilowany jako bibliotekę dynamiczną, należy wziąć pod uwagę konwersją biblioteką statyczną.  
  
    1.  W Eksploratorze rozwiązań, w menu skrótów projektu w ramach testu, wybierz **właściwości**. Zostanie otwarte okno właściwości projektu.  
  
    2.  Wybierz **właściwości konfiguracji**, **ogólne**.  
  
    3.  Ustaw **typu konfiguracji** do **biblioteka statyczna (lib)**.  
  
 Przejdź do procedury [Aby połączyć testy z plików obiektu lub biblioteki](#objectRef).  
  
###  <a name="projectRef"></a>Odwołanie do wyeksportowanych funkcji DLL z projektu testowego  
  
-   Jeśli projekt w ramach testu jest biblioteki DLL, które eksportuje funkcji, które mają zostać przetestowane, można dodać odwołania do projektu kodu z projektu testowego.  
  
    1.  Tworzenie projektu C++ testu.  
  
        1.  Na **pliku** menu, wybierz **nowy**, **projektu**, **Visual C++, testowanie**, **C++ jednostkowy projekt testowy**.  
  
    2.  W Eksploratorze rozwiązań, w menu skrótów projektu testowego, wybierz **odwołania**. Zostanie otwarte okno właściwości projektu.  
  
    3.  Wybierz **wspólne właściwości**, **Framework i odwołania**, a następnie wybierz pozycję **Dodaj nowe odwołanie** przycisku.  
  
    4.  Wybierz **projektów**, a następnie projektu do sprawdzenia.  
  
         Wybierz **Dodaj** przycisku.  
  
    5.  We właściwościach projektu testowego Dodaj lokalizację projektu w ramach testu do katalogi dołączenia.  
  
         Wybierz **właściwości konfiguracji**, **katalogi VC ++**, **Dołącz katalogi**.  
  
         Wybierz **Edytuj**, a następnie Dodaj nagłówek katalogu projektu w ramach testu.  
  
 Przejdź do [pisania testów jednostkowych](#addTests).  
  
###  <a name="objectRef"></a>Aby połączyć testy z plików obiektu lub biblioteki  
  
-   Jeśli kod w ramach testu nie eksportuje funkcji, które mają zostać przetestowane, można dodać danych wyjściowych **.obj** lub **.lib** pliku zależności projektu testowego.  
  
    1.  Tworzenie projektu C++ testu.  
  
        1.  Na **pliku** menu, wybierz **nowy**, **projektu**, **Visual C++, testowanie**, **C++ jednostkowy projekt testowy**.  
  
    2.  W Eksploratorze rozwiązań, w menu skrótów projektu testowego, wybierz **właściwości**. Zostanie otwarte okno właściwości projektu.  
  
    3.  Wybierz **właściwości konfiguracji**, **konsolidatora**, **dane wejściowe**, **dodatkowe zależności**.  
  
         Wybierz **Edytuj**i Dodaj nazwy **.obj** lub **.lib** plików. Nie należy używać nazw pełną ścieżkę.  
  
    4.  Wybierz **właściwości konfiguracji**, **konsolidatora**, **ogólne**, **katalogi bibliotek dodatkowe**.  
  
         Wybierz **Edytuj**i Dodaj ścieżkę katalogu **.obj** lub **.lib** plików. Ścieżka jest zwykle w folderze kompilacji projektu w ramach testu.  
  
    5.  Wybierz **właściwości konfiguracji**, **katalogi VC ++**, **Dołącz katalogi**.  
  
         Wybierz **Edytuj**, a następnie Dodaj nagłówek katalogu projektu w ramach testu.  
  
 Przejdź do [pisania testów jednostkowych](#addTests).  
  
###  <a name="sameProject"></a>Aby dodać testów jednostkowych w tym samym projekcie  
  
1.  Modyfikuj właściwości projektu kodu produktu użycie nagłówków i pliki bibliotek, które są wymagane w celu przeprowadzania testów jednostkowych.  
  
    1.  W Eksploratorze rozwiązań w menu skrótów projektu w ramach testu, wybierz polecenie Właściwości. Zostanie otwarte okno właściwości projektu.  
  
    2.  Wybierz **właściwości konfiguracji**, **katalogi VC ++**.  
  
    3.  Edytuj katalogi dołączania i biblioteki:  
  
        |||  
        |-|-|  
        |**Dołącz katalogi**|**$(VCInstallDir)UnitTest\include;$(IncludePath)**|  
        |**Katalogi bibliotek**|**$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|  
  
2.  Dodaj plik testu jednostkowego języka C++:  
  
    -   W Eksploratorze rozwiązań, w menu skrótów projektu, wybierz **Dodaj**, **nowy element**, a następnie wybierz pozycję **testu jednostkowego języka C++**.  
  
 Przejdź do [pisania testów jednostkowych](#addTests).  
  
##  <a name="addTests"></a>Pisanie testów jednostkowych  
  
1.  W każdym kodu plik testu jednostkowego dodać `#include` instrukcji w nagłówkach projektu w ramach testu.  
  
2.  Dodaj test klasy i metody do plików kodu testu jednostki. Na przykład:  
  
    ```cpp  
    #include "stdafx.h"  
    #include "CppUnitTest.h"  
    #include "MyProjectUnderTest.h"  
    using namespace Microsoft::VisualStudio::CppUnitTestFramework;  
    namespace MyTest  
    {  
      TEST_CLASS(MyTests)  
      {  
      public:  
          TEST_METHOD(MyTestMethod)  
          {  
              Assert::AreEqual(MyProject::Multiply(2,3), 6);  
          }  
      };  
    }  
    ```  
  
 Aby uzyskać więcej informacji, zobacz [testowania kodu natywnego za pomocą narzędzia Eksplorator testów jednostkowych](http://msdn.microsoft.com/en-us/8a09d6d8-3613-49d8-9ffe-11375ac4736c).  
  
## <a name="run-the-tests"></a>Uruchom testy  
  
1.  Na **testu** menu, wybierz **Windows**, **Eksploratora testów**.  
2. Jeśli wszystkie testy nie są widoczne w oknie, klikając prawym przyciskiem myszy jego węzła w kompilacji projektu testowego **Eksploratora rozwiązań** i wybierając polecenie **kompilacji** lub **odbudować**.
  
2.  W Eksploratorze testów, wybierz **Uruchom wszystkie**, lub wybierz określonych testów, który chcesz uruchomić. Kliknij prawym przyciskiem myszy na test na inne opcje, w tym, uruchomienie jej w trybie debugowania punkty włączone.
  
## <a name="see-also"></a>Zobacz też
[Szybki Start: Test programowanie sterowane za pomocą narzędzia Eksplorator testów](../test/quick-start-test-driven-development-with-test-explorer.md)

