---
title: "Jak przetestować biblioteki DLL programu Visual C++ dla aplikacji platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24afc90a-8774-4699-ab01-6602a7e6feb2
caps.latest.revision: "13"
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4fc133d96f8306b46e4d820b6f7256db8c471122
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="how-to-test-a-visual-c-dll-for-uwp-apps"></a>Jak przetestować biblioteki DLL programu Visual C++ dla aplikacji platformy uniwersalnej systemu Windows 
W tym temacie opisano jeden ze sposobów tworzenia testów jednostkowych dla biblioteki DLL języka C++ dla aplikacji systemu Windows platformy Uniwersalnej Framework testów firmy Microsoft dla języka C++. Biblioteki DLL RooterLib pokazuje niezrozumiała chwile teorii limit z calculus zaimplementowanie funkcji, która oblicza szacunkową pierwiastek kwadratowy z podanej liczbie. Biblioteka DLL może następnie uwzględniane w aplikacji platformy uniwersalnej systemu Windows, która przedstawia użytkownikowi fun, co można zrobić za pomocą matematycznych.  
  
 W tym temacie przedstawiono sposób użycia testowania jako pierwszy krok w rozwoju jednostek. W takie podejście należy najpierw zapisać metody testowej, która sprawdza określone zachowanie w systemie, testowany, a następnie napisać kod, który przekazuje testu. Wprowadzenie zmian w kolejności poniższych procedur, można cofnąć tej strategii do pierwszej operacji zapisu kod, który chcesz przetestować, a następnie wpisz testów jednostkowych.  
  
 W tym temacie tworzy także jedno rozwiązanie Visual Studio i oddzielne projektów testów jednostkowych i biblioteki DLL, która ma zostać przetestowana. Testy jednostkowe mogą również obejmować bezpośrednio w projekcie biblioteki DLL lub można utworzyć oddzielne rozwiązania dla testów jednostkowych i. BIBLIOTEKI DLL. Zobacz [Dodawanie testów jednostkowych do istniejących aplikacji C++](../test/unit-testing-existing-cpp-applications-with-test-explorer.md) uzyskać porady na temat struktury, których do użycia.  
  
##  <a name="In_this_topic"></a>W tym temacie  

 [Tworzenie rozwiązania i jednostkowy projekt testowy](#Create_the_solution_and_the_unit_test_project)  
  
 [Sprawdź, że testy uruchamiane w narzędzia Eksplorator testów](#Verify_that_the_tests_run_in_Test_Explorer)  
  
 [Dodaj do rozwiązania projektu biblioteki DLL](#Add_the_DLL_project_to_the_solution)  
  
 [Udostępnienie funkcji DLL dla kodowanego testu](#make_the_dll_functions_visible_to_the_test_code)  
  
 [Wielokrotnie powtarzane rozszerzyć testy i były przekazywane](#Iteratively_augment_the_tests_and_make_them_pass)  
  
 [Debuguj test się niepowodzeniem](#Debug_a_failing_test)  
  
 [Zrefaktoryzuj kod bez zmiany testów](#Refactor_the_code_without_changing_tests)  
  
##  <a name="Create_the_solution_and_the_unit_test_project"></a>Tworzenie rozwiązania i jednostkowy projekt testowy  
  
1.  Na **pliku** menu, wybierz **nowy**, a następnie wybierz pozycję **nowy projekt**.  
  
2.  W oknie dialogowym Nowy projekt, rozwiń węzeł **zainstalowana**, następnie rozwiń węzeł **Visual C++** i wybierz polecenie **UWP**. Następnie wybierz pozycję **Biblioteka testów jednostkowych (aplikacji platformy UWP)** z listy szablonów projektu.  
  
     ![Utwórz & C &43; 43; Biblioteka testów jednostkowych](../test/media/ute_cpp_windows_unittestlib_create.png "UTE_Cpp_windows_UnitTestLib_Create")  
  
3.  Nazwij projekt `RooterLibTests`; Określ lokalizację; Nazwa rozwiązania `RooterLib`; i upewnij się, że **Utwórz katalog rozwiązania** jest zaznaczony.  
  
     ![Określ nazwę rozwiązań i projektów i lokalizację](../test/media/ute_cpp_windows_unittestlib_createspecs.png "UTE_Cpp_windows_UnitTestLib_CreateSpecs")  
  
4.  W nowym projekcie, otwórz **unittest1.cpp**.  
  
     ![unittest1.cpp](../test/media/ute_cpp_windows_unittest1_cpp.png "UTE_Cpp_windows_unittest1_cpp")  
  
     Należy pamiętać o następujących kwestiach:  
  
    -   Każdy test jest definiowana za pomocą `TEST_METHOD(YourTestName){...}`.  
  
         Nie trzeba zapisać podpis funkcji z konwencjonalnej. Podpis jest tworzony za pomocą makra TEST_METHOD. Makro generuje funkcję wystąpienia, który zwraca typ void. Generuje on funkcję statyczną, która zwraca informacje na temat metody testowej. Informacje te pozwalają Eksploratora testów można znaleźć metody.  
  
    -   Metody testowe są podzielone na klasy przy użyciu `TEST_CLASS(YourClassName){...}`.  
  
         Gdy testy są uruchamiane, tworzone jest wystąpienie klasy każdego testu. Metody testowe są nazywane w nieokreślonej kolejności. Można określić specjalne metody, które są wywoływane przed i po każdej modułu, klasy lub metody. Aby uzyskać więcej informacji, zobacz [korzystanie z Microsoft.VisualStudio.TestTools.CppUnitTestFramework](../test/using-microsoft-visualstudio-testtools-cppunittestframework.md) w bibliotece MSDN.  
  
##  <a name="Verify_that_the_tests_run_in_Test_Explorer"></a>Sprawdź, że testy uruchamiane w narzędzia Eksplorator testów  
  
1.  Wstaw kod testu:  
  
    ```cpp  
    TEST_METHOD(TestMethod1)  
    {  
        Assert::AreEqual(1,1);  
    }  
    ```  
  
     Zwróć uwagę, że `Assert` klasa udostępnia kilka metod statycznych, których można użyć, aby zweryfikować wyniki w metodach.  
  
2.  Na **testu** menu, wybierz **Uruchom** , a następnie wybierz **Uruchom wszystkie**.  
  
     Projekt testowy kompiluje i uruchamia. Zostanie wyświetlone okno Eksploratora testów i test zostanie wyświetlony w obszarze **przekazany testy**. Okienko Podsumowanie w dolnej części okna zawiera dodatkowe szczegóły dotyczące wybranego testu.  
  
     ![Testowanie Explorer](../test/media/ute_cpp_testexplorer_testmethod1.png "UTE_Cpp_TestExplorer_TestMethod1")  
  
##  <a name="Add_the_DLL_project_to_the_solution"></a>Dodaj do rozwiązania projektu biblioteki DLL  
  
1.  W Eksploratorze rozwiązań wybierz nazwę rozwiązania. Z menu skrótów wybierz **Dodaj**, a następnie **Dodawanie nowego projektu**.  
  
     ![Utwórz projekt RooterLib](../test/media/ute_cpp_windows_rooterlib_create.png "UTE_Cpp_windows_RooterLib_Create")  
  
2.  W **Dodawanie nowego projektu** oknie dialogowym wybierz **DLL (aplikacji platformy UWP)**.  
  
3.  Dodaj następujący kod do **RooterLib.h** pliku:  
  
    ```cpp  
    // The following ifdef block is the standard way of creating macros which make exporting   
    // from a DLL simpler. All files within this DLL are compiled with the ROOTERLIB_EXPORTS  
    // symbol defined on the command line. This symbol should not be defined on any project  
    // that uses this DLL. This way any other project whose source files include this file see   
    // ROOTERLIB_API functions as being imported from a DLL, whereas this DLL sees symbols  
    // defined with this macro as being exported.  
    #ifdef ROOTERLIB_EXPORTS  
    #define ROOTERLIB_API  __declspec(dllexport)  
    #else  
    #define ROOTERLIB_API __declspec(dllimport)  
    #endif //ROOTERLIB_EXPORTS  
  
    class ROOTERLIB_API CRooterLib {  
    public:  
        CRooterLib(void);  
        double SquareRoot(double v);  
    };  
    ```  
  
     Komentarze wyjaśnić blok ifdef nie deweloperowi biblioteki DLL tylko dla każdego, kto odwołuje się do biblioteki DLL w ich projektu. ROOTERLIB_EXPORTS symbol można dodać do wiersza polecenia przy użyciu właściwości projektu biblioteki dll.  
  
     `CRooterLib` Klasy deklaruje konstruktora i `SqareRoot` metody narzędzia do szacowania.  
  
4.  Dodaj ROOTERLIB_EXPORTS symbol do wiersza polecenia.  
  
    1.  W Eksploratorze rozwiązań wybierz **RooterLib** projektu, a następnie wybierz pozycję **właściwości** z menu skrótów.  
  
         ![Dodawanie definicji symboli preprocesora](../test/media/ute_cpp_windows_addpreprocessorsymbol.png "UTE_Cpp_windows_AddPreprocessorSymbol")  
  
    2.  W oknie dialogowym strony właściwości RooterLib rozwiń **właściwości konfiguracji**, rozwiń węzeł **C++** i wybierz polecenie **preprocesora**.  
  
    3.  Wybierz  **\<Edytuj >** z **definicje preprocesora** listy, a następnie dodaj `ROOTERLIB_EXPORTS` w oknie dialogowym Definicje preprocesora.  
  
5.  Dodaj minimalnego implementacje zadeklarowanej funkcji. Otwórz **RooterLib.cpp** i Dodaj następujący kod:  
  
    ```  
    // constructor  
    CRooterLib::CRooterLib()  
    {  
    }  
  
    // Find the square root of a number.  
    double CRooterLib::SquareRoot(double v)  
    {  
        return 0.0;  
    }  
  
    ```  
  
##  <a name="make_the_dll_functions_visible_to_the_test_code"></a>Udostępnienie funkcji dll dla kodowanego testu  
  
1.  Dodaj RooterLib do projektu RooterLibTests.  
  
    1.  W Eksploratorze rozwiązań wybierz **RooterLibTests** projektu, a następnie wybierz pozycję **odwołania...**  menu skrótów.  
  
    2.  W oknie dialogowym właściwości projektu RooterLib rozwiń **wspólne właściwości** i wybierz polecenie **Framework i odwołania**.  
  
    3.  Wybierz **dodać nowego odwołania...**  
  
    4.  W **Dodaj odwołanie** okna dialogowego rozwiń **rozwiązania** , a następnie wybierz **projekty**. Następnie wybierz **RouterLib** elementu.  
  
2.  Załącz plik nagłówka RooterLib w **unittest1.cpp**.  
  
    1.  Otwórz **unittest1.cpp**.  
  
    2.  Dodaj ten kod poniżej `#include "CppUnitTest.h"` wiersza:  
  
        ```cpp  
        #include "..\RooterLib\RooterLib.h"  
        ```  
  
3.  Dodaj test, który używa funkcji zaimportowany. Dodaj następujący kod do **unittest1.cpp**:  
  
    ```  
    TEST_METHOD(BasicTest)  
    {  
        CRooterLib rooter;  
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
  
     Nowy test zostanie wyświetlony w Eksploratorze testów w **nie Uruchom testy** węzła.  
  
5.  W Eksploratorze testów, wybierz **Uruchom wszystkie**.  
  
     ![Podstawowy Test przekazany](../test/media/ute_cpp_testexplorer_basictest.png "UTE_Cpp_TestExplorer_BasicTest")  
  
 Ma ustawienie testu i projekty kodu i sprawdzić, czy można uruchamiać testy, które uruchamiania funkcji w projekcie kodu. Teraz można rozpocząć pisanie rzeczywistych testów i kod.  
  
##  <a name="Iteratively_augment_the_tests_and_make_them_pass"></a>Wielokrotnie powtarzane rozszerzyć testy i były przekazywane  
  
1.  Dodaj nowego testu:  
  
    ```  
    TEST_METHOD(RangeTest)  
    {  
        CRooterLib rooter;  
        for (double v = 1e-6; v < 1e6; v = v * 3.2)  
        {  
            double expected = v;  
            double actual = rooter.SquareRoot(v*v);  
            double tolerance = expected/1000;  
            Assert::AreEqual(expected, actual, tolerance);  
        }  
    };  
  
    ```  
  
    > [!TIP]
    >  Firma Microsoft zaleca, nie należy zmieniać testy, które zostały przekazane. Zamiast tego dodać nowego testu, zaktualizuj kod, dzięki czemu test zakończył się pomyślnie, a następnie dodaj innego testu i tak dalej.  
    >   
    >  Użytkownicy zmiany ich wymagań, wyłącz testy, które nie są już prawidłowe. Zapisz nowe testy i ich działania pojedynczo, w taki sam sposób przyrostowy.  
  
2.  W Eksploratorze testów, wybierz **Uruchom wszystkie**.  
  
3.  Test zakończy się niepowodzeniem.  
  
     ![Niepowodzenia RangeTest](../test/media/ute_cpp_testexplorer_rangetest_fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")  
  
    > [!TIP]
    >  Upewnij się, że każdy test zakończy się niepowodzeniem, natychmiast po jej napisano. Dzięki temu można uniknąć łatwe błąd zapisu testu, który nigdy nie zakończy się niepowodzeniem.  
  
4.  Ulepszanie testowanego kodu tak, aby nowy test zakończył się pomyślnie. Dodaj następujący kod do **RooterLib.cpp**:  
  
    ```cpp  
    #include <math.h>  
    ...  
    // Find the square root of a number.  
    double CRooterLib::SquareRoot(double v)  
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
  
5.  Skompiluj rozwiązanie, a następnie w Eksploratorze testów, wybierz pozycję **Uruchom wszystkie**.  
  
     Zarówno testy zostały zaliczone pomyślnie.  
  
> [!TIP]
>  Opracuj kodu, dodając testy jednym naraz. Upewnij się, że wszystkie testy zostały zaliczone pomyślnie po każdej iteracji.  
  
##  <a name="Debug_a_failing_test"></a>Debuguj test się niepowodzeniem  
  
1.  Dodawanie innego testu do **unittest1.cpp**:  
  
    ```  
    // Verify that negative inputs throw an exception.  
     TEST_METHOD(NegativeRangeTest)  
     {  
       wchar_t message[200];  
       CRooterLib rooter;  
       for (double v = -0.1; v > -3.0; v = v - 0.5)  
       {  
         try   
         {  
           // Should raise an exception:  
           double result = rooter.SquareRoot(v);  
  
           swprintf_s(message, L"No exception for input %g", v);  
           Assert::Fail(message, LINE_INFO());  
         }  
         catch (std::out_of_range ex)  
         {  
           continue; // Correct exception.  
         }  
         catch (...)  
         {  
           swprintf_s(message, L"Incorrect exception for %g", v);  
           Assert::Fail(message, LINE_INFO());  
         }  
       }  
    };  
  
    ```  
  
2.  W Eksploratorze testów, wybierz **Uruchom wszystkie**.  
  
     Test zakończy się niepowodzeniem. Wybierz nazwę testu w Eksploratorze testów. Zostanie wyróżniona potwierdzenia nie powiodło się. Komunikat o błędzie jest widoczny w okienku szczegółów Eksploratora testów.  
  
     ![Nie powiodło się NegativeRangeTests](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")  
  
3.  Aby zobaczyć, dlaczego test zakończy się niepowodzeniem, krok przy użyciu funkcji:  
  
    1.  Ustaw punkt przerwania na początku `SquareRoot` funkcji.  
  
    2.  Menu skrótów nie powiodło się testu, wybierz **Debuguj zaznaczone testy**.  
  
         Po zatrzymaniu uruchomienia na punkt przerwania, wykonywać krokowo kodu.  
  
    3.  Dodaj kod, aby **RooterLib.cpp** do catch wyjątku:  
  
        ```  
        #include <stdexcept>  
        ...  
        double CRooterLib::SquareRoot(double v)  
        {  
            //Validate the input parameter:  
            if (v < 0.0)   
            {  
              throw std::out_of_range("Can't do square roots of negatives");  
            }  
        ...  
  
        ```  
  
    1.  W Eksploratorze testów, wybierz **Uruchom wszystkie** poprawiony metoda testowa i upewnij się, że nie wprowadzono regresji.  
  
 Teraz przejść pomyślnie wszystkie testy.  
  
 ![Wszystkie testy zostały zaliczone pomyślnie](../test/media/ute_ult_alltestspass.png "UTE_ULT_AllTestsPass")  
  
##  <a name="Refactor_the_code_without_changing_tests"></a>Zrefaktoryzuj kod bez zmiany testów  
  
1.  Uproszczenia obliczeń centralnej w `SquareRoot` funkcji:  
  
    ```  
    // old code  
    //result = result - (result*result - v)/(2*result);  
    // new code  
    result = (result + v/result) / 2.0;  
  
    ```  
  
2.  Wybierz **Uruchom wszystkie** refactored metoda testowa i upewnij się, że nie wprowadzono regresji.  
  
    > [!TIP]
    >  Stabilna zestaw testów jednostkowych dobrej daje pewność, że nie użyto usterki po zmianie kodu.  
    >   
    >  Zachowaj refaktoryzacji oddzielona od innych zmian.
