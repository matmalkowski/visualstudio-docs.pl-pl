---
title: "Pisanie testów jednostkowych dla biblioteki DLL języka C++ w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84575412-1de7-4e53-811d-ae035eb21d13
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ac5389640c486d5b886454c15dc0e979c0683caf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Pisanie testów jednostkowych dla biblioteki DLL języka C++ w programie Visual Studio

 Istnieje kilka sposobów do testowania kodu biblioteki DLL, w zależności od tego, czy eksportuje te funkcje, które mają zostać przetestowane. Wybierz jedną z następujących sposobów:  
  
 **Testy jednostkowe wywołać tylko funkcje, które są eksportowane z biblioteki DLL:**  
 Dodaj projekt testowy oddzielne zgodnie z opisem w [pisania testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md). W projekcie testowym Dodaj odwołanie do projektu biblioteki DLL.  
  
 Przejdź do procedury [odwołanie z projektu DLL eksportowane funkcje do](#projectRef).  
  
 **Biblioteka DLL jest tworzone w postaci pliku .exe:**  
 Dodaj projekt testowy oddzielne. Umieść Link do pliku wyjściowego obiektu.  
  
 Przejdź do procedury [Aby połączyć testy z plików obiektu lub biblioteki](#objectRef).  
  
 **Funkcji niebędący elementem członkowskim wywołania testy jednostek, które nie są eksportowane z biblioteki DLL i biblioteki DLL może być utworzone jako bibliotekę statyczną:**  
 Zmień projektu biblioteki DLL, dzięki czemu jest on skompilowany do pliku lib. Dodaj projekt testowy oddzielne, który odwołuje się do projektu w ramach testu.  
  
 Takie podejście charakteryzuje się korzyści wynikające z umożliwienia testów używać członków wyeksportowane, ale nadal zachować testy w oddzielnych projektu.  
  
 Przejdź do procedury [zmienić biblioteki DLL do biblioteki statycznej](#staticLink).  
  
 **Testy jednostkowe musi wywoływać funkcje niebędący elementem członkowskim, które nie są eksportowane i kod muszą zostać skompilowane jako biblioteki dołączanej dynamicznie (DLL):**  
 Dodawanie testów jednostkowych w tym samym projekcie jako kod produktu.  
  
 Przejdź do procedury [dodać testów jednostkowych w tym samym projekcie](#sameProject).  
  
## <a name="creating-the-tests"></a>Tworzenie testów  
  
###  <a name="staticLink"></a>Aby zmienić biblioteki DLL do biblioteki statycznej  
  
-   Jeśli testy muszą używać elementów członkowskich, które nie są eksportowane przez projektu biblioteki DLL, a projekt w ramach testu jest skompilowany jako bibliotekę dynamiczną, należy wziąć pod uwagę konwersją biblioteką statyczną.  
  
    1.  W **Eksploratora rozwiązań**, w menu skrótów projektu w ramach testu, wybierz **właściwości**. Zostanie otwarte okno właściwości projektu.  
  
    2.  Wybierz **właściwości konfiguracji | Ogólne**.  
  
    3.  Ustaw **typu konfiguracji** do **biblioteka statyczna (lib)**.  
  
 Przejdź do procedury [Aby połączyć testy z plików obiektu lub biblioteki](#objectRef).  
  
###  <a name="projectRef"></a>Odwołanie do wyeksportowanych funkcji DLL z projektu testowego  
  
-   Jeśli projekt DLL eksportuje funkcji, które mają zostać przetestowane, można dodać odwołania do projektu kodu z projektu testowego.  
  
    1.  Utwórz natywny jednostkowy projekt testowy.  
  
        1.  Na **pliku** menu, wybierz **nowy | Projekt | Visual C++, Test | C++ jednostkowy projekt testowy**.  
  
    2.  W **Eksploratora rozwiązań**, w menu skrótów projektu testowego, wybierz **odwołania**. Zostanie otwarte okno właściwości projektu.  
  
    3.  Wybierz **wspólne właściwości | Framework i odwołania**, a następnie wybierz pozycję **Dodaj nowe odwołanie** przycisku.  
  
    4.  Wybierz **projektów**, a następnie projektu do sprawdzenia.  
  
         Wybierz **Dodaj** przycisku.  
  
    5.  We właściwościach projektu testowego Dodaj lokalizację projektu w ramach testu do katalogi dołączenia.  
  
         Wybierz **właściwości konfiguracji | Katalogi VC ++ | Dołącz katalogi**.  
  
         Wybierz **Edytuj**, a następnie Dodaj nagłówek katalogu projektu w ramach testu.  
  
 Przejdź do [pisania testów jednostkowych](#addTests).  
  
###  <a name="objectRef"></a>Aby połączyć testy z plików obiektu lub biblioteki  
  
-   Biblioteki DLL nie eksportuje funkcji, które mają zostać przetestowane, można dodać danych wyjściowych **.obj** lub **.lib** pliku zależności projektu testowego.  
  
    1.  Utwórz natywny jednostkowy projekt testowy.  
  
        1.  Na **pliku** menu, wybierz **nowy | Projekt | Visual C++ | Test | Natywny jednostkowy projekt testowy**.  
  
    2.  W **Eksploratora rozwiązań**, w menu skrótów projektu testowego, wybierz **właściwości**.  
  
    3.  Wybierz **właściwości konfiguracji | Konsolidator | Dane wejściowe | Dodatkowe zależności**.  
  
         Wybierz **Edytuj**i Dodaj nazwy **.obj** lub **.lib** plików. Nie należy używać nazw pełną ścieżkę.  
  
    4.  Wybierz **właściwości konfiguracji | Konsolidator | Ogólne | Katalogi bibliotek dodatkowe**.  
  
         Wybierz **Edytuj**i Dodaj ścieżkę katalogu **.obj** lub **.lib** plików. Ścieżka jest zwykle w folderze kompilacji projektu w ramach testu.  
  
    5.  Wybierz **właściwości konfiguracji | Katalogi VC ++ | Dołącz katalogi**.  
  
         Wybierz **Edytuj**, a następnie Dodaj nagłówek katalogu projektu w ramach testu.  
  
 Przejdź do [pisania testów jednostkowych](#addTests).  
  
###  <a name="sameProject"></a>Aby dodać testów jednostkowych w tym samym projekcie  
  
1.  Modyfikuj właściwości projektu kodu produktu użycie nagłówków i pliki bibliotek, które są wymagane w celu przeprowadzania testów jednostkowych.  
  
    1.  W **Eksploratora rozwiązań**, w menu skrótów projektu w ramach testu, wybierz polecenie Właściwości. Zostanie otwarte okno właściwości projektu.  
  
    2.  Wybierz **właściwości konfiguracji | Katalogi VC ++**.  
  
    3.  Edytuj katalogi dołączania i biblioteki:  
  
        |||  
        |-|-|  
        |**Dołącz katalogi** | **$(VCInstallDir)UnitTest\include;$(IncludePath)**|  
        |**Katalogi bibliotek** | **$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|  
  
2.  Dodaj plik testu jednostkowego języka C++:  
  
    -   W **Eksploratora rozwiązań**, w menu skrótów projektu, wybierz opcję **Dodaj | Nowy element | Test jednostkowy C++**.  
  
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
  
## <a name="run-the-tests"></a>Uruchom testy  
  
1.  Na **testu** menu, wybierz **systemu Windows | Testowanie Explorer**.  
2. Jeśli wszystkie testy nie są widoczne w oknie, klikając prawym przyciskiem myszy jego węzła w kompilacji projektu testowego **Eksploratora rozwiązań** i wybierając polecenie **kompilacji** lub **odbudować**.
  
2.  W Eksploratorze testów, wybierz **Uruchom wszystkie**, lub wybierz określonych testów, który chcesz uruchomić. Kliknij prawym przyciskiem myszy na test na inne opcje, w tym, uruchomienie jej w trybie debugowania punkty włączone.
  
## <a name="see-also"></a>Zobacz też
[Szybki start: programowanie sterowane testami za pomocą narzędzia Eksplorator testów](../test/quick-start-test-driven-development-with-test-explorer.md)

  
## <a name="see-also"></a>Zobacz też  
 [Pisanie testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md)   
 [Dokumentacja interfejsu API z Microsoft.VisualStudio.TestTools.CppUnitTestFramework](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)   
 [Wskazówki: Tworzenie i używanie biblioteki dołączanej dynamicznie (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)   
 [Importowanie i eksportowanie](/cpp/build/importing-and-exporting)
