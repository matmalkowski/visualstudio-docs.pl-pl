---
title: Jednostka testowania kodu Visual C# w programie Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: 5be318dd520cf9d7b5942200f635fa3f726634fc
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117404"
---
# <a name="unit-testing-visual-c-code"></a>Kod Visual C# testy jednostkowe

W tym temacie opisano jeden ze sposobów tworzenia testów jednostkowych dla klasy Visual C# w aplikacji platformy uniwersalnej systemu Windows. Klasa Rooter pokazuje niezrozumiała chwile teorii limit z calculus zaimplementowanie funkcji, która oblicza szacunkową pierwiastek kwadratowy z podanej liczbie. Aplikacja matematycznych następnie użyć tej funkcji do wyświetlenia użytkownika fun, co można zrobić za pomocą matematycznych.

W tym temacie przedstawiono sposób użycia testowania jako pierwszy krok w rozwoju jednostek. W takie podejście należy najpierw zapisać metody testowej, która sprawdza określone zachowanie w systemie, testowany, a następnie napisać kod, który przekazuje testu. Wprowadzenie zmian w kolejności poniższych procedur, można cofnąć tej strategii do pierwszej operacji zapisu kod, który chcesz przetestować, a następnie wpisz testów jednostkowych.

W tym temacie tworzy także jedno rozwiązanie Visual Studio i oddzielne projektów testów jednostkowych i biblioteki DLL, która ma zostać przetestowana. Testy jednostkowe mogą również obejmować bezpośrednio w projekcie biblioteki DLL, lub można utworzyć oddzielne rozwiązania testów jednostkowych i biblioteki DLL.

## <a name="create-the-solution-and-the-unit-test-project"></a>Tworzenie rozwiązania i jednostkowy projekt testowy

1. Na **pliku** menu, wybierz **nowy** > **projektu**.

2. W **nowy projekt** okna dialogowego rozwiń **zainstalowana** > **Visual C#** i wybierz polecenie **uniwersalnych systemu Windows**. Następnie wybierz pozycję **pusta aplikacja** z listy szablonów projektu.

3. Nazwij projekt `Maths` i upewnij się, że **Utwórz katalog rozwiązania** jest zaznaczone.

4. W Eksploratorze rozwiązań, wybieranie Nazwa rozwiązania, **Dodaj** z menu skrótów, a następnie wybierz pozycję **nowy projekt**.

5. W **nowy projekt** okna dialogowego rozwiń **zainstalowana**, następnie rozwiń węzeł **Visual C#** i wybierz polecenie **uniwersalnych systemu Windows**. Następnie wybierz pozycję **aplikacji testów jednostkowych (uniwersalna systemu Windows)** z listy szablonów projektu.

6. Otwórz *UnitTest1.cs* w edytorze programu Visual Studio.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
   using Microsoft.VisualStudio.TestTools.UnitTesting;
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

   - Każdy test jest definiowana za pomocą <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybutu. Metoda testowa musi zwracać typ void i nie może mieć żadnych parametrów.

   - Metody testowe musi być w klasie ozdobione <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atrybutu.

        Gdy testy są uruchamiane, tworzone jest wystąpienie klasy każdego testu. Metody testowe są nazywane w nieokreślonej kolejności.

   - Można określić specjalne metody, które są wywoływane przed i po każdej modułu, klasy lub metody. Aby uzyskać więcej informacji, zobacz [za pomocą środowiska MSTest w testach jednostkowych](../test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md).

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Sprawdź, że testy uruchamiane w narzędzia Eksplorator testów

1. Wstaw kod testu w TestMethod1 w **UnitTest1.cs** pliku:

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   Zwróć uwagę, że <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> klasa udostępnia kilka metod statycznych, których można użyć, aby zweryfikować wyniki w metodach.

2. Na **testu** menu, wybierz **Uruchom** , a następnie wybierz **Uruchom wszystkie**.

   Projekt testowy kompiluje i uruchamia. Zostanie wyświetlone okno Eksploratora testów i test zostanie wyświetlony w obszarze **przekazany testy**. Okienko Podsumowanie w dolnej części okna zawiera dodatkowe szczegóły dotyczące wybranego testu.

   ![Eksplorator testów](../test/media/ute_cpp_testexplorer_testmethod1.png)

## <a name="add-the-rooter-class-to-the-maths-project"></a>Dodaj klasę Rooter do projektu matematycznych

1. W Eksploratorze rozwiązań wybierz **matematycznych** nazwę projektu. Z menu skrótów wybierz **Dodaj**, a następnie **klasy**.

2. Nazwa pliku klasy *Rooter.cs*.

3. Dodaj następujący kod do klasy Rooter *Rooter.cs* pliku:

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

   `Rooter` Klasy deklaruje konstruktora i `SquareRoot` metody narzędzia do szacowania.

4. `SquareRoot` Metoda jest tylko minimalny implementacji wystarczającego do testowania podstawowej struktury testowania instalacji.

## <a name="couple-the-test-project-to-the-app-project"></a>Kilka projekt testowy do projektu aplikacji

1. Dodaj odwołanie do aplikacji matematycznych do projektu RooterTests.

    1. W Eksploratorze rozwiązań wybierz **RooterTests** projektu, a następnie wybierz pozycję **Dodaj odwołanie** menu skrótów.

    2. W **Dodaj odwołanie - RooterTests** okna dialogowego rozwiń **rozwiązania** i wybierz polecenie **projekty**. Następnie wybierz **matematycznych** elementu.

        ![Dodaj odwołanie do projektu matematycznych](../test/media/ute_cs_windows_addreference.png)

2. Dodaj using instrukcji *UnitTest1.cs* pliku:

    1. Otwórz *UnitTest1.cs*.

    2. Dodaj poniższy kod `using Microsoft.VisualStudio.TestTools.UnitTesting;` wiersza:

       ```csharp
       using Maths;
       ```

3. Dodaj test, który używa funkcji Rooter. Dodaj następujący kod do *UnitTest1.cs*:

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

4. Skompiluj rozwiązanie.

   Nowy test zostanie wyświetlony w Eksploratorze testów w **nie Uruchom testy** węzła.

5. W Eksploratorze testów, wybierz **Uruchom wszystkie**.

   ![Podstawowy Test zakończył się powodzeniem](../test/media/ute_cpp_testexplorer_basictest.png)

Ma ustawienie testu i projekty kodu i sprawdzić, czy można uruchamiać testy, które uruchamiania funkcji w projekcie kodu. Teraz można rozpocząć pisanie rzeczywistych testów i kod.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Wielokrotnie powtarzane rozszerzyć testy i były przekazywane

1. Dodaj nowego testu:

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
   > Firma Microsoft zaleca, nie należy zmieniać testy, które zostały przekazane. Zamiast tego dodać nowego testu, zaktualizuj kod, dzięki czemu test zakończył się pomyślnie, a następnie dodaj innego testu i tak dalej.
   >
   > Użytkownicy zmiany ich wymagań, wyłącz testy, które nie są już prawidłowe. Zapisz nowe testy i ich działania pojedynczo, w taki sam sposób przyrostowy.

2. W Eksploratorze testów, wybierz **Uruchom wszystkie**.

3. Test zakończy się niepowodzeniem.

   ![RangeTest kończy się niepowodzeniem](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Natychmiast po jej zostały zapisane, sprawdź, czy każdy test zakończy się niepowodzeniem. Dzięki temu można uniknąć łatwe błąd zapisu testu, który nigdy nie zakończy się niepowodzeniem.

4. Ulepszanie testowanego kodu tak, aby nowy test zakończył się pomyślnie. Zmień `SquareRoot` działać w *Rooter.cs* do poniższego:

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

5. Skompiluj rozwiązanie, a następnie w **Eksploratora testów**, wybierz **Uruchom wszystkie**.

   Teraz Przekaż wszystkich trzech testach.

> [!TIP]
> Opracuj kodu, dodając testy jednym naraz. Upewnij się, że wszystkie testy zostały zaliczone pomyślnie po każdej iteracji.

## <a name="debug-a-failing-test"></a>Debuguj test się niepowodzeniem

1. Dodawanie innego testu do *UnitTest1.cs*:

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

2. W **Eksploratora testów**, wybierz **Uruchom wszystkie**.

   Test zakończy się niepowodzeniem. Wybierz nazwę testu w **Eksploratora testów**. Zostanie wyróżniona potwierdzenia nie powiodło się. Komunikat o błędzie jest widoczny w okienku szczegółów **Eksploratora testów**.

   ![NegativeRangeTests nie powiodło się.](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Aby zobaczyć, dlaczego test zakończy się niepowodzeniem, krok przy użyciu funkcji:

    1. Ustaw punkt przerwania na początku `SquareRoot` funkcji.

    2. Menu skrótów nie powiodło się testu, wybierz **Debuguj zaznaczone testy**.

        Po zatrzymaniu uruchomienia na punkt przerwania, wykonywać krokowo kodu.

    3. Dodaj kod do metody Rooter do catch wyjątku:

        ```csharp
        public double SquareRoot(double x)
        {
            if (x < 0.0)
            {
                throw new ArgumentOutOfRangeException();
        }
        ```

4. W Eksploratorze testów, wybierz **Uruchom wszystkie** poprawiony metoda testowa i upewnij się, że nie wprowadzono regresji.

Teraz przejść pomyślnie wszystkie testy.

![Wszystkie testy zostały zaliczone pomyślnie](../test/media/ute_ult_alltestspass.png)

## <a name="refactor-the-code"></a>Zrefaktoryzuj kod

**Uproszczenia obliczeń centralnej w funkcji SquareRoot.**

1. Zmień implementację wyników

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;
    ```

2. Wybierz **Uruchom wszystkie** refactored metoda testowa i upewnij się, że nie wprowadzono regresji.

> [!TIP]
> Stabilna zestaw testów jednostkowych dobrej daje pewność, że nie użyto usterki po zmianie kodu.

**Zrefaktoryzuj kod testu w celu wyeliminowania zduplikowanych kodu.**

Należy pamiętać, że `RangeTest` metody twardych kodów denominator z `tolerance` zmiennej, która została przekazana do <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metody. Jeśli planujesz dodać dodatkowe testy, które używają tego samego obliczeń na uszkodzenia, użycie wartości ustalony w wielu miejscach może prowadzić do błędów.

1. Dodaj prywatnej metodę do klasy Unit1Test do obliczenia wartości tolerancji, a następnie zamiast tego wywołać tej metody.

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

2. Wybierz **Uruchom wszystkie** refactored metoda testowa i upewnij się, że nie wprowadzono wystąpił błąd.

> [!NOTE]
> Jeśli dodasz metody pomocnika do klasy testowej, które nie mają być wyświetlane w **Eksploratora testów**, nie dodawaj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybut do metody.