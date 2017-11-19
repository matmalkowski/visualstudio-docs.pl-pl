---
title: "Szybki Start: Programowanie sterowane za pomocą narzędzia Eksplorator testów Test | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5161b533-2127-4172-b473-d4ffc76ff05b
caps.latest.revision: "15"
ms.author: douge
manager: douge
ms.openlocfilehash: c52ce6556ae8937dd26c1be16cfaf1a4b05b1c74
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="quick-start-test-driven-development-with-test-explorer"></a>Szybki start: programowanie sterowane testami za pomocą narzędzia Eksplorator testów
Firma Microsoft zaleca utworzenie testów jednostkowych, aby zapewnić działanie wielu przyrostowe kroki tworzenia kodu. Istnieje kilka struktur, co umożliwia pisanie testów jednostkowych, w tym również opracowane przez strony trzecie. Niektóre platform testów są przeznaczone do testowania w różnych językach lub platform. Eksplorator testów udostępnia jeden interfejs dla testów jednostkowych w żadnym z tych platform. Karty są dostępne dla struktur najbardziej często używane, a może zapisywać karty dla innych platform.  
  
 Eksplorator testów zastępuje windows testu jednostki w starszej wersji programu Visual Studio. Korzyści obejmują:  
  
-   Uruchom .NET niezarządzanych, bazy danych i inne rodzaje testów za pomocą jednego interfejsu.  
  
-   Użyj jednostki test framework wybranych przez użytkownika, takie jak NUnit lub MSTest struktury.  
  
-   Zobacz w jednym oknie wszystkie informacje, które są potrzebne.  
  
## <a name="using-test-explorer"></a>Za pomocą narzędzia Eksplorator testów  
 ![Przycisk Uruchom wszystkie przedstawiający Eksploratora testów jednostkowych](../test/media/unittestexplorer-beta-.png "UnitTestExplorer(beta)")  
  
#### <a name="to-run-unit-tests-by-using-test-explorer"></a>Do uruchomienia testów jednostkowych za pomocą narzędzia Eksplorator testów  
  
1.  Tworzenie testów jednostkowych, korzystających z platform testów wybranych przez użytkownika.  
  
     Na przykład aby utworzyć testu używający MSTest Framework:  
  
    1.  Tworzenie projektu testu.  
  
         W **nowy projekt** okna dialogowego rozwiń **Visual Basic**, **Visual C#**, lub **Visual C++**, a następnie wybierz pozycję **testu**.  
  
         Wybierz **jednostkowy projekt testowy**.  
  
    2.  Zapis każdego testu jednostkowego jako metody. Prefiks każdej metody z `[TestMethod]` atrybutu.  
  
2.  Jeśli poszczególne testy nie ma żadnych zależności, które uniemożliwiają uruchomione w dowolnej kolejności, włącz wykonywanie równoległe testu z ![UTE &#95;parallelicon &#45; małych](../test/media/ute_parallelicon-small.png "UTE_parallelicon małych") przycisk przełączania na pasku narzędzi. To znacznie ograniczyć czas potrzebny na uruchamianie wszystkich testów.  
  
3.  Na pasku menu wybierz **testu**, **Uruchom testy jednostkowe**, **wszystkie testy**.  
  
     Buduje rozwiązanie, a następnie uruchom testy.  
  
     Eksplorator testów otwiera i wyświetla podsumowanie wyników.  
  
 **Aby wyświetlić pełną listę testów:** wybierz **Pokaż wszystko** w każdej kategorii.  
  
 **Aby wyświetlić szczegóły wyniku testu:** wybierz testu w Eksploratorze testów, aby wyświetlić szczegółowe informacje, takie jak komunikaty wyjątku w okienku szczegółów.  
  
 **Przejdź do kodu testu:** kliknij dwukrotnie testu w Eksploratorze testów, lub wybierz **Otwórz Test** menu skrótów.  
  
 **Aby debugować testu:** Otwórz menu skrótów dla jednego lub więcej testów, a następnie wybierz pozycję **Debuguj zaznaczone testy**.  
  
> [!IMPORTANT]
>  Wyniki, które są wyświetlane są dla ostatniego uruchomienia. Na pasku kolorowe wyniki wyświetlany tylko wyniki uruchomionych testów. Na przykład uruchomić wiele testów i niektóre z nich zakończyć się niepowodzeniem, a następnie uruchom tylko testy pomyślne, następnie na pasku wyników wyświetli wszystkie zielony.  
  
> [!NOTE]
>  Jeśli pojawi się żaden test, upewnij się, który zainstalowany adapter w celu nawiązania Eksploratora testów struktury testowej, którego używasz. Aby uzyskać więcej informacji, zobacz [przy użyciu różnych platform testów z Eksploratora testów](#frameworks).  
  
##  <a name="walkthrough"></a>Wskazówki: Korzystanie z metody tworzenia testów jednostkowych  
 W tym przewodniku pokazano, jak opracowanie metodę przetestowany w języku C# za pomocą środowiska testów jednostkowych firmy Microsoft. Można łatwo dostosować go dla innych języków i korzystania z innych platform testu, takie jak NUnit łącze. Aby uzyskać więcej informacji, zobacz [przy użyciu różnych platform testów](#frameworks).  
  
#### <a name="creating-the-test-and-method"></a>Tworzenie testu i — metoda  
  
1.  Utwórz projekt Visual biblioteki klas C#. Ten projekt będzie zawierać kod, który chcesz dostarczyć. W tym przykładzie o nazwie `MyMath`.  
  
2.  Tworzenie projektu testu.  
  
    -   W **nowy projekt** okno dialogowe, wybierz **Visual C#**, **testu** , a następnie wybierz **jednostkowy projekt testowy**.  
  
         ![Nowe projekty kodu oraz testów](../test/media/unittestexplorerwalk1.png "UnitTestExplorerWalk1")  
  
3.  Napisanie metody podstawowy test. Sprawdź wynik uzyskać określone dane wejściowe:  
  
    ```csharp  
  
    [TestMethod]  
    public void BasicRooterTest()  
    {  
      // Create an instance to test:  
      Rooter rooter = new Rooter();  
      // Define a test input and output value:  
      double expectedResult = 2.0;  
      double input = expectedResult * expectedResult;  
      // Run the method under test:  
      double actualResult = rooter.SquareRoot(input);  
      // Verify the result:  
      Assert.AreEqual(expectedResult, actualResult,  
          delta: expectedResult / 100);  
    }  
    ```  
  
4.  Generuj metoda testu.  
  
    1.  Umieść kursor na `Rooter`, a następnie w menu skrótów wybierz **Generuj**, **nowy typ**.  
  
    2.  W **wygenerować nowy typ** okno dialogowe, zestaw **projektu** do projektu biblioteki klas. W tym przykładzie jest `MyMath`.  
  
    3.  Umieść kursor na `SquareRoot`, a następnie w menu skrótów wybierz **Generuj**, **szkieletu metody**.  
  
5.  Uruchamianie testu jednostkowego.  
  
    1.  Na **testu** menu, wybierz **Uruchom testy jednostkowe**, **wszystkie testy**.  
  
         Rozwiązanie kompiluje i uruchamia.  
  
         Eksplorator testów otwiera i wyświetla wyniki.  
  
         Uruchomienie testu jest wyświetlany w obszarze **testy nie powiodło się**.  
  
6.  Wybierz nazwę testu.  
  
     Szczegóły testu są wyświetlane w dolnej części Eksploratora testów.  
  
7.  Wybierz elementy podrzędne **ślad stosu** aby zobaczyć, których nie powiodło się uruchomienie testu.  
  
 ![Przetestuj Eksploratora testów jednostek przedstawiający nie powiodło się. ] (../test/media/unittestexplorerwalkthrough2.png "UnitTestExplorerWalkthrough2")  
  
 W tym momencie utworzono test i szkieletu, który należy zmodyfikować tak, aby test zakończył się pomyślnie.  
  
#### <a name="after-every-change-make-all-the-tests-pass"></a>Po każdej zmianie wprowadź wszystkie testy przekazywania  
  
1.  W `MyMath\Rooter.cs`, poprawić kod `SquareRoot`:  
  
    ```csharp  
    public double SquareRoot(double input)  
     {  
       return input / 2;  
     }  
    ```  
  
2.  W Eksploratorze testów, wybierz **Uruchom wszystkie**.  
  
     Kod kompiluje i uruchamia testu.  
  
     Test zakończył się pomyślnie.  
  
     ![Jednostka Test Explorer przedstawiający testu przekazywanie. ] (../test/media/unittestexplorerwalkthrough3.png "UnitTestExplorerWalkthrough3")  
  
#### <a name="add-tests-to-extend-the-range-of-inputs"></a>Dodawanie testów, aby rozszerzyć zakres danych wejściowych  
  
1.  Aby ulepszyć Twoje pewność, że w kodzie działa we wszystkich przypadkach, Dodaj testy, które spróbuj większej liczby argumentów.  
  
    > [!TIP]
    >  Uniknąć, zmieniając istniejące testy, które przekazują. Zamiast tego należy dodać nowe testy. Zmień istniejące testy, tylko w przypadku zmiany wymagań użytkownika. Ta zasada zapewnia nie utracić istniejące funkcje podczas pracy w celu rozszerzenia kodu.  
  
     W klasie testu Dodaj następujący test, który próbuje zakres wartości wejściowych:  
  
    ```csharp  
    [TestMethod]  
    public void RooterValueRange()  
    {  
      // Create an instance to test:  
      Rooter rooter = new Rooter();  
      // Try a range of values:  
      for (double expectedResult = 1e-8;  
          expectedResult < 1e+8;  
          expectedResult = expectedResult * 3.2)  
      {  
        RooterOneValue(rooter, expectedResult);  
      }  
    }  
  
    private void RooterOneValue(Rooter rooter, double expectedResult)  
    {  
      double input = expectedResult * expectedResult;  
      double actualResult = rooter.SquareRoot(input);  
      Assert.AreEqual(expectedResult, actualResult,  
          delta: expectedResult / 1000);  
    }  
    ```  
  
2.  W Eksploratorze testów, wybierz **Uruchom wszystkie**.  
  
     Nowy test zakończy się niepowodzeniem, mimo że nadal przekazuje pierwszego testu.  
  
     Aby znaleźć punktu awarii, wybierz testu niepowodzenie, a następnie w dolnej części Eksploratora testów, wybierz pierwszy element z **ślad stosu**.  
  
3.  Sprawdź, czy metoda w ramach testu, aby zobaczyć, co może być nieprawidłowy. W `MyMath.Rooter` klasy, ponownego pisania kodu:  
  
    ```  
    public double SquareRoot(double input)  
    {  
      double result = input;  
      double previousResult = -input;  
      while (Math.Abs(previousResult - result) > result / 1000)  
      {  
        previousResult = result;  
        result = result - (result * result - input) / (2 * result);  
      }  
      return result;  
    }  
    ```  
  
4.  W Eksploratorze testów, wybierz **Uruchom wszystkie**.  
  
     Teraz Przekaż zarówno testy.  
  
#### <a name="add-tests-for-exceptional-cases"></a>Dodawanie testów dla wyjątku  
  
1.  Dodaj test ujemna dane wejściowe:  
  
    ```csharp  
    [TestMethod]  
     public void RooterTestNegativeInputx()  
     {  
         Rooter rooter = new Rooter();  
         try  
         {  
             rooter.SquareRoot(-10);  
         }  
         catch (ArgumentOutOfRangeException e)  
         {  
             return;  
         }  
         Assert.Fail();  
     }  
    ```  
  
2.  W Eksploratorze testów, wybierz **Uruchom wszystkie**.  
  
     Metoda w pętli do testu i należy anulować ręcznie.  
  
3.  Wybierz **anulować**.  
  
     Test zatrzyma się po 10 sekundach.  
  
4.  Usuń kod metody:  
  
    ```csharp  
  
    public double SquareRoot(double input)  
    {  
      if (input <= 0.0)   
      {  
        throw new ArgumentOutOfRangeException();  
      }   
    ...  
    ```  
  
5.  W Eksploratorze testów, wybierz **Uruchom wszystkie**.  
  
     Wszystkie testy zostały zaliczone pomyślnie.  
  
#### <a name="refactor-without-changing-tests"></a>Refaktoryzuj bez zmiany testów  
  
1.  Uprościć kod, ale nie należy zmieniać testy.  
  
    > [!TIP]
    >  A *refaktoryzacji* zmiana jest przeznaczona na powoduje, że kod lepiej lub aby wprowadzić kod łatwiejsze do zrozumienia. Nie jest on przeznaczony do zmiany zachowania kodu, a w związku z tym testy nie są zmieniane.  
    >   
    >  Firma Microsoft zaleca, wykonaj kroki refaktoryzacji oddzielnie z kroków, które rozszerzają funkcje. Utrzymywanie testy bez zmian daje pewność, że użytkownik nie przypadkowo wprowadziły usterki podczas refaktoryzacji.  
  
    ```csharp  
    public class Rooter  
    {  
      public double SquareRoot(double input)  
      {  
        if (input <= 0.0)   
        {  
          throw new ArgumentOutOfRangeException();  
        }  
        double result = input;  
        double previousResult = -input;  
        while (Math.Abs(previousResult - result) > result / 1000)  
        {  
          previousResult = result;  
          result = (result + input / result) / 2;  
          //was: result = result - (result * result - input) / (2*result);  
        }  
        return result;  
      }  
    }  
    ```  
  
2.  Wybierz **uruchomić wszystkie**.  
  
     Nadal przejść pomyślnie wszystkie testy.  
  
     ![Eksplorator testów jednostek pokazujący 3 testy przekazany. ] (../test/media/unittestexplorerwalkthrough4.png "UnitTestExplorerWalkthrough4")
