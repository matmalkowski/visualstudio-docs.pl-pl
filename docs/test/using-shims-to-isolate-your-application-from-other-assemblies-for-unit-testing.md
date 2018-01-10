---
title: "Stosowanie podkładek do izolowania aplikacji od innych zestawów w celu przeprowadzania testów jednostkowych | Dokumentacja firmy Microsoft"
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
ms.openlocfilehash: 3a0d2932e4fc14070759906ad27c36f63132559b
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing"></a>Stosowanie podkładek do izolowania aplikacji od innych zestawów w celu przeprowadzania testów jednostkowych
**Poprawki typy** są jednym z dwie technologie używane przez program Microsoft substytutów Framework do pozwalają łatwo odizolowanego składniki w ramach testu ze środowiska. Podkładek kierowanie wywołań określonych metod do kodu, który można zapisać jako część testu. Wiele metod zwraca różne wyniki zależy od warunków zewnętrznych, ale podkładki jest pod kontrolą testu i może zwrócić spójne wyniki przy każdym wywołaniu. Dzięki temu można łatwiej zapisu testów.  
  
 Użyć podkładek do izolowania kodu z zestawów, które nie są częścią rozwiązania. Aby wyizolować składniki rozwiązania od siebie, zaleca się używanie klas zastępczych.  
  
 Aby uzyskać przegląd i szybki start wskazówki, zobacz [izolowanie kodu w obszarze testów z Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)  
  
 **Wymagania**  
  
-   Visual Studio Enterprise  
  
 Zobacz [wideo (16 1-h): testowanie testować usunięcie kodu z substytutami w programie Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkId=261837)  
  
## <a name="in-this-topic"></a>W tym temacie:  
 Oto, co dowiesz się, w tym temacie:  
  
 [Przykład: Y2K usterki](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Example__The_Y2K_bug)  
  
 [Jak używać podkładek](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Fakes_requirements)  
  
-   [Dodawanie zestawów elementów sztucznych](#AddFakes)  
  
-   [Użyj ShimsContext](#ShimsContext)  
  
-   [Napisać testy z podkładek](#WriteTests)  
  
 [Podkładek dla różnych rodzajów metod](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Shim_basics)  
  
-   [Metody statyczne](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Static_methods)  
  
-   [Wystąpienie metody (dla wszystkich wystąpień)](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Instance_methods__for_all_instances_)  
  
-   [Wystąpienie metody (jedno wystąpienie środowiska wykonawczego)](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Instance_methods__for_one_instance_)  
  
-   [Konstruktory](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Constructors)  
  
-   [Podstawowe elementy członkowskie](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Base_members)  
  
-   [Konstruktory statyczne](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Static_constructors)  
  
-   [Finalizatory](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Finalizers)  
  
-   [Prywatnych metod](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Private_methods)  
  
-   [Interfejsy wiązania](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Binding_interfaces)  
  
 [Zmiana domyślnego zachowania](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Changing_the_default_behavior)  
  
 [Uzyskuje dostęp do środowiska wykrywania](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Detecting_environment_accesses)  
  
 [Współbieżność](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Concurrency)  
  
 [Wywołanie metody oryginalnego z metody podkładki](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Calling_the_original_method_from_the_shim_method)  
  
 [Ograniczenia](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Limitations)  
  
##  <a name="BKMK_Example__The_Y2K_bug"></a>Przykład: Y2K usterki  
 Zastanówmy metodę, która zgłasza wyjątek na 1 stycznia 2000:  
  
```csharp  
// code under test  
public static class Y2KChecker {  
    public static void Check() {  
        if (DateTime.Now == new DateTime(2000, 1, 1))  
            throw new ApplicationException("y2kbug!");  
    }  
}  
  
```  
  
 Testowanie ta metoda jest szczególnie problemy, ponieważ program jest zależny od `DateTime.Now`, metody, która zależy od komputera na zegara, środowisko zależnych deterministyczna — metoda. Ponadto `DateTime.Now` jest właściwość statyczna, więc nie można tutaj użyć typu klasy zastępczej. Ten problem jest objawowych wydania izolacji w testy jednostkowe: programy, które bezpośrednio wywołują API bazy danych, komunikować się z usługami sieci web i tak dalej są trudne do testu jednostkowego, ponieważ ich logiki zależy od środowiska.  
  
 Jest to, gdzie należy używać typów podkładki. Typy podkładek udostępniają mechanizm można przekierować dowolnej metody .NET do delegata zdefiniowanych przez użytkownika. Podkładki typy kod wygenerowany przez generator elementów sztucznych i używają delegatów, które nazywamy typy podkładki, aby określić nowy implementacje metod.  
  
 Następującego testu przedstawia sposób użycia typu podkładki `ShimDateTime`w celu zapewnienia niestandardowej implementacji DateTime.Now:  
  
```csharp  
//unit test code  
// create a ShimsContext cleans up shims   
using (ShimsContext.Create()  
    // hook delegate to the shim method to redirect DateTime.Now  
    // to return January 1st of 2000  
    ShimDateTime.NowGet = () => new DateTime(2000, 1, 1);  
    Y2KChecker.Check();  
}  
  
```  
  
##  <a name="BKMK_Fakes_requirements"></a>Jak używać podkładek  
  
###  <a name="AddFakes"></a>Dodawanie zestawów elementów sztucznych  
  
1.  W Eksploratorze rozwiązań rozwiń węzeł projektu testu jednostki **odwołania**.  
  
    -   Jeśli pracujesz w języku Visual Basic, musisz wybrać **Pokaż wszystkie pliki** na pasku narzędzi Eksplorator rozwiązań, aby zapoznać się z listą odwołania.  
  
2.  Wybierz zestaw, który zawiera definicje klas, dla których chcesz utworzyć podkładek. Na przykład jeśli chcesz użyć podkładek DateTime, wybierz System.dll  
  
3.  W menu skrótów wybierz **dodać zestawu elementów sztucznych**.  
  
###  <a name="ShimsContext"></a>Użyj ShimsContext  
 Korzystając z typów podkładek w frameworka testów jednostkowych, należy wpisać kod testu w `ShimsContext` do kontrolowania ważności Twojej podkładek. Jeśli to nie wymagamy, Twoje podkładek czy ostatni dopóki zamknąć elementu AppDomain. Najprostszym sposobem tworzenia `ShimsContext` przy użyciu statycznych `Create()` metody, jak pokazano w poniższym kodzie:  
  
```csharp  
//unit test code  
[Test]  
public void Y2kCheckerTest() {  
  using(ShimsContext.Create()) {  
    ...  
  } // clear all shims  
}  
  
```  
  
 Należy poprawnie usuwania każdy kontekst podkładki. Jako zasadą, wywoływanie zawsze `ShimsContext.Create` wewnątrz `using` instrukcji w celu zapewnienia prawidłowego rozliczanie zarejestrowanych podkładek. Na przykład możesz zarejestrować podkładki dla metody testowej, która zastępuje `DateTime.Now` metody z delegata, który zawsze zwraca pierwszy stycznia 2000. Jeśli zapomnisz wyczyść zarejestrowanych podkładki w metodzie testowej, pozostałe uruchomienia testu zawsze zwróci wartość pierwszego stycznia 2000 jako DateTime.Now. Może to być suprising i skomplikowana.  
  
###  <a name="WriteShims"></a>Pisanie testów z podkładek  
 W kodzie testu, Wstaw *przekierowania* dla metody ma być fałszywe. Na przykład:  
  
```csharp  
[TestClass]  
public class TestClass1  
{   
        [TestMethod]  
        public void TestCurrentYear()  
        {  
            int fixedYear = 2000;  
  
            using (ShimsContext.Create())  
            {  
              // Arrange:  
                // Detour DateTime.Now to return a fixed date:  
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
  
 Nazwy klas podkładki składają się dodając `Fakes.Shim` oryginalną nazwę typu.  
  
 Podkładek pracy przez wstawienie *przekierowania* do kodu testowanej aplikacji. Wszędzie tam, gdzie występuje wywołanie do metody oryginalnej, system elementów sztucznych wykonuje przekierowania, tak, aby zamiast wywoływania metody prawdziwe, jest nazywany kodu podkładki.  
  
 Zwróć uwagę, że przekierowania są tworzone i usuwane w czasie wykonywania. Należy zawsze utworzyć przekierowania w życie `ShimsContext`. Po usunięciu, zostaną usunięte wszystkie podkładek utworzonego podczas aktywnej. W tym celu najlepiej wewnątrz `using` instrukcji.  
  
 Może pojawić się kompilacji o błędzie informujący, czy przestrzeń nazw elementów sztucznych nie istnieje. Ten błąd pojawia się czasem, jeśli istnieją inne błędy kompilacji. Usuń inne błędy i zostanie on znikają.  
  
##  <a name="BKMK_Shim_basics"></a>Podkładek dla różnych rodzajów metod  
 Typy podkładek umożliwiają Zastąp dowolnej metody .NET, w tym metody statyczne lub metody-virtual, z własnego delegatów.  
  
###  <a name="BKMK_Static_methods"></a>Metody statyczne  
 Właściwości, aby dołączyć podkładek do metody statyczne są umieszczane w typu podkładki. Każda właściwość ma tylko elementu setter, który może służyć do podłączenia delegata do metody docelowej. Przykładowo, podana klasy `MyClass` z metodą statyczną `MyMethod`:  
  
```csharp  
//code under test  
public static class MyClass {  
    public static int MyMethod() {  
        ...  
    }  
}  
```  
  
 Firma Microsoft dołączyć podkładki do `MyMethod` zwraca zawsze 5:  
  
```csharp  
// unit test code  
ShimMyClass.MyMethod = () =>5;  
```  
  
###  <a name="BKMK_Instance_methods__for_all_instances_"></a>Wystąpienie metody (dla wszystkich wystąpień)  
 Podobnie do metody statyczne metody wystąpienia można obsługiwane dla wszystkich wystąpień. Właściwości, aby dołączyć te ustawienia są umieszczane w zagnieżdżony typ o nazwie wszystkich wystąpień, aby uniknąć pomyłek. Przykładowo, podana klasy `MyClass` z metodą wystąpienia `MyMethod`:  
  
```csharp  
// code under test  
public class MyClass {  
    public int MyMethod() {  
        ...  
    }  
}  
```  
  
 Możesz dołączyć podkładki do `MyMethod` zwraca zawsze 5, niezależnie od tego, wystąpienie:  
  
```csharp  
// unit test code  
ShimMyClass.AllInstances.MyMethod = () => 5;  
```  
  
 Struktura wygenerowanego typu ShimMyClass wygląda następujący kod:  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public static class AllInstances {  
        public static Func<MyClass, int>MyMethod {  
            set {  
                ...  
            }  
        }  
    }  
}  
```  
  
 Należy zauważyć, że substytutów przekazuje wystąpienia środowiska wykonawczego w tym przypadku jako pierwszego argumentu delegata.  
  
###  <a name="BKMK_Instance_methods__for_one_instance_"></a>Wystąpienie metody (jedno wystąpienie środowiska wykonawczego)  
 Wystąpienie metody można można również obsługiwane przez różnych delegatów, oparte na odbiorcy wywołania. Dzięki temu tej samej metody wystąpienia mają różne zachowania dla każdego wystąpienia typu. Właściwości, aby skonfigurować te ustawienia są metody wystąpieniu samego typu podkładki. Każdego typu podkładki wystąpień jest także powiązany z wystąpieniem pierwotnych z typem zastąpionym podkładką.  
  
 Przykładowo, podana klasy `MyClass` z metodą wystąpienia `MyMethod`:  
  
```csharp  
// code under test  
public class MyClass {  
    public int MyMethod() {  
        ...  
    }  
}  
```  
  
 Firma Microsoft można skonfigurować dwa typy podkładek MyMethod tak, aby pierwszy zawsze zwraca 5, a drugi zawsze zwraca 10:  
  
```csharp  
// unit test code  
var myClass1 = new ShimMyClass()  
{  
    MyMethod = () => 5  
};  
var myClass2 = new ShimMyClass { MyMethod = () => 10 };  
```  
  
 Struktura wygenerowanego typu ShimMyClass wygląda następujący kod:  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public Func<int> MyMethod {  
        set {  
            ...  
        }  
    }  
    public MyClass Instance {  
        get {  
            ...  
        }  
    }  
}  
```  
  
 Wystąpienie rzeczywiste typem zastąpionym podkładką jest możliwy za pośrednictwem właściwości wystąpienie:  
  
```csharp  
// unit test code  
var shim = new ShimMyClass();  
var instance = shim.Instance;  
```  
  
 Typu podkładki ma również niejawna konwersja z typem zastąpionym podkładką, dzięki czemu można użyć typu podkładki, ponieważ jest zwykle po prostu:  
  
```csharp  
// unit test code  
var shim = new ShimMyClass();  
MyClass instance = shim; // implicit cast retrieves the runtime  
                         // instance  
```  
  
###  <a name="BKMK_Constructors"></a>Konstruktory  
 Konstruktorów również mogą być obsługiwane aby można było dołączyć typy podkładek do przyszłych obiektów. Każdy Konstruktor jest ujawniona jako statycznej metody konstruktora w typie podkładki. Przykładowo, podana klasy `MyClass` przy użyciu konstruktora biorąc całkowitą:  
  
```csharp  
// code under test  
public class MyClass {  
    public MyClass(int value) {  
        this.Value = value;  
    }  
    ...  
}  
```  
  
 Skonfigurowanie typu podkładki konstruktora, aby każde wystąpienie przyszłych zwraca -5, po wywołaniu metody pobierającej wartość, niezależnie od wartości w Konstruktorze:  
  
```csharp  
// unit test code  
ShimMyClass.ConstructorInt32 = (@this, value) => {  
    var shim = new ShimMyClass(@this) {  
        ValueGet = () => -5  
    };  
};  
```  
  
 Należy pamiętać, że każdy typ podkładki udostępnia dwa konstruktory. W razie potrzeby nowego wystąpienia podczas biorąc zastąpionym podkładką wystąpienie jako argument powinien być używany w Konstruktorze podkładek tylko konstruktora, należy użyć konstruktora domyślnego:  
  
```csharp  
// unit test code  
public ShimMyClass() { }  
public ShimMyClass(MyClass instance) : base(instance) { }  
```  
  
 Struktura wygenerowanego typu ShimMyClass podobny kod followoing:  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass>  
{  
    public static Action<MyClass, int> ConstructorInt32 {  
        set {  
            ...  
        }  
    }  
  
    public ShimMyClass() { }  
    public ShimMyClass(MyClass instance) : base(instance) { }  
    ...  
}  
```  
  
###  <a name="BKMK_Base_members"></a>Podstawowe elementy członkowskie  
 Tworząc podkładki dla typu podstawowego i przekazując wystąpienia podrzędnych jako parametr do konstruktora klasy podstawowej podkładki można uzyskać dostępu do właściwości podkładki podstawowe elementy członkowskie.  
  
 Przykładowo, podana klasy `MyBase` z metodą wystąpienia `MyMethod` i podtypu `MyChild`:  
  
```csharp  
public abstract class MyBase {  
    public int MyMethod() {  
        ...  
    }  
}  
  
public class MyChild : MyBase {  
}  
  
```  
  
 Firma Microsoft można skonfigurować podkładkę z `MyBase` przez utworzenie nowej `ShimMyBase` podkładek:  
  
```csharp  
// unit test code  
var child = new ShimMyChild();  
new ShimMyBase(child) { MyMethod = () => 5 };  
```  
  
 Należy pamiętać, że typ podrzędny podkładki jest niejawnie przekonwertowana na wystąpienie podrzędnych podczas przekazany jako parametr do konstruktora podstawowego podkładki.  
  
 Struktura wygenerowanego typu ShimMyChild i ShimMyBase podobny następujący kod:  
  
```csharp  
// Fakes generated code  
public class ShimMyChild : ShimBase<MyChild> {  
    public ShimMyChild() { }  
    public ShimMyChild(Child child)  
        : base(child) { }  
}  
public class ShimMyBase : ShimBase<MyBase> {  
    public ShimMyBase(Base target) { }  
    public Func<int> MyMethod  
    { set { ... } }  
}  
```  
  
###  <a name="BKMK_Static_constructors"></a>Konstruktory statyczne  
 Typy podkładek ujawnia metody statycznej `StaticConstructor` do poprawki statycznego konstruktora typu. Ponieważ konstruktory statyczne są wykonywane, gdy tylko, należy upewnić się, że podkładki skonfigurowano przed uzyskaniem dostępu do dowolnego członka typu.  
  
###  <a name="BKMK_Finalizers"></a>Finalizatory  
 Finalizatory nie są obsługiwane w substytutami.  
  
###  <a name="BKMK_Private_methods"></a>Prywatnych metod  
 Generator kodu elementów sztucznych spowoduje utworzenie właściwości podkładki dla prywatnych metod, w których tylko typy widoczne w podpisie, tj. typy parametrów i typ zwracany jest widoczny.  
  
###  <a name="BKMK_Binding_interfaces"></a>Interfejsy wiązania  
 Gdy typem zastąpionym podkładką implementuje interfejs, generatora kodu emituje metodę, która umożliwi jednocześnie powiązać wszystkie elementy członkowskie z tego interfejsu.  
  
 Przykładowo, podana klasy `MyClass` implementującej `IEnumerable<int>`:  
  
```csharp  
public class MyClass : IEnumerable<int> {  
    public IEnumerator<int> GetEnumerator() {  
        ...  
    }  
    ...  
}  
  
```  
  
 Możemy użyć podkładek implementacje `IEnumerable<int>` w MyClass przez wywołanie metody Bind:  
  
```csharp  
// unit test code  
var shimMyClass = new ShimMyClass();  
shimMyClass.Bind(new List<int> { 1, 2, 3 });  
  
```  
  
 Struktura wygenerowanego typu ShimMyClass podobny następujący kod:  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public ShimMyClass Bind(IEnumerable<int> target) {  
        ...  
    }  
}  
  
```  
  
##  <a name="BKMK_Changing_the_default_behavior"></a>Zmiana domyślnego zachowania  
 Każdy typ wygenerowanego podkładki posiada wystąpienia `IShimBehavior` interfejs, za pomocą `ShimBase<T>.InstanceBehavior` właściwości. Zachowanie jest używana zawsze, gdy klient wywołuje elementu członkowskiego wystąpienia, który nie został jawnie obsługiwane.  
  
 Jeśli zachowanie nie została jawnie ustawiona, zostanie użyty wystąpienia zwrócony przez statycznych `ShimsBehaviors.Current` właściwości. Domyślnie ta właściwość zwraca zachowanie, która zgłasza `NotImplementedException` wyjątku.  
  
 To zachowanie można zmienić w dowolnym momencie przez ustawienie `InstanceBehavior` właściwości na dowolne wystąpienie podkładki. Na przykład poniższy fragment zmiany podkładki zachowanie, które nie działają lub zwraca wartość domyślna typu zwracanego — to znaczy default(T):  
  
```csharp  
// unit test code  
var shim = new ShimMyClass();  
//return default(T) or do nothing  
shim.InstanceBehavior = ShimsBehaviors.DefaultValue;  
  
```  
  
 To zachowanie można zmienić globalnie dla wszystkich wystąpień zastąpionym podkładką dla którego `InstanceBehavior` właściwość nie została jawnie ustawiona przez ustawienie statycznych `ShimsBehaviors.Current` właściwości:  
  
```csharp  
// unit test code  
// change default shim for all shim instances  
// where the behavior has not been set  
ShimsBehaviors.Current =   
    ShimsBehaviors.DefaultValue;  
  
```  
  
##  <a name="BKMK_Detecting_environment_accesses"></a>Uzyskuje dostęp do środowiska wykrywania  
 Istnieje możliwość zachowanie dołączone do wszystkich elementów członkowskich, łącznie z metody statyczne określonego typu, przypisując `ShimsBehaviors.NotImplemented` zachowania do właściwości statycznej `Behavior` odpowiedniego typu podkładki:  
  
```csharp  
// unit test code  
// assigning the not implemented behavior  
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;  
// shorthand  
ShimMyClass.BehaveAsNotImplemented();  
  
```  
  
##  <a name="BKMK_Concurrency"></a>Współbieżność  
 Typy podkładek dotyczą wszystkich wątków w domenie aplikacji i nie mają koligacji wątku. Jest to ważne faktem, jeśli planujesz używać uruchamiający, która obsługuje współbieżności: testy typów podkładek nie można uruchamiać jednocześnie. Ta właściwość nie jest enfored przez środowisko uruchomieniowe substytutami.  
  
##  <a name="BKMK_Calling_the_original_method_from_the_shim_method"></a>Wywołanie metody oryginalnego z metody podkładki  
 Załóżmy, możemy faktycznie zapisywanie tekstu do systemu plików po sprawdzania poprawności nazwy pliku przekazywany do metody. W takim przypadku chcemy czy wywołać metodę oryginalnego środku metody podkładki.  
  
 Pierwszym sposobem rozwiązania tego problemu jest powodującą otoczenie wywołania oryginalnej metody przy użyciu delegata i `ShimsContext.ExecuteWithoutShims()` zgodnie z poniższym kodem:  
  
```csharp  
// unit test code  
ShimFile.WriteAllTextStringString = (fileName, content) => {  
  ShimsContext.ExecuteWithoutShims(() => {  
  
      Console.WriteLine("enter");  
      File.WriteAllText(fileName, content);  
      Console.WriteLine("leave");  
  });  
};  
  
```  
  
 Innym rozwiązaniem jest podkładki do wartości null, wywołaj metodę oryginalnego i przywrócić podkładki.  
  
```csharp  
// unit test code  
ShimsDelegates.Action<string, string> shim = null;  
shim = (fileName, content) => {  
  try {  
    Console.WriteLine("enter");  
    // remove shim in order to call original method  
    ShimFile.WriteAllTextStringString = null;  
    File.WriteAllText(fileName, content);  
  }  
  finally  
  {  
    // restore shim  
    ShimFile.WriteAllTextStringString = shim;  
    Console.WriteLine("leave");  
  }  
};  
// initialize the shim  
ShimFile.WriteAllTextStringString = shim;  
  
```  
  
##  <a name="BKMK_Limitations"></a>Ograniczenia  
 Nie można użyć podkładek dla wszystkich typów z biblioteki .NET klasy podstawowej **mscorlib** i **systemu**.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
### <a name="guidance"></a>Wskazówki  
 [Testowanie pod kątem ciągłego dostarczania w programie Visual Studio 2012 — rozdział 2: testy jednostkowe: testowanie wewnątrz](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Zobacz też  
 [Izolowanie testowanego pomocą struktury Microsoft Fakes kodu](../test/isolating-code-under-test-with-microsoft-fakes.md)   
 [Blog Provost Peterowi: Visual Studio 2012 podkładek](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)   
 [Wideo (16 1-h): testowanie testować usunięcie kodu z substytutami w programie Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkId=261837)
