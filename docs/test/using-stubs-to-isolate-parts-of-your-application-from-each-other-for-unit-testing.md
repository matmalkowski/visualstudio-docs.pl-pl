---
title: Stosowanie wycinków kodu do izolowania poszczególnych części aplikacji w celu testowania w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 8c77c9502d062d92aad944748f113bfc37855dfe
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="use-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing"></a>Użyj klas zastępczych do izolowania części aplikacji ze sobą w celu przeprowadzania testów jednostkowych

*Stub typy* są jednym z dwóch technologii dostępnych w ramach Microsoft Fakes umożliwia łatwe izolowanie testów z innymi składnikami, które wywołuje składnik. Odcinek jest niewielkim fragmentem kodu, który zajmuje miejsce innego składnika podczas testu. Korzyścią wynikającą z zastosowania wycinka są spójne wyniki, co ułatwia tworzenie testów. Testy można będzie uruchomić, nawet jeśli inne składniki jeszcze nie działają.

Zawiera omówienie i szybki start-Podręcznik do elementów sztucznych, można znaleźć [izolowanie kodu w obszarze testów z Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).

Aby użyć wycinków, trzeba napisać składnik w taki sposób, aby korzystał tylko z interfejsów, a nie z klas, i odwoływał się do innych części aplikacji. To dobra praktyka tworzenia projektów, ponieważ zmiany są wprowadzane tylko w jednej części i jest mniej prawdopodobne, że inne również będą wymagać zmian. Do celów testowych pozwala zastąpić wycinkiem rzeczywisty składnik.

Na diagramie składnikiem StockAnalyzer jest ten, który chcemy przetestować. Zwykle używa on innego składnika RealStockFeed. RealStockFeed zwraca jednak różne wyniki przy każdym wywołaniu jego metod, co utrudnia test StockAnalyzer.  Podczas testowania można zastąpić go inną klasą StubStockFeed.

![Rzeczywista i klasy Stub spełniać jeden interfejs.](../test/media/fakesinterfaces.png)

Wycinki opierają się w ten sposób na swoich możliwościach bycia strukturą kodu, dlatego zwykle są one używane w celu wyizolowania jednej strony aplikacji z innej. Aby odłączyć je od innych zestawów niebędących pod kontrolą, takich jak System.dll, normalnie zostałyby użyte podkładki. Zobacz [stosowanie podkładek do izolowania aplikacji od innych zestawów w celu przeprowadzania testów jednostkowych](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).

## <a name="how-to-use-stubs"></a>Jak używać wycinków

### <a name="design-for-dependency-injection"></a>Zaprojektowane do wstrzykiwania zależności

Aby korzystać z wycinków, aplikacja musi być tak zaprojektowana, aby różne składniki nie były zależne od siebie, ale tylko od definicji interfejsu. Zamiast być połączone w czasie kompilacji, składniki są połączone w czasie wykonywania. Ten wzór pomaga stworzyć oprogramowanie, które będzie niezawodne i łatwe do zaktualizowania, ponieważ zmiany zwykle nie są propagowane przez granice składnika. Zaleca się po nim, nawet jeśli nie używasz klas zastępczych. Jeśli piszesz nowy kod jest czytelna [iniekcji zależności](http://en.wikipedia.org/wiki/Dependency_injection) wzorca. Jeśli piszesz testy dla istniejącego oprogramowania, możliwe, że trzeba będzie je refraktoryzować. Jeżeli byłoby to niepraktyczne, można rozważyć użycie zamiast niego podkładki.

Zacznijmy od tej dyskusji motywujące przykład, jeden na diagramie. Klasa, którą odczytuje StockAnalyzer, udostępnia ceny i generuje interesujące wyniki. Obejmuje ona niektóre metody publiczne, które chcemy sprawdzić. Aby zachować prostych czynności, po prostu Przyjrzyjmy się jednej z tych metod, bardzo proste jedną, która zgłasza bieżącej ceny określony udział. Chcemy napisać test jednostkowy tej metody. W tym miejscu jest pierwszy projekt testu:

```csharp
[TestMethod]
public void TestMethod1()
{
    // Arrange:
    var analyzer = new StockAnalyzer();
    // Act:
    var result = analyzer.GetContosoPrice();
    // Assert:
    Assert.AreEqual(123, result); // Why 123?
}
```

```vb
<TestMethod()> Public Sub TestMethod1()
    ' Arrange:
    Dim analyzer = New StockAnalyzer()
    ' Act:
    Dim result = analyzer.GetContosoPrice()
    ' Assert:
    Assert.AreEqual(123, result) ' Why 123?
End Sub
```

Jeden z problemów z tym testem staje się natychmiast oczywisty: ceny udziału różnią się, więc potwierdzenie zwykle zakończy się niepowodzeniem.

Innym problemem może być to, że składnik StockFeed, który jest używany przez StockAnalyzer, jest wciąż w fazie opracowywania. W tym miejscu jest pierwszy projekt kod metody w ramach testu:

```csharp
public int GetContosoPrice()
{
    var stockFeed = new StockFeed(); // NOT RECOMMENDED
    return stockFeed.GetSharePrice("COOO");
}
```

```vb
Public Function GetContosoPrice()
    Dim stockFeed = New StockFeed() ' NOT RECOMMENDED
    Return stockFeed.GetSharePrice("COOO")
End Function
```

W obecnym stanie metoda ta nie może kompilować lub może zgłosić wyjątek, ponieważ praca w klasie StockFeed nie została jeszcze zakończona. Wstrzyknięcie interfejsu rozwiązuje oba te problemy. Wstrzyknięcie interfejsu wykorzystuje następującą regułę:

Kod każdego składnika aplikacji powinno nigdy nie jawnie odwoływać się do klasy w innym składniku w deklaracji lub w `new` instrukcji. Zamiast tego zmienne i parametry powinny być zadeklarowane razem z interfejsami. Składnik wystąpienia powinny być tworzone tylko kontenera elementu.

- Przez "component" Firma Microsoft oznacza klasę lub grupę klas, które opracowanie i zaktualizować razem. Składnikiem jest zazwyczaj kod w jednym projekcie programu Visual Studio. Mniej ważne jest rozdzielenie klas w ramach jednego składnika, ponieważ są one aktualizowane w tym samym czasie.

- Ponadto nie jest tak ważne, takich jak rozdzielenie składniki od klasy stosunkowo stabilna platformy *System.dll*. Pisanie interfejsów dla wszystkich tych klas spowodowałoby zaśmiecenie kodu.

Kod StockAnalyzer z StockFeed jest oddzielana przy użyciu interfejsu następująco:

```csharp
public interface IStockFeed
{
    int GetSharePrice(string company);
}

public class StockAnalyzer
{
    private IStockFeed stockFeed;
    public StockAnalyzer(IStockFeed feed)
    {
        stockFeed = feed;
    }
    public int GetContosoPrice()
    {
        return stockFeed.GetSharePrice("COOO");
    }
}
```

```vb
Public Interface IStockFeed
    Function GetSharePrice(company As String) As Integer
End Interface

Public Class StockAnalyzer
    ' StockAnalyzer can be connected to any IStockFeed:
    Private stockFeed As IStockFeed
    Public Sub New(feed As IStockFeed)
        stockFeed = feed
    End Sub
    Public Function GetContosoPrice()
        Return stockFeed.GetSharePrice("COOO")
    End Function
End Class
```

W tym przykładzie StockAnalyzer przekazuje implementację IStockFeed podczas konstruowania. W ukończonej aplikacji kod inicjowania może wykonać połączenie:

```csharp
analyzer = new StockAnalyzer(new StockFeed());
```

Istnieją bardziej elastyczne sposoby wykonywania tego połączenia. Na przykład StockAnalyzer może zaakceptować obiekt fabryki, który może utworzyć wystąpienie różnych implementacji IStockFeed w różnych warunkach.

### <a name="generate-stubs"></a>Generowanie wycinków

Klasy, którą chcesz przetestować z innymi składnikami, które używa już odłączona. Oddzielenie powoduje, że aplikacja staje się bardziej solidna i elastyczna, a ponadto pozwala połączyć składnik testu z implementacją wycinka w ramach testowania interfejsów.

Można po prostu zwyczajnie napisać wycinki jako klasy. Jednak środowisko Microsoft Fakes zapewnia bardziej dynamiczny sposób tworzenia najodpowiedniejszych wycinków dla każdego testu.

Aby użyć wycinków, należy najpierw wygenerować typy wycinków z definicji interfejsu.

#### <a name="add-a-fakes-assembly"></a>Dodawanie zestawu elementów sztucznych

1. W Eksploratorze rozwiązań rozwiń węzeł projektu testu jednostki **odwołania**.

   Jeśli pracujesz w języku Visual Basic, musisz wybrać **Pokaż wszystkie pliki** na pasku narzędzi Eksplorator rozwiązań, aby zapoznać się z listą odwołania.

2. Wybierz zestaw zawierający definicje interfejsu, dla których chcesz utworzyć wycinki.

3. W menu skrótów wybierz **dodać zestawu elementów sztucznych**.

### <a name="write-your-test-with-stubs"></a>Napisz test z wycinkami

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

Specjalny element tutaj magic jest klasa `StubIStockFeed`. Dla każdego typu publicznego w zestawie, do którego istnieje odwołanie, mechanizm Microsoft Fakes generuje klasę wycinków. Nazwa Klasa zastępcza jest nazwa interfejsu, pochodną z "`Fakes.Stub`" jako prefiksu i nazwy typu parametrów dołączane.

Wycinki kodu są generowane także dla metod pobierających i ustawiających właściwości, dla zdarzeń i metod ogólnych.

### <a name="verify-parameter-values"></a>Sprawdź wartości parametrów

Można zweryfikować, że jeżeli składnik wywołuje inny składnik, przekazuje poprawne wartości. Teraz można umieścić potwierdzenie w wycinku lub przechowywać wartość i weryfikować ją w głównej części testu. Na przykład:

```csharp
[TestClass]
class TestMyComponent
{
    [TestMethod]
    public void TestVariableContosoPrice()
    {
        // Arrange:
        int priceToReturn;
        string companyCodeUsed;
        var componentUnderTest = new StockAnalyzer(new StubIStockFeed()
            {
               GetSharePriceString = (company) =>
                  {
                     // Store the parameter value:
                     companyCodeUsed = company;
                     // Return the value prescribed by this test:
                     return priceToReturn;
                  };
            };
        // Set the value that will be returned by the stub:
        priceToReturn = 345;

        // Act:
        int actualResult = componentUnderTest.GetContosoPrice();

        // Assert:
        // Verify the correct result in the usual way:
        Assert.AreEqual(priceToReturn, actualResult);

        // Verify that the component made the correct call:
        Assert.AreEqual("COOO", companyCodeUsed);
    }
...
}
```

```vb
<TestClass()> _
Class TestMyComponent
    <TestMethod()> _
    Public Sub TestVariableContosoPrice()
        ' Arrange:
        Dim priceToReturn As Integer
        Dim companyCodeUsed As String = ""
        Dim stockFeed As New StockAnalysis.Fakes.StubIStockFeed()
        With stockFeed
            ' Implement the interface's method:
            .GetSharePriceString = _
                Function(company)
                    ' Store the parameter value:
                    companyCodeUsed = company
                    ' Return a fixed result:
                    Return priceToReturn
                End Function
        End With
        ' Create an object to test:
        Dim componentUnderTest As New StockAnalyzer(stockFeed)
        ' Set the value that will be returned by the stub:
        priceToReturn = 345

        ' Act:
        Dim actualResult As Integer = componentUnderTest.GetContosoPrice()

        ' Assert:
        ' Verify the correct result in the usual way:
        Assert.AreEqual(priceToReturn, actualResult)
        ' Verify that the component made the correct call:
        Assert.AreEqual("COOO", companyCodeUsed)
    End Sub
...
End Class
```

## <a name="stubs-for-different-kinds-of-type-members"></a>Wycinki dla różnych rodzajów elementów członkowskich typu

### <a name="methods"></a>Metody

Jak opisano w przykładzie, metody można dzielić na wycinki, dołączając delegata do instancji klasy wycinka. Nazwa typu wycinka pochodzi od nazwy metody i parametrów. Przykładowo, podana następujące `IMyInterface` interfejsu i metoda `MyMethod`:

```csharp
// application under test
interface IMyInterface
{
    int MyMethod(string value);
}
```

Firma Microsoft, Dołącz szkielet do `MyMethod` zawsze zwraca 1:

```csharp
// unit test code
var stub = new StubIMyInterface ();
stub.MyMethodString = (value) => 1;
```

Jeśli nie podano wycinka dla funkcji, środowisko Fakes wygeneruje funkcję zwracającą wartość domyślną typu zwracanego. W przypadku numerów wartość domyślna to 0, a dla typu klasy jest `null` (C#) lub `Nothing` (Visual Basic).

### <a name="properties"></a>Właściwości

Metody pobierające i ustawiające są widoczne jako oddzielne delegaty i mogą tworzyć poszczególne wycinki. Rozważmy na przykład `Value` właściwości `IMyInterface`:

```csharp
// code under test
interface IMyInterface
{
    int Value { get; set; }
}
```

Firma Microsoft dołączyć do metody pobierającej i ustawiającej z delegatów `Value` do symulowania auto właściwością:

```csharp
// unit test code
int i = 5;
var stub = new StubIMyInterface();
stub.ValueGet = () => i;
stub.ValueSet = (value) => i = value;
```

Jeśli nie podano metody zastępczej ani dla metod ustawiających, ani pobierających właściwości, środowisko Fakes wygeneruje odcinek, który przechowuje wartości, tak aby właściwość zastępcza działała jak prosta zmienna.

### <a name="events"></a>Zdarzenia

Zdarzenia są uwidocznione jako pola delegatów. W rezultacie wszystkie zdarzenia przekształcone na wycinki mogą być łatwo wywoływane przez wywołanie zdarzenia pola pomocniczego. Zastanówmy można zastąpić klasą zastępczą interfejsu:

```csharp
// code under test
interface IWithEvents
{
    event EventHandler Changed;
}
```

Aby podnieść `Changed` zdarzeń, możemy po prostu wywołać delegata zapasowy:

```csharp
// unit test code
  var withEvents = new StubIWithEvents();
  // raising Changed
  withEvents.ChangedEvent(withEvents, EventArgs.Empty);
```

### <a name="generic-methods"></a>Metody ogólne

Istnieje możliwość stub metody ogólne, podając delegata podczas tworzenia wystąpienia każdej żądanej metody. Na przykład, biorąc pod uwagę następujący interfejs, zawierający metodę ogólną:

```csharp
// code under test
interface IGenericMethod
{
    T GetValue<T>();
}
```

można zapisać testu, który zastępcze `GetValue<int>` podczas tworzenia wystąpienia:

```csharp
// unit test code
[TestMethod]
public void TestGetValue()
{
    var stub = new StubIGenericMethod();
    stub.GetValueOf1<int>(() => 5);

    IGenericMethod target = stub;
    Assert.AreEqual(5, target.GetValue<int>());
}
```

Jeśli kod zostały do wywołania `GetValue<T>` z innego wystąpienia elementu zastępczego po prostu wywołać to zachowanie.

### <a name="stubs-of-virtual-classes"></a>Wycinki wirtualnych klas

W poprzednich przykładach wycinki zostały wygenerowane z interfejsów. Można również wygenerować wycinki z klasy, która ma składowe virtual lub abstract. Na przykład:

```csharp
// Base class in application under test
    public abstract class MyClass
    {
        public abstract void DoAbstract(string x);
        public virtual int DoVirtual(int n)
        { return n + 42; }
        public int DoConcrete()
        { return 1; }
    }
```

W wycinku wygenerowanym z tej klasy można ustawić metody delegowane dla DoAbstract() i DoVirtual(), ale nie DoConcrete().

```csharp
// unit test
  var stub = new Fakes.MyClass();
  stub.DoAbstractString = (x) => { Assert.IsTrue(x>0); };
  stub.DoVirtualInt32 = (n) => 10 ;
```

Jeśli nie podasz delegata dla metody wirtualnej, środowisko Fakes może zapewnić zachowanie domyślne albo wywoływać metodę w klasie bazowej. Aby wywołać metodę podstawową, należy ustawić `CallBase` właściwości:

```csharp
// unit test code
var stub = new Fakes.MyClass();
stub.CallBase = false;
// No delegate set - default delegate:
Assert.AreEqual(0, stub.DoVirtual(1));

stub.CallBase = true;
// No delegate set - calls the base:
Assert.AreEqual(43,stub.DoVirtual(1));
```

## <a name="debug-stubs"></a>Debugowanie klas zastępczych

Typy wycinków zostały tak zaprojektowane, aby zapewniać płynność debugowania. Domyślnie debuger pomija kod generowany, powinien więc wejść bezpośrednio do niestandardowych implementacji elementu członkowskiego, które zostały dołączone do wycinka.

## <a name="stub-limitations"></a>Ograniczenia dotyczące wycinka

1. Podpisy metod z wskaźniki nie są obsługiwane.

2. Zapieczętowane klasy lub metod statycznych nie można zastąpić jej metodą zastępczą ponieważ stub typy korzystają z metody wirtualnej wysyłania. W takich przypadkach użyć typów podkładki, zgodnie z opisem w [stosowanie podkładek do izolowania aplikacji od innych zestawów w celu przeprowadzania testów jednostkowych](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

## <a name="change-the-default-behavior-of-stubs"></a>Zmień domyślne zachowanie klas zastępczych

Każdy typ wygenerowanego stub posiada wystąpienia `IStubBehavior` interfejsu (za pośrednictwem `IStub.InstanceBehavior` właściwości). Zachowanie jest wywoływane za każdym razem, gdy klient wywołuje element członkowski, który nie ma dołączonego niestandardowego delegata. Jeśli zachowanie nie została ustawiona, zostanie użyty wystąpienia zwrócony przez `StubsBehaviors.Current` właściwości. Domyślnie ta właściwość zwraca zachowanie, która zgłasza `NotImplementedException` wyjątku.

To zachowanie można zmienić w dowolnym momencie przez ustawienie `InstanceBehavior` właściwości na dowolne wystąpienie klasy zastępczej. Na przykład poniższy fragment kodu zmienia zachowanie, które nie działają lub zwraca wartość domyślna typu zwracanego: `default(T)`:

```csharp
// unit test code
var stub = new StubIFileSystem();
// return default(T) or do nothing
stub.InstanceBehavior = StubsBehaviors.DefaultValue;
```

Zachowanie można zmienić globalnie do wszystkich obiektów, dla których zachowanie nie została ustawiona przez ustawienie zastąpić klasą zastępczą `StubsBehaviors.Current` właściwości:

```csharp
// Change default behavior for all stub instances
// where the behavior has not been set.
StubBehaviors.Current = BehavedBehaviors.DefaultValue;
```

## <a name="see-also"></a>Zobacz także

- [Izolowanie testowanego kodu za pomocą struktury Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)