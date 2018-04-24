---
title: Dokumentacja języka DGML (Directed Graph Markup Language)
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: a792c643a19f4aa54d16b73c5fb9c39a22767414
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="directed-graph-markup-language-dgml-reference"></a>Dokumentacja języka DGML (Directed Graph Markup Language)

Kierowane Graph Markup Language (DGML) opisano informacje używane do wizualizacji i wykonywać analizy złożoność i jest używany format, aby utrwalić map kodu w programie Visual Studio. Używa XML proste do opisania zarówno cykliczne, jak i acykliczne wykresy ukierunkowanej. Wykres kierowany jest zestawem węzłów połączonych przez łącza lub krawędzie. Węzły i łącza mogą być używane do reprezentacji struktur sieciowych, takich jak elementy projektu oprogramowania.

Należy pamiętać, że niektóre wersje programu Visual Studio obsługują tylko podzestaw możliwości DGML, zobacz [obsługę wersji architektura i modelowanie narzędzia](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Podczas edycji pliku .dgml technologia IntelliSense pomaga identyfikować atrybuty, które są dostępne dla każdego elementu i ich wartości. Aby określić kolor w atrybucie, użyj nazw dla pospolitych kolorów, takich jak „Niebieski” lub wartości szesnastkowych ARGB, takich jak „#ffa0b1c3”. DGML używa małego podzbioru formatów definicji koloru Windows Presentation Foundation (WPF). Aby uzyskać więcej informacji, zobacz [klasy kolory](http://go.microsoft.com/fwlink/?LinkId=182345).

##  <a name="DGML"></a> Składnia DGML

W poniższej tabeli opisano typy elementów, które są używane w DGML:

-   `<DirectedGraph></DirectedGraph>`

     Ten element jest elementem głównym dokumentu (.dgml) mapy kodu. Wszystkie inne elementy DGML pojawiają się w zakresie tego elementu.

     Na poniższej liście opisano opcjonalne atrybuty, które mogą obejmować:

     `Background` -Kolor tła mapy

     `BackgroundImage` -Lokalizacja pliku obrazu do użycia jako tło w formie mapy.

     `GraphDirection` — Jeśli mapy jest równa układu drzewa (`Sugiyama`), Rozmieść węzłów, dzięki czemu większość łącza przepływu w określonym kierunku: `TopToBottom`, `BottomToTop`, `LeftToRight`, lub `RightToLeft`. Zobacz [zmiany układu mapy](../modeling/browse-and-rearrange-code-maps.md#Selecting).

     `Layout` -Ustawienia mapy następujących układów: `None`, `Sugiyama` (drzewa układ), `ForceDirected` (szybkie klastry) lub `DependencyMatrix`. Zobacz [zmiany układu mapy](../modeling/browse-and-rearrange-code-maps.md#Selecting).

     `NeighborhoodDistance` -Gdy mapy ustawiono układ drzewa lub układ szybkie klastry, wyświetlenie tylko tych węzłów, które są przez określoną liczbę (1-7) łącza od wybranych węzłów. Zobacz [zmiany układu mapy](../modeling/browse-and-rearrange-code-maps.md#Selecting).

     Przykład:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <DirectedGraph Title="DrivingTest" Background="Blue" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
       <Nodes>
          ...
       </Nodes>
       <Links>
          ...
       </Links>
       <Categories>
          ...
       </Categories>
       <Properties>
          ...
       </Properties>
    </DirectedGraph>
    ```

-   `<Nodes></Nodes>`

     Ten opcjonalny element zawiera listę `<Node/>` elementów, które definiują węzły na mapie. Aby uzyskać więcej informacji, zobacz `<Node/>` elementu.

    > [!NOTE]
    > Podczas odwoływania się niezdefiniowane węzła w `<Link/>` tworzy mapę elementu `<Node/>` elementu automatycznie.

     Przykład:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
       <Nodes>
          <Node ... />
       </Nodes>
       <Links>
          <Link ... />
       </Links>
    </DirectedGraph>
    ```

-   `<Node/>`

     Element ten określa pojedynczy węzeł. Wygląda na to, w ramach `<Nodes><Nodes/>` elementu listy.

     Element ten musi zawierać następujące atrybuty:

     `Id` — Unikatowa nazwa węzła i wartość domyślną `Label` atrybut, jeśli nie oddzielne `Label` jest określony atrybut. Ta nazwa musi być zgodna `Source` lub `Target` atrybut łącza, która odwołuje się on.

     Na poniższej liście opisano niektóre z opcjonalnych atrybutów, z których można skorzystać:

     `Label` — Nazwa wyświetlana węzła.

     Atrybuty stylu. Zobacz [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

     `Category` -Nazwa kategorii, który identyfikuje elementy, które współużytkują ten atrybut. Aby uzyskać więcej informacji, zobacz `<Category/>` elementu.

     `Property` -Nazwa właściwości, która identyfikuje elementów, które mają taką samą wartość właściwości. Aby uzyskać więcej informacji, zobacz `<Property/>` elementu.

     `Group` — Jeśli węzeł zawiera inne węzły, ustaw ten atrybut `Expanded` lub `Collapsed` aby pokazać lub ukryć jego zawartość. Musi istnieć `<Link/>` element, który zawiera `Category="Contains"` atrybutu i określa węzła nadrzędnego jako węzeł źródłowy i podrzędnym jako węzeł docelowy. Zobacz [grupować elementy kodu](../modeling/customize-code-maps-by-editing-the-dgml-files.md#OrganizeNodes).

     `Visibility` -Ustawioną wartość tego atrybutu `Visible`, `Hidden`, lub `Collapsed`. Używa `System.Windows.Visibility`. Zobacz [Ukryj lub Pokaż węzły i linki](../modeling/browse-and-rearrange-code-maps.md#HidingShowing).

     `Reference` — Wartość tego atrybutu, aby utworzyć łącze do dokumentu lub adresu URL. Zobacz [dokumenty lub połączyć adresy URL elementy kodu i linki](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AddReferences).

     Przykład:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
       <Nodes>
          <Node Id="Driver" Label="Student" Category="Person" />
          <Node Id="Passenger" Label="Instructor" Category="Person" />
          <Node Id="Car" Label="Car" Category="Automobile" />
          <Node Id="Truck" Label="Truck" Category="Automobile" />
       </Nodes>
       <Links>
          <Link ... />
       </Links>
       <Categories>
          <Category Id="Person" Background="Orange" />
          <Category Id="Automobile" Background="Yellow"/>
       </Categories>
    </DirectedGraph>
    ```

-   `<Links></Links>`

     Ten element zawiera listę `<Link>` elementów, które definiują łącza między węzłami. Aby uzyskać więcej informacji, zobacz `<Link/>` elementu.

     Przykład:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
       <Links>
          <Link ... />
       </Links>
    </DirectedGraph>
    ```

-   `<Link/>`

     Element ten określa pojedyncze łącze, które łączy węzeł źródłowy z węzłem docelowym. Wygląda na to, w ramach `<Links></Links>` elementu listy.

    > [!NOTE]
    > Jeśli węzłem Niezdefiniowany odwołuje się do tego elementu, dokumentu mapy automatycznie tworzy węzeł, który ma określone atrybuty, jeśli istnieje.

     Element ten musi zawierać następujące atrybuty:

     `Source` -Węzeł źródłowy łącza

     `Target` -Węzeł docelowy łącza

     Na poniższej liście opisano niektóre z opcjonalnych atrybutów, z których można skorzystać:

     `Label` -Nazwę wyświetlaną łącza

     Atrybuty stylu. Zobacz [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

     `Category` -Nazwa kategorii, który identyfikuje elementy, które współużytkują ten atrybut. Aby uzyskać więcej informacji, zobacz `<Category/>` elementu.

     `Property` -Nazwa właściwości, która identyfikuje elementów, które mają taką samą wartość właściwości. Aby uzyskać więcej informacji, zobacz `<Property/>` elementu.

     Przykład:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
       <Nodes>
          <Node Id="Driver" Label="Student" Category="Person" />
          <Node Id="Passenger" Label="Instructor" Category="Person" />
          <Node Id="Car" Label="Car" Category="Automobile" />
          <Node Id="Truck" Label="Truck" Category="Automobile" />
       </Nodes>
       <Links>
          <Category Id="Person" Background="Orange" />
          <Category Id="Automobile" Background="Yellow"/>
          <Link Source="Driver" Target="Car" Label="Passed" Stroke="Black" Background="Green" Category="PassedTest" />
          <Link Source="Driver" Target="Truck" Label="Failed" Stroke="Black" Background="Red" Category="PassedTest" />
       </Links>
    </DirectedGraph>
    ```

-   `<Categories></Categories>`

     Ten element zawiera listę `<Category/>` elementów. Aby uzyskać więcej informacji, zobacz `<Category/>` elementu.

     Przykład:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
       <Categories>
           <Category ... />
       </Categories>
    </DirectedGraph>
    ```

-   `<Category/>`

     Ten element definiuje `Category` atrybut, który służy do identyfikowania elementy, które współużytkują ten atrybut. A `Category` atrybut może służyć do organizowania elementów mapy, podaj atrybuty udostępnione przez dziedziczenie lub zdefiniować dodatkowe metadane.

     Element ten musi zawierać następujące atrybuty:

     `Id` — Unikatowa nazwa kategorii i wartość domyślną `Label` atrybut, jeśli nie oddzielne `Label` jest określony atrybut.

     Na poniższej liście opisano niektóre z opcjonalnych atrybutów, z których można skorzystać:

     `Label` — Przyjazne czytnika nazwę kategorii.

     `BasedOn` Kategoria nadrzędna, z którego `<Category/>` bieżącego elementu dziedziczy.

     W tym przykładzie dla tego elementu `FailedTest` dziedziczy kategorii jego `Stroke` atrybutu z `PassedTest` kategorii. Zobacz sekcję "Aby utworzyć hierarchiczne kategorie" w [mapy Dostosuj kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

     Kategorie zapewniają również zachowanie niektóre podstawowe szablonu steruje wyglądem węzły i łącza, gdy zostaną one wyświetlone na mapie. Zobacz [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

     Przykład:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
       <Nodes>
          <Node Id="Driver" Label="Driver" Category="Person" />
          <Node Id="Car" Label="Car" Category="Automobile" />
          <Node Id="Truck" Label="Truck" Category="Automobile" />
          <Node Id="Passenger" Category="Person" />
       </Nodes>
       <Links>
          <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
          <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
       </Links>
       <Categories>
          <Category Id="Person" Background="Orange" />
          <Category Id="Automobile" Background="Yellow"/>
          <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
          <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
       </Categories>
    </DirectedGraph>
    ```

-   `<Properties></Properties>`

     Ten element zawiera listę `<Property/>` elementów. Aby uzyskać więcej informacji, zobacz `<Property/>` elementu.

     Przykład:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
       <Properties>
           <Property ... />
       </Properties>
    </DirectedGraph>
    ```

-   `<Property/>`

     Ten element definiuje `Property` atrybut, który można przypisać wartości do dowolnego DGML elementu lub atrybutu, łącznie z kategorii i inne właściwości.

     Element ten musi zawierać następujące atrybuty:

    -   `Id` -Unikatową nazwę właściwości i wartość domyślną `Label` atrybut, jeśli nie oddzielne `Label` jest określony atrybut.

    -   `DataType` — Typ danych przechowywanych we właściwości

     Jeśli chcesz, aby właściwość pojawią się w **właściwości** okna, użyj `Label` właściwości w celu określenia nazwy wyświetlanej właściwości.

     Zobacz [przypisać kategorie elementy kodu i linki](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AssignCategories).

     Przykład:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
       <Nodes>
          <Node Id="Driver" Label="Driver" Category="Person" DrivingAge="18"/>
          <Node Id="Car" Label="Car" Category="Automobile" />
          <Node Id="Truck" Label="Truck" Category="Automobile" />
          <Node Id="Passenger" Category="Person" />
       </Nodes>
       <Links>
          <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
          <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
       </Links>
       <Categories>
          <Category Id="Person" Background="Orange" />
          <Category Id="Automobile" Background="Yellow"/>
          <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
          <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
       </Categories>
       <Properties>
           <Property Id="DrivingAge" Label="Driving Age" DataType="System.Int32" />
       </Properties>
    </DirectedGraph>
    ```

###  <a name="AddAlias"></a> Aliasy dla często używanych ścieżek

Zamienianie najczęściej używanych ścieżek na aliasy pomaga zredukować rozmiar pliku .dgml i czas wymagany do załadowania lub zapisania pliku. Aby utworzyć alias, Dodaj `<Paths></Paths>` sekcji na końcu pliku .dgml. W tej sekcji należy dodać `<Path/>` element do definiowania aliasu dla ścieżki:

```xml
<Paths>
   <Path Id="MyPathAlias" Value="C:\...\..." />
</Paths>
```

Aby odwołać alias z elementu w pliku .dgml, ujmij `Id` z \<ścieżki / > element o dolara ($) i nawiasów (()):

```xml
<Nodes>
   <Node Id="MyNode" Reference="$(MyPathAlias)MyDocument.txt" />
</Nodes>
<Properties>
   <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
</Properties>
```

## <a name="see-also"></a>Zobacz też

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)