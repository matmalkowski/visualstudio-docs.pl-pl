---
title: Kodowanie ustawienia Konwencji EditorConfig dla programu Visual Studio .NET | Dokumentacja firmy Microsoft
ms.date: 02/28/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- coding conventions [EditorConfig]
- EditorConfig coding conventions
- language conventions [EditorConfig]
- formatting conventions [EditorConfig]
author: kuhlenh
ms.author: kaseyu
manager: douge
ms.technology: vs-ide-general
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b313271e29bba660af1aa48654bfdfefb81e39f1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>Ustawienia EditorConfig Konwencji kodowania platformy .NET

W programie Visual Studio 2017 r, można zdefiniować i obsługa styl spójności kodu w Twojej ścieżki bazowej kodu z użyciem [EditorConfig](../ide/create-portable-custom-editor-options.md) pliku. EditorConfig zawiera kilka podstawowych właściwości formatowania, takich jak `indent_style` i `indent_size`. W programie Visual Studio .NET kodowania konwencje ustawienia można również skonfigurować przy użyciu pliku EditorConfig. Pliki EditorConfig pozwala włączyć lub wyłączyć poszczególne .NET konwencje kodowania i konfigurowania stopnia, do którego ma Konwencję wymuszane za pośrednictwem poziom ważności. Aby dowiedzieć się więcej o sposobie używania EditorConfig, aby wymusić spójność baza kodu, przeczytaj [Tworzenie niestandardowego edytora przenośne opcji](../ide/create-portable-custom-editor-options.md). Można również sprawdzić [pliku .editorconfig platformę .NET kompilatora](https://github.com/dotnet/roslyn/blob/master/.editorconfig) jako przykład.

Istnieją trzy obsługiwane .NET kodowania Konwencji kategorie:

- [Konwencje języka](#language-conventions)

   Reguły dotyczące języka C# lub Visual Basic. Na przykład można określić reguły wokół przy użyciu `var` lub typów jawnych podczas definiowania zmiennych i preferowanie zabudowanych wyrażenia elementów członkowskich.

- [Konwencji formatowania](#formatting-conventions)

   Zasady dotyczące układ i struktura kodu w celu ułatwienia odczytu. Na przykład można określić zasady wokół nawiasów klamrowych Allman lub preferowanie spacje w blokach formantu.

- [Konwencje nazewnictwa](../ide/editorconfig-naming-conventions.md)

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
        - dotnet\_style\_qualification\_for_field
        - dotnet\_style\_qualification\_for_property
        - dotnet\_style\_qualification\_for_method
        - dotnet\_style\_qualification\_for_event
    - [Słowa kluczowe języka zamiast framework nazwy typów dla odwołania do typu](#language_keywords)
        - DotNet\_styl\_wstępnie zdefiniowanych\_typu\_dla\_zmiennych lokalnych\_parameters_members
        - DotNet\_styl\_wstępnie zdefiniowanych\_typu\_dla\_member_access
    - [Modyfikator preferencji](#normalize_modifiers)
        - dotnet\_style\_require\_accessibility_modifiers
        - CSharp\_preferowanych\_modifier_order
        - Visual\_podstawowe\_preferowanych\_modifier_order
    - [Wyrażenie poziom preferencji](#expression_level)
        - dotnet\_style\_object_initializer
        - dotnet\_style\_collection_initializer
        - DotNet\_styl\_jawne\_tuple_names
        - DotNet\_preferowane\_wywnioskować\_tuple_names
        - dotnet\_prefer\_inferred\_anonymous\_type\_member_names
    - ["Null" Sprawdzanie preferencji](#null_checking)
        - dotnet\_style\_coalesce_expression
        - dotnet\_style\_null_propagation
- Ustawienia stylu kodu C#
    - [Typy jawne i niejawne](#var)
        - CSharp\_styl\_var\_dla\_wbudowane\_in_types
        - CSharp\_styl\_var\_podczas\_typu\_is_apparent
        - CSharp\_styl\_var_elsewhere
    - [Elementy członkowskie z wyrażeniem w treści](#expression_bodied_members)
        - CSharp\_styl\_wyrażenie\_bodied_methods
        - CSharp\_styl\_wyrażenie\_bodied_constructors
        - CSharp\_styl\_wyrażenie\_bodied_operators
        - CSharp\_styl\_wyrażenie\_bodied_properties
        - CSharp\_styl\_wyrażenie\_bodied_indexers
        - csharp\_style\_expression\_bodied_accessors
    - [Dopasowanie wzorca](#pattern_matching)
        - CSharp\_styl\_wzorzec\_pasującego\_za pośrednictwem\_jest\_z\_cast_check
        - CSharp\_styl\_wzorzec\_pasującego\_za pośrednictwem\_jako\_z\_null_check
    - [Wbudowane deklaracje zmiennej](#inlined_variable_declarations)
        - csharp\_style\_inlined\_variable_declaration
    - [Wyrażenie poziom preferencji](#expression_level_csharp)
        - CSharp\_preferowane\_proste\_default_expression
        - CSharp\_styl\_deconstructed\_variable_declaration
        - CSharp\_styl\_wzorzec\_lokalnego\_za pośrednictwem\_anonymous_function
    - ["Null" Sprawdzanie preferencji](#null_checking_csharp)
        - CSharp\_styl\_throw_expression
        - csharp\_style\_conditional\_delegate_call
    - [Preferencje blok kodu](#code_block)
        - CSharp\_prefer_braces

### <a name="net-code-style-settings"></a>Ustawienia stylu kodu platformy .NET

Reguły stylu w tej sekcji dotyczą zarówno C# i Visual Basic. Aby wyświetlić przykłady kodu w Twoim preferowanym języku programowania, wybierz je z listy rozwijanej **języka** menu w prawym górnym rogu okna przeglądarki.

#### <a name="this_and_me"></a>"This." i "Me." Kwalifikatory

Ta zasada styl (reguły IDE0003 identyfikatorów i IDE0009) mogą być stosowane do pól, właściwości, metody lub zdarzenia. Wartość **true** oznacza preferowane symbolu kod, aby być poprzedzone znakiem `this.` w języku C# lub `Me.` w języku Visual Basic. Wartość **false** oznacza preferowane elementu kodu _nie_ do być poprzedzone znakiem `this.` lub `Me.`.

W poniższej tabeli przedstawiono nazwy reguł, właściwe języki programowania i wartości domyślnych:

| Nazwa zasady | Właściwe języki | Wartość domyślna w usłudze Visual Studio |
| ----------- | -------------------- | ----------------------|
| dotnet_style_qualification_for_field | C# i Visual Basic | false: Brak |
| dotnet_style_qualification_for_property | C# i Visual Basic | false: Brak |
| dotnet_style_qualification_for_method | C# i Visual Basic | false: Brak |
| dotnet_style_qualification_for_event | C# i Visual Basic | false: Brak |

**dotnet\_style\_qualification\_for_field**

- Jeśli ta reguła jest równa **true**, preferowane pola mają być poprzedzone znakiem `this.` w języku C# lub `Me.` w języku Visual Basic.
- Jeśli ta reguła jest równa **false**, preferowane pola _nie_ do być poprzedzone znakiem `this.` lub `Me.`.

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

**dotnet\_style\_qualification\_for_property**

- Jeśli ta reguła jest równa **true**, preferowane właściwości, które mają być poprzedzone znakiem `this.` w języku C# lub `Me.` w języku Visual Basic.
- Jeśli ta reguła jest równa **false**, preferowane właściwości _nie_ do być poprzedzone znakiem `this.` lub `Me.`.

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

**dotnet\_style\_qualification\_for_method**

- Jeśli ta reguła jest równa **true**, metody, aby być poprzedzona słowem wybrać `this.` w języku C# lub `Me.` w języku Visual Basic.
- Jeśli ta reguła jest równa **false**, preferowane metody _nie_ do być poprzedzone znakiem `this.` lub `Me.`.

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

**dotnet\_style\_qualification\_for_event**

- Jeśli ta reguła jest równa **true**, zdarzenia, które mają być poprzedzona słowem wybrać `this.` w języku C# lub `Me.` w języku Visual Basic.
- Jeśli ta reguła jest równa **false**, preferowane zdarzenia _nie_ do być poprzedzone znakiem `this.` lub `Me.`.

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

Te reguły mogą występować w *.editorconfig* plików w następujący sposób:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="language_keywords"></a>Słowa kluczowe języka zamiast framework nazwy typów dla odwołania do typu

Ta zasada styl można zastosować do zmiennych lokalnych, parametrów metod i elementów członkowskich klasy lub oddzielne zasady do typu w wyrażeniach dostępu do elementu członkowskiego. Wartość **true** oznacza preferowane jest słowo kluczowe języka (np. `int` lub `Integer`) zamiast nazwy typu (np. `Int32`) dla typów, które mają słowa kluczowego reprezentujące je. Wartość **false** oznacza preferowane jest nazwa typu zamiast słowo kluczowe języka.

W poniższej tabeli przedstawiono nazwy reguł, identyfikatory reguły właściwe języki programowania i wartości domyślnych:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Domyślne usługi Visual Studio |
| --------- | ------- | -------------------- | ----------------------|
| dotnet_style_predefined_type_for_locals_parameters_members | IDE0012 i IDE0014 | C# i Visual Basic | wartość true: Brak |
| dotnet_style_predefined_type_for_member_access | IDE0013 i IDE0015 | C# i Visual Basic | wartość true: Brak |

**DotNet\_styl\_wstępnie zdefiniowanych\_typu\_dla\_zmiennych lokalnych\_parameters_members**

- Jeśli ta reguła jest równa **true**, preferowane jest słowem kluczowym języka dla zmiennych lokalnych, parametrów metod i klasy elementów członkowskich, zamiast nazwy typu dla typów, które mają słowa kluczowego reprezentujące je.
- Jeśli ta reguła jest równa **false**, preferowane jest nazwa typu dla zmiennych lokalnych, parametrów metod i klasy elementów członkowskich, zamiast słowo kluczowe języka.

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

**dotnet\_style\_predefined\_type\_for\_member_access**

- Jeśli ta reguła jest równa **true**, preferowane jest słowem kluczowym języka dla wyrażeń dostępu do elementów członkowskich, zamiast nazwy typu dla typów, które mają słowa kluczowego reprezentujące je.
- Jeśli ta reguła jest równa **false**, preferowane jest nazwa typu dla wyrażeń dostępu do elementów członkowskich, zamiast słowo kluczowe języka.

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

Te reguły mogą występować w *.editorconfig* plików w następujący sposób:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="normalize_modifiers"></a>Modyfikator preferencji

Reguły stylu w tej sekcji dotyczą modyfikator preferencje, w tym wymagające modyfikatory dostępności i określając odpowiednią modyfikator porządek sortowania.

W poniższej tabeli przedstawiono nazwy reguł, identyfikatory reguły właściwe języki programowania, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Domyślne usługi Visual Studio | Visual Studio 2017 wersji |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| dotnet_style_require_accessibility_modifiers | IDE0040 | C# i Visual Basic | for_non_interface_members:none | 15.5 |
| csharp_preferred_modifier_order | IDE0036 | C# | publiczne, prywatne, chronionych, wewnętrzne, statyczne i zewnętrzne, new, wirtualny, abstrakcyjny, sealed zastąpienie, tylko do odczytu, async niebezpieczne, nietrwałe,: Brak | 15.5 |
| visual_basic_preferred_modifier_order | IDE0036 | Visual Basic | Częściowy, domyślny, Private, chroniony, publiczny, Friend, NotOverridable, możliwym do zastąpienia, MustOverride, przeciążenia, zastąpienia, MustInherit NotInheritable, statyczna, udostępniony, cieni, tylko do odczytu, WriteOnly, wymiar, stała, WithEvents, rozszerzanie i zwężanie niestandardowe, Asynchroniczne: Brak | 15.5 |

**dotnet\_style\_require\_accessibility_modifiers**

Ta zasada nie akceptuje **true** lub **false** wartości; zamiast tego przyjmuje wartość z następującej tabeli:

| Wartość | Opis |
| ----- |:----------- |
| Zawsze | Modyfikatory dostępności należy określić preferowany |
| for\_non\_interface_members | Preferowane modyfikatory dostępności, które mają zostać zadeklarowane z wyjątkiem członków interfejsu publicznego. To obecnie nie różnią się od **zawsze** i będzie działać jako przyszłych sprawdzające dla, jeśli C# dodaje domyślnych metod interfejsu. |
| Nigdy nie | Nie preferowane modyfikatory dostępności należy określić |

Przykłady kodu:

```csharp
// dotnet_style_require_accessibility_modifiers = always
// dotnet_style_require_accessibility_modifiers = for_non_interface_members
class MyClass
{
    private const string thisFieldIsConst= "constant";
}

// dotnet_style_require_accessibility_modifiers = never
class MyClass
{
    const string thisFieldIsConst= "constant";
}
```

**csharp_preferred_modifier_order**

- Gdy ta zasada jest ustawiona na listę modyfikatorów, preferowane określonej kolejności.
- Gdy ta zasada zostanie pominięty z pliku, kolejność modyfikator nie jest preferowane.

Przykłady kodu:

```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async
class MyClass
{
    private static readonly int _daysInYear = 365;
}
```

**visual_basic_preferred_modifier_order**

- Gdy ta zasada jest ustawiona na listę modyfikatorów, preferowane określonej kolejności.
- Gdy ta zasada zostanie pominięty z pliku, kolejność modyfikator nie jest preferowane.

Przykłady kodu:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

Te reguły mogą występować w *.editorconfig* plików w następujący sposób:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_require_accessibility_modifiers = always:suggestion

# CSharp code style settings:
[*.cs]
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Visual Basic code style settings:
[*.vb]
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

#### <a name="expression_level"></a>Wyrażenie poziom preferencji

Styl reguł w tej sekcji dotyczą wyrażenia poziom preferencji, łącznie z użyciem inicjatory obiektów, inicjatory kolekcji, nazwy krotki jawne lub wykrywany i wywnioskować typy anonimowe.

W poniższej tabeli przedstawiono nazwy reguł, identyfikatory reguły właściwe języki programowania, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Domyślne usługi Visual Studio | Visual Studio 2017 wersji |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_object_initializer | IDE0017 | C# i Visual Basic | PRAWDA: sugestii | Pierwsze wydanie |
| dotnet_style_collection_initializer | IDE0028 | C# i Visual Basic | PRAWDA: sugestii | Pierwsze wydanie |
| dotnet_style_explicit_tuple_names | IDE0033 | C# 7.0 + i Visual Basic 15 + | PRAWDA: sugestii | Pierwsze wydanie |
| dotnet_style_prefer_inferred_tuple_names | IDE0037 | C# 7.1 + i Visual Basic 15 + | PRAWDA: sugestii | 15,6 |
| dotnet_style_prefer_inferred_anonymous_type_member_names | IDE0037 | C# i Visual Basic | PRAWDA: sugestii | 15,6 |

**dotnet\_style\_object_initializer**

- Jeśli ta reguła jest równa **true**, preferowane obiektów, aby można było zainicjować przy użyciu inicjatory obiektów, kiedy to możliwe.
- Jeśli ta reguła jest równa **false**, wybrać obiekty do *nie* można zainicjować przy użyciu inicjatory obiektów.

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

**dotnet\_style\_collection_initializer**

- Jeśli ta reguła jest równa **true**, wybrać kolekcje, aby można było zainicjować przy użyciu inicjatory kolekcji, jeśli to możliwe.
- Jeśli ta reguła jest równa **false**, preferowane kolekcje w celu *nie* można zainicjować przy użyciu inicjatory kolekcji.

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

**dotnet\_style\_explicit\_tuple_names**

- Jeśli ta reguła jest równa **true**, wolą krotki nazwy właściwości ItemX.
- Jeśli ta reguła jest równa **false**, preferowane właściwości ItemX nazwy spójnej kolekcji.

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

**dotnet\_style\_prefer\_inferred\_tuple_names**

- Jeśli ta reguła jest równa **true**, preferowane nazwy elementów wywnioskowanych spójnej kolekcji.
- Jeśli ta reguła jest równa **false**, preferowane nazwy elementów jawne spójnej kolekcji.

Przykłady kodu:

```csharp
// dotnet_style_prefer_inferred_tuple_names = true
var tuple = (age, name);

// dotnet_style_prefer_inferred_tuple_names = false
var tuple = (age: age, name: name);
```

**dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names**

- Jeśli ta reguła jest równa **true**, preferowane nazwy elementów członkowskich wywnioskowanego typu anonimowego.
- Jeśli ta reguła jest równa **false**, preferowane nazwy elementów członkowskich jawnego typu anonimowego.

Przykłady kodu:

```csharp
// dotnet_style_prefer_inferred_anonymous_type_member_names = true
var anon = new { age, name };

// dotnet_style_prefer_inferred_anonymous_type_member_names = false
var anon = new { age = age, name = name };

```

Te reguły mogą występować w *.editorconfig* plików w następujący sposób:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
```

#### <a name="null_checking"></a>Preferencje sprawdzanie wartości null

Reguły stylu w tej sekcji dotyczą preferencje sprawdzanie wartości null.

W poniższej tabeli przedstawiono nazwy reguł, identyfikatory reguły właściwe języki programowania, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Domyślne usługi Visual Studio | Visual Studio 2017 wersji |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_coalesce_expression | IDE0029 | C# i Visual Basic | PRAWDA: sugestii | Pierwsze wydanie |
| dotnet_style_null_propagation | IDE0031 | C# w wersji 6.0 + i Visual Basic 14 + | PRAWDA: sugestii | Pierwsze wydanie |

**dotnet\_style\_coalesce_expression**

- Jeśli ta reguła jest równa **true**, preferowane null łączącego wyrażenia trójargumentowy sprawdzania.
- Jeśli ta reguła jest równa **false**, preferowane trójargumentowy sprawdzanie do wyrażeń łączącego wartości null.

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

**dotnet\_style\_null_propagation**

- Jeśli ta reguła jest równa **true**, wolą używać operatora warunkowego wartości null, jeśli to możliwe.
- Jeśli ta reguła jest równa **false**, wolą używać trójargumentowy sprawdzanie wartości null, jeśli jest to możliwe.

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

Te reguły mogą występować w *.editorconfig* plików w następujący sposób:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
```

### <a name="c-code-style-settings"></a>Ustawienia stylu kodu C#

Reguły stylu w tej sekcji dotyczą C# tylko.

#### <a name="var"></a>Typy jawne i niejawne

Reguły stylu w tej sekcji (reguły IDE0007 identyfikatorów i IDE0008) dotyczą stosowania [var](/dotnet/csharp/language-reference/keywords/var) — słowo kluczowe w porównaniu z typem jawnym w deklaracji zmiennej. Typy wbudowane, gdy typem jest widoczna i innych miejscach, można osobno zastosowana ta reguła.

W poniższej tabeli przedstawiono nazwy reguł, właściwe języki programowania i wartości domyślnych:

| Nazwa zasady | Właściwe języki | Domyślne usługi Visual Studio |
| ----------- | -------------------- | ----------------------|
| csharp_style_var_for_built_in_types | C# | wartość true: Brak |
| csharp_style_var_when_type_is_apparent | C# | wartość true: Brak |
| csharp_style_var_elsewhere | C# | wartość true: Brak |

**csharp\_style\_var\_for\_built\_in_types**

- Jeśli ta reguła jest równa **true**, preferowane `var` służy do deklarowania zmiennych z typami wbudowanych systemu, takich jak `int`.
- Jeśli ta reguła jest równa **false**, Preferuj jawnego typu przed `var` do deklarowania zmiennych z typami wbudowany system takich jak `int`.

Przykłady kodu:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

**CSharp\_styl\_var\_podczas\_typu\_is_apparent**

- Jeśli ta reguła jest równa **true**, preferowane `var` kiedy typ jest wymienione po prawej stronie wyrażenia deklaracji.
- Jeśli ta reguła jest równa **false**, Preferuj jawnego typu przed `var` kiedy typ jest wymienione po prawej stronie wyrażenia deklaracji.

Przykłady kodu:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

**csharp\_style\_var_elsewhere**

- Jeśli ta reguła jest równa **true**, preferowane `var` za pośrednictwem jawnego typu we wszystkich przypadkach, chyba że zastąpione przez inną regułę stylu kodu.
- Jeśli ta reguła jest równa **false**, Preferuj jawnego typu przed `var` we wszystkich przypadkach, chyba że zastąpione przez inną regułę stylu kodu.

Przykłady kodu:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

Przykład *.editorconfig* pliku:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="expression_bodied_members"></a>Zabudowanych wyrażenia elementów członkowskich

Reguły stylu w tej sekcji dotyczą stosowania [zabudowanych wyrażenia elementów członkowskich](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) po logiki składa się z jednego wyrażenia. Ta zasada może odnosić się do metody, konstruktorów, operatory, właściwości, indeksatorów i metody dostępu.

W poniższej tabeli przedstawiono nazwy reguł, identyfikatory reguły, wersje odpowiedni język, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Domyślne usługi Visual Studio | Visual Studio 2017 wersji |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_style_expression_bodied_methods | IDE0022 | C# W WERSJI 6.0 + | false: Brak | 15.3 |
| csharp_style_expression_bodied_constructors | IDE0021 | C# 7.0 + | false: Brak | 15.3 |
| csharp_style_expression_bodied_operators | IDE0023 i IDE0024 | C# 7.0 + | false: Brak | 15.3 |
| csharp_style_expression_bodied_properties | IDE0025 | C# 7.0 + | wartość true: Brak | 15.3 |
| csharp_style_expression_bodied_indexers | IDE0026 | C# 7.0 + | wartość true: Brak | 15.3 |
| csharp_style_expression_bodied_accessors | IDE0027 | C# 7.0 + | wartość true: Brak | 15.3 |

**csharp\_style\_expression\_bodied_methods**

Ta reguła akceptuje wartości z poniższej tabeli:

| Wartość | Opis |
| ----- |:----------- |
| true | Preferowane jest zabudowanych wyrażenia elementów członkowskich dla metod |
| when_on_single_line | Preferowane zabudowanych wyrażenia elementów członkowskich dla metod, gdy będą one jednym wierszu |
| false | Preferowane jest treści bloku dla metod |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

**CSharp\_styl\_wyrażenie\_bodied_constructors**

Ta reguła akceptuje wartości z poniższej tabeli:

| Wartość | Opis |
| ----- |:----------- |
| true | Preferowane jest zabudowanych wyrażenia elementów członkowskich dla konstruktorów |
| when_on_single_line | Preferowane zabudowanych wyrażenia elementów członkowskich dla konstruktorów, gdy będą one jednym wierszu |
| false | Preferowane jest treści bloku dla konstruktorów |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

**CSharp\_styl\_wyrażenie\_bodied_operators**

Ta reguła akceptuje wartości z poniższej tabeli:

| Wartość | Opis |
| ----- |:----------- |
| true | Preferowane jest zabudowanych wyrażenia elementów członkowskich dla operatorów |
| when_on_single_line | Preferowane zabudowanych wyrażenia elementów członkowskich dla operatorów, gdy będą one jednym wierszu |
| false | Preferowane treści bloku dla operatorów |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

**CSharp\_styl\_wyrażenie\_bodied_properties**

Ta reguła akceptuje wartości z poniższej tabeli:

| Wartość | Opis |
| ----- |:----------- |
| true | Preferowane właściwości zabudowanych wyrażenia elementów członkowskich |
| when_on_single_line | Preferowane zabudowanych wyrażenia elementów członkowskich dla właściwości, gdy będą one jednym wierszu |
| false | Preferowane jest treści bloku dla właściwości |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

**CSharp\_styl\_wyrażenie\_bodied_indexers**

Ta reguła akceptuje wartości z poniższej tabeli:

| Wartość | Opis |
| ----- |:----------- |
| true | Preferowane jest zabudowanych wyrażenia elementów członkowskich dla indeksatorów |
| when_on_single_line | Preferowane zabudowanych wyrażenia elementów członkowskich dla indeksatorów, gdy będą one jednym wierszu |
| false | Preferowane jest treści bloku dla indeksatorów |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _value[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

**csharp\_style\_expression\_bodied_accessors**

Ta reguła akceptuje wartości z poniższej tabeli:

| Wartość | Opis |
| ----- |:----------- |
| true | Preferowane jest zabudowanych wyrażenia elementów członkowskich dla metod dostępu |
| when_on_single_line | Preferowane zabudowanych wyrażenia elementów członkowskich dla metod dostępu, gdy będą one jednym wierszu |
| false | Preferowane treści bloku dla metod dostępu |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

Przykład *.editorconfig* pliku:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
csharp_style_expression_bodied_constructors = false:none
csharp_style_expression_bodied_operators = false:none
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
```

#### <a name="pattern_matching"></a>Dopasowanie wzorca

Reguły stylu w tej sekcji dotyczą stosowania [dopasowanie wzorca](/dotnet/csharp/pattern-matching) w języku C#.

W poniższej tabeli przedstawiono nazwy reguł, identyfikatory reguły, wersje odpowiedni język i wartości domyślnych:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Domyślne usługi Visual Studio |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_pattern_matching_over_is_with_cast_check | IDE0020 | C# 7.0 + | PRAWDA: sugestii |
| csharp_style_pattern_matching_over_as_with_null_check | IDE0019 | C# 7.0 + | PRAWDA: sugestii |

**csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check**

- Jeśli ta reguła jest równa **true**, preferowane, zamiast dopasowywania do wzorca `is` wyrażenia z typu rzutowania.
- Jeśli ta reguła jest równa **false**, preferowane `is` wyrażenia z typu rzutowania zamiast dopasowywania do wzorca.

Przykłady kodu:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

**csharp\_style\_pattern\_matching\_over\_as\_with\_null_check**

- Jeśli ta reguła jest równa **true**, preferowane, zamiast dopasowywania do wzorca `as` wyrażenia o wartości null sprawdza, czy jest coś określonego typu.
- Jeśli ta reguła jest równa **false**, preferowane `as` wyrażenia ze sprawdzenia wartości null zamiast wzorzec dopasowany do ustalenia, czy jest coś określonego typu.

Przykłady kodu:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

Przykład *.editorconfig* pliku:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="inlined_variable_declarations"></a>Wbudowane deklaracje zmiennej

Ten styl określa, czy reguła dotyczy `out` zmienne są deklarowane jako wbudowany, czy nie. Uruchamianie w języku C# 7, można [zadeklarować zmiennej poza na liście argumentów w wywołaniu metody](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument), a nie w deklaracji zmiennej oddzielne.

W poniższej tabeli przedstawiono nazwę reguły, identyfikator reguły, wersje odpowiedni język i wartości domyślnych:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Domyślne usługi Visual Studio |
| --------- | -------- | -------------------- | ----------------------|
| csharp_style_inlined_variable_declaration | IDE0018 | C# 7.0 + | PRAWDA: sugestii |

**csharp\_style\_inlined\_variable_declaration**

- Jeśli ta reguła jest równa **true**, preferowane `out` zmienne, które mają być zadeklarowana śródwierszowo na liście argumentów w wywołaniu metody, jeśli to możliwe.
- Jeśli ta reguła jest równa **false**, preferowane `out` zmienne, które mają być zadeklarowana przed wywołaniem metody.

Przykłady kodu:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Przykład *.editorconfig* pliku:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

#### <a name="expression_level_csharp"></a>Wyrażenie poziom preferencji

Reguły stylu w tej sekcji dotyczą wyrażenia poziom preferencji, łącznie z użyciem [domyślne wyrażenia](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference), zmienne deconstructed i funkcje lokalne za pośrednictwem funkcji anonimowych.

W poniższej tabeli przedstawiono nazwę reguły, identyfikator reguły, wersje odpowiedni język, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Domyślne usługi Visual Studio | Visual Studio 2017 wersji |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_prefer_simple_default_expression | IDE0034 | C# 7.1+ | PRAWDA: sugestii | 15.3 |
| csharp_style_deconstructed_variable_declaration | IDE0042 | C# 7.0 + | PRAWDA: sugestii | 15.5 |
| csharp_style_pattern_local_over_anonymous_function | IDE0039 | C# 7.0 + | PRAWDA: sugestii | 15.5 |

**CSharp\_preferowane\_proste\_default_expression**

Dotyczy to reguły stylu przy użyciu [ `default` dosłownie wyrażenia wartości domyślnej](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) gdy kompilator może wnioskować o typie wyrażenia.

- Jeśli ta reguła jest równa **true**, preferowane `default` za pośrednictwem `default(T)`.
- Jeśli ta reguła jest równa **false**, preferowane `default(T)` za pośrednictwem `default`.

Przykłady kodu:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

**csharp\_style\_deconstructed\_variable_declaration**

- Jeśli ta reguła jest równa **true**, preferowane deconstructed deklaracja zmiennej.
- Jeśli ta reguła jest równa **false**, nie preferowane deconstruction w deklaracjach zmiennych.

Przykłady kodu:

```csharp
// csharp_style_deconstructed_variable_declaration = true
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");

// csharp_style_deconstructed_variable_declaration = false
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");
```

**csharp\_style\_pattern\_local\_over\_anonymous_function**

- Jeśli ta reguła jest równa **true**, preferowane funkcje lokalne za pośrednictwem funkcji anonimowych.
- Jeśli ta reguła jest równa **false**, Preferuj funkcje anonimowe przed funkcje lokalne.

Przykłady kodu:

```csharp
// csharp_style_pattern_local_over_anonymous_function = true
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}

// csharp_style_pattern_local_over_anonymous_function = false
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};
```

Przykład *.editorconfig* pliku:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
```

#### <a name="null_checking_csharp"></a>"Null" Sprawdzanie preferencji

Te reguły dotyczą stylu składni wokół `null` sprawdzania, w tym o korzystaniu z `throw` wyrażenia lub `throw` instrukcje oraz czy należy sprawdzić wartość null lub użyj warunkowego operatora łączącego (`?.`) podczas wywoływania [wyrażenia lambda](/dotnet/csharp/lambda-expressions).

W poniższej tabeli przedstawiono nazwy reguł, identyfikatory reguły, wersje odpowiedni język i wartości domyślnych:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Domyślne usługi Visual Studio |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_throw_expression | IDE0016 | C# 7.0 + | PRAWDA: sugestii |
| csharp_style_conditional_delegate_call | IDE0041 | C# W WERSJI 6.0 + | PRAWDA: sugestii |

**csharp\_style\_throw_expression**

- Jeśli ta reguła jest równa **true**, wolą używać `throw` wyrażenia zamiast `throw` instrukcje.
- Jeśli ta reguła jest równa **false**, wolą używać `throw` instrukcje zamiast `throw` wyrażenia.

Przykłady kodu:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

**csharp\_style\_conditional\_delegate_call**

- Jeśli ta reguła jest równa **true**, wolą używać operatora łączącego warunkowego (`?.`) podczas wywoływania wyrażenia lambda, zamiast wykonywania o wartości null Sprawdź.
- Jeśli ta reguła jest równa **false**, preferowane sprawdzania wartości null przed wywołaniem wyrażenia lambda, zamiast operatora łączącego warunkowego (`?.`).

Przykłady kodu:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

Przykład *.editorconfig* pliku:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="code_block"></a>Preferencje blok kodu

Ta zasada styl dotyczy użycia nawiasów klamrowych `{ }` otaczającego bloków kodu.

W poniższej tabeli przedstawiono nazwę reguły, identyfikator reguły, wersje odpowiedni język, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Domyślne usługi Visual Studio | Visual Studio 2017 wersji |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_prefer_braces | IDE0011 | C# | wartość true: Brak | 15.3 |

**CSharp\_preferowane\_nawiasów klamrowych**

- Jeśli ta reguła jest równa **true**, preferowane nawiasy klamrowe, nawet w przypadku jeden wiersz kodu.
- Jeśli ta reguła jest równa **false**, preferowane nie nawiasów klamrowych, jeśli dozwolone.

Przykłady kodu:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

Przykład *.editorconfig* pliku:

```EditorConfig
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
- Ustawienia formatowania C#
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

#### <a name="usings"></a>Organizacja deklaracji Using

Ta reguła formatowania dotyczy umieszczania System.* przy użyciu dyrektyw względem innych przy użyciu dyrektyw.

W poniższej tabeli przedstawiono nazwy reguły właściwe języki, wartości domyślnej i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Właściwe języki | Domyślne usługi Visual Studio | Visual Studio 2017 wersji |
| ----------- | -------------------- | ----------------------| ----------------  |
| dotnet_sort_system_directives_first |  C# i Visual Basic | true | 15.3  |

**dotnet\_sort\_system\_directives_first**

- Jeśli ta reguła jest równa **true**posortować alfabetycznie przy użyciu dyrektyw System.* i umieść je przed innymi deklaracje Using.
- Jeśli ta reguła jest równa **false**, nie umieszczaj System.* przy użyciu dyrektyw przed innymi przy użyciu dyrektyw.

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

Przykład *.editorconfig* pliku:

```EditorConfig
# .NET formatting settings:
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
```

### <a name="c-formatting-settings"></a>Ustawienia formatowania C#

Reguły formatowania w tej sekcji dotyczą tylko kod w języku C#.

#### <a name="newline"></a>Opcje nowego wiersza

Te reguły formatowania dotyczy stosowania nowych wierszy w celu formatowania kodu.

W poniższej tabeli przedstawiono "nowy wiersz" nazwy reguł właściwe języki, wartości domyślne, a najpierw obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Właściwe języki | Domyślne usługi Visual Studio | Visual Studio 2017 wersji |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_new_line_before_open_brace |  C# | wszystkie | 15.3  |
| csharp_new_line_before_else |  C# | true | 15.3  |
| csharp_new_line_before_catch |  C# | true | 15.3  |
| csharp_new_line_before_finally |  C# | true | 15.3  |
| csharp_new_line_before_members_in_object_initializers |  C# | true | 15.3  |
| csharp_new_line_before_members_in_anonymous_types |  C# | true | 15.3  |
| csharp_new_line_between_query_expression_clauses |  C# | true | 15.3  |

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

- Jeśli ta reguła jest równa **true**, umieść `else` instrukcje w nowym wierszu.
- Jeśli ta reguła jest równa **false**, umieść `else` instrukcje w tym samym wierszu.

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

**csharp\_new\_line\_before_catch**

- Jeśli ta reguła jest równa **true**, umieść `catch` instrukcje w nowym wierszu.
- Jeśli ta reguła jest równa **false**, umieść `catch` instrukcje w tym samym wierszu.

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

- Jeśli ta reguła jest równa **true**, wymagają `finally` instrukcje do nowego wiersza po klamrowym nawiasie zamykającym.
- Jeśli ta reguła jest równa **false**, wymagają `finally` instrukcje w tym samym wierszu co zamykający nawias klamrowy.

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

- Jeśli ta reguła jest równa **true**, wymagają członkami intiializers obiektu w osobnych wierszach.
- Jeśli ta reguła jest równa **false**, wymagają członkami inicjatory obiektów w tym samym wierszu.

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

- Jeśli ta reguła jest równa **true**, wymagają elementy członkowskie typów anonimowych w osobnych wierszach.
- Jeśli ta reguła jest równa **false**, wymagają elementów członkowskich typu anonimowego na tym samym wierszu.

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

- Jeśli ta reguła jest równa **true**, wymagają elementy klauzule wyrażenia zapytania w osobnych wierszach.
- Jeśli ta reguła jest równa **false**, wymagają elementy klauzule wyrażenia zapytania w tym samym wierszu.

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

Przykład *.editorconfig* pliku:

```EditorConfig
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

#### <a name="indent"></a>Opcje wcięć

Te reguły formatowania dotyczy stosowania wcięcia w celu formatowania kodu.

W poniższej tabeli przedstawiono nazwy reguł, właściwe języki, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Właściwe języki | Domyślne usługi Visual Studio | Visual Studio 2017 wersji |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_indent_case_contents |  C# | true | 15.3  |
| csharp_indent_switch_labels |  C# | true | 15.3  |
| csharp_indent_labels |  C# | no_change | 15.3  |

**csharp\_indent\_case_contents**

- Jeśli ta reguła jest równa **true**, wcięcie `switch` przypadek zawartość.
- Jeśli ta reguła jest równa **false**, nie wcięcie `switch` przypadek zawartość.

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

**csharp\_indent\_switch_labels**

- Jeśli ta reguła jest równa **true**, wcięcie `switch` etykiety.
- Jeśli ta reguła jest równa **false**, nie wcięcie `switch` etykiety.

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

**csharp\_indent_labels**

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

Przykład *.editorconfig* pliku:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
```

#### <a name="spacing"></a>Opcje odstępów

Te reguły formatowania dotyczą znaków miejsca do formatowania kodu.

W poniższej tabeli przedstawiono nazwy reguł, właściwe języki, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Właściwe języki | Domyślne usługi Visual Studio | Visual Studio 2017 wersji |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_space_after_cast |  C# | false | 15.3  |
| csharp_space_after_keywords_in_control_flow_statements |  C# | true | 15.3  |
| csharp_space_between_method_declaration_parameter_list_parentheses |  C# | false | 15.3  |
| csharp_space_between_method_call_parameter_list_parentheses |  C# | false | 15.3  |
| csharp_space_between_parentheses |  C# | false | 15.3  |

**csharp\_space\_after_cast**

- Jeśli ta reguła jest równa **true**, wymagają odstęp między rzutowanie i wartość.
- Jeśli ta reguła jest równa **false**, wymagają _nie_ odstęp między rzutowanie i wartość.

Przykłady kodu:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

**csharp_space_after_keywords_in_control_flow_statements**

- Jeśli ta reguła jest równa **true**, takich jak wymagają spację po słów kluczowych w instrukcji przepływu sterowania `for` pętli.
- Jeśli ta reguła jest równa **false**, wymagają _nie_ miejsce po słów kluczowych w instrukcji przepływu sterowania, takich jak `for` pętli.

Przykłady kodu:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

**csharp_space_between_method_declaration_parameter_list_parentheses**

- Jeśli ta reguła jest równa **true**, umieść znak spacji po nawiasie otwierającym, a także przed nawiasem zamykającym w liście parametrów deklaracji metody.
- Jeśli ta reguła jest równa **false**, nie umieszczaj znaków spacji po nawiasie otwierającym, a także przed nawiasem zamykającym w liście parametrów deklaracji metody.

Przykłady kodu:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

**csharp_space_between_method_call_parameter_list_parentheses**

- Jeśli ta reguła jest równa **true**, umieść znak spacji po nawiasie otwierającym, a także przed nawiasem zamykającym wywołania metody.
- Jeśli ta reguła jest równa **false**, nie umieszczaj znaków spacji po nawiasie otwierającym, a także przed nawiasem zamykającym wywołania metody.

Przykłady kodu:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

**csharp_space_between_parentheses**

Ta reguła akceptuje wartości co najmniej jeden z następującej tabeli:

| Wartość | Opis |
| ----- |:------------|
| control_flow_statements | Umieść odstęp między nawiasy instrukcjach przepływu sterowania |
| wyrażenia | Umieść odstęp między nawiasy wyrażeń |
| type_casts | Umieść odstęp między nawiasy w rzutowania typów |

Jeśli Pomiń tę regułę, lub użyj wartości innych niż `control_flow_statements`, `expressions`, lub `type_casts`, ustawienie nie ma zastosowania.

Przykłady kodu:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

Przykład *.editorconfig* pliku:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_parentheses = control_flow_statements, type_casts
```

#### <a name="wrapping"></a>Opcje zawijania

Te reguły formatowania dotyczy stosowania pojedynczych wierszy w porównaniu z osobnych wierszach instrukcje i bloków kodu.

W poniższej tabeli przedstawiono nazwy reguł, właściwe języki, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Właściwe języki | Domyślne usługi Visual Studio | Visual Studio 2017 wersji |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_preserve_single_line_statements |  C# | true | 15.3  |
| csharp_preserve_single_line_blocks |  C# | true | 15.3  |

**csharp_preserve_single_line_statements**

- Jeśli ta reguła jest równa **true**, pozostaw instrukcje i element członkowski deklaracje w tym samym wierszu.
- Jeśli ta reguła jest równa **false**, pozostaw instrukcje i element członkowski deklaracje w różnych wierszy.

Przykłady kodu:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

**csharp_preserve_single_line_blocks**

- Jeśli ta reguła jest równa **true**, pozostaw blok kodu w pojedynczym wierszu.
- Jeśli ta reguła jest równa **false**, pozostaw blok kodu w osobnych wierszach.

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

Przykład *.editorconfig* pliku:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

## <a name="see-also"></a>Zobacz także

- [Szybkie akcje](../ide/quick-actions.md)
- [Konwencje nazewnictwa .NET dla EditorConfig](../ide/editorconfig-naming-conventions.md)
- [Tworzenie niestandardowego edytora przenośne opcji](../ide/create-portable-custom-editor-options.md)
- [Plik .editorconfig platformę .NET kompilatora](https://github.com/dotnet/roslyn/blob/master/.editorconfig)
