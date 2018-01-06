---
title: Szybkie akcje | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.workload: multiple
ms.openlocfilehash: 7e70e4366ca91e00beeb4fff49ec30d4618bde81
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="quick-actions"></a>Szybkie akcje

[Szybkie akcje](refactoring-code-generation-quick-actions.md#quick-actions) pozwalają łatwo zrefaktoryzuj, generowanie lub modyfikację kodu za pomocą jednej akcji. Szybkie akcje są dostępne w języku C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp)i plików kodu programu Visual Basic. Niektóre akcje są specyficzne dla języka, a inne dotyczą wszystkich wersji językowych. Szybkie akcje mogą być stosowane przy użyciu ikoną żarówki ![małych ikon żarówki](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall"), lub naciskając klawisz **Ctrl** + **.** gdy kursor znajduje się na odpowiedni wiersz kodu.

Pojawi się, że żarówki, jeśli istnieje czerwona falista i Visual Studio ma sugestię jak rozwiązać problem. Na przykład jeśli masz wskazaniem czerwona falista błąd żarówka będą wyświetlane, gdy poprawki są dostępne dla tego błędu. Dla żadnego języka stron trzecich mogą zapewnić diagnostyki niestandardowej i sugestie, na przykład jako część zestawu SDK i programu Visual Studio żarówki uaktywni się oparte na tych zasad.

## <a name="to-see-a-light-bulb"></a>Aby wyświetlić żarówka

1. W wielu przypadkach żarówki samorzutnie są wyświetlane po wskaźnika myszy w punkcie błąd lub na lewym marginesie edytora przenoszenia karetkę do wiersza, która zawiera błąd w nim. Gdy pojawi się czerwona falista, możesz go, aby wyświetlić żarówkę Aktywuj. Może również spowodować żarówka wyświetlany, gdy używasz myszy lub klawiatury można przejść do dowolnej lokalizacji w wierszu gdzie występuje problem.

1. Naciśnij klawisz **Ctrl** + **.** dowolne miejsce na linię, aby wywołać żarówkę i przejść bezpośrednio do listy potencjalnych poprawek.

   ![Żarówki z ustawiając kursor myszy](../ide/media/vs2015_lightbulb_hover.png "VS2017_LightBulb_Hover")

## <a name="to-see-potential-fixes"></a>Aby wyświetlić potencjalne rozwiązania

Kliknij strzałkę w dół lub potencjalne Pokaż poprawki łącze, aby wyświetlić listę szybkie akcje wykonywane przez żarówkę dla Ciebie.

![Żarówki rozwinięty](../ide/media/vs2015_lightbulb_hover_expanded.png "VS2017_LightBulb_hover_expanded")

## <a name="common-quick-actions"></a>Typowe szybkie akcje

Poniżej przedstawiono niektóre typowe szybkie akcje, które mają zastosowanie zarówno C# i Visual Basic kodu:

- [Akcje, które błędy](#fix)
- [Akcje, które usunąć niepotrzebne kodu](#remove)
- [Działania polegające na dodawaniu Brak kodu](#add)
- [Kod — przekształcenia](#transform)

### <a id="fix"></a>Akcje, które błędy

#### <a name="correct-misspelled-symbol-or-keyword"></a>Popraw błędnie symbolu lub słowo kluczowe

|  Identyfikator błędu | Właściwe języki |  Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| CS0103, BC30002 | C# i Visual Basic | Visual Studio 2015 Update 2 |

Jeśli przypadkowo błędnie typu lub słowo kluczowe w programie Visual Studio tej akcji szybkiego automatycznie poprawi go dla Ciebie. Zobaczysz te elementy w menu żarówki jako  **"Zmień"*zawiera błąd pisowni word*"do"*poprawić wyraz*"**.  Na przykład:

```csharp
// Before
private viod MyMethod()
{
}

// Change 'viod' to 'void'

// After
private void MyMethod()
{
}
```

```vb
' Before
Function MyFunction as Intger
End Function

' Change 'Intger' to 'Integer'

' After
Function MyFunction as Integer
End Function
```

#### <a name="resolve-git-merge-conflict"></a>Rozwiązanie konfliktu scalania git

|  Identyfikator błędu | Właściwe języki |  Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| CS8300, BC37284  | C# i Visual Basic | Visual Studio 2017 wersji 15 ustęp 3 |

Te szybkie akcje umożliwiają rozwiązywanie konfliktów scalania git "podejmując zmiany", które powoduje usunięcie powodujące konflikt kodu i znaczników.  

```csharp
// Before
private void MyMethod()
{
<<<<<<< HEAD
    if (true)
    {

    }
=======
    if (false)
    {

    }
>>>>>>> upstream
}

// Take changes from 'HEAD'

// After
private void MyMethod()
{
    if (true)
    {

    }
}
```

#### <a name="make-method-synchronous"></a>Wprowadź synchroniczne — metoda

|  Identyfikator błędu | Właściwe języki |  Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| CS1998, BC42356 | C# i Visual Basic | Visual Studio 2015 Update 2 |

Przy użyciu `async` lub `Async` — słowo kluczowe dla metody, należy spodziewać się, że gdzieś wewnątrz tej metody `await` lub `Await` również będzie można użyć słowa kluczowego.  Jednak jeśli nie jest to wymagane, szybkie działanie będzie się, że będzie umożliwiają metoda synchroniczna przez usunięcie `async` lub `Async` — słowo kluczowe i zmiany zwracanego typu. Użyj **upewnij metoda synchroniczna** opcji z menu Szybkie akcje.

```csharp
// Before
async Task<int> MyAsyncMethod()
{
    return 3;
}

// Make method synchronous

// After
int MyAsyncMethod()
{
    return 3;
}
```

```vb
' Before
Async Function MyAsyncMethod() As Task(Of Integer)
    Return 3
End Function

' Make method synchronous

' After
Function MyAsyncMethod() As Integer
    Return 3
End Function
```

#### <a name="make-method-asynchronous"></a>Wprowadź asynchroniczne — metoda

|  Identyfikator błędu | Właściwe języki |  Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| CS4032, BC37057 | C# i Visual Basic | Visual Studio 2017 |

Korzystając z `await` lub `Await` — słowo kluczowe wewnątrz metody, oczekuje się, że metoda sam jest oznaczona atrybutem `async` lub `Async` — słowo kluczowe.  Jednak jeśli nie jest to wymagane, szybkie działanie będzie się, że będzie umożliwiają metody asynchronicznej. Użyj **upewnij asynchronicznej metody/funkcja** opcji z menu Szybkie akcje.

```csharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method asynchronous

// After
async Task<int> MyAsyncMethod()
{
    return await Task.Run(...);
}
```

```vb
' Before
Function MyAsyncMethod() as Integer
    Return  Await Task.Run(...)
End Function

' Make method asynchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

### <a id="remove"></a>Akcje, które usunąć niepotrzebne kodu

#### <a name="remove-unnecesary-usingsimports"></a>Usuń niepotrzebnymi deklaracje Using/importów

|  Właściwe języki |  Obsługiwana wersja |
|  -------------------- | ----------------  |
|  C# i Visual Basic | Visual Studio 2015 RTW |

**Usunąć niepotrzebne deklaracje Using/importów** szybkich akcji usunie wszystkie nieużywane `using` i `Import` instrukcji dla bieżącego pliku.  Po wybraniu tego elementu importów nieużywanej przestrzeni nazw zostaną natychmiast usunięte.

#### <a name="remove-unnecessary-cast"></a>Usuwania niepotrzebnego rzutowania

|  Identyfikator diagnostyczny | Właściwe języki |  Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| IDE0004 | C# i Visual Basic | Visual Studio 2015 RTW |

Jeśli rzutowania typu na inny typ, który nie wymaga rzutowania **Usuń niepotrzebnego rzutowania** elementu szybkich akcji spowoduje usunięcie rzutowanie w kodzie.

```csharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```

```vb
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

#### <a name="remove-unused-variables"></a>Usuń nieużywane zmienne

|  Identyfikator diagnostyczny | Właściwe języki |  Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| CS0219, BC42024 | C# i Visual Basic | Visual Studio 2017 wersji 15 ustęp 3 |

Ta akcja szybkiego umożliwia usunięcie zmiennych, które są zadeklarowane, ale nigdy używana w kodzie.

```csharp
// Before
public MyMethod()
{
    var unused = 8;
    var used = 1;
    return DoStuff(used);
}

// Remove unused variables

// After
public MyMethod()
{
    var used = 1;
    return DoStuff(used);
}
```

#### <a name="remove-type-from-default-value-expression"></a>Usuwanie typu z **domyślne** wyrażenie wartości

|  Identyfikator diagnostyczny | Właściwe języki |  Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| IDE0034 | C# 7.1 + | Visual Studio 2017 wersji 15 ustęp 3 |

Ta akcja szybkie usuwa typu wartości wyrażenia wartości domyślnej i używa [ `default` literału](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) gdy kompilator może wnioskować o typie wyrażenia.

```csharp
// Before
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }

// Simplify default expression

// After
void DoWork(CancellationToken cancellationToken = default) { ... }

```

### <a id="add"></a>Działania polegające na dodawaniu Brak kodu

#### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Dodaj deklaracje Using/Importy dla typów zestawów odwołań, pakiety NuGet lub innych typów w rozwiązaniu

|  Identyfikator diagnostyczny | Właściwe języki |  Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| CS0103, BC30451 | C# i Visual Basic| Visual Studio 2015 Update 2 |

Używanie typów znajduje się w innych projektów w rozwiązaniu będzie ona wyświetlana szybkie automatycznie, jednak inne muszą być włączone z **Narzędzia > Opcje > C#** lub **podstawowe > Zaawansowane** karty:

- Sugeruj użycie/Importy dla typów w zestawach odwołania
- Sugeruj użycie/Importy dla typów w pakietach NuGet

Po włączeniu użycie typu w przestrzeni nazw, która jest on aktualnie zaimportowany, ale istnieje odwołanie do zestawu lub pakietu NuGet, zostanie utworzona instrukcji za pomocą import.

```csharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```

```vb
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

// After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

#### <a name="add-missing-casesdefault-caseboth"></a>Dodaj brakujące przypadków lub domyślnego zarówno case

|  Identyfikator diagnostyczny | Właściwe języki |  Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| IDE0010 | C# i Visual Basic| Visual Studio 2017 wersji 15 ustęp 3 |

Podczas tworzenia `switch` instrukcji w języku C# lub `Select Case` instrukcji w języku Visual Basic, można użyć Akcja kodu można automatycznie dodać ma wielkość elementów i/lub instrukcji case domyślne.

Należy wziąć pod uwagę następujące wyliczenie i opróżnić `switch` lub `Select Case` instrukcji:

```csharp
enum MyEnum
{
    Item1,
    Item2,
    Item3
}

...

MyEnum myEnum = MyEnum.Item1;

switch(myEnum)
{
}
```

```vb
Enum MyEnum
    Item1
    Item2
    Item3
End Enum

...

Dim myEnum as MyEnum = MyEnum.Item1

Select Case myEnum
End Select
```

Przy użyciu **Dodaj** szybkie Akcja wypełnia przypadków brakujących i dodaje przypadek domyślny:

```csharp
switch(myEnum)
{
    case MyEnum.Item1:
        break;
    case MyEnum.Item2:
        break;
    case MyEnum.Item3:
        break;
    default:
        break;
}
```

```vb
Select Case myEnum
    Case MyEnum.Item1
        Exit Select
    Case MyEnum.Item2
        Exit Select
    Case Else
        Exit Select
End Select
```

#### <a name="add-null-checks-for-parameters"></a>Dodaj sprawdzenia wartości null dla parametrów

| Właściwe języki |  Obsługiwana wersja |
| -------------------- | ----------------  |
| C# i Visual Basic| Visual Studio 2017 wersji 15 ustęp 3 |

Ta akcja szybkiego umożliwia dodanie kontrolę w kodzie, aby sprawdzić, czy parametr jest pusty.

```csharp
// Before
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty) // cursor inside myProperty
    {
        MyProperty = myProperty;
    }
}

// Add null check

// After
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty)
    {
        MyProperty = myProperty ?? throw new ArgumentNullException(nameof(myProperty));
    }
}
```

#### <a name="add-argument-name"></a>Dodaj nazwy argumentu

| Właściwe języki |  Obsługiwana wersja |
| -------------------- | ----------------  |
| C# i Visual Basic| Visual Studio 2017 wersji 15 ustęp 3 |

```csharp
// Before
var date = new DateTime(1997, 7, 8);

// Include argument name 'year' (include trailing arguments)

// After
var date = new DateTime(year: 1997, month: 7, day: 8);
```

#### <a name="add-braces"></a>Dodaj nawiasy klamrowe

|  Identyfikator diagnostyczny | Właściwe języki |  Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| IDE0011 | C# | Visual Studio 2017 RTW |

Dodaj nawiasy klamrowe szybkich akcji opakowuje nawiasów klamrowych otaczających jednowierszowego `if` instrukcje.

```csharp
// Before
if (true)
    return "hello,world";

// Add braces

// After
if (true)
{
    return "hello,world";
}
```

#### <a name="add-and-order-modifiers"></a>Dodaj i kolejność modyfikatorów

|  Identyfikator diagnostyczny | Właściwe języki |  Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| IDE0036 | C# i Visual Basic| Visual Studio 2017 wersji 15,5 cala |
| IDE0040 | C# i Visual Basic| Visual Studio 2017 wersji 15,5 cala |

Te szybkie akcje zorganizowane modyfikatory, umożliwiając sortowania istniejących i Dodaj brakujące modyfikatory dostępności.

```csharp
// Before
enum Color
{
    Red, White, Blue
}

// Add accessibility modifiers

// After
internal enum Color
{
    Red, White, Blue
}
```

```csharp
// Before
static private int thisFieldIsPublic;

// Order modifiers

// After
private static int thisFieldIsPublic;
```

### <a id="transform"></a>Kod — przekształcenia

#### <a name="convert-if-construct-to-switch"></a>Konwertuj **Jeśli** konstrukcji **przełącznika**

| Właściwe języki |  Obsługiwana wersja |
| -------------------- | ----------------  |
| C# i Visual Basic| Visual Studio 2017 wersji 15 ustęp 3 |

Ta akcja szybkiego umożliwia konwertowanie **if to inaczej** konstrukcji **przełącznika** utworzenia.

```csharp
// Before
if (obj is string s)
{
  Console.WriteLine("obj is a string: " + s);
}

else if (obj is int i && i > 10)
{
  Console.WriteLine("obj is an int greater than 10");
}

// Convert to switch

// After
switch (obj)
{
  case string s:
    Console.WriteLine("Obj is a string: " + s);
    break;
  case int i when i > 10:
    Console.WriteLine("obj is an int greater than 10");
    break;
}
```

```vb
' Before
If TypeOf obj Is String s Then
    Console.WriteLine("obj is a string: " + s)
Else If TypeOf obj Is Integer i And i > 10 Then
    Console.WriteLine("obj is an int greater than 10")
End If

' Convert to switch

' After
Select Case obj
  Case String s
    Console.WriteLine("Obj is a string: " + s)
    Exit Sub
  Case Integer i when i > 10
    Console.WriteLine("obj is an int greater than 10")
    Exit Sub
End Select
```

#### <a name="convert-to-interpolated-string"></a>Konwertuj na ciągu interpolowanym

| Właściwe języki |  Obsługiwana wersja |
| -------------------- | ----------------  |
| C# w wersji 6.0 + i Visual Basic 14 + | Visual Studio 2017 RTW |

[Ciągi interpolowane](/dotnet/csharp/language-reference/keywords/interpolated-strings) są łatwe express ciągi zawierające osadzone zmienne, podobnie jak  **[String.Format](https://msdn.microsoft.com/library/system.string.format.aspx)**  metody.  Ta akcja szybkie rozpoznaje przypadku ciągi połączonych lub przy użyciu **String.Format**, a zmiany użycie w ciągu interpolowanym.

```csharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```

```vb
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

#### <a name="use-object-initializers"></a>Inicjatory obiektów użycia

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| IDE0017 | C# i Visual Basic | Visual Studio 2017 RTW |

Ta akcja szybkie pozwala na użycie [obiekt inicjatory](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) zamiast wywoływania tne konstruktora o dodatkowe wiersze i instrukcje przypisania.

```csharp
// Before
var c = new Customer();
c.Age = 21;

// Object initialization can be simplified

// After
var c = new Customer() { Age = 21 };
```

```vb
' Before
Dim c = New Customer()
c.Age = 21

' Object initialization can be simplified

' After
Dim c = New Customer() With {.Age = 21}
```

#### <a name="use-collection-initializers"></a>Inicjatory kolekcji użycia

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| IDE0028 | C# i Visual Basic | Visual Studio 2017 RTW |

Ta akcja szybkie pozwala używać [inicjatory kolekcji](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) zamiast wielu wywołań `Add` metody klasy.

```csharp
// Before
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);

// Collection initialization can be simplified

// After
var list = new List<int> { 1, 2, 3 };
```

```vb
' Before
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)

' Collection initialization can be simplified

' After
Dim list = New List(Of Integer) From {1, 2, 3}

```

#### <a name="convert-auto-property-to-full-property"></a>Konwertuj właściwości automatycznej pełne właściwości

|  Właściwe języki |  Obsługiwana wersja |
|  -------------------- | ----------------  |
| C# i Visual Basic | Visual Studio 2017 wersji 15,5 cala |

Ta akcja szybkiego umożliwia konwertowanie właściwości automatycznej właściwością pełne i na odwrót.

```csharp
// Before
private int MyProperty { get; set; }

// Convert to full property

// After
private int MyProperty
{
    get { return _myProperty; }
    set { _myProperty = value; }
}
```

```vb
' Before
Public Property Name As String

' Convert to full property

' After
Private _Name As String

Public Property Name As String
    Get
        Return _Name
    End Get
    Set
        _Name = Value
    End Set
End Property
```

#### <a name="convert-block-body-to-expression-bodied-member"></a>Konwertuj treści bloku zabudowanych wyrażenie elementu członkowskiego

|  Identyfikator diagnostyczny | Właściwe języki |  Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| IDE0021-27 | C# W WERSJI 6.0 + | Visual Studio 2017 RTW |

Ta akcja szybkiego umożliwia konwertowanie treści bloku zabudowanych wyrażenia elementów członkowskich dla metod, konstruktorów operatorów, właściwości, indeksatorów i metody dostępu.

```csharp
//Before
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get { return _myProperty; }
        set
        {
            _myProperty = value;
        }
    }

    public MyClass4(int myProperty)
    {
        MyProperty = myProperty;
    }

    public void PrintProperty()
    {
        Console.WriteLine(MyProperty);
    }
}

// Use expression body for accessors/constructors/methods

// After
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get => _myProperty;
        set => _myProperty = value;
    }

    public MyClass4(int myProperty) => MyProperty = myProperty;

    public void PrintProperty() => Console.WriteLine(MyProperty);
}
```

#### <a name="convert-anonymous-function-to-local-function"></a>Konwertuj funkcji anonimowej funkcji lokalnej

|  Identyfikator diagnostyczny | Właściwe języki |  Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| IDE0039 | C# 7.0 + | Visual Studio 2017 wersji 15,5 cala |

Ta akcja szybkie konwertuje funkcje anonimowe funkcje lokalne.

```csharp
// Before
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};

// Use local function

// After
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}
```

#### <a name="convert-referenceequals-to-is-null"></a>Konwertuj `ReferenceEquals` do`is null`

|  Identyfikator diagnostyczny | Właściwe języki |  Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| IDE0041 | C# 7.0 + | Visual Studio 2017 wersji 15,5 cala |

Ta akcja szybkie sugeruje użycie [dopasowanie wzorca](/dotnet/csharp/pattern-matching) zamiast ```ReferenceEquals``` kodowania wzorca, jeśli jest to możliwe.

```csharp
// Before
var value = "someString";
if (object.ReferenceEquals(value, null))
{
    return;
}

// Use 'is null' check

// After
var value = "someString";
if (value is null)
{
    return;
}
```

#### <a name="introduce-pattern-matching"></a>Wprowadzenie dopasowanie wzorca

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| IDE0020 | C# 7.0 + | Visual Studio 2017 RTW |
| IDE0019 | C# 7.0 + | Visual Studio 2017 RTW |

Ta akcja szybkie sugeruje użycie [dopasowanie wzorca](/dotnet/csharp/pattern-matching) rzutowania i sprawdzenia wartości null w języku C#.   

```csharp
// Before
if (o is int)
{
    var i = (int)o;
    ...
}

// Use pattern matching

// After
if (o is int i)
{
    ...
}

```

```csharp
// Before
var s = o as string;
if (s != null)
{
    ...
}

// Use pattern matching

// After
if (o is string s)
{
    ...
}
```

#### <a name="change-base-for-numeric-literals"></a>Podstawa zmiany w literałach numerycznych

| Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| C# 7.0 + i Visual Basic 14 + | Visual Studio 2017 wersji 15 ustęp 3 |

Ta akcja szybkie pozwala konwersji literał liczbowy z jednego podstawowego systemu liczbowego. Na przykład można zmienić liczbę szesnastkową lub format binarny. 

```csharp
// Before
int countdown = 2097152;

// Convert to hex

// After
int countdown = 0x200000;
```

```vb
' Before
Dim countdown As Integer = 2097152

' Convert to hex

' After
Dim countdown As Integer = &H200000
```

#### <a name="insert-digit-separators-into-literals"></a>Wstaw separatory cyfr do literałów

| Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| C# 7.0 + i Visual Basic 14 + | Visual Studio 2017 wersji 15 ustęp 3 |

Ta akcja szybkiego umożliwia dodawanie znaków separatora w wartości literału.

```csharp
// Before
int countdown = 1000000;

// Separate thousands

// After
int countdown = 1_000_000;
```

```vb
' Before
Dim countdown As Integer = 1000000

' Separate thousands

' After
Dim countdown As Integer = 1_000_000
```

#### <a name="use-explicit-tuple-names"></a>Użyj jawnego krotki nazw

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| IDE0033 | C# 7.0 + i Visual Basic 15 + | Visual Studio 2017 RTW |

Ta akcja szybkie identyfikuje obszary, w przypadku nazwa jawnej spójnej kolekcji można użyć zamiast Item1, Item2 itp.

```csharp
// Before
(string name, int age) customer = GetCustomer();
var name = customer.Item1;

// Use explicit tuple name

// After
(string name, int age) customer = GetCustomer();
var name = customer.name;
```

```vb
' Before
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1

' Use explicit tuple name

' After
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name
```

#### <a name="use-inferred-names"></a>Użyj wywnioskować nazw

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| IDE0037 | C# | Visual Studio 2017 v. 15.5 |
| IDE0037 | C# 7.1 + | Visual Studio 2017 v. 15.5 |

Jeśli użytkownicy mogą używać tych wskazują szybkie akcje wywnioskować nazwy elementów członkowskich typów anonimowych lub użyj C# 7.1 w wywnioskować nazwy elementów spójnej kolekcji.

```csharp
// Before
var anon = new { age = age, name = name };

// Use inferred member name

// After
var anon = new { age, name };
```

```csharp
// Before
var tuple = (age: age, name: name);

// Use inferred tuple element name

// After
var tuple = (age, name);
```

#### <a name="deconstruct-tuple-declaration"></a>Deconstruct krotki deklaracji

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ----------------  |
| IDE0042 | C# 7.0 + | Visual Studio 2017 v. 15.5 |

Ta akcja szybkiego umożliwia deconstruct deklaracje zmiennej spójnej kolekcji. 

```csharp
// Before
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");

//Deconstruct variable declaration

// After
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");
```

## <a name="see-also"></a>Zobacz także

[Style kodu i szybkie akcje](code-styles-and-quick-actions.md)  
[Pisanie i refaktoryzacja kodu (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
