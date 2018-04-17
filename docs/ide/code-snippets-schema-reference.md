---
title: Odwołanie do schematu wstawki kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- schema reference [Visual Studio]
- snippets [Visual Studio], schema reference
- code snippets [Visual Studio], schema reference
- IntelliSense Code Snippets, XML Schema
ms.assetid: 58a60621-725f-4763-93b7-62ea5424ef88
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 91002c27f37918b0db4b4ca4fb2dd5ab5211efe7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="code-snippets-schema-reference"></a>Odwołanie do schematu wstawki kodu
Wstawki kodu IntelliSense są wstępnie utworzone fragmenty kodu, które są gotowe do wstawienia do aplikacji z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Umożliwiają one poprawę wydajności pracy, ponieważ zmniejszają ilość czasu spędzanego na wielokrotnym wpisywaniu tego samego kodu czy wyszukiwaniu przykładów. Służy do tworzenia własnych fragmentów kodu i dodaj je do wstawki kodu schematu XML fragmentu kodu IntelliSense który [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] już zawiera.  
  
##  <a name="assembly"></a> Assembly — element  
 Określa nazwę zestawu, do którego się odwołuje fragment kodu.
  
 Wartość tekstu **zestawu** element jest albo przyjazną nazwą zestawu, `System.dll`, lub jego silnych nazw, takich jak `System,Version=1.0.0.1,Culture=neutral,PublicKeyToken=9b35aa323c18d4fb1`.  
  
```xml  
<Assembly>  
    AssemblyName  
</Assembly>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Reference — element](../ide/code-snippets-schema-reference.md#reference)|Zawiera informacje o odwołaniach do zestawów wymaganych przez fragment kodu.|  
  
 Wartość tekstowa jest wymagana. Tekst określa zestaw, do którego odwołuje się fragment kodu.  
  
##  <a name="author"></a> Element autora  
 Określa nazwę autora fragmentu kodu. **Menedżerze fragmentów kodu** Wyświetla nazwę przechowywane w `Author` element fragmentu kodu.  
  
```xml  
<Author>  
   Code Snippet Author  
</Author>    
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header)|Zawiera ogólne informacje o fragmencie kodu.|  
  
 Wartość tekstowa jest wymagana. Tekst określa autora fragmentu kodu.  
  
## <a name="a-namecode--code-element"></a><a name="code" /> Code element  
Stanowi kontener dla krótkich bloków kodu.  
  
### <a name="keywords"></a>Słowa kluczowe
Dwa wyrazy zastrzeżone są dostępne do użycia w tekście `Code` element: `$end$` i `$selected$`. `$end$` oznacza na położenie kursora po wstawieniu fragmentu kodu. `$selected$` reprezentuje tekstu zaznaczonego w dokumencie, który można wstawiać do fragment kodu, gdy jest wywoływana. Na przykład podane fragment kodu, który zawiera:  
  
```  
$selected$ is a great color.  
```  
  
Wyraz "Blue" jest zaznaczone, gdy użytkownik wywoła szablonu, wynikiem jest:  
  
```  
Blue is a great color.  
```  
  
Nie można użyć albo `$end$` lub `$selected$` więcej niż jeden raz we fragmencie kodu. Jeśli to zrobisz, drugie wystąpienie jest rozpoznawana. Podane fragment kodu, który zawiera:  
  
```  
$selected$ is a great color. I love $selected$.  
```  
  
Jeśli wybrano słowo "Blue", wynik jest:  
  
```  
 is a great color. I love Blue.  
```  
  
Początkowa miejsca pojawia się, ponieważ brakuje miejsca między `$selected$` i `is`.  
  
Wszystkie inne `$` słowa kluczowe dynamicznie są zdefiniowane w `<Literal>` i `<Object>` tagów.  

Struktura elementu kodu jest następujący:
  
```xml  
<Code Language="Language"  
    Kind="method body/method decl/type decl/page/file/any"  
    Delimiter="Delimiter">  
    Code to insert  
</Code>  
```

Wartość tekstowa jest wymagana. Ten tekst Określa kod, wraz z literały oraz obiekty, które można używać podczas następujący fragment kodu zostaną wstawione do pliku kodu.  

### <a name="attributes"></a>Atrybuty
Dostępne są trzy atrybuty dla elementu kodu:

- **Język** - _wymagane_ atrybut, który określa język fragmentu kodu. Wartość może być jedną z następujących czynności:

   |Wartość|Opis|  
   |-----|-----------|  
   |`VB`|Identyfikuje fragment kodu języka Visual Basic.|  
   |`CSharp`|Identyfikuje fragment kodu języka C#.|  
   |`CPP`|Identyfikuje fragment kodu języka C++.|  
   |`XML`|Identyfikuje fragment kodu języka XML.|  
   |`JavaScript`|Identyfikuje fragment kodu języka JavaScript.|  
   |`SQL`|Identyfikuje fragment kodu języka SQL.|  
   |`HTML`|Identyfikuje fragment kodu języka HTML.|
 
- **Rodzaj** - _opcjonalnie_ atrybut, który określa rodzaj kodu, który zawiera wstawkę i lokalizacji, w którym należy wstawić fragment kodu dla fragmentu kodu do kompilacji. Wartość może być jedną z następujących czynności:

   |Wartość|Opis|  
   |-----|-----------|  
   |`method body`|Określa, że fragment kodu jest treścią metody i w związku z tym należy go wstawić do deklaracji metody.|  
   |`method decl`|Określa, że fragment kodu jest metodą i w związku z tym należy go wstawić do klasy lub modułu.|  
   |`type decl`|Określa, że fragment kodu jest typem i w związku z tym należy go wstawić do klasy, modułu lub przestrzeni nazw.|  
   |`file`|Określa, że fragment jest kompletnym plikiem kodu. Takie fragmenty kodu można wstawiać autonomicznie do pliku kodu albo do przestrzeni nazw.|  
   |`any`|Określa, że fragment można wstawić w dowolnym miejscu. Ten tag jest używany we fragmentach kodu niezależnych od kontekstu, takich jak komentarze.|

- **Ogranicznik** - _opcjonalnie_ atrybut, który określa ogranicznik używany do opisania literałów i obiektów w kodzie. Domyślnie jest ogranicznik `$`.

### <a name="parent-element"></a>Element nadrzędny
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Fragment kodu — element](../ide/code-snippets-schema-reference.md#snippet)|Zawiera odwołania, definicje importu, deklaracje i kod dla fragmentu kodu.|
  
##  <a name="codesnippet"></a> CodeSnippet element  
 Umożliwia określenie nagłówka oraz wielu fragmentów kodu IntelliSense, które można wstawiać do plików kodu programu Visual Studio.  
  
```xml  
<CodeSnippet Format="x.x.x">  
    <Header>... </Header>  
    <Snippet>... </Snippet>  
</CodeSnippet>  
```  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Format`|Atrybut wymagany. Określa wersję schematu fragmentu kodu. Atrybut Format musi być ciągiem tekstowym o składni x.x.x, gdzie każdy znak „x” reprezentuje wartość liczbową numeru wersji. Visual Studio zignoruje fragmenty kodu o `Format` atrybutów, których nie zna.|  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header)|Element wymagany. Zawiera ogólne informacje o fragmencie kodu. Musi istnieć dokładnie jeden `Header` element we fragmencie kodu.|  
|[Fragment kodu — element](../ide/code-snippets-schema-reference.md#snippet)|Element wymagany. Zawiera kod, który będzie wstawiany przez program Visual Studio. Musi istnieć dokładnie jeden `Snippet` element we fragmencie kodu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[CodeSnippets element](../ide/code-snippets-schema-reference.md#codesnippets)|Element główny schematu XML fragmentu kodu.|  
  
##  <a name="codesnippets"></a> CodeSnippets element  
 Grupy [CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet) elementów. `CodeSnippets` Element jest elementem głównym fragmentu kodu schematu XML.  
  
```xml  
<CodeSnippets>  
    <CodeSnippet>... </CodeSnippet>  
</CodeSnippets>  
```  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[CodeSnippet element](../ide/code-snippets-schema-reference.md#codesnippet)|Element opcjonalny. Element nadrzędny dla wszystkich danych fragmentu kodu. Może wynosić zero lub więcej `CodeSnippet` elementów w `CodeSnippets` elementu.|  
  
##  <a name="declarations"></a> Deklaracje — element  
 Określa literały i obiekty tworzące sekcje fragmentu kodu, które można edytować.  
  
```xml  
<Declarations>  
    <Literal>... </Literal>  
    <Object>... </Object>  
</Declarations>  
```  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Element literał](../ide/code-snippets-schema-reference.md#literal)|Element opcjonalny. Definiuje literały fragmentu kodu, które można edytować. Może wynosić zero lub więcej `Literal` elementów w `Declarations` elementu.|  
|[Object element](../ide/code-snippets-schema-reference.md#object)|Element opcjonalny. Definiuje obiekty fragmentu kodu, które można edytować. Może wynosić zero lub więcej `Object` elementów w `Declarations` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Fragment kodu — element](../ide/code-snippets-schema-reference.md#snippet)|Zawiera odwołania, definicje importu, deklaracje i kod dla fragmentu kodu.|  
  
##  <a name="default"></a> Domyślny element  
 Określa domyślną wartość literału lub obiektu fragmentu kodu IntelliSense.  
  
```xml  
<Default>  
    Default value  
</Default>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Element literał](../ide/code-snippets-schema-reference.md#literal)|Definiuje pola literałów fragmentu kodu, które można edytować.|  
|[Object element](../ide/code-snippets-schema-reference.md#object)|Definiuje pola obiektów fragmentu kodu, które można edytować.|  
  
 Wartość tekstowa jest wymagana. Ten tekst określa domyślną wartość literału lub obiektu wypełniającego pola fragment kodu, który można edytować.  
  
##  <a name="description"></a> Opis elementu  
 Określa opisowe informacje o zawartości fragmentu kodu IntelliSense.  
  
```xml  
<Description>  
    Code Snippet Description  
</Description>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header)|Zawiera ogólne informacje o fragmencie kodu.|  
  
 Wartość tekstowa jest wymagana. Ten tekst opisuje fragment kodu.  
  
##  <a name="function"></a> Element — funkcja  
 Określa funkcję do wykonania, gdy w programie Visual Studio na literale lub obiekcie zostanie ustawiony fokus.  
  
> [!NOTE]
>  `Function` Jest obsługiwany tylko w wstawki kodu C#.  
  
```xml  
<Function>  
    FunctionName  
</Function>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Element literał](../ide/code-snippets-schema-reference.md#literal)|Definiuje pola literałów fragmentu kodu, które można edytować.|  
|[Object element](../ide/code-snippets-schema-reference.md#object)|Definiuje pola obiektów fragmentu kodu, które można edytować.|  
  
 Wartość tekstowa jest wymagana. Ten tekst określa funkcję do wykonania, gdy w programie Visual Studio na literale lub polu obiektu zostanie ustawiony fokus.  
  
##  <a name="header"></a> Element nagłówka  
 Zawiera ogólne informacje o fragmencie kodu IntelliSense.  
  
```xml  
<Header>  
    <Title>... </Title>  
    <Author>... </Author>  
    <Description>... </Description>  
    <HelpUrl>... </HelpUrl>  
    <SnippetTypes>... </SnippetTypes>  
    <Keywords>... </Keywords>  
    <Shortcut>... </Shortcut>  
</Header>  
```  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Element autora](../ide/code-snippets-schema-reference.md#author)|Element opcjonalny. Imię i nazwisko/nazwa osoby lub firmy, która utworzyła fragment kodu. Może być zero lub jeden `Author` elementów w `Header` elementu.|  
|[Opis elementu](../ide/code-snippets-schema-reference.md#description)|Element opcjonalny. Opis fragmentu kodu. Może być zero lub jeden `Description` elementów w `Header` elementu.|  
|[HelpUrl element](../ide/code-snippets-schema-reference.md#helpurl)|Element opcjonalny. Adres URL strony zawierającej poszerzone informacje o fragmencie kodu. Może być zero lub jeden `HelpURL` elementy w elemencie nagłówka. **Uwaga:** programu Visual Studio nie używa `HelpUrl` elementu. Element jest częścią schematu XML fragmentu kodu IntelliSense. Wszystkie fragmenty kodu zawierające element będą weryfikowane, ale wartość elementu nigdy nie jest używana.|  
|[Element słowa kluczowe](../ide/code-snippets-schema-reference.md#keywords)|Element opcjonalny. Grupy `Keyword` elementów. Może być zero lub jeden `Keywords` elementów w `Header` elementu.|  
|[Element skrótów](../ide/code-snippets-schema-reference.md#shortcut)|Element opcjonalny. Określa tekst skrótu, który pozwala wstawić fragment kodu. Może być zero lub jeden `Shortcut` elementów w `Header` elementu.|  
|[SnippetTypes element](../ide/code-snippets-schema-reference.md#snippettypes)|Element opcjonalny. Grupy `SnippetType` elementów. Może być zero lub jeden `SnippetTypes` elementów w `Header` elementu. Jeśli istnieją nie `SnippetTypes` elementów, fragment kodu zawsze jest prawidłowy.|  
|[Tytuł elementu](../ide/code-snippets-schema-reference.md#title)|Element wymagany. Przyjazna nazwa fragmentu kodu. Musi istnieć dokładnie jeden `Title` element `Header` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[CodeSnippet element](../ide/code-snippets-schema-reference.md#codesnippet)|Element nadrzędny dla wszystkich danych fragmentu kodu.|  
  
##  <a name="helpurl"></a> HelpUrl element  
 Określa adres URL strony zawierającej poszerzone informacje o fragmencie kodu.  
  
> [!NOTE]
>  Program Visual Studio nie używa `HelpUrl` elementu. Element jest częścią schematu XML fragmentu kodu IntelliSense. Wszystkie fragmenty kodu zawierające element będą weryfikowane, ale wartość elementu nigdy nie jest używana.  
  
```xml  
<HelpUrl>  
    www.microsoft.com  
</HelpUrl>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header)|Zawiera ogólne informacje o fragmencie kodu.|  
  
 Wartość tekstowa jest opcjonalna. Ten tekst określa adres URL strony, na której można znaleźć więcej informacji o fragmencie kodu.  
  
##  <a name="id"></a> Identyfikator elementu  
 Określa unikatowy identyfikator `Literal` lub `Object` elementu. Nie dwóch literały lub obiektów w tym samym fragment kodu może mieć tej samej wartości tekstowej ich `ID` elementów. Literały oraz obiekty nie mogą zawierać `ID` element o wartości punktu końcowego. Wartość `$end$` jest zarezerwowany i jest używany do oznaczania na położenie kursora po wstawieniu fragmentu kodu.  
  
```xml  
<ID>  
    Unique Identifier  
</ID>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Element literał](../ide/code-snippets-schema-reference.md#literal)|Definiuje pola literałów fragmentu kodu, które można edytować.|  
|[Object element](../ide/code-snippets-schema-reference.md#object)|Definiuje pola obiektów fragmentu kodu, które można edytować.|  
  
 Wartość tekstowa jest wymagana. Ten tekst określa unikatowy identyfikator obiektu lub literału.  
  
##  <a name="import"></a> Import — element  
 Określa zaimportowaną przestrzeń nazw używaną przez fragment kodu IntelliSense.  
  
> [!NOTE]
>  `Import` Jest obsługiwany tylko dla projektów języka Visual Basic.  
  
```xml  
<Import>  
    <Namespace>... </Namespace>  
</Import>  
```  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Namespace — element](../ide/code-snippets-schema-reference.md#namespace)|Element wymagany. Określa przestrzeń nazw używaną przez fragment kodu. Musi istnieć dokładnie jeden `Namespace` element `Import` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Element importów](../ide/code-snippets-schema-reference.md#imports)|Element GROUPING dla **importu** elementów.|  
  
##  <a name="imports"></a> Element importów  
 Poszczególne grupy `Import` elementów.  
  
> [!NOTE]
>  `Imports` Jest obsługiwany tylko dla projektów języka Visual Basic.  
  
```xml  
<Imports>  
    <Import>... </Import>  
<Imports>  
```  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Import — element](../ide/code-snippets-schema-reference.md#import)|Element opcjonalny. Zawiera zaimportowane przestrzenie nazw fragmentu kodu. Może wynosić zero lub więcej **importu** elementów w `Imports` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Fragment kodu — element](../ide/code-snippets-schema-reference.md#snippet)|Zawiera odwołania, definicje importu, deklaracje i kod dla fragmentu kodu.|  
  
##  <a name="keyword"></a> Element — słowo kluczowe  
 Określa niestandardowe słowo kluczowe fragmentu kodu. Słowa kluczowe fragmentu kodu są wykorzystywane przez program Visual Studio. Stanowią standardowy mechanizm, przy użyciu którego dostawcy treści internetowych mogą dodawać słowa kluczowe na potrzeby wyszukiwania lub kategoryzacji.  
  
```xml  
<Keyword>  
    Code Snippet Keyword  
</Keyword>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Element słowa kluczowe](../ide/code-snippets-schema-reference.md#keywords)|Poszczególne grupy `Keyword` elementów.|  
  
 Wartość tekstowa jest wymagana. Słowo kluczowe fragmentu kodu.  
  
##  <a name="keywords"></a> Element słowa kluczowe  
 Poszczególne grupy `Keyword` elementów. Słowa kluczowe fragmentu kodu są wykorzystywane przez program Visual Studio. Stanowią standardowy mechanizm, przy użyciu którego dostawcy treści internetowych mogą dodawać słowa kluczowe na potrzeby wyszukiwania lub kategoryzacji.  
  
```xml  
<Keywords>  
    <Keyword>... </Keyword>  
    <Keyword>... </Keyword>  
<Keywords>  
```  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Element — słowo kluczowe](../ide/code-snippets-schema-reference.md#keyword)|Element opcjonalny. Zawiera poszczególne słowa kluczowe fragmentu kodu. Może wynosić zero lub więcej `Keyword` elementów w `Keywords` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header)|Zawiera ogólne informacje o fragmencie kodu.|  
  
##  <a name="literal"></a> Element literał  
 Definiuje literały fragmentu kodu, które można edytować. `Literal` Element służy do identyfikacji zastępnika dla części kodu, która zawiera się całkowicie w obrębie fragmentu, ale może będzie dostosowywana po wstawieniu do kodu. Jako literały należy na przykład deklarować ciągi literałowe, wartości liczbowe i nazwy niektórych zmiennych.  
  
 Literały oraz obiekty nie mogą zawierać **identyfikator** wybrany element o wartości ani na końcu. Wartość `$selected$` reprezentuje tekstu zaznaczonego w dokumencie, który można wstawiać do fragment kodu, gdy jest wywoływana. `$end$` oznacza na położenie kursora po wstawieniu fragmentu kodu.  
  
```xml  
<Literal Editable="true/false">  
   <ID>... </ID>  
   <ToolTip>... </ToolTip>  
   <Default>... </Default>  
   <Function>... </Function>  
</Literal>  
```  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Editable`|Opcjonalne `Boolean` atrybutu. Określa, czy po wstawieniu fragmentu kodu można edytować literał. Wartość domyślna tego atrybutu to `true`.|  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Domyślny element](../ide/code-snippets-schema-reference.md#default)|Element wymagany. Określa domyślną wartość literału po wstawieniu fragmentu kodu. Musi istnieć dokładnie jeden `Default` element `Literal` elementu.|  
|[Element — funkcja](../ide/code-snippets-schema-reference.md#function)|Element opcjonalny. Określa funkcję do wykonania, gdy w programie Visual Studio na literale zostanie ustawiony fokus. Może być zero lub jeden `Function` elementów w `Literal` elementu.|  
|[Identyfikator elementu](../ide/code-snippets-schema-reference.md#id)|Element wymagany. Określa unikatowy identyfikator literału. Musi istnieć dokładnie jeden `ID` element `Literal` elementu.|  
|[Etykietka narzędzia elementu](../ide/code-snippets-schema-reference.md#tooltip)|Element opcjonalny. Opisuje oczekiwaną wartość i użycie literału. Może być zero lub jeden **Tooltip** elementów w `Literal` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Deklaracje — element](../ide/code-snippets-schema-reference.md#declarations)|Zawiera literały i obiekty fragmentu kodu, które można edytować.|  
  
##  <a name="namespace"></a> Namespace — element  
 Określa przestrzeń nazw, którą należy zaimportować, aby fragment kodu został skompilowany i działał. Przestrzeń nazw określona w `Namespace` elementu jest automatycznie dodawany do `Imports` instrukcji na początku kodu, jeśli jeszcze nie istnieje.  
  
> [!NOTE]
>  `Namespace` Jest obsługiwany tylko dla projektów języka Visual Basic.  
  
```xml  
<Namespace>  
    Namespace  
</Namespace>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Import — element](../ide/code-snippets-schema-reference.md#import)|Importowanie określonej przestrzeni nazw.|  
  
 Wartość tekstowa jest wymagana. Ten tekst określa obszar nazw, wstawki zakłada jest importowany.  
  
##  <a name="object"></a> Object element  
 Definiuje obiekty fragmentu kodu, które można edytować. `Object` Element służy do identyfikowania elementu, który jest wymagany przez fragment kodu, ale może być zdefiniowana poza fragment, do samej siebie. Na przykład formanty interfejsu Windows Forms, formanty środowiska ASP.NET, wystąpienia obiektów i wystąpienia typów powinny być deklarowane jako obiekty. Deklaracje obiektu wymagają określenia typu, który wykonuje się za pomocą `Type` elementu.  
  
```xml  
<Object Editable="true/false">  
    <ID>... </ID>  
    <Type>... </Type>  
    <ToolTip>... </ToolTip>  
    <Default>... </Default>  
    <Function>... </Function>  
</Object>  
```  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Editable`|Opcjonalne `Boolean` atrybutu. Określa, czy po wstawieniu fragmentu kodu można edytować literał. Wartość domyślna tego atrybutu to `true`.|  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Domyślny element](../ide/code-snippets-schema-reference.md#default)|Element wymagany. Określa domyślną wartość literału po wstawieniu fragmentu kodu. Musi istnieć dokładnie jeden `Default` element `Literal` elementu.|  
|[Element — funkcja](../ide/code-snippets-schema-reference.md#function)|Element opcjonalny. Określa funkcję do wykonania, gdy w programie Visual Studio na literale zostanie ustawiony fokus. Może być zero lub jeden `Function` elementów w `Literal` elementu.|  
|[Identyfikator elementu](../ide/code-snippets-schema-reference.md#id)|Element wymagany. Określa unikatowy identyfikator literału. Musi istnieć dokładnie jeden `ID` element `Literal` elementu.|  
|[Etykietka narzędzia elementu](../ide/code-snippets-schema-reference.md#tooltip)|Element opcjonalny. Opisuje oczekiwaną wartość i użycie literału. Może być zero lub jeden **Tooltip** elementów w `Literal` elementu.|  
|[Typ elementu](../ide/code-snippets-schema-reference.md#type)|Element wymagany. Określa typ obiektu. Musi istnieć dokładnie jeden `Type` element `Object` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Deklaracje — element](../ide/code-snippets-schema-reference.md#declarations)|Zawiera literały i obiekty fragmentu kodu, które można edytować.|  
  
##  <a name="reference"></a> Reference — element  
 Określa informacje o odwołaniach do zestawów wymaganych przez fragment kodu. 
  
```xml  
<Reference>  
    <Assembly>... </Assembly>  
    <Url>... </Url>  
</Reference>  
```  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Assembly — element](../ide/code-snippets-schema-reference.md#assembly)|Element wymagany. Zawiera nazwę zestawu, do którego się odwołuje fragment kodu. Musi istnieć dokładnie jeden `Assembly` element `Reference` elementu.|  
|[Adres URL elementu](../ide/code-snippets-schema-reference.md#url)|Element opcjonalny. Zawiera adres URL strony z dodatkowymi informacjami o zestawie, do którego prowadzi odwołanie. Może być zero lub jeden `Url` elementów w `Reference` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Element odwołania](../ide/code-snippets-schema-reference.md#references)|Element GROUPING dla `Reference` elementów.|  
  
##  <a name="references"></a> Element odwołania  
 Poszczególne grupy `Reference` elementów.  
  
```xml  
<References>  
    <Reference>... </Reference>  
</References>  
```  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Reference — element](../ide/code-snippets-schema-reference.md#reference)|Element opcjonalny. Zawiera informacje o odwołaniach do zestawów z fragmentu kodu. Może wynosić zero lub więcej `Reference` elementów w `References` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Fragment kodu — element](../ide/code-snippets-schema-reference.md#snippet)|Zawiera odwołania, definicje importu, deklaracje i kod dla fragmentu kodu.|  
  
##  <a name="shortcut"></a> Element skrótów  
 Określa tekst skrótu służący do wstawiania fragmentu kodu. Wartość tekstu `Shortcut` element może zawierać tylko znaki alfanumeryczne, łączniki (-) i podkreślenia (_).  
  
> [!CAUTION]
>  _ i - nie są obsługiwane znaki w C++ skrótów fragmentu.  
  
```xml  
<Shortcut>  
    Shortcut Text  
</Shortcut>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header)|Zawiera ogólne informacje o fragmencie kodu.|  
  
 Wartość tekstowa jest opcjonalna. Ten tekst jest używany jako skrót do wstawiania fragmentu kodu.  
  
##  <a name="snippet"></a> Fragment kodu — element  
 Określa odwołania, definicje importu, deklaracje i kod dla fragmentu kodu.  
  
```xml  
<Snippet>  
    <References>... </References>  
    <Imports>... </Imports>  
    <Declarations>... </Declarations>  
    <Code>... </Code>  
</Snippet>    
```  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[Code element](../ide/code-snippets-schema-reference.md#code)|Element wymagany. Określa kod, który ma zostać wstawiony do pliku dokumentacji. Musi istnieć dokładnie jeden `Code` element `Snippet` elementu.|  
|[Deklaracje — element](../ide/code-snippets-schema-reference.md#declarations)|Element opcjonalny. Określa literały i obiekty tworzące sekcje fragmentu kodu, które można edytować. Może być zero lub jeden `Declarations` elementów w `Snippet` elementu.|  
|[Element importów](../ide/code-snippets-schema-reference.md#imports)|Element opcjonalny. Poszczególne grupy `Import` elementów. Może być zero lub jeden `Imports` elementów w `Snippet` elementu.|  
||Element opcjonalny. Poszczególne grupy `Reference` elementów. Może być zero lub jeden `References` elementów w `Snippet` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[CodeSnippet element](../ide/code-snippets-schema-reference.md#codesnippet)|Umożliwia określenie nagłówka oraz wielu fragmentów kodu IntelliSense, które można wstawiać do plików kodu programu Visual Studio.|  
  
##  <a name="snippettype"></a> SnippetType element  
 Określa, w jaki sposób program Visual Studio wstawia fragment kodu.  
  
```xml  
<SnippetType>  
    SurroundsWith/Expansion  
<SnippetType>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[SnippetTypes element](../ide/code-snippets-schema-reference.md#snippettypes)|Grupy `SnippetType` elementów.|  
  
 Wartość tekstowa musi być jedną z następujących:  
  
-   `SurroundsWith`: umożliwia kodu umieszczanie fragmentów kodu wokół wybranej części kodu.  
  
-   `Expansion`: umożliwia fragment kodu, który ma zostać wstawiony wskazywanej przez kursor.  
  
-   `Refactoring`: Określa, że fragment kodu jest używany podczas refaktoryzacji C#. `Refactoring` Nie można używać w wstawki kodu niestandardowego.  
  
##  <a name="snippettypes"></a> SnippetTypes element  
 Poszczególne grupy `SnippetType` elementów. Jeśli `SnippetTypes` element nie jest obecny, fragment kodu może zostać wstawiony w dowolne miejsce w kodzie.  
  
```xml  
<SnippetTypes>  
    <SnippetType>... </SnippetType>  
    <SnippetType>... </SnippetType>  
<SnippetTypes>  
```  
  
|Element podrzędny|Opis|  
|-------------------|-----------------|  
|[SnippetType element](../ide/code-snippets-schema-reference.md#snippettype)|Element opcjonalny. Określa, w jaki sposób program Visual Studio wstawia fragment kodu do kodu. Może wynosić zero lub więcej `SnippetType` elementów w `SnippetTypes` elementu.|  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header)|Określa ogólne informacje o fragmencie kodu.|  
  
##  <a name="title"></a> Tytuł elementu  
 Określa tytuł fragmentu kodu. Tytuł przechowywane w `Title` element wstawki kodu programu pojawia się w **selektor wstawek kodu** i w opisie wstawki kodu programu w **Menedżerze fragmentów kodu**.  
  
```xml  
<Title>  
    Code Snippet Title  
<Title>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Element nagłówka](../ide/code-snippets-schema-reference.md#header)|Określa ogólne informacje o fragmencie kodu.|  
  
 Wartość tekstowa jest wymagana. Tekst określa tytuł fragmentu kodu.  
  
##  <a name="tooltip"></a> Etykietka narzędzia elementu  
 Opisuje oczekiwaną wartość i użycie literału lub obiektu we fragmencie kodu. Informacje te będą wyświetlane w programie Visual Studio w etykietce narzędzia po wstawieniu fragmentu kodu do projektu. Tekst etykietki narzędzia jest wyświetlany, gdy wskaźnik myszy znajdzie się nad literałem lub obiektem.  
  
```xml  
<ToolTip>  
    ToolTip description  
</ToolTip>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Element literał](../ide/code-snippets-schema-reference.md#literal)|Definiuje pola literałów fragmentu kodu, które można edytować.|  
|[Object element](../ide/code-snippets-schema-reference.md#object)|Definiuje pola obiektów fragmentu kodu, które można edytować.|  
  
 Wartość tekstowa jest wymagana. Ten tekst określa opis etykietki narzędzia, który zostanie skojarzony z obiektem lub literałem we fragmencie kodu.  
  
##  <a name="type"></a> Typ elementu  
 Określa typ obiektu. `Object` Element służy do identyfikowania elementu, który jest wymagany przez fragment kodu, ale może być zdefiniowana poza fragment, do samej siebie. Na przykład formanty interfejsu Windows Forms, formanty środowiska ASP.NET, wystąpienia obiektów i wystąpienia typów powinny być deklarowane jako obiekty. Deklaracje obiektu wymagają określenia typu, który wykonuje się za pomocą `Type` elementu.  
  
```xml  
<Type>  
    Type  
</Type>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Object element](../ide/code-snippets-schema-reference.md#object)|Definiuje pola obiektów fragmentu kodu, które można edytować.|  
  
 Wartość tekstowa jest wymagana. Ten tekst określa typ obiektu.  
  
##  <a name="url"></a> Adres URL elementu  
 Określa adres URL strony z dodatkowymi informacjami o zestawie, do którego prowadzi odwołanie.  
  
> [!NOTE]
>  `Url` Jest obsługiwany tylko dla projektów języka Visual Basic.  
  
```xml  
<Url>  
    www.microsoft.com  
</Url>  
```  
  
|Element nadrzędny|Opis|  
|--------------------|-----------------|  
|[Reference — element](../ide/code-snippets-schema-reference.md#reference)|Określa odwołania do zestawów wymagane we fragmencie kodu.|  
  
 Wartość tekstowa jest wymagana. Ten tekst określa adres URL strony z dodatkowymi informacjami o zestawie, do którego prowadzi odwołanie. Ten adres URL jest wyświetlany, gdy do projektu nie można dodać odwołania.  
  
## <a name="see-also"></a>Zobacz także  
 [Wstawki kodu](../ide/code-snippets.md)   
 [Wskazówki: Tworzenie wstawek kodu](../ide/walkthrough-creating-a-code-snippet.md)