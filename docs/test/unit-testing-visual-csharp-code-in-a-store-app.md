---
title: Jednostka testowania kodu Visual C# w aplikacji platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: 0e0af23cca96238a0ea7bbcde11ac4507e55a9bc
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="unit-testing-visual-c-code-in-a-uwp-app"></a>Jednostka testowania kodu Visual C# w aplikacji platformy uniwersalnej systemu Windows

W tym temacie opisano jeden ze sposobów tworzenia testów jednostkowych dla klasy Visual C# w aplikacji platformy uniwersalnej systemu Windows. Klasa Rooter pokazuje niezrozumiała chwile teorii limit z calculus zaimplementowanie funkcji, która oblicza szacunkową pierwiastek kwadratowy z podanej liczbie. Aplikacja matematycznych następnie użyć tej funkcji do wyświetlenia użytkownika fun, co można zrobić za pomocą matematycznych.

W tym temacie przedstawiono sposób użycia testowania jako pierwszy krok w rozwoju jednostek. W takie podejście należy najpierw zapisać metody testowej, która sprawdza określone zachowanie w systemie, testowany, a następnie napisać kod, który przekazuje testu. Wprowadzenie zmian w kolejności poniższych procedur, można cofnąć tej strategii do pierwszej operacji zapisu kod, który chcesz przetestować, a następnie wpisz testów jednostkowych.

W tym temacie tworzy także jedno rozwiązanie Visual Studio i oddzielne projektów testów jednostkowych i biblioteki DLL, która ma zostać przetestowana. Testy jednostkowe mogą również obejmować bezpośrednio w projekcie biblioteki DLL, lub można utworzyć oddzielne rozwiązania testów jednostkowych i biblioteki DLL.

##  <a name="BKMK_Create_the_solution_and_the_unit_test_project"></a>Tworzenie rozwiązania i jednostkowy projekt testowy  
  
1.  Na **pliku** menu, wybierz **nowy** > **projektu...** .
  
2.  W **nowy projekt** okna dialogowego rozwiń **zainstalowana** > **Visual C#** i wybierz polecenie **uniwersalnych systemu Windows**. Następnie wybierz pozycję **pusta aplikacja** z listy szablonów projektu.
  
3.  Nazwij projekt `Maths` i upewnij się, że **Utwórz katalog rozwiązania** jest zaznaczone.  
  
4.  W Eksploratorze rozwiązań, wybieranie Nazwa rozwiązania, **Dodaj** z menu skrótów, a następnie wybierz pozycję **nowy projekt**.  
  
5.  W **nowy projekt** okna dialogowego rozwiń **zainstalowana**, następnie rozwiń węzeł **Visual C#** i wybierz polecenie **uniwersalnych systemu Windows** . Następnie wybierz pozycję **aplikacji testów jednostkowych (uniwersalna systemu Windows)** z listy szablonów projektu.
  
6.  Otwórz UnitTest1.cs w edytorze programu Visual Studio.  
  
    ```csharp  
  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;  
    using Maths;  
  
    namespace RooterTests  
    {  
        [TestClass]  
        public class UnitTest1  
  
            [TestMethod]  
            public void TestMethod1()  
            {  
  
            }  
  
    ```  
  
     Należy pamiętać o następujących kwestiach:  
  
    1.  Każdy test jest definiowana za pomocą `[TestMethod]`. Metoda testowa musi zwracać typ void i nie może mieć żadnych parametrów.  
  
    2.  Metody testowe musi być w klasie ozdobione `[TestClass]` atrybutu.  
  
         Gdy testy są uruchamiane, tworzone jest wystąpienie klasy każdego testu. Metody testowe są nazywane w nieokreślonej kolejności.  
  
    3.  Można określić specjalne metody, które są wywoływane przed i po każdej modułu, klasy lub metody. Aby uzyskać więcej informacji, zobacz [przy użyciu członków Microsoft.VisualStudio.TestTools.UnitTesting w testach jednostkowych](../test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md) w bibliotece MSDN.  
  
##  <a name="BKMK_Verify_that_the_tests_run_in_Test_Explorer"></a>Sprawdź, że testy uruchamiane w narzędzia Eksplorator testów  
  
1.  Wstaw kod testu w `TestMethod1` z **UnitTest1.cs** pliku:  
  
    ```csharp  
  
    [TestMethod]  
    public void TestMethod1()  
    {  
        Assert.AreEqual(0, 0);  
    }  
  
    ```  
  
     Zwróć uwagę, że `Assert` klasa udostępnia kilka metod statycznych, których można użyć, aby zweryfikować wyniki w metodach.  
  
2.  Na **testu** menu, wybierz **Uruchom** , a następnie wybierz **Uruchom wszystkie**.  
  
     Projekt testowy kompiluje i uruchamia. Zostanie wyświetlone okno Eksploratora testów i test zostanie wyświetlony w obszarze **przekazany testy**. Okienko Podsumowanie w dolnej części okna zawiera dodatkowe szczegóły dotyczące wybranego testu.  
  
     ![Testowanie Explorer](../test/media/ute_cpp_testexplorer_testmethod1.png "UTE_Cpp_TestExplorer_TestMethod1")  
  
##  <a name="BKMK_Add_the_Rooter_class_to_the_Maths_project"></a>Dodaj klasę Rooter do projektu matematycznych  
  
1.  W Eksploratorze rozwiązań wybierz **matematycznych** nazwę projektu. Z menu skrótów wybierz **Dodaj**, a następnie **klasy**.  
  
2.  Nazwa pliku klasy`Rooter.cs`  
  
3.  Dodaj następujący kod do klasy Rooter **Rooter.cs** pliku:  
  
    ```csharp  
  
    public Rooter()  
    {  
    }  
  
    // estimate the square root of a number  
    public double SquareRoot(double x)  
    {  
        return 0.0;  
    }  
  
    ```  
  
     `Rooter` Klasy deklaruje konstruktora i `SqareRoot` metody narzędzia do szacowania.  
  
4.  `SqareRoot` Metoda jest tylko minimalny implementacji wystarczającego do testowania podstawowej struktury testowania instalacji.  
  
##  <a name="BKMK_Couple_the_test_project_to_the_app_project"></a>Kilka projekt testowy do projektu aplikacji  
  
1.  Dodaj odwołanie do aplikacji matematycznych do projektu RooterTests.  
  
    1.  W Eksploratorze rozwiązań wybierz **RooterTests** projektu, a następnie wybierz pozycję **Dodawanie odwołania...**  menu skrótów.  
  
    2.  Na **Dodaj odwołanie - RooterTests** okna dialogowego rozwiń **rozwiązania** i wybierz polecenie **projekty**. Następnie wybierz **matematycznych** elementu.  
  
         ![Dodaj odwołanie do projektu matematycznych](../test/media/ute_cs_windows_addreference.png "UTE_Cs_windows_AddReference")  
  
2.  Dodawanie przy użyciu instrukcji w pliku UnitTest1.cs:  
  
    1.  Otwórz **UnitTest1.cs**.  
  
    2.  Dodaj poniższy kod `using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;` wiersza:  
  
        ```csharp  
        using Maths;  
        ```  
  
3.  Dodaj test, który używa funkcji Rooter. Dodaj następujący kod do **UnitTest1.cpp**:  
  
    ```csharp  
    [TestMethod]  
    public void BasicTest()  
    {  
        Maths.Rooter rooter = new Rooter();  
        double expected = 0.0;  
        double actual = rooter.SquareRoot(expected * expected);  
        double tolerance = .001;  
        Assert.AreEqual(expected, actual, tolerance);  
    }  
  
    ```  
  
4.  Skompiluj rozwiązanie.  
  
     Nowy test zostanie wyświetlony w Eksploratorze testów w **nie Uruchom testy** węzła.  
  
5.  W Eksploratorze testów, wybierz **Uruchom wszystkie**.  
  
     ![Podstawowy Test przekazany](../test/media/ute_cpp_testexplorer_basictest.png "UTE_Cpp_TestExplorer_BasicTest")  
  
 Ma ustawienie testu i projekty kodu i sprawdzić, czy można uruchamiać testy, które uruchamiania funkcji w projekcie kodu. Teraz można rozpocząć pisanie rzeczywistych testów i kod.  
  
##  <a name="BKMK_Iteratively_augment_the_tests_and_make_them_pass"></a>Wielokrotnie powtarzane rozszerzyć testy i były przekazywane  
  
1.  Dodaj nowego testu:  
  
    ```csharp  
    [TestMethod]  
    public void RangeTest()  
    {  
        Rooter rooter = new Rooter();  
        for (double v = 1e-6; v < 1e6; v = v * 3.2)  
        {  
            double expected = v;  
            double actual = rooter.SquareRoot(v*v);  
            double tolerance = ToleranceHelper(expected);  
            Assert.AreEqual(expected, actual, tolerance);  
        }  
    }  
  
    ```  
  
    > [!TIP]
    >  Firma Microsoft zaleca, nie należy zmieniać testy, które zostały przekazane. Zamiast tego dodać nowego testu, zaktualizuj kod, dzięki czemu test zakończył się pomyślnie, a następnie dodaj innego testu i tak dalej.  
    >   
    >  Użytkownicy zmiany ich wymagań, wyłącz testy, które nie są już prawidłowe. Zapisz nowe testy i ich działania pojedynczo, w taki sam sposób przyrostowy.  
  
2.  W Eksploratorze testów, wybierz **Uruchom wszystkie**.  
  
3.  Test zakończy się niepowodzeniem.  
  
     ![Niepowodzenia RangeTest](../test/media/ute_cpp_testexplorer_rangetest_fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")  
  
    > [!TIP]
    >  Natychmiast po jej zostały zapisane, sprawdź, czy każdy test zakończy się niepowodzeniem. Dzięki temu można uniknąć łatwe błąd zapisu testu, który nigdy nie zakończy się niepowodzeniem.  
  
4.  Ulepszanie testowanego kodu tak, aby nowy test zakończył się pomyślnie. Zmień `SqareRoot` działać w **Rooter.cs** do poniższego:  
  
    ```csharp  
    public double SquareRoot(double x)  
    {  
        double estimate = x;  
        double diff = x;  
        while (diff > estimate / 1000)  
        {  
            double previousEstimate = estimate;  
            estimate = estimate - (estimate * estimate - x) / (2 * estimate);  
            diff = Math.Abs(previousEstimate - estimate);  
        }  
        return estimate;  
    }  
  
    ```  
  
5.  Skompiluj rozwiązanie, a następnie w Eksploratorze testów, wybierz pozycję **Uruchom wszystkie**.  
  
     Teraz Przekaż wszystkich trzech testach.  
  
> [!TIP]
>  Opracuj kodu, dodając testy jednym naraz. Upewnij się, że wszystkie testy zostały zaliczone pomyślnie po każdej iteracji.  
  
##  <a name="BKMK_Debug_a_failing_test"></a>Debuguj test się niepowodzeniem  
  
1.  Dodawanie innego testu do **UnitTest1.cs**:  
  
    ```csharp  
    // Verify that negative inputs throw an exception.  
    [TestMethod]  
    public void NegativeRangeTest()  
    {  
        string message;  
        Rooter rooter = new Rooter();  
        for (double v = -0.1; v > -3.0; v = v - 0.5)  
        {  
            try  
            {  
                // Should raise an exception:  
                double actual = rooter.SquareRoot(v);  
  
                message = String.Format("No exception for input {0}", v);  
                Assert.Fail(message);  
            }  
            catch (ArgumentOutOfRangeException ex)  
            {  
                continue; // Correct exception.  
            }  
            catch (Exception e)  
            {  
                message = String.Format("Incorrect exception for {0}", v);  
                Assert.Fail(message);  
            }  
        }  
    }  
  
    ```  
  
2.  W Eksploratorze testów, wybierz **Uruchom wszystkie**.  
  
     Test zakończy się niepowodzeniem. Wybierz nazwę testu w Eksploratorze testów. Zostanie wyróżniona potwierdzenia nie powiodło się. Komunikat o błędzie jest widoczny w okienku szczegółów Eksploratora testów.  
  
     ![NegativeRangeTests failed](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")  
  
3.  Aby zobaczyć, dlaczego test zakończy się niepowodzeniem, krok przy użyciu funkcji:  
  
    1.  Ustaw punkt przerwania na początku `SquareRoot` funkcji.  
  
    2.  Menu skrótów nie powiodło się testu, wybierz **Debuguj zaznaczone testy**.  
  
         Po zatrzymaniu uruchomienia na punkt przerwania, wykonywać krokowo kodu.  
  
    3.  Dodaj kod do metody Rooter do catch wyjątku:  
  
        ```csharp  
        public double SquareRoot(double x)  
        {  
            if (x < 0.0)  
            {  
                throw new ArgumentOutOfRangeException();  
        }  
  
        ```  
  
    1.  W Eksploratorze testów, wybierz **Uruchom wszystkie** poprawiony metoda testowa i upewnij się, że nie wprowadzono regresji.  
  
 Teraz przejść pomyślnie wszystkie testy.  
  
 ![Wszystkie testy zostały zaliczone pomyślnie](../test/media/ute_ult_alltestspass.png "UTE_ULT_AllTestsPass")  
  
##  <a name="BKMK_Refactor_the_code_"></a>Zrefaktoryzuj kod  
 **Uproszczenia obliczeń centralnej w funkcji SquareRoot.**  
  
1.  Zmień implementację wyników  
  
    ```csharp  
    // old code  
    //result = result - (result*result - v)/(2*result);  
    // new code  
    result = (result + v/result) / 2.0;  
  
    ```  
  
2.  Wybierz **Uruchom wszystkie** refactored metoda testowa i upewnij się, że nie wprowadzono regresji.  
  
> [!TIP]
>  Stabilna zestaw testów jednostkowych dobrej daje pewność, że nie użyto usterki po zmianie kodu.  
  
 **Zrefaktoryzuj kod testu w celu wyeliminowania zduplikowanych kodu.**  
  
 Należy pamiętać, że `RangeTest` metody twardych kodów denominator zmiennej tolerancji, który jest używany w `Assert` metody. Jeśli planujesz dodać dodatkowe testy, które używają tego samego obliczeń na uszkodzenia, użycie wartości ustalony w wielu miejscach może prowadzić do błędów.  
  
1.  Metoda prywatna należy dodać do klasy Unit1Test do obliczenia wartości na uszkodzenia, a następnie zamiast tego wywołać tej metody.  
  
    ```csharp  
    private double ToleranceHelper(double expected)  
    {  
        return expected / 1000;  
    }  
  
    ...  
  
    [TestMethod]  
    public void RangeTest()  
    {  
        ...  
        // old code  
        // double tolerance = expected/1000;  
        // new code  
        double tolerance = ToleranceHelper(expected);  
        Assert.AreEqual(expected, actual, tolerance);  
    }  
    ...  
  
    ```  
  
2.  Wybierz **Uruchom wszystkie** refactored metoda testowa i upewnij się, że nie wprowadzono wystąpił błąd.  
  
> [!NOTE]
>  Aby dodać metody pomocnika do klasy testowej, nie należy dodawać `[TestMethod]` atrybut do metody. Eksplorator testów nie rejestruje metody do uruchomienia.
