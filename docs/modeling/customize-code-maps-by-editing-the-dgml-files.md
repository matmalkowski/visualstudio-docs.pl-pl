---
title: Dostosowanie map kodu przez edycję plików DGML
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency graphs, creating path aliases
- dependency graphs, linking items to nodes
- graph documents, creating path aliases
- dependency graphs, grouping nodes
- graph documents, editing
- graph documents, linking items to nodes
- graph documents, customizing
- graph documentings, assigning categories and properties
- dependency graphs, editing
- dependency graphs, customizing
- graph documents, grouping nodes
- dependency graphs, assigning categories and properties
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7ee92121e57b7c3f6391d290ff0c5fde0d689e3c
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="customize-code-maps-by-editing-the-dgml-files"></a>Dostosowanie map kodu przez edycję plików DGML
Aby dostosować mapę kodu, można edytować plik skierowane Graph Markup Language (.dgml) mapy. Na przykład można edytować elementy, aby określić niestandardowe style, przypisać właściwości i kategorii elementy kodu i linki, lub Podłącz dokumenty lub adresy URL do elementów kodu lub do łącza. Aby uzyskać więcej informacji o elementach DGML, zobacz [skierowane do Graph Markup Language) dokumentacja języka (DGML](../modeling/directed-graph-markup-language-dgml-reference.md).

 Edytuj plik .dgml mapy kodu w edytorze tekstu lub edytora XML. Jeśli tablica jest częścią rozwiązania Visual Studio, wybierz go w **Eksploratora rozwiązań**, otwórz menu skrótów i wybierz **Otwórz za pomocą**, **edytora XML (tekst)**.

> [!NOTE]
>  Aby utworzyć mapy kodu, musi mieć Visual Studio Enterprise. Podczas edytowania mapy kodu w programie Visual Studio go czyści wszystkie nieużywane DGML elementów i atrybutów, usuwając je podczas zapisywania pliku .dgml. Tworzy również elementy kodu automatycznie po dodaniu ręcznie nowe łącza. Podczas zapisywania pliku .dgml wszelkie atrybuty, które są dodawane do elementu, mogą się ponownie rozmieszczać w kolejności alfabetycznej.

##  <a name="OrganizeNodes"></a> Elementy kodu grupy
 Można dodawać nowych grup lub przekonwertować istniejące węzły w grupie.

1.  Otwórz plik .dgml w edytorze tekstu lub edytora XML.

2.  Aby dokonać konwersji elementu kodu do grupy, należy znaleźć `<Node/>` element dla tego elementu kodu.

     \- lub -

     Aby dodać nową grupę, Znajdź `<Nodes>` sekcji. Dodaj nową `<Node/>` elementu.

3.  W `<Node/>` elementu, Dodaj `Group` atrybutu, aby określić, czy grupa zostanie wyświetlona rozwinięte lub zwinięte. Na przykład:

    ```xml
    <Nodes>
       <Node Id="MyFirstGroup" Group="Expanded" />
       <Node Id="MySecondGroup" Group="Collapsed" />
    </Nodes>
    ```

4.  W `<Links>` sekcji, upewnij się, że `<Link/>` element, który ma następujące atrybuty istnieje dla każdej relacji między element kodu grupy i jego elementy potomne kodu:

    -   A `Source` atrybut, który określa element kodu grupy

    -   A `Target` atrybut, który określa element podrzędny kodu

    -   A `Category` atrybut, który określa `Contains` relacji między elementem kodu grupy i jej podrzędne elementu kodu

     Na przykład:

    ```xml
    <Links>
       <Link Category="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildOne" />
       <Link Category ="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildTwo" />
       <Link Category ="Contains" Source="MySecondNewGroup" Target="SecondGroupChildOne" />
       <Link Category="Contains" Source="MySecondNewGroup" Target="SecondGroupChildTwo" />
    </Links>
    ```

     Aby uzyskać więcej informacji na temat `Category` atrybutów, zobacz [przypisać kategorie elementy kodu i linki](#AssignCategories).

##  <a name="ChangeGraphStyle"></a> Zmień styl mapy
 Kolor tła i kolor obramowania mapy można zmienić, edytując plik .dgml mapy. Aby zmienić styl elementy kodu i łączy, zobacz [Zmień styl elementy kodu i linki](#Highlight).

1.  Otwórz plik .dgml w edytorze tekstu lub edytora XML.

2.  W `<DirectedGraph>` elementu, Dodaj dowolny z następujących atrybutów, aby zmienić jego styl:

     Kolor tła

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     Kolor obramowania

    ```xml
    Stroke="StrokeValue"
    ```

     Na przykład:

    ```xml
    <DirectedGraph Background="Green" xmlns="http://schemas.microsoft.com/vs/2009/dgml" >
       ...
       ...
    </DirectedGraph>
    ```

##  <a name="Highlight"></a> Zmień styl elementy kodu i łączy

###  <a name="CreateCustomStyles"></a>
 Niestandardowe style można stosować do następujących elementów kodu:

-   Elementy jednego kodu i linki

-   Grupy elementów kodu i linki

-   Grupy elementów kodu i linki na podstawie określonych warunków

> [!TIP]
>  Jeśli masz powtarzające się style przez wiele elementów kodu lub łącza, można rozważyć zastosowanie kategorii te elementy kodu lub łącza, a następnie zastosować styl do tej kategorii. Aby uzyskać więcej informacji, zobacz [Przypisz kategorie, aby elementy kodu i linki](#AssignCategories) i [przypisać właściwości elementy kodu i linki](#AssignProperties).

##### <a name="to-apply-a-custom-style-to-a-single-code-element"></a>Aby zastosować styl niestandardowy element pojedynczy kod

1.  Otwórz plik .dgml w edytorze tekstu lub edytora XML.

2.  Znajdź element kodu `<Node/>` elementu. Dodaj te atrybuty, aby dostosować styl jego:

     Kolor tła

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     Kontur

    ```xml
    Stroke="ColorNameOrHexadecimalValue"
    ```

     Grubość konturu

    ```xml
    StrokeThickness="StrokeValue"
    ```

     Kolor tekstu

    ```xml
    Foreground="ColorNameOrHexadecimalValue"
    ```

     Ikona

    ```xml
    Icon="IconFilePathLocation"
    ```

     Rozmiar tekstu

    ```xml
    FontSize="FontSizeValue"
    ```

     Typ tekstu

    ```xml
    FontFamily="FontFamilyName"
    ```

     Waga tekstu

    ```xml
    FontWeight="FontWeightValue"
    ```

     Styl tekstu

    ```xml
    FontStyle="FontStyleName"
    ```

     Na przykład można określić `Italic` jako styl tekstu.

     Tekstura

    ```xml
    Style="Glass"
    ```

     - lub -

    ```xml
    Style="Plain"
    ```

     Kształt

     Aby zastąpić kształt ikony, ustaw `Shape` właściwości `None` i ustaw `Icon` właściwości do ścieżki pliku ikony.

    ```xml
    Shape="ShapeFilePathLocation"
    ```

     Na przykład:

    ```xml
    <Nodes>
       <Node Id="MyNode" Background="#FF008000" Stroke="#FF000000"
       Foreground="#FFFFFFFF" Icon="...\Icons\Globe.png"/>
    </Nodes>
    ```

##### <a name="to-apply-a-custom-style-to-a-single-link"></a>Aby zastosować styl niestandardowy do pojedynczego łącza

1.  Otwórz plik .dgml w edytorze tekstu lub edytora XML.

2.  Znajdź `<Link/>` element, który zawiera nazwy elementu kodu źródłowego i docelowego elementu kodu.

3.  W `<Link/>` elementu, Dodaj dowolny z następujących atrybutów, aby dostosować styl jego:

     Kolor konturu i grotu strzałki

    ```xml
    Stroke="ColorNameOrHexadecimalValue"
    ```

     Grubość konturu

    ```xml
    StrokeThickness="StrokeValue"
    ```

     Styl konturu

    ```xml
    StrokeDashArray="StrokeArrayValues"
    ```

     Na przykład:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Background="Green" Stroke="#FF000000" StrokeDashArray="2,2"/>
    </Links>
    ```

##### <a name="to-apply-custom-styles-to-a-group-of-code-elements-or-links"></a>Aby zastosować style niestandardowe do grupy elementy kodu lub łącza

1.  Otwórz plik .dgml w edytorze tekstu lub edytora XML.

2.  Jeśli `<Styles></Styles>` element nie istnieje, dodaj je w obszarze `<DirectedGraph></DirectedGraph>` elementu po `<Links></Links>` elementu.

3.  W `<Styles></Styles>` elementu w obszarze `<Style/>` element i określ następujące atrybuty:

    -   `TargetType="Node` &#124; `Link | Graph"`

    -   `GroupLabel="` *NameInLegendBox* `"`

    -   `ValueLabel="` *NameInStylePickerBox* `"`

     Aby zastosować niestandardowy styl do wszystkich typów docelowych, nie należy używać warunku.

##### <a name="to-apply-a-conditional-style-to-groups-of-code-elements-or-links"></a>Aby zastosować styl warunkowy do grup elementów kodu lub łącza

1.  Otwórz plik .dgml w edytorze tekstu lub edytora XML.

2.  W `<Style/>` elementu, Dodaj `<Condition/>` element, który zawiera `Expression` atrybutu, aby określić wyrażenie zwracające wartość logiczną.

     Na przykład:

    ```xml
    <Condition Expression="MyCategory"/>
    ```

     - lub -

    ```xml
    <Condition Expression="MyCategory > 100"/>
    ```

     - lub -

    ```xml
    <Condition Expression="HasCategory('MyCategory')"/>
    ```

     Wyrażenie to używa następującej składni notacji Backusa-Naura (BNF):

     <Expression> ::= <BinaryExpression> &#124; <UnaryExpression> &#124; "("<Expression>")" &#124; <MemberBindings> &#124; <Literal> &#124; <Number>

     <BinaryExpression> ::= <Expression> <Operator> <Expression>

     <UnaryExpression> ::= "!" <Expression> &#124; "+" <Expression> &#124; "-" <Expression>

     <Operator> :: = "<" &#124; "\<=" &#124; "=" &#124; "> =" &#124; ">" &#124; "! =" &#124; "lub" &#124; "i" &#124; "+" &#124; "*" &#124; "/" &#124; "-"

     <MemberBindings> ::= <MemberBindings> &#124; <MemberBinding> "." <MemberBinding>

     <MemberBinding> ::= <MethodCall> &#124; <PropertyGet>

     <MethodCall> ::= <Identifier> "(" <MethodArgs> ")"

     <PropertyGet> :: = Identyfikator

     <MethodArgs> ::= <Expression> &#124; <Expression> "," <MethodArgs> &#124; <empty>

     <Identifier> ::= [^. ]*

     <Literal> :: = pojedynczych lub podwójnych cudzysłowach literału ciągu znaków

     <Number> :: = ciąg cyfr z opcjonalnym separatorem dziesiętnym

     Można określić wiele `<Condition/>` elementów, które muszą być spełnione, aby zastosować styl wszystkie.

3.  W następnym wierszu po `<Condition/>` elementu, Dodaj jeden lub wiele `<Setter/>` elementy, aby określić `Property` atrybut i stałym `Value` atrybutu lub obliczanej `Expression` atrybut do zastosowania do mapy, elementy kodu lub linki, które spełniają warunek.

     Na przykład:

    ```xml
    <Setter Property="BackGround" Value="Green"/>
    ```

 Jako proste pełny przykład, następujący warunek określa, że element kodu zostanie wyświetlony zielony lub czerwony na podstawie jego `Passed` kategoria jest ustawiona na `True` lub `False`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
   <Nodes>
      <Node Id="MyFirstNode" Passed="True" />
      <Node Id="MySecondNode" Passed="False" />
   </Nodes>
   <Links>
   </Links>
   <Styles>
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="True">
         <Condition Expression="Passed='True'"/>
         <Setter Property="Background" Value="Green"/>
      </Style>
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="False">
         <Condition Expression="Passed='False'"/>
         <Setter Property="Background" Value="Red"/>
      </Style>
   </Styles>
</DirectedGraph>
```

 Poniższa tabela zawiera niektóre przykładowe warunki, których można użyć:

 Ustaw rozmiar czcionki w zależności od liczby wierszy kodu, który również zmienia rozmiar elementu kodu. W tym przykładzie używane pojedyncze wyrażenie warunkowe do ustawiania wielu właściwości `FontSize` i `FontFamily`.

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Class1" LinesOfCode ="200" />
   <Node Id="Class2" LinesOfCode ="1000" />
   <Node Id="Class3" LinesOfCode ="20" />
</Nodes>
<Properties>
   <Property Id="LinesOfCode" Label="LinesOfCode" Description="LinesOfCode" DataType="System.Int32" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="LinesOfCode" ValueLabel="Function">
      <Condition Expression="LinesOfCode > 0" />
      <Setter Property="FontSize" Expression="Math.Max(9,Math.Sqrt(LinesOfCode))" />
      <Setter Property="FontFamily" Value="Papyrus" />
   </Style>
</Styles>
</DirectedGraph>
```

 Kolor tła elementu kodu na podstawie `Coverage` właściwości. Style są oceniane w kolejności, podobnie jak `if-else` instrukcje.

 W tym przykładzie:

1.  Jeśli `Coverage` jest > 80, a następnie ustaw `Background` właściwości zielony.

2.  Else if `Coverage` > 50, a następnie ustaw `Background` właściwości odcień pomarańczowy na podstawie wartości z `Coverage` właściwości.

3.  Ustaw w przeciwnym razie `Background` właściwości odcień czerwony na podstawie wartości z `Coverage` właściwości.

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Class1" Coverage="58" />
   <Node Id="Class2" Coverage="95" />
   <Node Id="Class3" Coverage="32" />
</Nodes>
<Properties>
   <Property Id="Coverage" Label="Coverage" Description="Code coverage as a percentage of blocks" DataType="Double" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Good">
      <Condition Expression="Coverage > 80" />
      <Setter Property="Background" Value="Green" />
   </Style>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="OK">
      <Condition Expression="Coverage > 50" />
      <Setter Property="Background" Expression="Color.FromRgb(180 * Math.Max(1, (80 - Coverage) / 30), 180, 0)" />
   </Style>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Bad">
      <Setter Property="Background" Expression="Color.FromRgb(180, 180 * Coverage / 50, 0)" />
   </Style>
</Styles>
</DirectedGraph>
```

 Ustaw `Shape` właściwości `None` tak, aby ikony zastępuje kształtu. Użyj `Icon` właściwości w celu określenia lokalizacji ikony.

```xml
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Automation" Category="Test" Label="Automation" />
   <Node Id="C# Provider" Category="Provider" Label="C# Provider" />
</Nodes>
<Categories>
   <Category Id="Provider" Icon="...\Icons\Module.png" Shape="None" />
   <Category Id="Test" Icon="...\Icons\Page.png" Shape="None" />
</Categories>
<Properties>
   <Property Id="Icon" DataType="System.String" />
   <Property Id="Label" Label="Label" Description="Displayable label of an Annotatable object" DataType="System.String" />
   <Property Id="Shape" DataType="System.String" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="Group" ValueLabel="Has category">
      <Condition Expression="HasCategory('Group')" />
      <Setter Property="Background" Value="#80008080" />
   </Style>
   <Style TargetType="Node">
      <Setter Property="HorizontalAlignment" Value="Center" />
   </Style>
</Styles>
</DirectedGraph>
```

##  <a name="AssignProperties"></a> Przypisz właściwości elementy kodu i linki
 Przez przypisanie właściwości można organizować elementy kodu i linki. Na przykład można wybrać elementy kodu, które mają określone właściwości, aby grupować, zmień ich styl lub je ukryć.

#### <a name="to-assign-a-property-to-a-code-element"></a>Aby przypisać właściwości do elementu kodu

1.  Otwórz plik .dgml w edytorze tekstu lub edytora XML.

2.  Znajdź `<Node/>` element dla tego elementu kodu. Określ nazwę właściwości i jej wartość. Na przykład:

    ```xml
    <Nodes>
       <Node Id="MyNode" MyPropertyName="PropertyValue" />
    </Nodes>
    ```

3.  Dodaj `<Property/>` elementu `<Properties>` sekcji, aby określić atrybuty, takie jak jego widoczne nazwę i typ danych:

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property" DataType="System.DataType"/>
    </Properties>
    ```

#### <a name="to-assign-a-property-to-a-link"></a>Aby przypisać właściwość do łącza

1.  Otwórz plik .dgml w edytorze tekstu lub edytora XML.

2.  Znajdź `<Link/>` element, który zawiera nazwy elementu kodu źródłowego i docelowego elementu kodu.

3.  W `<Node/>` elementu, określ nazwę właściwości i jej wartość. Na przykład:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" MyPropertyName="PropertyValue" />
    </Links>
    ```

4.  Dodaj `<Property/>` elementu `<Properties>` sekcji, aby określić atrybuty, takie jak jego widoczne nazwę i typ danych:

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property Name" DataType="System.DataType"/>
    </Properties>
    ```

##  <a name="AssignCategories"></a> Przypisz kategorie, aby elementy kodu i linki
 Poniższe sekcje pokazują, jak można organizować elementy kodu przez przypisanie kategorii i w jaki sposób można utworzyć hierarchiczne kategorie, które ułatwiają organizowanie elementów kodu i dodać atrybuty do kategorii podrzędnych za pomocą dziedziczenia.

#### <a name="to-assign-a-category-to-a-code-element"></a>Przypisywanie kategorii do elementu kodu

-   Otwórz plik .dgml w edytorze tekstu lub edytora XML.

-   Znajdź `<Node/>` elementu dla elementu kodu, który ma.

-   W `<Node/>` elementu, Dodaj `Category` atrybutu, aby określić nazwę kategorii. Na przykład:

    ```xml
    <Nodes>
       <Node Id="MyNode" Category="MyCategory" />
    </Nodes>
    ```

     Dodaj `<Category/>` elementu `<Categories>` sekcji, aby mogli używać `Label` atrybutu określ tekst wyświetlany w tej kategorii:

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-assign-a-category-to-a-link"></a>Przypisywanie kategorii do łącza

1.  Otwórz plik .dgml w edytorze tekstu lub edytora XML.

2.  Znajdź `<Link/>` element, który zawiera nazwy elementu kodu źródłowego i docelowego elementu kodu.

3.  W `<Link/>` elementu, Dodaj `Category` atrybutu, aby określić nazwę kategorii. Na przykład:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Category="MyCategory"
    </Links>
    ```

4.  Dodaj `<Category/>` elementu `<Categories>` sekcji, aby mogli używać `Label` atrybutu określ tekst wyświetlany w tej kategorii:

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-create-hierarchical-categories"></a>Tworzenie kategorii hierarchicznych

1.  Otwórz plik .dgml w edytorze tekstu lub edytora XML.

2.  Dodaj `<Category/>` elementu dla kategorii nadrzędnej, a następnie dodaj `BasedOn` atrybutu kategorii podrzędnych `<Category/>` elementu.

     Na przykład:

    ```xml
    <Nodes>
       <Node Id="MyFirstNode" Label="My First Node" Category= "MyCategory" />
       <Node Id="MySecondNode" Label="My Second Node" />
    </Nodes>
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" />
    </Links>
    <Categories>
       <Category Id="MyCategory" Label="My Category" BasedOn="MyParentCategory"/>
       <Category Id="MyParentCategory" Label="My Parent Category" Background="Green"/>
    </Categories>
    ```

     W tym przykładzie tła `MyFirstNode` jest zielony ponieważ jego `Category` dziedziczy atrybut `Background` atrybutu `MyParentCategory`.

##  <a name="AddReferences"></a> Połącz dokumenty lub adresy URL do elementów kodu i linki
 Możesz połączyć dokumentów lub adresy URL elementy kodu lub łącza edycji pliku .dgml mapy i dodając `Reference` atrybutu `<Node/>` elementu element kodu lub `<Link/>` elementu dla łącza. Można otworzyć i wyświetlić tej zawartości z elementu kodu lub łącza. `Reference` Atrybut określa ścieżkę do tej zawartości. Może to być ścieżka względem lokalizacji pliku .dgml lub ścieżka bezwzględna.

> [!CAUTION]
>  Jeśli używane są ścieżki względne, a plik .dgml zostanie przeniesiony do innej lokalizacji, ścieżki te nie zostaną rozpoznane. Podczas próby otwarcia i wyświetlenia połączonej zawartości pojawi się komunikat o błędzie z informacją, że nie można wyświetlić zawartości.

 Na przykład można połączyć następujące elementy kodu:

-   Do opisania zmian do klasy, można połączyć adresu URL elementu kodu pracy, dokumentu lub innego pliku .dgml do elementu kodu dla klasy.

-   Diagram zależności można połączyć elementu kodu grupy, który reprezentuje warstwę architektura logiczna oprogramowania.

-   Aby wyświetlić więcej informacji na temat składników, która uwidacznia interfejs, można połączyć diagram składnika do elementu kodu dla tego interfejsu.

-   Element kodu połączyć elementu roboczego Team Foundation Server lub usterki lub inne informacje dotyczące elementu kodu.

#### <a name="to-link-a-document-or-url-to-a-code-element"></a>Aby utworzyć łącze dokumentu lub adresu URL do elementu kodu

1.  Otwórz plik .dgml w edytorze tekstu lub edytora XML.

2.  Znajdź `<Node/>` elementu dla elementu kodu, który ma.

3.  Wykonaj jedno z zadań z tabeli poniżej:

     Element jednego kodu

    -   W `<Node/>` lub `<Link/>` elementu, Dodaj `Reference` atrybutu, aby określić lokalizację elementu kodu.

        > [!NOTE]
        >  Może mieć tylko jeden `Reference` atrybutu dla każdego elementu.

     Na przykład:

    ```xml
    <Nodes>
       <Node Id="MyNode" Reference="MyDocument.txt" />
    </Nodes>
    <Properties>
       <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
    </Properties>
    ```

     Wiele elementów kodu

    1.  W `<Node/>` lub `<Link/>` elementu, Dodaj nowy atrybut do określenia lokalizacji każdego odwołania.

    2.  W `<Properties>` sekcji:

        1.  Dodaj `<Property/>` elementu dla każdego nowego typu odwołania.

        2.  Ustaw `Id` atrybutu na nazwę nowego atrybutu odwołania.

        3.  Dodaj `IsReference` atrybutu i ustaw ją na `True` do utworzenia odwołania są wyświetlane na element kodu **przejdź do odwołania** menu skrótów.

        4.  Użyj `Label` Określ tekst wyświetlany w elemencie kod dla atrybutu **przejdź do odwołania** menu skrótów.

     Na przykład:

    ```xml
    <Nodes>
       <Node Id="MyNode" SequenceDiagram="MySequenceDiagram.sequencediagram" ActiveBugs="MyActiveBugs.wiq"/>
    </Nodes>
    <Properties>
       <Property Id="SequenceDiagram" Label="My Sequence Diagram" DataType="System.String" IsReference="True" />
       <Property Id="ActiveBugs" Label="Active Bugs" DataType="System.String" IsReference="True" />
    </Properties>
    ```

     Na mapie nazwa elementu kodu pojawi się podkreślony. Po otwarciu menu skrótów dla elementu kodu lub link, zostanie wyświetlony **przejdź do odwołania** menu skrótów, które zawiera elementy połączone kodu do wyboru.

4.  Użyj `ReferenceTemplate` atrybutu na określenie ciągu wspólne, takie jak adres URL, który jest używany przez wiele odwołań zamiast powtarzające się tego ciągu w adresie.

     `ReferenceTemplate` Atrybut Określa symbol zastępczy wartości odwołania. W poniższym przykładzie `{0}` symbol zastępczy w `ReferenceTemplate` atrybutu zostaną zastąpione wartościami `MyFirstReference` i `MySecondReference` atrybutów w `<Node/>` elementem Pełna ścieżka:

    ```xml
    <Nodes>
       <Node Id="MyNode" MyFirstReference="MyFirstDocument" MySecondReference="MySecondDocument"/>
       <Node Id="MySecondNode" MyFirstReference="AnotherFirstDocument" MySecondReference="AnotherSecondDocument"/>
    </Nodes>
    <Properties>
       <Property Id="MyFirstReference" Label="My First Document" DataType="System.String" IsReference="True" ReferenceTemplate="http://www.Fabrikam.com/FirstDocuments/{0}.asp"/>
       <Property Id="MySecondReference" Label="My Second Document" DataType="System.String" IsReference="True" ReferenceTemplate=" http://www.Fabrikam.com/SecondDocuments/{0}.asp"/>
    </Properties>
    ```

5.  Aby wyświetlić kod przywoływany element lub elementy kodu z mapy, otwórz menu skrótów dla elementu kodu lub łącze. Wybierz **przejdź do odwołania** , a następnie elementu kodu.

## <a name="see-also"></a>Zobacz też

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)
- [Dokumentacja języka DGML (Directed Graph Markup Language)](../modeling/directed-graph-markup-language-dgml-reference.md)
