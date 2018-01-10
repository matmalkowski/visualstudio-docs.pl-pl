---
title: "Izolowanie testowanego pomocą struktury Microsoft Fakes kodu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
dev_langs:
- VB
- CSharp
ms.openlocfilehash: 42164191a3782de31245b1bc46cddce57a56de02
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="isolating-code-under-test-with-microsoft-fakes"></a>Izolowanie testowanego kodu za pomocą struktury Microsoft Fakes

Microsoft Fakes pomaga wyizolować kodu podczas testowania za pomocą zastąpienia innych części aplikacji z *klas zastępczych* lub *podkładek*. Są to małe fragmenty kodu, będące pod kontrolą Twoich testów. Izolując kod do testowania, wiesz, że jeśli test wypadnie niepomyślnie, przyczyna leży tam, a nie w żadnym innym miejscu. Podkładki i wycinki pozwalają na testowanie kodu, nawet jeśli pozostałe części aplikacji jeszcze nie działają.

Podróbki występują w dwóch wersjach:

-   A [stub](#stubs) zastępuje klasy małych substitute, który implementuje ten interfejs.  Aby użyć wycinków, należy tak zaprojektować aplikację, aby każdy składnik zależał jedynie od interfejsów, a nie od innych składników. (Przez „składnik” rozumie się klasy lub grupy klas, które są zaprojektowane i aktualizowane łącznie i zwykle są zawarte w zestawie).

-   A [podkładki](#shims) modyfikuje skompilowany kod aplikacji w czasie wykonywania, aby zamiast wywołania określonej metody kod podkładki, który zapewnia test został uruchomiony. Podkładek może być używany do zastąpienia wywołań zestawy, których nie można modyfikować, takich jak zestawów platformy .NET.

![Substytuty zastąpić inne składniki](../test/media/fakes-2.png "2 elementów sztucznych")  

**Wymagania**

-   Visual Studio Enterprise

## <a name="choosing-between-stub-and-shim-types"></a>Wybór między typami podkładek i wycinków  
Projekt Visual Studio zazwyczaj zostanie zakwalifikowany jako składnik, ponieważ klasy te są opracowywane i aktualizowane równocześnie. Można rozważyć użycie wycinków i podkładek do wywołań, które dany projekt kieruje w stronę innych projektów w rozwiązaniu, lub w stronę innych zestawów, do których projekt się odnosi.  
  
Jako ogólnej wskazówki należy użyć fragmentów dla wywołań w ramach rozwiązania Visual Studio i podkładek dla wywołań do innych zestawów, do których istnieje odwołanie. Dzieje się tak, ponieważ wewnątrz własnego rozwiązania warto ćwiczyć rozdzielanie par składników przez definiowanie interfejsów w sposób wymagany przez wycinkowanie. Zespoły zewnętrzne, takie jak System.dll, zazwyczaj nie są wyposażone w osobne definicje interfejsu, więc zamiast tego należy używać podkładek.  
  
Inne zagadnienia to:  
  
**Wydajność.** Podkładki działają wolniej, ponieważ przepisują kod w czasie wykonywania. Wycinki kodu nie mają dodatkowego obciążenia i są równie szybkie, jak metody wirtualne.  
  
**Metody statyczne typy zapieczętowane.** Możesz używać wycinków tylko do implementacji interfejsów. Tym samym typy wycinka nie mogą być stosowane dla metod statycznych, metod niewirtualnych, zaplombowanych metod wirtualnych, metod w zaplombowanych typach itd.  
  
**Wewnętrzne typy.** Zarówno klas zastępczych i podkładek użyciem wewnętrzne typy, które są udostępniane za pomocą atrybutu zestawu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.  
  
**Prywatnych metod.** Podkładki zastępują wywołania metod prywatnych, jeśli widoczne są wszystkie typy podpisów metody. Wycinki kodu mogą zastąpić jedynie metody widoczne.  
  
**Interfejsy i metody abstrakcyjne.** Wycinki kodu zapewniają implementacje interfejsów i metody abstrakcyjne, które mogą służyć do testowania. Nie można podkładek Instrumentacja interfejsów i metody abstrakcyjne, ponieważ nie zawierają treści metody.  
  
Zasadniczo zaleca się używanie typów wycinków w celu odseparowania od zależności w ramach własnej bazy kodów. Można to zrobić, ukrywając składniki za interfejsami. Typy podkładek można wykorzystywać do izolowania od składników innych firm, które nie mają sprawdzalnego API.  
  
##  <a name="stubs"></a>Wprowadzenie do korzystania z klas zastępczych  
Aby uzyskać bardziej szczegółowy opis, zobacz [stosowanie wycinków kodu do izolowania części aplikacji ze sobą w celu przeprowadzania testów jednostkowych](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).  
  
1.  **Wstaw interfejsów**  
  
     Aby użyć wycinków, musisz napisać kod, który chcesz przetestować w taki sposób, aby nie wymieniał wprost klas w innych składnikach Twojej aplikacji. Przez „składnik” rozumie się klasę lub grupę klas, które są opracowane i aktualizowane łącznie i zwykle są zawarte w jednym projekcie Visual Studio. Zmienne i parametry powinny być zdeklarowane przy użyciu interfejsów, a wystąpienia innych składników powinny zostać przekazane lub utworzone za pomocą fabryki. Jeśli na przykład StockFeed jest klasą w innym składniku aplikacji, zostałoby to uznane za nieprawidłowe:  
  
     `return (new StockFeed()).GetSharePrice("COOO"); // Bad`  
  
     Zamiast tego zdefiniuj interfejs, który może być implementowany przez inny składnik, a także przez wycinek dla celów testowych:  
  
    ```csharp  
    public int GetContosoPrice(IStockFeed feed)  
    { return feed.GetSharePrice("COOO"); }  
  
    ```  
  
    ```vb  
    Public Function GetContosoPrice(feed As IStockFeed) As Integer  
     Return feed.GetSharePrice("COOO")  
    End Function  
  
    ```  
  
2.  **Dodawanie zestawu elementów sztucznych**  
  
    1.  W Eksploratorze rozwiązań rozwiń listę odwołania projektu testowego. Jeśli pracujesz w języku Visual Basic, należy wybrać **Pokaż wszystkie pliki** aby zobaczyć listę odwołań.  
  
    2.  Wybierz odwołanie do zestawu, w którym zdefiniowano interfejs (na przykład IStockFeed). W menu skrótów to odwołanie, wybierz **dodać zestawu elementów sztucznych**.  
  
    3.  Ponownie skompiluj rozwiązanie.  
  
3.  W testach należy skonstruować wystąpienia wycinka i podać kod dla jego metody:  
  
    ```csharp  
    [TestClass]  
    class TestStockAnalyzer  
    {  
        [TestMethod]  
        public void TestContosoStockPrice()  
        {  
          // Arrange:  
  
            // Create the fake stockFeed:  
            IStockFeed stockFeed =   
                 new StockAnalysis.Fakes.StubIStockFeed() // Generated by Fakes.  
                     {  
                         // Define each method:  
                         // Name is original name + parameter types:  
                         GetSharePriceString = (company) => { return 1234; }  
                     };  
  
            // In the completed application, stockFeed would be a real one:  
            var componentUnderTest = new StockAnalyzer(stockFeed);  
  
          // Act:  
            int actualValue = componentUnderTest.GetContosoPrice();  
  
          // Assert:  
            Assert.AreEqual(1234, actualValue);  
        }  
        ...  
    }  
    ```  
  
    ```vb  
    <TestClass()> _  
    Class TestStockAnalyzer  
  
        <TestMethod()> _  
        Public Sub TestContosoStockPrice()  
            ' Arrange:  
            ' Create the fake stockFeed:  
            Dim stockFeed As New StockAnalysis.Fakes.StubIStockFeed  
            With stockFeed  
                .GetSharePriceString = Function(company)  
                                           Return 1234  
                                       End Function  
            End With  
            ' In the completed application, stockFeed would be a real one:  
            Dim componentUnderTest As New StockAnalyzer(stockFeed)  
            ' Act:  
            Dim actualValue As Integer = componentUnderTest.GetContosoPrice  
            ' Assert:  
            Assert.AreEqual(1234, actualValue)  
        End Sub  
    End Class  
  
    ```  
  
    Specjalny element tutaj magic jest klasa `StubIStockFeed`. Dla każdego interfejsu w zestawie, do którego istnieje odwołanie, mechanizm Microsoft Fakes generuje klasę zastępczą. Nazwa Klasa zastępcza jest nazwa interfejsu, pochodną z "`Fakes.Stub`" jako prefiksu i nazwy typu parametrów dołączane.  
  
    Wycinki kodu są generowane także dla metod pobierających i ustawiających właściwości, dla zdarzeń i metod ogólnych. Aby uzyskać więcej informacji, zobacz [stosowanie wycinków kodu do izolowania części aplikacji ze sobą w celu przeprowadzania testów jednostkowych](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).  
  
##  <a name="shims"></a>Wprowadzenie do podkładek  
(Aby uzyskać bardziej szczegółowy opis, zobacz [stosowanie podkładek do izolowania aplikacji od innych zestawów w celu przeprowadzania testów jednostkowych](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).)  
  
Załóżmy, że składnik zawiera wywołania `DateTime.Now`:  
  
```csharp  
// Code under test:  
    public int GetTheCurrentYear()  
    {  
       return DateTime.Now.Year;  
    }  
  
```  
  
Podczas testowania, które chcesz użyć podkładek `Now` właściwości, ponieważ rzeczywista wersja inconveniently zwraca inną wartość przy każdym wywołaniu.  
  
Aby użyć podkładek, nie trzeba zmodyfikować kod aplikacji lub zapisać go w określony sposób.  
  
1.  **Dodawanie zestawu elementów sztucznych**  
  
     W Eksploratorze rozwiązań Otwórz odwołania do projektu testu jednostki i wybierz odwołanie do zestawu, który zawiera metodę, która ma być fałszywe. W tym przykładzie `DateTime` klasa znajduje się w **System.dll**.  Aby wyświetlić odwołania w projektach Visual Basic, wybierz pozycję **Pokaż wszystkie pliki**.  
  
     Wybierz **dodać zestawu elementów sztucznych**.  
  
2.  **Włóż podkładki ShimsContext**  
  
    ```csharp  
    [TestClass]  
    public class TestClass1  
    {   
            [TestMethod]  
            public void TestCurrentYear()  
            {  
                int fixedYear = 2000;  
  
                // Shims can be used only in a ShimsContext:  
                using (ShimsContext.Create())  
                {  
                  // Arrange:  
                    // Shim DateTime.Now to return a fixed date:  
                    System.Fakes.ShimDateTime.NowGet =   
                    () =>  
                    { return new DateTime(fixedYear, 1, 1); };  
  
                    // Instantiate the component under test:  
                    var componentUnderTest = new MyComponent();  
  
                  // Act:  
                    int year = componentUnderTest.GetTheCurrentYear();  
  
                  // Assert:   
                    // This will always be true if the component is working:  
                    Assert.AreEqual(fixedYear, year);  
                }  
            }  
    }
    ```

    ```vb  
    <TestClass()> _  
    Public Class TestClass1  
        <TestMethod()> _  
        Public Sub TestCurrentYear()  
            Using s = Microsoft.QualityTools.Testing.Fakes.ShimsContext.Create()  
                Dim fixedYear As Integer = 2000  
                ' Arrange:  
                ' Detour DateTime.Now to return a fixed date:  
                System.Fakes.ShimDateTime.NowGet = _  
                    Function() As DateTime  
                        Return New DateTime(fixedYear, 1, 1)  
                    End Function  
  
                ' Instantiate the component under test:  
                Dim componentUnderTest = New MyComponent()  
                ' Act:  
                Dim year As Integer = componentUnderTest.GetTheCurrentYear  
                ' Assert:   
                ' This will always be true if the component is working:  
                Assert.AreEqual(fixedYear, year)  
            End Using  
        End Sub  
    End Class  
    ```  

    Nazwy klas podkładki składają się dodając `Fakes.Shim` oryginalną nazwę typu. Nazwy parametrów są dołączane do nazwy metody. (Nie trzeba dodać wszystkie odwołania do zestawu do System.Fakes).  

W poprzednim przykładzie podkładka jest wykorzystana do metody statycznej. Aby użyć podkładki dla metody wystąpienia, należy zapisać `AllInstances` pomiędzy nazwą typu, a nazwa metody:  

```  
System.IO.Fakes.ShimFile.AllInstances.ReadToEnd = ...  
```  

(Brak nie "System.IO.Fakes" zestawu do odwołania. Przestrzeń nazw jest generowany przez proces tworzenia podkładki. Ale "using" lub "Import" można użyć w zwykły sposób).  

Można również utworzyć podkładki dla konkretnych wystąpień, konstruktorów i właściwości. Aby uzyskać więcej informacji, zobacz [stosowanie podkładek do izolowania aplikacji od innych zestawów w celu przeprowadzania testów jednostkowych](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).  

## <a name="in-this-section"></a>W tej sekcji  
 [Stosowanie wycinków kodu do izolowania od siebie poszczególnych części aplikacji w celu przeprowadzania testów jednostkowych](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)  
  
 [Stosowanie podkładek do izolowania aplikacji od innych zestawów w celu przeprowadzania testów jednostkowych](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)  
  
 [Konwencje dotyczące generowania kodu, jego kompilowania i nazywania w Microsoft Fakes](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md)
