---
title: Kodowanie Konwencji ustawienia EditorConfig .NET | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 10/13/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
helpviewer_keywords: editor
ms.assetid: 
caps.latest.revision: "1"
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.technology: vs-ide-general
ms.openlocfilehash: f59065777de938c07a88d722cabdba82d6b19c02
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>Ustawienia EditorConfig Konwencji kodowania platformy .NET
Można zdefiniować i obsługa styl spójności kodu w Twojej ścieżki bazowej kodu z użyciem [EditorConfig](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options) pliku. EditorConfig zawiera kilka podstawowych właściwości formatowania, takich jak `indent_style` i `indent_size`. W programie Visual Studio .NET kodowania konwencje ustawienia można również skonfigurować przy użyciu pliku EditorConfig. Pliki EditorConfig pozwala włączyć lub wyłączyć poszczególne .NET konwencje kodowania i konfigurowania stopnia, do którego ma Konwencję wymuszane za pośrednictwem poziom ważności. Aby dowiedzieć się więcej o sposobie używania EditorConfig, aby wymusić spójność baza kodu, przeczytaj [Tworzenie niestandardowego edytora przenośne opcji](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options). Można również sprawdzić [pliku .editorconfig platformę .NET kompilatora](https://github.com/dotnet/roslyn/blob/master/.editorconfig) jako przykład.  

Istnieją trzy obsługiwane .NET kodowania Konwencji kategorie:  
- [Konwencje języka](#language-conventions)  
   Reguły dotyczące języka C# lub Visual Basic. Na przykład można określić reguły wokół przy użyciu `var` lub typów jawnych podczas definiowania zmiennych i preferowanie zabudowanych wyrażenia elementów członkowskich.  
- [Konwencji formatowania](#formatting-conventions)  
   Zasady dotyczące układ i struktura kodu w celu ułatwienia odczytu. Na przykład można określić zasady wokół nawiasów klamrowych Allman lub preferowanie spacje w blokach formantu.  
- [Konwencje nazewnictwa](#naming-conventions)  
   Zasady dotyczące nazewnictwa elementów kodu. Na przykład można określić, że `async` metody musi kończyć się "Async".  

## <a name="language-conventions"></a>Konwencje języka  
Zasady konwencje języka mają następujący format:  

`options_name = false|true : none|suggestion|warning|error`  

Dla każdej reguły Konwencji język należy określić **true** (preferowane ten styl) lub **false** (nie chce ten styl), a **ważność**. Ważność określa poziom wymuszania stylu.  

W poniższej tabeli wymieniono wartości ważności możliwe i ich wpływu:  

Ważność | Efekt
:------- | ------
Brak lub dyskretnej | Nie pokazuj żadnych czynności do użytkownika podczas naruszenia tej reguły. Funkcje generowania kodu będzie generować kod jednak w tym stylem.  
Sugestia | W przypadku naruszenia tej reguły stylu przedstawiono go do użytkownika jako sugestię. Sugestie są wyświetlane jako szare wielokropek w dwóch pierwszych znaków.  
ostrzeżenie | Pokaż ostrzeżenie kompilatora, gdy naruszenia tej reguły stylu.  
Błąd | W przypadku naruszenia tej reguły stylu, Pokaż błąd kompilatora.  

Na poniższej liście przedstawiono dopuszczalny języka reguł Konwencji:  

- Ustawienia stylu kodu platformy .NET
    - ["This." i "Me." kwalifikatorów](#this_and_me)
        - DotNet\_styl\_kwalifikacji\_for_field
        - DotNet\_styl\_kwalifikacji\_for_property
        - DotNet\_styl\_kwalifikacji\_for_method
        - DotNet\_styl\_kwalifikacji\_for_event
    - [Słowa kluczowe języka zamiast framework nazwy typów dla odwołania do typu](#language_keywords)
        - DotNet\_styl\_wstępnie zdefiniowanych\_typu\_dla\_zmiennych lokalnych\_parameters_members
        - DotNet\_styl\_wstępnie zdefiniowanych\_typu\_dla\_member_access
    - [Wyrażenie poziom preferencji](#expression_level)
        - DotNet\_styl\_object_initializer
        - DotNet\_styl\_collection_initializer
        - DotNet\_styl\_jawne\_tuple_names
        - DotNet\_styl\_coalesce_expression
        - DotNet\_styl\_null_propagation
- Ustawienia stylu kodu C#
    - [Typy jawne i niejawne](#var)
        - CSharp\_styl\_var\_dla\_wbudowane\_in_types
        - CSharp\_styl\_var\_podczas\_typu\_is_apparent
        - CSharp\_styl\_var_elsewhere
    - [Zabudowanych wyrażenia elementów członkowskich](#expression_bodied_members)
        - CSharp\_styl\_wyrażenie\_bodied_methods
        - CSharp\_styl\_wyrażenie\_bodied_constructors
        - CSharp\_styl\_wyrażenie\_bodied_operators
        - CSharp\_styl\_wyrażenie\_bodied_properties
        - CSharp\_styl\_wyrażenie\_bodied_indexers
        - CSharp\_styl\_wyrażenie\_bodied_accessors
    - [Dopasowanie wzorca](#pattern_matching)
        - CSharp\_styl\_wzorzec\_pasującego\_za pośrednictwem\_jest\_z\_cast_check
        - CSharp\_styl\_wzorzec\_pasującego\_za pośrednictwem\_jako\_z\_null_check
    - [Wbudowane deklaracje zmiennej](#inlined_variable_declarations)
        - CSharp\_styl\_wbudowanego\_variable_declaration
    - [Wyrażenie poziom preferencji](#expression_level_csharp)
        - CSharp\_preferowane\_proste\_default_expression
    - ["Null" Sprawdzanie preferencji](#null_checking)
        - CSharp\_styl\_throw_expression
        - CSharp\_styl\_warunkowego\_delegate_call
    - [Preferencje blok kodu](#code_block)
        - CSharp\_prefer_braces

### <a name="net-code-style-settings"></a>Ustawienia stylu kodu platformy .NET  
Reguły stylu w tej sekcji dotyczą zarówno C# i Visual Basic. Aby wyświetlić przykłady kodu w Twoim preferowanym języku programowania, wybierz je z listy rozwijanej **języka** menu w prawym górnym rogu okna przeglądarki.  

#### <a name="this_and_me">"This." i "Me." kwalifikatorów</a>
Ta zasada styl (reguły IDE0003 identyfikatorów i IDE0009) mogą być stosowane do pól, właściwości, metody lub zdarzenia. Wartość **true** oznacza preferowane symbolu kod, aby być poprzedzone znakiem `this.` w języku C# lub `Me.` w języku Visual Basic. Wartość **false** oznacza preferowane elementu kodu _nie_ do być poprzedzone znakiem `this.` lub `Me.`.  

W poniższej tabeli przedstawiono nazwy reguł, właściwe języki programowania, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:  

| Nazwa reguły | Właściwe języki | Wartość domyślna w usłudze Visual Studio | Obsługiwana wersja |
| ----------- | -------------------- | ----------------------| ----------------  |
| dotnet_style_qualification_for_field | C# i Visual Basic | false: Brak | Visual Studio 2017 RTW |
| dotnet_style_qualification_for_property | C# i Visual Basic | false: Brak | Visual Studio 2017 RTW |
| dotnet_style_qualification_for_method | C# i Visual Basic | false: Brak | Visual Studio 2017 RTW |
| dotnet_style_qualification_for_event | C# i Visual Basic | false: Brak | Visual Studio 2017 RTW |   

**DotNet\_styl\_kwalifikacji\_for_field**  
Jeśli ta reguła jest równa **true**, preferowane pola mają być poprzedzone znakiem `this.` w języku C# lub `Me.` w języku Visual Basic.  
Jeśli ta reguła jest równa **false**, preferowane pola _nie_ do być poprzedzone znakiem `this.` lub `Me.`.  

Przykłady kodu:  

```csharp
// dotnet_style_qualification_for_field = true
this.capacity = 0;

// dotnet_style_qualification_for_field = false
capacity = 0;
```
```vb
' dotnet_style_qualification_for_field = true
Me.capacity = 0

' dotnet_style_qualification_for_field = false
capacity = 0
```  

**DotNet\_styl\_kwalifikacji\_for_property**  
Jeśli ta reguła jest równa **true**, preferowane właściwości, które mają być poprzedzone znakiem `this.` w języku C# lub `Me.` w języku Visual Basic.  
Jeśli ta reguła jest równa **false**, preferowane właściwości _nie_ do być poprzedzone znakiem `this.` lub `Me.`.  

Przykłady kodu:  

```csharp
// dotnet_style_qualification_for_property = true
this.ID = 0;

// dotnet_style_qualification_for_property = false
ID = 0;
```
```vb
' dotnet_style_qualification_for_property = true
Me.ID = 0

' dotnet_style_qualification_for_property = false
ID = 0
```  

**DotNet\_styl\_kwalifikacji\_for_method**  
Jeśli ta reguła jest równa **true**, metody, aby być poprzedzona słowem wybrać `this.` w języku C# lub `Me.` w języku Visual Basic.  
Jeśli ta reguła jest równa **false**, preferowane metody _nie_ do być poprzedzone znakiem `this.` lub `Me.`.  

Przykłady kodu:  

```csharp
// dotnet_style_qualification_for_method = true
this.Display();

// dotnet_style_qualification_for_method = false
Display();
```
```vb
' dotnet_style_qualification_for_method = true
Me.Display()

' dotnet_style_qualification_for_method = false
Display()
```  

**DotNet\_styl\_kwalifikacji\_for_event**  
Jeśli ta reguła jest równa **true**, zdarzenia, które mają być poprzedzona słowem wybrać `this.` w języku C# lub `Me.` w języku Visual Basic.  
Jeśli ta reguła jest równa **false**, preferowane zdarzenia _nie_ do być poprzedzone znakiem `this.` lub `Me.`.  

Przykłady kodu:  

```csharp
// dotnet_style_qualification_for_event = true
this.Elapsed += Handler;

// dotnet_style_qualification_for_event = false
Elapsed += Handler;
```
```vb
' dotnet_style_qualification_for_event = true
AddHandler Me.Elapsed, AddressOf Handler

' dotnet_style_qualification_for_event = false
AddHandler Elapsed, AddressOf Handler
```  

W pliku .editorconfig te reguły może wyglądać następująco:  

```
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="language_keywords">Słowa kluczowe języka zamiast framework nazwy typów dla odwołania do typu</a>
Ta zasada styl można zastosować do zmiennych lokalnych, parametrów metod i elementów członkowskich klasy lub oddzielne zasady do typu w wyrażeniach dostępu do elementu członkowskiego. Wartość **true** oznacza preferowane jest słowo kluczowe języka (np. `int` lub `Integer`) zamiast nazwy typu (np. `Int32`) dla typów, które mają słowa kluczowego reprezentujące je. Wartość **false** oznacza preferowane jest nazwa typu zamiast słowo kluczowe języka.  

W poniższej tabeli przedstawiono nazwy reguł, identyfikatory reguły właściwe języki programowania, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:  

| Nazwa reguły | Identyfikator reguły | Właściwe języki | Domyślny program Visual Studio | Obsługiwana wersja |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| dotnet_style_predefined_type_for_locals_parameters_members | IDE0012 i IDE0014 | C# i Visual Basic | wartość true: Brak | Visual Studio 2017 RTW |
| dotnet_style_predefined_type_for_member_access | IDE0013 i IDE0015 | C# i Visual Basic | wartość true: Brak | Visual Studio 2017 RTW |  

**DotNet\_styl\_wstępnie zdefiniowanych\_typu\_dla\_zmiennych lokalnych\_parameters_members**  
Jeśli ta reguła jest równa **true**, preferowane jest słowem kluczowym języka dla zmiennych lokalnych, parametrów metod i klasy elementów członkowskich, zamiast nazwy typu dla typów, które mają słowa kluczowego reprezentujące je.  
Jeśli ta reguła jest równa **false**, preferowane jest nazwa typu dla zmiennych lokalnych, parametrów metod i klasy elementów członkowskich, zamiast słowo kluczowe języka.  

Przykłady kodu:  

```csharp
// dotnet_style_predefined_type_for_locals_parameters_members = true
private int _member;

// dotnet_style_predefined_type_for_locals_parameters_members = false
private Int32 _member;
```
```vb
' dotnet_style_predefined_type_for_locals_parameters_members = true
Private _member As Integer

' dotnet_style_predefined_type_for_locals_parameters_members = false
Private _member As Int32
``` 

**DotNet\_styl\_wstępnie zdefiniowanych\_typu\_dla\_member_access**   
Jeśli ta reguła jest równa **true**, preferowane jest słowem kluczowym języka dla wyrażeń dostępu do elementów członkowskich, zamiast nazwy typu dla typów, które mają słowa kluczowego reprezentujące je.  
Jeśli ta reguła jest równa **false**, preferowane jest nazwa typu dla wyrażeń dostępu do elementów członkowskich, zamiast słowo kluczowe języka.  

Przykłady kodu:  

```csharp
// dotnet_style_predefined_type_for_member_access = true
var local = int.MaxValue;

// dotnet_style_predefined_type_for_member_access = false
var local = Int32.MaxValue;
```
```vb
' dotnet_style_predefined_type_for_member_access = true
Dim local = Integer.MaxValue

' dotnet_style_predefined_type_for_member_access = false
Dim local = Int32.MaxValue
```  

W pliku .editorconfig te reguły może wyglądać następująco:  

```
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

#### <a name="expression_level">Wyrażenie poziom preferencji</a>  
Reguły stylu w tej sekcji dotyczą wyrażenia poziom preferencji, łącznie z użyciem inicjatory obiektów, inicjatory kolekcji nazw jawne spójnej kolekcji, null łączącego wyrażenia i operatory trzyargumentowe i operatora warunkowego wartości null.  

W poniższej tabeli przedstawiono nazwy reguł, identyfikatory reguły właściwe języki programowania, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:  

| Nazwa reguły | Identyfikator reguły | Właściwe języki | Domyślny program Visual Studio | Obsługiwana wersja |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| dotnet_style_object_initializer | IDE0017 | C# i Visual Basic | PRAWDA: sugestii | Visual Studio 2017 RTW |
| dotnet_style_collection_initializer | IDE0028 | C# i Visual Basic | PRAWDA: sugestii | Visual Studio 2017 RTW |
| dotnet_style_explicit_tuple_names | IDE0033 | C# 7.0 + i Visual Basic 15 + | PRAWDA: sugestii | Visual Studio 2017 RTW |
| dotnet_style_coalesce_expression | IDE0029 | C# i Visual Basic | PRAWDA: sugestii | Visual Studio 2017 RTW |
| dotnet_style_null_propagation | IDE0031 | C# w wersji 6.0 + i Visual Basic 14 + | PRAWDA: sugestii | Visual Studio 2017 RTW | 

**DotNet\_styl\_object_initializer**  
Jeśli ta reguła jest równa **true**, preferowane obiektów, aby można było zainicjować przy użyciu inicjatory obiektów, kiedy to możliwe.  
Jeśli ta reguła jest równa **false**, wybrać obiekty do *nie* można zainicjować przy użyciu inicjatory obiektów.  

Przykłady kodu:  

```csharp
// dotnet_style_object_initializer = true
var c = new Customer() { Age = 21 };

// dotnet_style_object_initializer = false
var c = new Customer();
c.Age = 21;
```
```vb
' dotnet_style_object_initializer = true
Dim c = New Customer() With {.Age = 21}

' dotnet_style_object_initializer = false
Dim c = New Customer()
c.Age = 21
```

**DotNet\_styl\_collection_initializer**  
Jeśli ta reguła jest równa **true**, wybrać kolekcje, aby można było zainicjować przy użyciu inicjatory kolekcji, jeśli to możliwe.  
Jeśli ta reguła jest równa **false**, preferowane kolekcje w celu *nie* można zainicjować przy użyciu inicjatory kolekcji.

Przykłady kodu:

```csharp
// dotnet_style_collection_initializer = true
var list = new List<int> { 1, 2, 3 };

// dotnet_style_collection_initializer = false
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);
```
```vb
' dotnet_style_collection_initializer = true
Dim list = New List(Of Integer) From {1, 2, 3}

' dotnet_style_collection_initializer = false
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)
```  

**DotNet\_styl\_jawne\_tuple_names**  
Jeśli ta reguła jest równa **true**, wolą krotki nazwy właściwości ItemX.  
Jeśli ta reguła jest równa **false**, preferowane właściwości ItemX nazwy spójnej kolekcji.  

Przykłady kodu:  

```csharp
// dotnet_style_explicit_tuple_names = true
(string name, int age) customer = GetCustomer();
var name = customer.name;

// dotnet_style_explicit_tuple_names = false
(string name, int age) customer = GetCustomer();
var name = customer.Item1;
```
```vb
 ' dotnet_style_explicit_tuple_names = true
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name

' dotnet_style_explicit_tuple_names = false
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1
```

**DotNet\_styl\_coalesce_expression**  
Jeśli ta reguła jest równa **true**, preferowane null łączącego wyrażenia trójargumentowy sprawdzania.  
Jeśli ta reguła jest równa **false**, preferowane trójargumentowy sprawdzanie do wyrażeń łączącego wartości null.

Przykłady kodu:  

```csharp
// dotnet_style_coalesce_expression = true
var v = x ?? y;

// dotnet_style_coalesce_expression = false
var v = x != null ? x : y; // or
var v = x == null ? y : x;
```
```vb
' dotnet_style_coalesce_expression = true
Dim v = If(x, y)

' dotnet_style_coalesce_expression = false
Dim v = If(x Is Nothing, y, x) ' or
Dim v = If(x IsNot Nothing, x, y)
```

**DotNet\_styl\_null_propagation**  
Jeśli ta reguła jest równa **true**, wolą używać operatora warunkowego wartości null, jeśli to możliwe.  
Jeśli ta reguła jest równa **false**, wolą używać trójargumentowy sprawdzanie wartości null, jeśli jest to możliwe.  

Przykłady kodu:  

```csharp
// dotnet_style_null_propagation = true
var v = o?.ToString();

// dotnet_style_null_propagation = false
var v = o == null ? null : o.ToString(); // or
var v = o != null ? o.String() : null;
```
```vb
' dotnet_style_null_propagation = true
Dim v = o?.ToString()

' dotnet_style_null_propagation = false
Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or
Dim v = If(o IsNot Nothing, o.ToString(), Nothing)
```  

W pliku .editorconfig te reguły może wyglądać następująco:  

```
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
``` 

### <a name="c-code-style-settings"></a>Ustawienia stylu kodu C#  
Reguły stylu w tej sekcji dotyczą C# tylko.  

#### <a name="var">Typy jawne i niejawne</a>
Reguły stylu w tej sekcji (reguły IDE0007 identyfikatorów i IDE0008) dotyczą stosowania [var](/dotnet/csharp/language-reference/keywords/var) — słowo kluczowe w porównaniu z typem jawnym w deklaracji zmiennej. Typy wbudowane, gdy typem jest widoczna i innych miejscach, można osobno zastosowana ta reguła.  

W poniższej tabeli przedstawiono nazwy reguł, właściwe języki programowania, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:  

| Nazwa reguły | Właściwe języki | Domyślny program Visual Studio | Obsługiwana wersja |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_style_var_for_built_in_types | C# | wartość true: Brak | Visual Studio 2017 RTW |
| csharp_style_var_when_type_is_apparent | C# | wartość true: Brak | Visual Studio 2017 RTW |
| csharp_style_var_elsewhere | C# | wartość true: Brak | Visual Studio 2017 RTW |

**CSharp\_styl\_var\_dla\_wbudowane\_in_types**  
Jeśli ta reguła jest równa **true**, preferowane `var` służy do deklarowania zmiennych z typami wbudowanych systemu, takich jak `int`.  
Jeśli ta reguła jest równa **false**, Preferuj jawnego typu przed `var` do deklarowania zmiennych z typami wbudowany system takich jak `int`.

Przykłady kodu:  

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

**CSharp\_styl\_var\_podczas\_typu\_is_apparent**  
Jeśli ta reguła jest równa **true**, preferowane `var` kiedy typ jest wymienione po prawej stronie wyrażenia deklaracji.  
Jeśli ta reguła jest równa **false**, Preferuj jawnego typu przed `var` kiedy typ jest wymienione po prawej stronie wyrażenia deklaracji.  

Przykłady kodu:  

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

**CSharp\_styl\_var_elsewhere**  
Jeśli ta reguła jest równa **true**, preferowane `var` za pośrednictwem jawnego typu we wszystkich przypadkach, chyba że zastąpione przez inną regułę stylu kodu.  
Jeśli ta reguła jest równa **false**, Preferuj jawnego typu przed `var` we wszystkich przypadkach, chyba że zastąpione przez inną regułę stylu kodu.  

Przykłady kodu:  

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

Przykładowy plik .editorconfig:  

```
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
``` 

#### <a name="expression_bodied_members">Zabudowanych wyrażenia elementów członkowskich</a>
Reguły stylu w tej sekcji dotyczą stosowania [zabudowanych wyrażenia elementów członkowskich](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) po logiki składa się z jednego wyrażenia. Ta zasada może odnosić się do metody, konstruktorów, operatory, właściwości, indeksatorów i metody dostępu.  

W poniższej tabeli przedstawiono nazwy reguł, identyfikatory reguły, wersje odpowiedni język, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:  

| Nazwa reguły | Identyfikator reguły | Właściwe języki | Domyślny program Visual Studio | Obsługiwana wersja |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_style_expression_bodied_methods | IDE0022 | C# W WERSJI 6.0 + | false: Brak | Visual Studio 2017 RTW |
| csharp_style_expression_bodied_constructors | IDE0021 | C# 7.0 + | false: Brak | Visual Studio 2017 RTW |
| csharp_style_expression_bodied_operators | IDE0023 i IDE0024 | C# 7.0 + | false: Brak | Visual Studio 2017 RTW |
| csharp_style_expression_bodied_properties | IDE0025 | C# 7.0 + | wartość true: Brak | Visual Studio 2017 RTW |
| csharp_style_expression_bodied_indexers | IDE0026 | C# 7.0 + | wartość true: Brak | Visual Studio 2017 RTW |
| csharp_style_expression_bodied_accessors | IDE0027 | C# 7.0 + | wartość true: Brak | Visual Studio 2017 RTW |  

**CSharp\_styl\_wyrażenie\_bodied_methods**  
Jeśli ta reguła jest równa **true**, preferowane zabudowanych wyrażenia elementów członkowskich dla metod.  
Jeśli ta reguła jest równa **false**, nie preferowane zabudowanych wyrażenia elementów członkowskich dla metod.  

Przykłady kodu:  

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```  

**CSharp\_styl\_wyrażenie\_bodied_constructors**  
Jeśli ta reguła jest równa **true**, preferowane zabudowanych wyrażenia elementów członkowskich dla konstruktorów.  
Jeśli ta reguła jest równa **false**, nie preferowane zabudowanych wyrażenia elementów członkowskich dla konstruktorów.  

Przykłady kodu:  

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```  

**CSharp\_styl\_wyrażenie\_bodied_operators**  
Jeśli ta reguła jest równa **true**, preferowane zabudowanych wyrażenia elementów członkowskich dla operatorów.  
Jeśli ta reguła jest równa **false**, nie preferowane zabudowanych wyrażenia elementów członkowskich dla operatorów.  

Przykłady kodu:  

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```  

**CSharp\_styl\_wyrażenie\_bodied_properties**  
Jeśli ta reguła jest równa **true**, preferowane właściwości zabudowanych wyrażenia elementów członkowskich.  
Jeśli ta reguła jest równa **false**, nie preferowane zabudowanych wyrażenia elementów członkowskich dla właściwości.  

Przykłady kodu:  

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```  

**CSharp\_styl\_wyrażenie\_bodied_indexers**  
Jeśli ta reguła jest równa **true**, preferowane zabudowanych wyrażenia elementów członkowskich dla indeksatorów.  
Jeśli ta reguła jest równa **false**, nie preferowane zabudowanych wyrażenia elementów członkowskich dla indeksatorów.  

Przykłady kodu:  

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _value[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```  

**CSharp\_styl\_wyrażenie\_bodied_accessors**  
Jeśli ta reguła jest równa **true**, preferowane zabudowanych wyrażenia elementów członkowskich dla metod dostępu.  
Jeśli ta reguła jest równa **false**, nie preferowane zabudowanych wyrażenia elementów członkowskich dla metod dostępu.  

Przykłady kodu:  

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```  

Przykładowy plik .editorconfig:  

```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
csharp_style_expression_bodied_constructors = false:none
csharp_style_expression_bodied_operators = false:none
csharp_style_expression_bodied_properties = true:none
csharp_style_expression_bodied_indexers = false:none
csharp_style_expression_bodied_accessors = false:none
```  

#### <a name="pattern_matching">Dopasowanie wzorca</a>
Reguły stylu w tej sekcji dotyczą stosowania [dopasowanie wzorca](/dotnet/csharp/pattern-matching) w języku C#.  

W poniższej tabeli przedstawiono nazwy reguł, identyfikatory reguły, wersje odpowiedni język, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:  

| Nazwa reguły | Identyfikator reguły | Właściwe języki | Domyślny program Visual Studio | Obsługiwana wersja |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_style_pattern_matching_over_is_with_cast_check | IDE0020 | C# 7.0 + | PRAWDA: sugestii | Visual Studio 2017 RTW |
| csharp_style_pattern_matching_over_as_with_null_check | IDE0019 | C# 7.0 + | PRAWDA: sugestii | Visual Studio 2017 RTW |

**CSharp\_styl\_wzorzec\_pasującego\_za pośrednictwem\_jest\_z\_cast_check**  
Jeśli ta reguła jest równa **true**, preferowane, zamiast dopasowywania do wzorca `is` wyrażenia z typu rzutowania.  
Jeśli ta reguła jest równa **false**, preferowane `is` wyrażenia z typu rzutowania zamiast dopasowywania do wzorca.  

Przykłady kodu:  

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

**CSharp\_styl\_wzorzec\_pasującego\_za pośrednictwem\_jako\_z\_null_check**  
Jeśli ta reguła jest równa **true**, preferowane, zamiast dopasowywania do wzorca `as` wyrażenia o wartości null sprawdza, czy jest coś określonego typu.  
Jeśli ta reguła jest równa **false**, preferowane `as` wyrażenia ze sprawdzenia wartości null zamiast wzorzec dopasowany do ustalenia, czy jest coś określonego typu.  

Przykłady kodu:  

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

Przykładowy plik .editorconfig:  

```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="inlined_variable_declarations">Wbudowane deklaracje zmiennej</a>
Ten styl określa, czy reguła dotyczy `out` zmienne są deklarowane jako wbudowany, czy nie. Uruchamianie w języku C# 7, można [zadeklarować zmiennej poza na liście argumentów w wywołaniu metody](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument), a nie w deklaracji zmiennej oddzielne.  

W poniższej tabeli przedstawiono nazwę reguły, identyfikator reguły, wersje odpowiedni język, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:  

| Nazwa reguły | Identyfikator reguły | Właściwe języki | Domyślny program Visual Studio | Obsługiwana wersja |
| --------- | -------- | -------------------- | ----------------------| ----------------  |
| csharp_style_inlined_variable_declaration | IDE0018 | C# 7.0 + | PRAWDA: sugestii | Visual Studio 2017 RTW |

**CSharp\_styl\_wbudowanego\_variable_declaration**  
Jeśli ta reguła jest równa **true**, preferowane `out` zmienne, które mają być zadeklarowana śródwierszowo na liście argumentów w wywołaniu metody, jeśli to możliwe.  
Jeśli ta reguła jest równa **false**, preferowane `out` zmienne, które mają być zadeklarowana przed wywołaniem metody.  

Przykłady kodu:  

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = fale
int i;
if (int.TryParse(value, out i) {...}
```

Przykładowy plik .editorconfig:  

```
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

#### <a name="expression_level_csharp">Wyrażenie poziom preferencji</a>
Dotyczy to reguły stylu przy użyciu [ `default` dosłownie wyrażenia wartości domyślnej](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) gdy kompilator może wnioskować o typie wyrażenia.  

W poniższej tabeli przedstawiono nazwę reguły, identyfikator reguły, wersje odpowiedni język, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:  

| Nazwa reguły | Identyfikator reguły | Właściwe języki | Domyślny program Visual Studio | Obsługiwana wersja |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_prefer_simple_default_expression | IDE0034 | C# 7.1 + | PRAWDA: sugestii | Visual Studio 2017 v. 15.3 |

**CSharp\_preferowane\_proste\_default_expression**  
Jeśli ta reguła jest równa **true**, preferowane `default` za pośrednictwem `default(T)`.  
Jeśli ta reguła jest równa **false**, preferowane `default(T)` za pośrednictwem `default`.  

Przykłady kodu:  

```csharp 
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

Przykładowy plik .editorconfig:  

```
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
``` 

#### <a name="null_checking">"Null" Sprawdzanie preferencji</a>
Te reguły dotyczą stylu składni wokół `null` sprawdzania, w tym o korzystaniu z `throw` wyrażenia lub `throw` instrukcje oraz czy należy sprawdzić wartość null lub użyj warunkowego operatora łączącego (`?.`) podczas wywoływania [wyrażenia lambda](/dotnet/csharp/lambda-expressions).  

W poniższej tabeli przedstawiono nazwy reguł, identyfikatory reguły, wersje odpowiedni język, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:  

| Nazwa reguły | Identyfikator reguły | Właściwe języki | Domyślny program Visual Studio | Obsługiwana wersja |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_style_throw_expression | IDE0016 | C# 7.0 + | PRAWDA: sugestii | Visual Studio 2017 RTW |
| csharp_style_conditional_delegate_call | IDE0041 | C# W WERSJI 6.0 + | PRAWDA: sugestii | Visual Studio 2017 RTW |

**CSharp\_styl\_throw_expression**  
Jeśli ta reguła jest równa **true**, wolą używać `throw` wyrażenia zamiast `throw` instrukcje.  
Jeśli ta reguła jest równa **false**, wolą używać `throw` instrukcje zamiast `throw` wyrażenia.  

Przykłady kodu:  

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

**CSharp\_styl\_warunkowego\_delegate_call**   
Jeśli ta reguła jest równa **true**, wolą używać operatora łączącego warunkowego (`?.`) podczas wywoływania wyrażenia lambda, zamiast wykonywania o wartości null Sprawdź.  
Jeśli ta reguła jest równa **false**, preferowane sprawdzania wartości null przed wywołaniem wyrażenia lambda, zamiast operatora łączącego warunkowego (`?.`).  

Przykłady kodu:  

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

Przykładowy plik .editorconfig:  

```
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestions:
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="code_block">Preferencje blok kodu</a>
Ta zasada styl dotyczy użycia nawiasów klamrowych `{ }` otaczającego bloków kodu.  

W poniższej tabeli przedstawiono nazwę reguły, identyfikator reguły, wersje odpowiedni język, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:  

| Nazwa reguły | Identyfikator reguły | Właściwe języki | Domyślny program Visual Studio | Obsługiwana wersja |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_prefer_braces | IDE0011 | C# | wartość true: Brak | Visual Studio 2017 v. 15.3 |

**CSharp\_preferowane\_nawiasów klamrowych**   
Jeśli ta reguła jest równa **true**, preferowane nawiasy klamrowe, nawet w przypadku jeden wiersz kodu.  
Jeśli ta reguła jest równa **false**, preferowane nie nawiasów klamrowych, jeśli dozwolone.  

Przykłady kodu:  

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

Przykładowy plik .editorconfig:  

```
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:none
```

## <a name="formatting-conventions"></a>Konwencji formatowania
Większości reguł dla Konwencji formatowania mają następujący format:  

`rule_name = false|true`  

Określ albo **true** (preferowane ten styl) lub **false** (nie preferowane ten styl). Nie określaj ważności. Kilka reguł, a nie wartość PRAWDA lub FAŁSZ można określić inne wartości, które opisują, gdzie i kiedy należy zastosować regułę.  

Poniższa lista zawiera reguły Konwencji formatowania dostępne w programie Visual Studio:  

- Ustawienia formatowania platformy .NET
    - [Organizacja deklaracji Using](#usings)
        - dotnet_sort_system_directives_first
- C# ustawienia
    - [Opcje nowego wiersza](#newline)
        - csharp_new_line_before_open_brace
        - csharp_new_line_before_else
        - csharp_new_line_before_catch
        - csharp_new_line_before_finally
        - csharp_new_line_before_members_in_object_initializers
        - csharp_new_line_before_members_in_anonymous_types
        - csharp_new_line_between_query_expression_clauses
    - [Opcje wcięć](#indent)
        - csharp_indent_case_contents
        - csharp_indent_switch_labels
        - csharp_indent_labels
    - [Opcje odstępów](#spacing)
        - csharp_space_after_cast
        - csharp_space_after_keywords_in_control_flow_statements
        - csharp_space_between_method_declaration_parameter_list_parentheses
        - csharp_space_between_method_call_parameter_list_parentheses
        - csharp_space_between_parentheses
    - [Opcje zawijania](#wrapping)
        - csharp_preserve_single_line_statements
        - csharp_preserve_single_line_blocks

### <a name="net-formatting-settings"></a>Ustawienia formatowania platformy .NET
Reguły formatowania w tej sekcji dotyczą C# i Visual Basic.  

#### <a name="usings">Organizacja deklaracji Using</a>
Ta reguła formatowania dotyczy umieszczania System.* przy użyciu dyrektyw względem innych przy użyciu dyrektyw.  

W poniższej tabeli przedstawiono nazwy reguły właściwe języki, wartości domyślnej i pierwszej obsługiwanej wersji programu Visual Studio:  

| Nazwa reguły | Właściwe języki | Domyślny program Visual Studio | Obsługiwana wersja |
| ----------- | -------------------- | ----------------------| ----------------  |
| dotnet_sort_system_directives_first |  C# i Visual Basic | true | Visual Studio 2017 v. 15.3  |

**DotNet\_sortowania\_systemu\_directives_first**  
Jeśli ta reguła jest równa **true**posortować alfabetycznie przy użyciu dyrektyw System.* i umieść je przed innymi deklaracje Using.  
Jeśli ta reguła jest równa **false**, nie umieszczaj System.* przy użyciu dyrektyw przed innymi przy użyciu dyrektyw.  

Przykłady kodu:  

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

Przykładowy plik .editorconfig:  

```
# .NET formatting settings:
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
``` 

### <a name="csharp_formatting">Ustawienia formatowania C#</a>  
Reguły formatowania w tej sekcji dotyczą tylko kod w języku C#.  

#### <a name="newline">Opcje nowego wiersza</a>  
Te reguły formatowania dotyczy stosowania nowych wierszy w celu formatowania kodu.  

W poniższej tabeli przedstawiono "nowy wiersz" nazwy reguł właściwe języki, wartości domyślne, a najpierw obsługiwanej wersji programu Visual Studio:  

| Nazwa reguły | Właściwe języki | Domyślny program Visual Studio | Obsługiwana wersja |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_new_line_before_open_brace |  C# | wszystkie | Visual Studio 2017 v. 15.3  |
| csharp_new_line_before_else |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_new_line_before_catch |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_new_line_before_finally |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_new_line_before_members_in_object_initializers |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_new_line_before_members_in_anonymous_types |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_new_line_between_query_expression_clauses |  C# | true | Visual Studio 2017 v. 15.3  |

**CSharp\_nowe\_wiersza\_przed\_open_brace**  
Ta zasada dotyczy czy otwierający nawias klamrowy `{` powinny być umieszczane na tym samym wierszu co poprzedni kod lub w nowym wierszu. Dla tej reguły, nie należy określać **true** lub **false**. Zamiast tego określ **wszystkie**, **Brak**, lub co najmniej jeden kod elementów takich jak **metody** lub **właściwości**, aby zdefiniować, kiedy ta reguła powinna być stosowane. W poniższej tabeli przedstawiono to pełna lista dopuszczalne wartości:  

| Wartość | Opis 
| ------------- |:-------------|
| metody dostępu, anonymous_methods, anonymous_types, control_blocks, zdarzenia, indeksatorów, wyrażenia lambda, local_functions, metody, object_collection, właściwości, typów.<br>(Dla wielu typów, oddziel ','). | Wymagaj nawiasy klamrowe w nowym wierszu dla określonego kodu elementy (znanej także jako styl "Allman") |
| wszystkie | Wymagaj nawiasy klamrowe w nowym wierszu dla wszystkie wyrażenia (styl "Allman") |
| brak | Wymagaj nawiasy klamrowe w tej samej linii wszystkie wyrażenia ("K & R") |

Przykłady kodu:  

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod() 
{
    if (...) 
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

**CSharp\_nowe\_wiersza\_before_else**  
Jeśli ta reguła jest równa **true**, umieść `else` instrukcje w nowym wierszu.  
Jeśli ta reguła jest równa **false**, umieść `else` instrukcje w tym samym wierszu.  

Przykłady kodu:  

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

**CSharp\_nowe\_wiersza\_before_catch**    
Jeśli ta reguła jest równa **true**, umieść `catch` instrukcje w nowym wierszu.  
Jeśli ta reguła jest równa **false**, umieść `catch` instrukcje w tym samym wierszu.  

Przykłady kodu:  

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

**CSharp\_nowe\_wiersza\_before_finally**      
Jeśli ta reguła jest równa **true**, wymagają `finally` instrukcje do nowego wiersza po klamrowym nawiasie zamykającym.  
Jeśli ta reguła jest równa **false**, wymagają `finally` instrukcje w tym samym wierszu co zamykający nawias klamrowy.  

Przykłady kodu:  

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

**CSharp\_nowe\_wiersza\_przed\_członków\_w\_object_initializers**       
Jeśli ta reguła jest równa **true**, wymagają członkami intializers obiektu w osobnych wierszach.  
Jeśli ta reguła jest równa **false**, wymagają członkami inicjatory obiektów w tym samym wierszu.  

Przykłady kodu:  

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

**CSharp\_nowe\_wiersza\_przed\_członków\_w\_anonymous_types**       
Jeśli ta reguła jest równa **true**, wymagają elementy członkowskie typów anonimowych w osobnych wierszach.  
Jeśli ta reguła jest równa **false**, wymagają elementów członkowskich typu anonimowego na tym samym wierszu.  

Przykłady kodu:  

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

**csharp_new_line_between_query_expression_clauses**       
Jeśli ta reguła jest równa **true**, wymagają elementy klauzule wyrażenia zapytania w osobnych wierszach.  
Jeśli ta reguła jest równa **false**, wymagają elementy klauzule wyrażenia zapytania w tym samym wierszu.  

Przykłady kodu:  

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

Przykładowy plik .editorconfig:  

```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
``` 

#### <a name="indent">Opcje wcięć</a>  
Te reguły formatowania dotyczy stosowania wcięcia w celu formatowania kodu.  

W poniższej tabeli przedstawiono nazwy reguł, właściwe języki, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:  

| Nazwa reguły | Właściwe języki | Domyślny program Visual Studio | Obsługiwana wersja |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_indent_case_contents |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_indent_switch_labels |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_indent_labels |  C# | no_change | Visual Studio 2017 v. 15.3  |

**CSharp\_wcięcie\_case_contents**  
Jeśli ta reguła jest równa **true**, wcięcie `switch` przypadek zawartość.  
Jeśli ta reguła jest równa **false**, nie wcięcie `switch` przypadek zawartość.  

Przykłady kodu:  

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**CSharp\_wcięcie\_switch_labels**  
Jeśli ta reguła jest równa **true**, wcięcie `switch` etykiety.  
Jeśli ta reguła jest równa **false**, nie wcięcie `switch` etykiety.  

Przykłady kodu:  

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**CSharp\_indent_labels**  
Ta zasada nie akceptuje **true** lub **false** wartości; zamiast tego przyjmuje wartość z następującej tabeli:  

| Wartość | Opis |
| ----- |:----------- |
| flush_left | Etykiety są umieszczane w kolumnie z lewej strony |
| one_less_than_current | Etykiety są umieszczane w jednej mniej wcięcie dla bieżącego kontekstu |
| no_change | Etykiety są umieszczane na tym samym wcięcie jako bieżący kontekst |

Przykłady kodu:  

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...) 
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...) 
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...) 
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

Przykładowy plik .editorconfig:  

```
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
``` 

#### <a name="spacing">Opcje odstępów</a>  
Te reguły formatowania dotyczą znaków miejsca do formatowania kodu.  

W poniższej tabeli przedstawiono nazwy reguł, właściwe języki, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:  

| Nazwa reguły | Właściwe języki | Domyślny program Visual Studio | Obsługiwana wersja |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_space_after_cast |  C# | false | Visual Studio 2017 v. 15.3  |
| csharp_space_after_keywords_in_control_flow_statements |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_space_between_method_declaration_parameter_list_parentheses |  C# | false | Visual Studio 2017 v. 15.3  |
| csharp_space_between_method_call_parameter_list_parentheses |  C# | false | Visual Studio 2017 v. 15.3  |
| csharp_space_between_parentheses |  C# | false | Visual Studio 2017 v. 15.3  |

**CSharp\_miejsca\_after_cast**  
Jeśli ta reguła jest równa **true**, wymagają odstęp między rzutowanie i wartość.  
Jeśli ta reguła jest równa **false**, wymagają _nie_ odstęp między rzutowanie i wartość.  

Przykłady kodu:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

**csharp_space_after_keywords_in_control_flow_statements**  
Jeśli ta reguła jest równa **true**, takich jak wymagają spację po słów kluczowych w instrukcji przepływu sterowania `for` pętli.  
Jeśli ta reguła jest równa **false**, wymagają _nie_ miejsce po słów kluczowych w instrukcji przepływu sterowania, takich jak `for` pętli.  

Przykłady kodu:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

**csharp_space_between_method_declaration_parameter_list_parentheses**  
Jeśli ta reguła jest równa **true**, umieść znak spacji po nawiasie otwierającym, a także przed nawiasem zamykającym w liście parametrów deklaracji metody.  
Jeśli ta reguła jest równa **false**, nie umieszczaj znaków spacji po nawiasie otwierającym, a także przed nawiasem zamykającym w liście parametrów deklaracji metody.  

Przykłady kodu:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

**csharp_space_between_method_call_parameter_list_parentheses**  
Jeśli ta reguła jest równa **true**, umieść znak spacji po nawiasie otwierającym, a także przed nawiasem zamykającym wywołania metody.  
Jeśli ta reguła jest równa **false**, nie umieszczaj znaków spacji po nawiasie otwierającym, a także przed nawiasem zamykającym wywołania metody.  

Przykłady kodu:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

**csharp_space_between_parentheses**  
Ta zasada nie akceptuje **true** lub **false** wartości; zamiast tego przyjmuje wartość z następującej tabeli:  

| Wartość | Opis |
| ----- |:------------|
| control_flow_statements | Umieść odstęp między nawiasy instrukcjach przepływu sterowania |
| wyrażenia | Umieść odstęp między nawiasy wyrażeń |
| type_casts | Umieść odstęp między nawiasy w rzutowania typów |

Przykłady kodu:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for( int i;i<x;i++ ) { ... }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3);

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

Przykładowy plik .editorconfig:  

```
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_parentheses = control_flow_statements, type_casts
``` 

#### <a name="wrapping">Opcje zawijania</a>
Te reguły formatowania dotyczy stosowania pojedynczych wierszy w porównaniu z osobnych wierszach instrukcje i bloków kodu.  

W poniższej tabeli przedstawiono nazwy reguł, właściwe języki, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:  

| Nazwa reguły | Właściwe języki | Domyślny program Visual Studio | Obsługiwana wersja |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_preserve_single_line_statements |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_preserve_single_line_blocks |  C# | true | Visual Studio 2017 v. 15.3  |

**csharp_preserve_single_line_statements**   
Jeśli ta reguła jest równa **true**, pozostaw instrukcje i element członkowski deklaracje w tym samym wierszu.  
Jeśli ta reguła jest równa **false**, pozostaw instrukcje i element członkowski deklaracje w różnych wierszy.  

Przykłady kodu:  

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0; 
string name = "John";
```

**csharp_preserve_single_line_blocks**  
Jeśli ta reguła jest równa **true**, pozostaw blok kodu w pojedynczym wierszu.  
Jeśli ta reguła jest równa **false**, pozostaw blok kodu w osobnych wierszach.  

Przykłady kodu:  

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{ 
    get; set;
}
```

Przykładowy plik .editorconfig:  

```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

## <a name="naming-conventions"></a>Konwencje nazewnictwa  
Konwencje nazewnictwa dotyczą nazw elementów kodu, takich jak klasy, właściwości i metody. Na przykład można określić, że metod asynchronicznych musi kończyć się "Async". Konwencje nazewnictwa powinna być wyświetlana z określonych najbardziej do najmniej specyficznych. Pierwsza reguła napotkano, który można zastosować jest tylko regułę, która została zastosowana.  

Dla każdej nazwy reguły Konwencji identyfikowane przez **namingRuleTitle**, należy określić **symbole** dotyczy, nazewnictwa **styl**, a **ważność** :  
  
`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`  
`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`  
`dotnet_naming_rule.<namingRuleTitle>.severity = none|suggestion|warning|error`  

### <a name="symbols"></a>Symbole
Identyfikator grupy symboli, aby zastosować regułę nazewnictwa z tą właściwością: `dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`. Określ rodzaj symbole, które modyfikatorów i poziomów ułatwień dostępu, które są uwzględniane w grupie z następującymi właściwościami:  

| Właściwość | Możliwe wartości |
| ------------- |:-------------:|
| DotNet\_nazewnictwa\_symboli.\< symbolTitle\>.applicable\_typów | *, klasy, struktury, interfejsu, enum, właściwości, — metoda, pola, zdarzenia, przestrzeń nazw, delegata, type_parameter |
| DotNet\_nazewnictwa\_symboli.\< symbolTitle\>.applicable_accessibilities | *, publiczne, wewnętrzne (C#), friend (Visual Basic), prywatnych, chronionych, chronionych\_chronionych wewnętrznych (C#),\_friend (Visual Basic) |
| DotNet\_nazewnictwa\_symboli.\< symbolTitle\>.required\_modyfikatorów | abstract (C#), must_inherit (Visual Basic), asynchroniczne, stała, tylko do odczytu, statyczne (C#) udostępnionych (Visual Basic) |  

### <a name="style"></a>Styl
Zidentyfikuj styl nazewnictwa, aby zastosować do grupy symboli z tą właściwością: `dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`.  

Określ styl nazewnictwa przy użyciu co najmniej jeden z następujących właściwości:  

|  Właściwość | Możliwe wartości |
| ------------- |:-------------:|
| dotnet_naming_style. \<styleTitle\>.required_prefix | Wymagane znaki, które musi znajdować się na początku identyfikator. |  
| dotnet_naming_style. \<styleTitle\>.required_suffix | Wymagane znaki, które muszą występować na końcu identyfikator. |  
| dotnet_naming_style. \<styleTitle\>.word_separator | Wymagane znak między wyrazami w identyfikatorze. | 
| dotnet_naming_style. \<styleTitle\>.capitalization | pascal_case, camel_case, first_word_upper, all_upper, all_lower |

> [!NOTE]
> Należy określić styl wielkość liter w ramach swojego nazewnictwa stylu, w przeciwnym razie własnego stylu nazewnictwa zostaną zignorowane.  

#### <a name="severity"></a>Ważność
Zidentyfikuj poziom ważności dla reguły nazewnictwa z tą właściwością: `dotnet_naming_rule.<namingRuleTitle>.severity`.  

W poniższej tabeli przedstawiono ważność opcje wartości:  

Ważność | Efekt
------------ | -------------
Brak lub dyskretnej | Gdy nie trwa występuje ten styl, nie pokazuj żadnych użytkownikowi; Jednak funkcje generowania kodu wygenerować nowy kod w tym stylem.  
Sugestia | Gdy nie trwa występuje ten styl, Pokaż go do użytkownika jako sugestia (podstawowy kropki na pierwszych dwóch znaków). Go nie ma znaczenia w czasie kompilacji.  
ostrzeżenie | Gdy nie trwa występuje ten styl, Pokaż ostrzeżenie kompilatora.  
Błąd | Gdy nie trwa występuje ten styl, Pokaż błąd kompilatora.   

### <a name="example-editorconfig-file-with-naming-conventions"></a>Przykładowy plik .editorconfig z konwencje nazewnictwa
```
# Dotnet Naming Conventions
[*.{cs,vb}] 
dotnet_naming_rule.async_methods_end_in_async.symbols  = any_async_methods
dotnet_naming_rule.async_methods_end_in_async.style    = end_in_async
dotnet_naming_rule.async_methods_end_in_async.severity = suggestion

dotnet_naming_symbols.any_async_methods.applicable_kinds           = method
dotnet_naming_symbols.any_async_methods.applicable_accessibilities = *
dotnet_naming_symbols.any_async_methods.required_modifiers         = async

dotnet_naming_style.end_in_async.required_suffix = Async
dotnet_naming_style.end_in_async.capitalization  = pascal_case
``` 

## <a name="see-also"></a>Zobacz także
[Szybkie akcje](../ide/quick-actions.md)  
[Tworzenie niestandardowego edytora przenośne opcji](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options)  
[Plik .editorconfig platformę .NET kompilatora](https://github.com/dotnet/roslyn/blob/master/.editorconfig)  
