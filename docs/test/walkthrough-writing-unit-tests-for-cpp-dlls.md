---
title: "Porady: pisanie testów jednostkowych dla bibliotek DLL C++ | Dokumentacja firmy Microsoft"
ms.date: 11/04/2017
ms.technology: vs-ide-test
ms.topic: article
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 40ec25b25c3aefd6cc5e759c70362cf7e5f1855e
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-write-unit-tests-for-c-dlls"></a>Porady: pisanie testów jednostkowych dla biblioteki DLL języka C++

Ten przewodnik opisuje sposób rozwijać natywnej biblioteki DLL C++ przy użyciu metodologii pierwszego testu. Podstawowe kroki są następujące:

1.  [Tworzenie projektu testu natywnego](#create_test_project). Projekt testowy znajduje się w tym samym rozwiązaniu jako projektu biblioteki DLL.

2.  [Tworzenie projektu biblioteki DLL](#create_dll_project). W tym przewodniku tworzy nowej biblioteki DLL, ale jest podobna procedura testowania istniejącej biblioteki DLL.

3.  [Uwidaczniania funkcji DLL testów](#make_functions_visible).

4.  [Wielokrotnie powtarzane rozszerzyć testy](#iterate). Firma Microsoft zaleca cyklu "czerwony zielony zrefaktoryzuj", w którym programowanie kodu zostanie przeprowadzony przez testy.

5.  [Debugowanie w przypadku braku testy](#debug). Testy można uruchomić w trybie debugowania.

6.  [Refaktoryzuj podczas aktualizowania testy bez zmian](#refactor). Refaktoryzacja oznacza poprawy struktury kodu bez zmiany zachowania zewnętrznych. Możesz zrobić to, aby zwiększyć wydajność, rozszerzalności lub czytelność kodu. Ponieważ jest nie należy zmienić to zachowanie, nie należy zmieniać testów podczas wprowadzania zmian refaktoryzacji w kodzie. Testy pomocy, upewnij się, że nie znajdą się usterki podczas są refaktoryzacji.

7.  [Sprawdź pokrycia](using-code-coverage-to-determine-how-much-code-is-being-tested.md). Testy jednostkowe są bardziej użyteczna, gdy korzystają oni więcej kodu. Może odnajdywać, które części kodu zostały już użyte przez testy.

8.  [Izolowanie jednostki z zasobów zewnętrznych](using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md). Zazwyczaj biblioteki DLL jest zależny od innych składników systemu, które tworzysz, takie jak innych bibliotek DLL, baz danych lub podsystemami zdalnego. Warto przetestować każda jednostka w izolacji od jego zależności. Zewnętrzne składniki można wykonać testy działać wolniej. Podczas tworzenia inne składniki mogą być niekompletne.

##  <a name="create_test_project"></a> Utwórz natywny jednostkowy projekt testowy

1.  Na **pliku** menu, wybierz **nowy | Projekt**.

     W oknie dialogowym Rozwiń **zainstalowana | Szablony | Visual C++ | Test**.

     Wybierz **natywny jednostkowy projekt testowy** szablon lub zainstalowany niezależnie od preferowanego framework. Jeśli wybierzesz inny szablon, takich jak Google testu lub Boost.Test podstawowych zasad są takie same, chociaż niektóre szczegóły będą się różnić.

     W tym przewodniku, nosi nazwę projektu testowego `NativeRooterTest`.

     ![Tworzenie projektu testu jednostkowego języka C++](../test/media/utecpp01.png "UteCpp01")

2.  W nowym projekcie sprawdzić **unittest1.cpp**

     ![Projekt testowy z TESTEM&#95;klasy i testowania&#95;metody](../test/media/utecpp2.png "UteCpp2")

     Zwróć uwagę, że:

    -   Każdy test jest definiowana za pomocą `TEST_METHOD(YourTestName){...}`.

         Nie trzeba zapisać podpis funkcji z konwencjonalnej. Podpis jest tworzony za pomocą makra TEST_METHOD. Makro generuje funkcję wystąpienia, który zwraca typ void. Generuje on funkcję statyczną, która zwraca informacje na temat metody testowej. Informacje te pozwalają Eksploratora testów można znaleźć metody.

    -   Metody testowe są podzielone na klasy przy użyciu `TEST_CLASS(YourClassName){...}`.

         Gdy testy są uruchamiane, tworzone jest wystąpienie klasy każdego testu. Metody testowe są nazywane w nieokreślonej kolejności. Można określić specjalne metody, które są wywoływane przed i po każdej modułu, klasy lub metody.

3.  Sprawdź, że testy uruchamiane w Eksploratorze testów:

    1.  Wstaw kod testu:

        ```cpp
        TEST_METHOD(TestMethod1)
        {
            Assert::AreEqual(1,1);
        }
        ```

         Zwróć uwagę, że `Assert` klasa udostępnia kilka metod statycznych, których można użyć, aby zweryfikować wyniki w metodach.

    2.  Na **testu** menu, wybierz **Uruchom | Wszystkie testy**.

         Test kompiluje i uruchamia.

         Eksplorator testów jest wyświetlana.

         Uruchomienie testu jest wyświetlany w obszarze **przekazany testy**.

         ![Jednostki Eksploratora testów z jednej testowej przekazany](../test/media/utecpp04.png "UteCpp04")

##  <a name="create_dll_project"></a> Tworzenie projektu biblioteki DLL

1.  Utwórz **Visual C++** projektu przy użyciu **projektu Win32** szablonu.

     W tym przewodniku projektu o nazwie `RootFinder`.

     ![Tworzenie projektu C++ Win32](../test/media/utecpp05.png "UteCpp05")

2.  Wybierz **DLL** i **eksportować symbole** w Kreatorze aplikacji Win32.

     **Eksportować symbole** opcja generuje wygodny makra, które służy do deklarowania wyeksportowanych metod.

     ![Kreator projektu C++ ustaw dla biblioteki DLL i eksportowanie symboli](../test/media/utecpp06.png "UteCpp06")

3.  Deklarowanie wyeksportowanej funkcji w pliku .h główna:

     ![Nowy kod projektu i .h plik DLL przy użyciu interfejsu API makr](../test/media/utecpp07.png "UteCpp07")

     Deklarator `__declspec(dllexport)` powoduje, że publiczne i chronione elementy członkowskie klasy jako widoczny spoza biblioteki DLL. Aby uzyskać więcej informacji, zobacz [korzystanie z dllimport i dllexport w klasach C++](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes).

4.  W pliku .cpp podmiotu zabezpieczeń Dodaj minimalnego treści funkcji:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

##  <a name="make_functions_visible"></a> Kilka projekt testowy do projektu biblioteki DLL

1.  Dodaj projektu biblioteki DLL do odwołań projektu do projektu testowego:

    1.  Otwórz właściwości projektu testowego i wybierz polecenie **wspólne właściwości**, **Framework i odwołania**.

         ![Właściwości projektu C++ | Struktura i odwołań](../test/media/utecpp08.png "UteCpp08")

    2.  Wybierz **Dodaj nowe odwołanie**.

         W **Dodaj odwołanie** oknie dialogowym Wybierz projektu biblioteki DLL a wybierz **Dodaj**.

         ![Właściwości projektu C++ | Dodaj nowe odwołanie](../test/media/utecpp09.png "UteCpp09")

2.  W pliku .cpp testu jednostki główną należy dołączyć plik .h kodu biblioteki DLL:

    ```cpp
    #include "..\RootFinder\RootFinder.h"
    ```

3.  Dodaj podstawowy test, który używa wyeksportowanej funkcji:

    ```cpp
    TEST_METHOD(BasicTest)
    {
       CRootFinder rooter;
       Assert::AreEqual(
          // Expected value:
          0.0,
          // Actual value:
          rooter.SquareRoot(0.0),
          // Tolerance:
          0.01,
         // Message:
         L"Basic test failed",
         // Line number - used if there is no PDB file:
         LINE_INFO());
    }
    ```

4.  Skompiluj rozwiązanie.

     Nowego testu jest widoczny w Eksploratorze testów.

5.  W Eksploratorze testów, wybierz **Uruchom wszystkie**.

     ![Eksplorator testów jednostkowych &#45; podstawowy Test przekazany](../test/media/utecpp10.png "UteCpp10")

 Ma ustawienie testu i projekty kodu i sprawdzić, czy można uruchamiać testy, które uruchamiania funkcji w projekcie kodu. Teraz można rozpocząć pisanie rzeczywistych testów i kod.

##  <a name="iterate"></a> Wielokrotnie powtarzane rozszerzyć testy i były przekazywane

1.  Dodaj nowego testu:

    ```cpp
    TEST_METHOD(RangeTest)
    {
      CRootFinder rooter;
      for (double v = 1e-6; v < 1e6; v = v * 3.2)
      {
        double actual = rooter.SquareRoot(v*v);
        Assert::AreEqual(v, actual, v/1000);
      }
    }
    ```

    > [!TIP]
    > Firma Microsoft zaleca, nie należy zmieniać testy, które zostały przekazane. Zamiast tego dodać nowego testu, zaktualizuj kod, dzięki czemu test zakończył się pomyślnie, a następnie dodaj innego testu i tak dalej.
    >
    > Użytkownicy zmiany ich wymagań, wyłącz testy, które nie są już prawidłowe. Zapisz nowe testy i ich działania pojedynczo, w taki sam sposób przyrostowy.

2.  Skompiluj rozwiązanie, a następnie w Eksploratorze testów, wybierz **Uruchom wszystkie**.

     Nowy test zakończy się niepowodzeniem.

     ![Niepowodzenia RangeTest](../test/media/ute_cpp_testexplorer_rangetest_fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")

    > [!TIP]
    > Upewnij się, że każdy test zakończy się niepowodzeniem, natychmiast po jej napisano. Dzięki temu można uniknąć łatwe błąd zapisu testu, który nigdy nie zakończy się niepowodzeniem.

3.  Tak, aby nowy test zakończył się pomyślnie, należy zwiększyć kod biblioteki DLL:

    ```cpp
    #include <math.h>
    ...
    double CRootFinder::SquareRoot(double v)
    {
      double result = v;
      double diff = v;
      while (diff > result/1000)
      {
        double oldResult = result;
        result = result - (result*result - v)/(2*result);
        diff = abs (oldResult - result);
      }
      return result;
    }
    ```

4.  Skompiluj rozwiązanie, a następnie w Eksploratorze testów, wybierz pozycję **Uruchom wszystkie**.

     Zarówno testy zostały zaliczone pomyślnie.

     ![Eksplorator testów jednostkowych &#45; zakresu pomyślny](../test/media/utecpp12.png "UteCpp12")

    > [!TIP]
    > Opracuj kodu, dodając testy jednym naraz. Upewnij się, że wszystkie testy zostały zaliczone pomyślnie po każdej iteracji.

##  <a name="debug"></a> Debuguj test się niepowodzeniem

1.  Dodawanie innego testu:

    ```cpp
    #include <stdexcept>
    ...
    // Verify that negative inputs throw an exception.
    TEST_METHOD(NegativeRangeTest)
    {
      wchar_t message[200];
      CRootFinder rooter;
      for (double v = -0.1; v > -3.0; v = v - 0.5)
      {
        try
        {
          // Should raise an exception:
          double result = rooter.SquareRoot(v);

          _swprintf(message, L"No exception for input %g", v);
          Assert::Fail(message, LINE_INFO());
        }
        catch (std::out_of_range ex)
        {
          continue; // Correct exception.
        }
        catch (...)
        {
          _swprintf(message, L"Incorrect exception for %g", v);
          Assert::Fail(message, LINE_INFO());
        }
      }
    }
    ```

2.  Skompiluj rozwiązanie, a następnie wybierz pozycję **Uruchom wszystkie**.

3.  Otwórz lub kliknij dwukrotnie testu nie powiodło się.

     Zostanie wyróżniona potwierdzenia nie powiodło się. Komunikat o błędzie jest widoczny w okienku szczegółów Eksploratora testów.

     ![NegativeRangeTests failed](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")

4.  Aby zobaczyć, dlaczego test zakończy się niepowodzeniem, krok przy użyciu funkcji:

    1.  Ustaw punkt przerwania na początku funkcji SquareRoot.

    2.  Menu skrótów nie powiodło się testu, wybierz **Debuguj zaznaczone testy**.

         Po zatrzymaniu uruchomienia na punkt przerwania, wykonywać krokowo kodu.

5.  Wstawianie kodu w funkcji, które tworzysz:

    ```cpp

    #include <stdexcept>
    ...
    double CRootFinder::SquareRoot(double v)
    {
        // Validate parameter:
        if (v < 0.0)
        {
          throw std::out_of_range("Can't do square roots of negatives");
        }

    ```

6.  Teraz przejść pomyślnie wszystkie testy.

     ![Wszystkie testy zostały zaliczone pomyślnie](../test/media/ute_ult_alltestspass.png "UTE_ULT_AllTestsPass")

> [!TIP]
>  Jeśli poszczególne testy nie ma żadnych zależności, które uniemożliwiają uruchomione w dowolnej kolejności, włącz wykonywanie równoległe testu z ![UTE&#95;parallelicon&#45;małych](../test/media/ute_parallelicon-small.png "małych UTE_parallelicon") przycisk przełączania na pasku narzędzi. To znacznie ograniczyć czas potrzebny na uruchamianie wszystkich testów.

##  <a name="refactor"></a> Zrefaktoryzuj kod bez zmiany testów

1.  Uproszczenia obliczeń centralnej w funkcji SquareRoot:

    ```
    // old code:
    //   result = result - (result*result - v)/(2*result);
    // new code:
         result = (result + v/result)/2.0;

    ```

2.  Skompiluj rozwiązanie, a następnie wybierz pozycję **Uruchom wszystkie**, aby upewnić się, że nie zostały wprowadzone wystąpił błąd.

    > [!TIP]
    > Dobry zestaw testów jednostkowych daje pewność, że nie użyto usterki po zmianie kodu.
    >
    > Zachowaj refaktoryzacji oddzielona od innych zmian.

## <a name="next-steps"></a>Następne kroki

-   **Izolacja.** Większość bibliotek DLL są zależne od innych podsystemów, takie jak bazy danych i inne biblioteki dll. Tych składników często są tworzone jednocześnie. Aby umożliwić testowanie wykonywanego inne składniki nie są jeszcze dostępne jednostki, należy zastąpić mock lub

-   **Tworzenie testów weryfikacji.** Może mieć testów wykonanych na serwerze kompilacji zespołu w ustalonych odstępach czasu. Dzięki temu usterki nie są wprowadzane podczas pracy kilka członków zespołu jest zintegrowany.

-   **Testów zaewidencjonowania.** Aby wprowadzić, że niektóre testy są wykonywane przed każdego członka zespołu sprawdza kod do kontroli źródła. Jest to zazwyczaj podzbiór pełny zestaw testów weryfikacji kompilacji.

     Można również wprowadzić minimalny poziom pokrycia kodu.

## <a name="see-also"></a>Zobacz także

- [Dodawanie testów jednostkowych do istniejących aplikacji C++](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)
- [Using Microsoft.VisualStudio.TestTools.CppUnitTestFramework](../test/using-microsoft-visualstudio-testtools-cppunittestframework.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Przewodnik: tworzenie i używanie biblioteki dołączanej dynamicznie (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Importowanie i eksportowanie](/cpp/build/importing-and-exporting)
