---
title: Szybkie akcje | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 05/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: e173fb7d-c5bd-4568-ba0f-aa61913b3244
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 1ba45a0ac183c4f2249461048277eda7cffad1e9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="quick-actions"></a>Szybkie akcje

[Szybkie akcje](refactoring-code-generation-quick-actions.md#quick-actions) pozwalają łatwo zrefaktoryzuj, generowanie lub modyfikację kodu za pomocą jednej akcji.  Gdy istnieje wiele szybkie akcje, które dotyczą przede wszystkim C# lub Visual Basic, dostępne są także te, które dotyczą zarówno C# i Visual Basic projektów.  Te mogą być stosowane przy użyciu ikoną żarówki ![małych ikon żarówki](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall"), lub naciskając klawisz **Ctrl +.** gdy kursor znajduje się na odpowiedni wiersz kodu.

Pojawi się, że żarówki, jeśli istnieje czerwona falista i Visual Studio ma sugestię jak rozwiązać problem. Na przykład jeśli masz wskazaniem czerwona falista błąd żarówka będą wyświetlane, gdy poprawki są dostępne dla tego błędu. Dla żadnego języka stron trzecich mogą zapewnić diagnostyki niestandardowej i sugestie, na przykład jako część zestawu SDK i programu Visual Studio żarówki uaktywni się oparte na tych zasad.  

### <a name="to-see-a-light-bulb"></a>Aby wyświetlić żarówka  

1. W wielu przypadkach żarówki samorzutnie są wyświetlane po wskaźnika myszy w punkcie błąd lub na lewym marginesie edytora przenoszenia karetkę do wiersza, która zawiera błąd w nim. Gdy pojawi się czerwona falista, możesz go, aby wyświetlić żarówkę Aktywuj. Może również spowodować żarówka wyświetlany, gdy używasz myszy lub klawiatury można przejść do dowolnej lokalizacji w wierszu gdzie występuje problem.  

2. Naciśnij klawisz **Ctrl +.** dowolne miejsce na linię, aby wywołać żarówkę i przejść bezpośrednio do listy potencjalnych poprawek.  

   ![Żarówki z ustawiając kursor myszy](../ide/media/vs2015_lightbulb_hover.png "VS2017_LightBulb_Hover")  

### <a name="to-see-potential-fixes"></a>Aby wyświetlić potencjalne rozwiązania  
Kliknij strzałkę w dół lub potencjalne Pokaż poprawki łącze, aby wyświetlić listę szybkie akcje wykonywane przez żarówkę dla Ciebie.  

![Żarówki rozwinięty](../ide/media/vs2015_lightbulb_hover_expanded.png "VS2017_LightBulb_hover_expanded")

## <a name="common-quick-actions"></a>Typowe szybkie akcje
Poniżej przedstawiono niektóre typowe szybkie akcje, które mają zastosowanie zarówno C# i Visual Basic kodu.

### <a name="add-missing-casesdefault-caseboth"></a>Dodaj brakujące przypadków lub domyślnego zarówno case
Podczas tworzenia `switch` instrukcji w języku C# lub `Select Case` instrukcji w języku Visual Basic, można użyć Akcja kodu można automatycznie dodać ma wielkość elementów i/lub instrukcji case domyślne.  Dla pustą instrukcję podobne do poniższych:

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

Przy użyciu **Dodaj** szybkiego działania Wypełnij przypadków brakujących i przypadek domyślny spowoduje utworzenie następujących:

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

### <a name="correct-misspelled-type"></a>Niepoprawny typ błędnie
Jeśli przypadkowo błędem typu w programie Visual Studio, ta akcja szybkie automatycznie poprawi go dla Ciebie.  Zostaną wyświetlone te elementy w menu żarówki jako  **"Zmień"*zawiera błąd pisowni typu*"do"*Popraw typu*"**.  Na przykład:

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

### <a name="remove-unnecessary-cast"></a>Usuwania niepotrzebnego rzutowania
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

### <a name="replace-method-with-property--replace-property-with-method"></a>Zastąp metodę z właściwością / zastąpić właściwość — metoda
Te szybkie akcje przekonwertuje metody do właściwości lub na odwrót.  W poniższym przykładzie pokazano zmiany z metody do właściwości.  W przeciwnym przypadku po prostu Odwróć *przed* i *po* sekcje.

```csharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```
```vb
Dim MyValue As Integer

' Before
Function GetMyValue() As Integer
    Return MyValue
End Function

' Replace 'GetMyValue' with property

' After
ReadOnly Property MyValue As Integer
    Get
        Return MyValue
    End Get
End Property
```

### <a name="make-method-synchronous"></a>Wprowadź synchroniczne — metoda
Przy użyciu `async` / `Async` — słowo kluczowe dla metody, należy spodziewać się, że gdzieś wewnątrz tej metody `await` / `Await` również będzie można użyć słowa kluczowego.  Jednak jeśli nie jest to wymagane, szybkie działanie będzie się, że będzie umożliwiają metoda synchroniczna przez usunięcie `async` / `Async` — słowo kluczowe i zmiany zwracanego typu.  Użyj **upewnij metoda synchroniczna** opcji z menu Szybkie akcje.

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

### <a name="make-method-asynchronous"></a>Wprowadź asynchroniczne — metoda
Korzystając z `await` / `Await` — słowo kluczowe wewnątrz metody, oczekuje się, że metoda sam jest oznaczona atrybutem `async` / `Async` — słowo kluczowe.  Jednak jeśli nie jest to wymagane, szybkie działanie będzie się, że będzie umożliwiają metody asynchronicznej.  Użyj **upewnij asynchronicznej metody/funkcja** opcji z menu Szybkie akcje.

```csharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method synchronous

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

' Make method synchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

### <a name="remove-unnecesary-usingsimports"></a>Usuń niepotrzebnymi deklaracje Using/importów
**Usunąć niepotrzebne deklaracje Using/importów** szybkich akcji usunie wszystkie nieużywane `using` i `Import` instrukcji dla bieżącego pliku.  Po wybraniu tego elementu importów nieużywanej przestrzeni nazw zostaną natychmiast usunięte.

### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Dodaj deklaracje Using/Importy dla typów zestawów odwołań, pakiety NuGet lub innych typów w rozwiązaniu
Używanie typów znajduje się w innych projektów w rozwiązaniu będzie ona wyświetlana szybkie automatycznie, jednak inne muszą być włączone z **Narzędzia > Opcje > C#** lub **podstawowe > Zaawansowane** karty:  

* Sugeruj użycie/Importy dla typów w zestawach odwołania
* Sugeruj użycie/Importy dla typów w pakietach NuGet

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

### <a name="convert-to-interpolated-string"></a>Konwertuj na ciągu Interpolowanym
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

### <a name="remove-merge-conflict-markers"></a>Usuń znaczniki konfliktu scalania
Te szybkie akcje umożliwiają rozwiązywanie konfliktów scalania "podejmując zmiany", które powoduje usunięcie powodujące konflikt kodu i znaczników. (Dostępne tylko w programie Visual Studio 2017 (wersja 15 ustęp 3 — wersja zapoznawcza).)

![Refaktoryzacja — Rozwiązywanie konfliktów scalania](../ide/media/vside-refactoring-merge-conflicts.png)

### <a name="add-null-checks-for-parameters"></a>Dodaj sprawdzenia wartości null dla parametrów
Ta akcja szybkiego umożliwia dodanie kontrolę w kodzie, aby sprawdzić, czy parametr jest pusty. (Dostępne tylko w programie Visual Studio 2017 (wersja 15 ustęp 3 — wersja zapoznawcza).)

![Refaktoryzacja — Dodawanie sprawdzania wartości null](../ide/media/vside-refactoring-nullcheck.png)

### <a name="constructor-generator-improvements"></a>Ulepszenia generator — Konstruktor
Podczas tworzenia konstruktora, ta akcja szybkiego umożliwia wybranie właściwości lub pól, aby wygenerować lub można wygenerować konstruktora z pustej treści. Można również użyć można dodać parametry do istniejących konstruktora z miejsce wywołania. (Dostępne tylko w programie Visual Studio 2017 (wersja 15 ustęp 3 — wersja zapoznawcza).)

![Refaktoryzacja - generowania konstruktorów](../ide/media/vside-refactoring-constructors.png)

### <a name="remove-unused-variables"></a>Usuń nieużywane zmienne
Ta akcja szybkiego umożliwia usunięcie zmiennych, które są zadeklarowane, ale nigdy używana w kodzie. (Dostępne tylko w programie Visual Studio 2017 (wersja 15 ustęp 3 — wersja zapoznawcza).)

![Refaktoryzacja — zmienne](../ide/media/vside-refactoring-unusedvars.png)

### <a name="generate-overrides"></a>Generowanie zastąpień
Ta akcja szybkiego umożliwia utworzenie zastąpienia z pusty wiersz w klasie lub strukturze. **Wybierz elementy członkowskie** okno dialogowe pozwala wybrać elementy członkowskie do przesłonięcia. (Dostępne tylko w programie Visual Studio 2017 (wersja 15 ustęp 3 — wersja zapoznawcza).)

![Refaktoryzacja - zastąpienia](../ide/media/vside-refactoring-overrides.png)

![Refaktoryzacja - zastępuje — okno dialogowe](../ide/media/vside-refactoring-overrides-dialog.png)

### <a name="change-base-for-numeric-literals"></a>Podstawa zmiany w literałach numerycznych
Ta akcja szybkie pozwala konwersji literał liczbowy z jednego podstawowego systemu liczbowego. Na przykład można zmienić liczbę szesnastkową lub format binarny. (Dostępne tylko w programie Visual Studio 2017 (wersja 15 ustęp 3 — wersja zapoznawcza).)

![Refaktoryzacja — Zmień podstawowy](../ide/media/vside-refactoring-changebase1.png)

![Refaktoryzacja — Zmień podstawowy](../ide/media/vside-refactoring-changebase2.png)

### <a name="insert-digit-separators-into-literals"></a>Wstaw separatory cyfr do literałów
Ta akcja szybkiego umożliwia dodawanie znaków separatora w wartości literału. (Dostępne tylko w programie Visual Studio 2017 (wersja 15 ustęp 3 — wersja zapoznawcza).)

![Refaktoryzacja - separatory cyfr zmiany](../ide/media/vside-refactoring-separators.png)

### <a name="convert-if-construct-to-switch"></a>Konwertuj **Jeśli** konstrukcji **przełącznika**
Ta akcja szybkiego umożliwia konwertowanie **if to inaczej** konstrukcji **przełącznika** utworzenia. (Dostępne tylko w programie Visual Studio 2017 (wersja 15 ustęp 3 — wersja zapoznawcza).)

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

## <a name="see-also"></a>Zobacz też
* [Style kodu i szybkie akcje](code-styles-and-quick-actions.md)
