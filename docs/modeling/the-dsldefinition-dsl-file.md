---
title: Plik DslDefinition.dsl
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8ca4046bdc6c6ee59dae223dd5f2dc5d354aab3a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31954414"
---
# <a name="the-dsldefinitiondsl-file"></a>Plik DslDefinition.dsl

W tym temacie opisano strukturę pliku DslDefinition.dsl w projekcie Dsl [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] rozwiązania, które definiuje *języka specyficznego dla domeny*. Plik DslDefinition.dsl opisano klasy i relacje języka specyficznego dla domeny, wraz z diagramu, kształtów, łączniki, format serializacji i **przybornika** języka specyficznego dla domeny i jego narzędzia do edycji. W rozwiązaniu języka specyficznego dla domeny kod, który definiuje te narzędzia jest generowany zgodnie z informacjami w pliku DslDefinition.dsl.

Ogólnie rzecz biorąc, użyj *projektanta języka specyficznego dla domeny* na edycję pliku DslDefinition.dsl. Jednak jego raw formularz jest XML i możesz otworzyć plik DslDefinition.dsl w edytorze XML. Może być przydatna zrozumienie, jakie informacje zawiera plik i sposób organizacji do celów debugowania i rozszerzenia.

Przykłady w tym temacie są pobierane z diagramu składników szablon rozwiązania. Aby zapoznać się przykładem, tworzenie rozwiązań języka specyficznego dla domeny, które jest oparty na szablonie rozwiązania modeli składnika. Po utworzeniu rozwiązania, plik DslDefinition.dsl zostanie wyświetlony w Projektancie języka specyficznego dla domeny. Zamknij plik, kliknij go prawym przyciskiem myszy **Eksploratora rozwiązań**, wskaż polecenie **Otwórz za pomocą**, kliknij przycisk **edytora XML**, a następnie kliknij przycisk **OK**.

## <a name="sections-of-the-dsldefinitiondsl-file"></a>Sekcji w pliku DslDefinition.dsl

Element główny jest \<Dsl >, a jego atrybuty zidentyfikować nazwę języka specyficznego dla domeny, przestrzeń nazw, i numery wersji głównej i pomocniczej dla wersji. `DslDefinitionModel` Schemat definiuje zawartości i struktury prawidłowy plik DslDefinition.dsl.

Elementy podrzędne \<Dsl > elementu głównego są następujące:

### <a name="classes"></a>Klasy

Ta sekcja definiuje każdej klasy domeny, który generuje klasę w wygenerowanym kodzie.

### <a name="relationships"></a>Relacje

Ta sekcja definiuje każdej relacji w modelu. Element źródłowy i docelowy reprezentować dwie strony relacji.

### <a name="types"></a>Types

Ta sekcja definiuje każdego typu i jego przestrzeni nazw. Właściwości domeny ma dwa typy. `DomainEnumerations` zdefiniowanych w modelu oraz generowanie typów do DomainModel.cs. `ExternalTypes` odwołuje się do typów, które są zdefiniowane w innym miejscu (takich jak `String` lub `Int32`) i nie generują żadnych czynności.

### <a name="shapes"></a>Kształty

Ta sekcja definiuje kształtów, które opisują sposób wyświetlania modelu w projektancie. Te kształty geometryczne są mapowane na klasy modelu w sekcji diagramu.

### <a name="connectors"></a>Łączniki

Ta sekcja definiuje wygląd łączniki, które są wyświetlane w projektancie. Opisy te style geometrycznych są mapowane na określonych relacji w modelu, w sekcji diagramu.

### <a name="xmlserializationbehavior"></a>XmlSerializationBehavior

Ta sekcja definiuje schemat serializacji i udostępnia dodatkowe informacje na temat sposobu każdej klasy jest zapisywane w pliku.

### <a name="explorerbehavior"></a>ExplorerBehavior

Ta sekcja definiuje sposób **DSL Explorer** okna jest wyświetlany, gdy użytkownik edytuje modelu.

### <a name="connectionbuilders"></a>ConnectionBuilders

Ta sekcja definiuje konstruktora połączenia dla każdego łącznik (utworzenie łącza między żadnych dwie klasy, która za pomocą narzędzia mogą zostać połączone). W tej sekcji określa, czy możesz połączyć źródłowe i klasy docelowej.

### <a name="diagram"></a>Diagram

Ta sekcja definiuje diagramu, i używać go do określania właściwości, takie jak kolor tła i klasy głównym. (Klasy głównym jest reprezentowana przez diagram całej klasy domeny). Sekcja Diagram zawiera również elementy ShapeMap i ConnectorMap, które określają kształtu lub łącznik, który reprezentuje każdej klasy domeny lub relacji.

### <a name="designer"></a>Projektant

Ta sekcja definiuje projektanta (Edytor), która gromadzi **przybornika**, ustawienia sprawdzania poprawności, diagram i schematu serializacji. W sekcji projektanta definiuje również klasy głównym modelu, który zazwyczaj jest także klasy głównym diagramu.

### <a name="explorer"></a>Explorer

W tej sekcji wymieniono **DSL Explorer** zachowanie (zdefiniowany w sekcji XmlSerializationBehavior).

## <a name="monikers-in-the-dsldefinitiondsl-file"></a>Monikery w pliku DslDefinition.dsl

W całym pliku DslDefinition.dsl można użyć monikerów wprowadzać odsyłacze do określonych elementów. Na przykład każda definicja relacji zawiera podsekcja źródła i podsekcji docelowej. Każdy podsekcja zawiera krótkiej nazwy klasy obiektów, które mogą być połączone z tym relacji:

```
<DomainRelationship ...        Name="LibraryHasMembers" Namespace="ExampleNamespace" >    <Source>      <DomainRole ...>
       <RolePlayer>
         <DomainClassMoniker Name="Library" />
       </RolePlayer>
     </DomainRole>
   </Source>
```

Zazwyczaj przestrzeń nazw elementu z odwołaniem (w tym przykładzie `Library` klasy domeny) jest taki sam jak element odwołujący się (w tym przypadku LibraryHasMembers relacji domeny). W takich przypadkach moniker musi podać tylko nazwę klasy. W przeciwnym razie należy użyć /Namespace/Name pełnej formy:

```
<DomainClassMoniker Name="/ExampleNameSpace/Library" />
```

Krótka nazwa systemu wymaga, aby elementów równorzędnych w drzewie XML miały unikatowe nazwy. Z tego powodu błędy sprawdzania poprawności wystąpić, jeśli użytkownik próbuje zapisać definicję języka specyficznego dla domeny, która zawiera, na przykład dwie klasy o tej samej nazwie. Takie błędy zduplikowana nazwa powinna zawsze poprawić, zanim zapiszesz plik DslDefinition.dsl, dzięki czemu możesz ponownie załadować go poprawnie później.

Każdy typ ma własny typ krótkiej nazwy: DomainClassMoniker, DomainRelationshipMoniker, i tak dalej.

## <a name="types"></a>Types

Sekcja Typy określa wszystkie typy, które zawiera plik DslDefinition.dsl jako typy właściwości. Tego typu można podzielić na dwa rodzaje: typy zewnętrzne, takie jak System.String oraz typy wyliczone.

### <a name="external-types"></a>Typów zewnętrznych

Przykład diagramu składników zawiera zestaw standardowych typów pierwotnych, mimo że tylko niektóre z nich są używane.

Każda definicja typu zewnętrznego składa się po prostu nazwy i przestrzeni nazw, takich jak parametry i systemu:

```
<ExternalType Name="String" Namespace="System" />
```

Pełne nazwy typów są używane zamiast słowa kluczowe równoważne kompilatora, takie jak "string".

Zewnętrzne typy nie są ograniczone do standardowej biblioteki typów.

### <a name="enumerations"></a>Wyliczenia

Typowy specyfikacji wyliczenie podobny w tym przykładzie:

```
<DomainEnumeration IsFlags="true" Name="PageSort"          Namespace="Fabrikam.Wizard">
  <Literals>
    <EnumerationLiteral Name="Start" Value="1"/>
    <EnumerationLiteral Name="Decision" Value="2"/>
  </Literals>
</DomainEnumeration>
```

`IsFlags` Atrybutu formantów czy wygenerowany kod jest poprzedzony `[Flags]` atrybutu środowisko uruchomieniowe języka wspólnego (CLR), który określa, czy wartości wyliczenia można łączyć bitowo. Jeśli ten atrybut ma ustawioną wartość true, należy określić wartości zasilania z dwóch wartości literałów.

## <a name="classes"></a>Klasy

Większość elementów w definicji dowolnego języka specyficznego dla domeny są bezpośrednio lub pośrednio wystąpienia `DomainClass`. Podklasy `DomainClass` obejmują `DomainRelationship`, `Shape`, `Connector`, i `Diagram`. `Classes` Sekcji pliku DslDefinition.dsl zawiera klasy domeny.

Każda klasa ma zestaw właściwości i może mieć klasy podstawowej. W przykładzie Diagram składnika `NamedElement` jest klasą abstrakcyjną, która ma `Name` właściwości, których typ to ciąg:

```
<DomainClass Id="ee3161ca-2818-42c8-b522-88f50fc72de8"  Name="NamedElement" Namespace="Fabrikam.CmptDsl5"      DisplayName="Named Element"  InheritanceModifier="Abstract">
  <Properties>
    <DomainProperty Id="ef553cf0-33b5-4e34-a30b-cfcfd86f2261"   Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">
      <Type>
        <ExternalTypeMoniker Name="/System/String" />
      </Type>
    </DomainProperty>
  </Properties>
</DomainClass>
```

`NamedElement` jest podstawą kilka innych klas takich jak `Component`, który zawiera właściwości oprócz `Name` właściwość, która ono odziedziczone po `NamedElement`. Węzeł podrzędny baseclass — zawiera odwołanie do krótkiej nazwy. Ponieważ przywoływany klasa znajduje się w tej samej przestrzeni nazw, tylko jego nazwa jest wymagana w monikerze:

```
<DomainClass Name="Component" Namespace="Fabrikam.CmptDsl5"              DisplayName="Component">
  <BaseClass>
    <DomainClassMoniker Name="NamedElement" />
  </BaseClass>
  <Properties>
    <DomainProperty Name="Kind" DisplayName="Kind" >
      <Type>
        <ExternalTypeMoniker Name="/System/String" />
      </Type>
    </DomainProperty>
  </Properties>
```

Każda klasa domeny (w tym relacje, kształtów, łączniki i diagramy) może mieć następujące atrybuty i węzłów podrzędnych:

-   **Id.** Ten atrybut jest identyfikatorem GUID. Jeśli nie zostanie określona wartość w pliku, Projektant języka specyficznego dla domeny utworzy wartość. (W ilustracjach w tym dokumencie, ten atrybut jest zwykle pominięte aby zaoszczędzić miejsce.)

-   **Nazwa i Namespace.** Te atrybuty Określ nazwę i przestrzeń nazw, klasy w wygenerowanym kodzie. Razem muszą być unikatowe w obrębie języka specyficznego dla domeny.

-   **InheritanceModifier.** Ten atrybut to "abstract", "sealed" lub none.

-   **DisplayName.** Ten atrybut jest nazwa wyświetlana w **właściwości** okna. Atrybut Nazwa wyświetlana może zawierać spacji i innych znaków interpunkcyjnych.

-   **GeneratesDoubleDerived.** Jeśli ten atrybut ma ustawioną wartość true, dwie klasy są generowane i jest podklasą innych. Wygenerowane metody są w podstawowym, a w podklasy konstruktorów. Przez ustawienie dla tego atrybutu, można zastąpić dowolnej metody wygenerowanego kodu niestandardowego.

-   **HasCustomConstructor**. Jeśli ten atrybut ma ustawioną wartość true, konstruktor został pominięty wygenerowany kod, aby mogły zapisywać własną wersję.

-   **Atrybuty**. Ten atrybut zawiera atrybuty CLR wygenerowanej klasy.

-   **Baseclass —**. Jeśli określisz klasy podstawowej, musi być tego samego typu. Na przykład klasa domeny musi mieć inną klasę domeny podstawowym i kształt Przedział musi mieć kształt Przedział. Jeśli nie określisz klasy podstawowej, klasa w wygenerowanym kodzie pochodzi z klasy standardowych ramy. Na przykład pochodną klasy domeny `ModelElement`.

-   **Właściwości**. Ten atrybut zawiera właściwości, które są obsługiwane pod kontrolą transakcji i utrwalone po zapisaniu modelu.

-   **ElementMergeDirectives**. Każdy element scalania dyrektywy określa, jak inne wystąpienie innej klasy jest dodawany do wystąpienia klasy nadrzędnej. Więcej szczegółów na temat dyrektywy scalania element można znaleźć w dalszej części tego tematu.

-   Klasa C# jest generowany dla każdej klasy domeny, który ma na liście `Classes` sekcji. Klasy C# są generowane w Dsl\GeneratedCode\DomainClasses.cs.

### <a name="properties"></a>Właściwości

Każda właściwość domeny ma nazwę i typ. Nazwa musi być unikatowa w obrębie klasy domeny i jego przechodnie podstawowych.

Typ musi odwoływać się do jednego z wymienionych w `Types` sekcji. Ogólnie rzecz biorąc krótka nazwa musi zawierać przestrzeni nazw.

```
<DomainProperty Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">
  <Type>
    <ExternalTypeMoniker Name="/System/String" />
  </Type>
</DomainProperty>
```

Każda właściwość domeny również może mieć następujące atrybuty:

-   **IsBrowsable**. Ten atrybut określa, czy właściwość jest wyświetlany w **właściwości** okna, gdy użytkownik kliknie obiekt klasy nadrzędnej.

-   **IsUIReadOnly**. Ten atrybut określa, czy użytkownik może zmienić właściwości w **właściwości** okna lub za pośrednictwem dekoratora, w którym przedstawiono właściwości.

-   **Rodzaj**. Ten atrybut zostanie ustawiony na normalny, obliczona lub wartości CustomStorage. Jeśli ustawisz ten atrybut obliczona, musisz podać kodu niestandardowego, który określa wartość, a właściwość będą tylko do odczytu. Jeśli ustawisz ten atrybut wartości CustomStorage, należy podać kod, który zarówno pobiera i ustawia wartości.

-   **IsElementName**. Jeśli ten atrybut ma ustawioną wartość true, jego wartość jest automatycznie ustawiana unikatowe wartości podczas tworzenia wystąpienia klasy nadrzędnej. Ten atrybut można ustawić wartość true dla tylko jednej właściwości każdej klasy, która musi mieć typ ciągu. W przykładzie Diagram składnika `Name` właściwości w `NamedElement` ma `IsElementName` ustawioną na true. Zawsze, gdy użytkownik tworzy `Component` elementu (który dziedziczy z `NamedElement`), jest inicjowana automatycznie podobną "Component6."

-   `DefaultValue`. Jeśli ten atrybut został określony, podanej wartości jest przypisany do tego atrybutu dla nowego wystąpienia tej klasy. Jeśli `IsElementName` jest ustawiony atrybut DefaultValue Określa początkowy część nowe parametry.

-   **Kategoria** jest nagłówka, w którym właściwość będą wyświetlane w **właściwości** okna.

## <a name="relationships"></a>Relacje

`Relationships` Sekcja zawiera wszystkie relacje języka specyficznego dla domeny. Każdy `Domain Relationship` jest binarna, a bezpośrednie łączenie członkami klasy źródłowej do elementów członkowskich klasy docelowej. Klasy źródłowa i docelowa są zazwyczaj klasy domeny, ale relacji z innymi relacje są również dozwolone.

Na przykład relacja połączenia łączy elementy członkowskie klasy OutPort do elementów członkowskich klasy portu podczerwieni. Każde wystąpienie łącza relacji łączy wystąpienia OutPort na wystąpienie InPort. Ponieważ jest w relacji wiele wiele każdego OutPort może mieć wiele łączy połączenia ze źródłami na nim, a każde wystąpienie portu podczerwieni mogą mieć wiele łącza, które odnoszą się do jego.

### <a name="source-and-target-roles"></a>Role źródłowe i docelowe

Każdej relacji zawiera role źródłowe i docelowe, które mają następujące atrybuty:

-   `RolePlayer` Atrybut odwołuje się do klasy domeny połączonego wystąpień: OutPort źródła, InPort dla elementu docelowego.

-   `Multiplicity` Atrybut ma cztery wartości (wartości ZeroMany, wartość ZeroOne jednego i OneMany). Ten atrybut określa numer łączy tę relację, która może być skojarzony z jednego obiektu pełniącego rolę.

-   `PropertyName` Atrybut określa nazwę, która jest używana w roli odtwarzanie klasy dostępu do obiektów na drugim końcu. Ta nazwa jest używana w szablonie lub kodu niestandardowego, aby przechodzić między nimi relacja. Na przykład `PropertyName` ustawiono atrybut roli źródłowej `Targets`. W związku z tym będzie działać następujący kod:

    ```
    OutPort op = ...; foreach (InPort ip in op.Targets) ...
    ```

     Konwencja liczbie mnogiej, jeśli liczebność jest wartości ZeroMany ani OneMany są nazwy właściwości.

     Liczebność roli odwołuje się do ile przeciwną roli może być skojarzony z każde wystąpienie tej roli. Na przykład w relacji ComponentHasPorts rola Serwer obiektów docelowych ma `RolePlayer` ustawionego atrybutu do portu, `PropertyName` ustawionego atrybutu do składnika i `Multiplicity` atrybut ustawiony na wartość ZeroOne. W związku z tym jest odpowiedni kod, aby użyć tej roli:

    ```
    ComponentPort p = ...; Component c = p.Component; if (c != null) ...
    ```

-   Rola `Name` to nazwa, która jest używana w ramach klasy relacji do odwoływania się do tego celu łącza. Konwencja Nazwa roli jest zawsze pojedynczej, ponieważ każde łącze ma tylko jedno wystąpienie na końcach. Następujący kod będzie działać:

    ```
    Connection connectionLink = ...; OutPort op = connectionLink.Source;
    ```

-   Domyślnie `IsPropertyGenerator` atrybut jest ustawiony na wartość true. Jeśli ma wartość false, ma właściwości zostanie utworzony w klasie obiektu pełniącego rolę. (W takim przypadku `op.Targets`, na przykład nie będzie działać). Jest jednak nadal możliwe użyć niestandardowego kodu, aby przechodzić między nimi relacja lub uzyskać dostępu do łączy się, jeśli kod niestandardowy jawnie używa relacji:

    ```
    OutPort op = ...; foreach (InPort ip in Connection.GetTargets(op)) ...
    foreach (Connection link in Connection.GetLinksToTargets(op)) ...
    ```

### <a name="relationship-attributes"></a>Atrybuty relacji

Oprócz tych atrybutów i węzły podrzędne, które są dostępne dla wszystkich klas każdej relacji ma następujące atrybuty:

-   **IsEmbedding**. Ten atrybut logiczny określa, czy relacja jest częścią drzewa osadzania. Każdy model muszą tworzyć drzewo o relacje osadzania. Każda klasa domeny w związku z tym musi być elementem docelowym co najmniej jedna relacja osadzania, chyba że jest głównym elementem modelu.

-   **AllowsDuplicates**. Ten atrybut Boolean, który ma wartość false, domyślnie, dotyczą tylko relacje, które mają liczebność "many" w pliku źródłowym i docelowym. Określa, czy użytkownicy języka może łączyć z jedną parą elementy źródłowe i docelowe przez więcej niż jednego łącza w tej samej relacji.

## <a name="designer-and-toolbox-tabs"></a>Projektant i kart z przybornika

Główna część **projektanta** jest sekcji pliku DslDefinition.dsl **ToolboxTab** elementów. Projektant jeden może mieć wiele z tych elementów, z których każdy reprezentuje kapusty sekcję w Projektancie wygenerowanego **przybornika**. Każdy **ToolboxTab** element może zawierać jeden lub więcej **ElementTool** elementów, **ConnectionTool** elementy, lub obie.

Element narzędzia można utworzyć wystąpienia klasy określonej domeny. Gdy użytkownik przeciąga narzędzia elementu na diagramie, wynik jest określana przez element scalania dyrektywy zgodnie z opisem w sekcji o dyrektywy scalania element w dalszej części tego tematu.

Narzędzia każdego połączenia można wywołać konstruktora określonego połączenia. Jeden konstruktor połączenia można utworzyć więcej niż jeden typ relacji, w zależności od tego, gdy użytkownik kliknie przycisk myszy, zgodnie z opisem w sekcji o konstruktorów połączenia.

Ani typu narzędzie tworzy bezpośrednio kształtów lub łączników. Każdy tworzy wystąpienie klasy domeny lub relacji domeny; mapowania kształt i łącznika następnie określ sposób wyświetlania tej domeny klasy lub relacji domeny.

## <a name="paths"></a>Ścieżki

Ścieżki domeny są wyświetlane w kilku lokalizacjach w pliku DslDefinition.dsl. Te ścieżki Określ szereg łącza z jednego elementu w modelu (to znaczy wystąpienia języka specyficznego dla domeny) do innej. Składnia ścieżki jest proste, ale pełne.

Ścieżki zostaną wyświetlone w pliku DslDefinition.dsl `<DomainPath>...</DomainPath>` tagów. Mimo że ścieżki nawigować przez kilka łączy, większość przykładów w praktyce przechodzenie przez tylko jeden link.

Ścieżka składa się sekwencji segmentów. Każdy z segmentów jest przeskoku od obiektu łącza lub łącze do obiektu. W związku z tym przeskoków alternatywny zwykle długie ścieżki. Przy pierwszym przeskoku z obiektu łącza, drugi przeskok jest obiektem na drugim końcu łącza, trzeci przeskoku ma dalej łącza i tak dalej. Okazjonalne wyjątek do tej sekwencji jest, gdzie relacji jest elementem źródłowa lub docelowa z inną relacją.

Każdy z segmentów rozpoczyna się od nazwy relacji. W przeskoku łącza obiektu relacji poprzedza kropkę i nazwa właściwości: "`Relationship . Property`". W przeskoku obiektu łącza, relacja poprzedza wykrzyknikiem i nazwa roli: "`Relationship ! Role`".

Przykład diagramu składników zawiera ścieżkę w ParentElementPath z ShapeMap InPort. Ta ścieżka rozpoczyna się w następujący sposób:

```
    ComponentHasPorts.Component
```

W tym przykładzie InPort jest podklasą klasy ComponentPort i ma relację ComponentHasPorts. Właściwość nosi nazwę składnika.

Podczas zapisywania C# w odniesieniu do tego modelu, można przejść przez łącze w jednym kroku przy użyciu właściwości, który generuje relacji w każdej klasy, które dotyczą:

```
     InPort port; ...  Component c = port.Component;
```

Jednak należy wykonać obie przeskoków jawnie w składnia ścieżki. Ze względu na to wymaganie można łatwiej dostęp do pośredniego łącza. Poniższy kod zakończeniu przeskoku z łącza do składnika:

```
    ComponentHasPorts.Component / ! Component
```

(Można pominąć nazwę relacji, w którym jest taki sam jak poprzedni segment).

## <a name="element-merge-directives"></a>Element dyrektywy scalania

Gdy użytkownik języka przeciągnie element z **przybornika** na diagramie, jest tworzony wystąpienia klasy tego narzędzia. Łącza są również między to wystąpienie i istniejące elementy modelu. Niektóre elementy, takie jak składniki lub komentarzy, są tworzone, gdy użytkownik języka przeciąga je z **przybornika** na pustą część diagramu. Innych elementów są tworzone, gdy język użytkownik przeciąga je na inne elementy hosta. Na przykład OutPort lub InPort jest tworzony podczas przeciągania go na składnik przez użytkownika język.

Potencjalne klasy obsługującej, takich jak składnika będzie akceptować nowego elementu tylko wtedy, gdy klasa hosta dyrektywę scalania element klasy nowego elementu. Na przykład węzeł DomainClass o nazwie = "Component" zawiera:

```
<DomainClass Name="Component" ...> ...
    <ElementMergeDirective>
      <Index>
        <DomainClassMoniker Name="ComponentPort" />
      </Index>
      <LinkCreationPaths>
        <DomainPath>ComponentHasPorts.Ports</DomainPath>
      </LinkCreationPaths>
    </ElementMergeDirective> ...
```

Krótkiej nazwy klasy, która znajduje się w węźle indeksu odwołuje się do klasy elementu, które mogą być akceptowane. W takim przypadku ComponentPort jest abstrakcyjna klasa podstawowa InPort i OutPort. W związku z tym jednej z tych elementów mogą być akceptowane.

ComponentModel, klasy głównym języka, ma element dyrektywy scalania dla składników i komentarze. Użytkownika języka można przeciągnij elementy dla tych klas bezpośrednio na diagramu, ponieważ puste części diagramu reprezentują klasy głównym. Jednak ComponentModel zawiera żadna dyrektywa scalania element ComponentPort. W związku z tym użytkownika języka nie można przeciągnąć InPorts lub OutPorts bezpośrednio na diagramie.

Dyrektywa scalania element określa, jakie łącza lub łącza są tworzone, aby nowy element można zintegrować lub scalić istniejącego modelu. ComponentPort wystąpienie ComponentHasPorts jest tworzone. DomainPath identyfikuje zarówno relacji, jak i właściwość klasy nadrzędnej portów, do których zostanie dodany nowy element.

Można utworzyć więcej niż jednego połączenia w dyrektywie scalania element umieszczając w niej więcej niż jedną ścieżkę tworzenia łącza. Jedna ze ścieżek musi być osadzony.

Można użyć więcej niż jeden segment w ścieżce tworzenia łącza. W takim przypadku ostatni segment definiuje, jakie link musi zostać utworzony. Wcześniej segmentów przejdź z klasy nadrzędnej obiektu, z którego można utworzyć nowy link.

Na przykład można dodać tej dyrektywy scalania element do klasy składnika:

```
<DomainClass Name="Component" ...> ...
  <ElementMergeDirective>
    <Index>
       <DomainClassMoniker Name="Comment"/>
    </Index>
    <LinkCreationPaths>
       <DomainPath>          ComponentModelHasComponents . ComponentModel / !ComponentModel         / ComponentModelHasComments.Comments       </DomainPath>
       <DomainPath>CommentsReferenceComponents.Comments</DomainPath>
    </LinkCreationPaths>
  </ElementMergeDirective>
```

Użytkownicy języka można przeciągnięcie komentarz do składnika i mieć nowy komentarz automatycznie utworzone z łączem do składnika.

Pierwszy ścieżki tworzenia łącza nawiguje między `Component` do `ComponentModel` , a następnie tworzy wystąpienie relacja osadzania `ComponentModelHasComments`. Drugi ścieżki tworzenia łącza tworzy łącze relacji odwołania CommentsReferenceComponents z hosta składnik do nowego komentarza. Wszystkie ścieżki tworzenia link musi rozpoczynać się od klasy obsługującej i musi się kończyć na łącze tej czynności na nowo wystąpień klasy.

## <a name="xmlclassdata"></a>XmlClassData

Każda klasa domeny (w tym relacje i inne podtypy) mogą mieć dodatkowe informacje zawarte w `XmlClassData` węzła, który jest wyświetlany w obszarze `XmlSerializationBehavior` sekcji pliku DslDefinition.dsl. Te informacje w szczególności dotyczy jak wystąpień klasy są przechowywane w postaci serializacji podczas zapisywania do pliku modelu.

Większość wygenerowany kod, który `XmlSerializationBehavior` ma wpływ `Dsl\GeneratedCode\Serializer.cs`.

Każdy `XmlClassData` węzła zawiera następujące węzły podrzędne i atrybuty:

-   Węzeł krótkiej nazwy, która odwołuje się do klasy, do którego odnosi się dane.

-   **XmlPropertyData** dla każdej właściwości, która jest zdefiniowana w klasie.

-   **XmlRelationshipData** dla każdej relacji, które są uzyskiwane w klasie. (Relacje również mieć własne węzłów XmlClassData).

-   **Właściwość TypeName** atrybut ciągu, który określa nazwę klasy pomocnika serializacji w wygenerowanym kodzie.

-   **ElementName** ciąg, który określa tagu XML serializacji wystąpienia tej klasy. Według Konwencji ElementName jest zwykle taka sama jak nazwa klasy z wyjątkiem pierwszej litery jest pisana małymi literami. Na przykład plik przykładowy model rozpoczyna się następująco:

    ```
    <componentModel ...
    ```

-   **MonikerElementName** w plikach serializacji modelu użytkownika. Ten atrybut wprowadza krótkiej nazwy, która odwołuje się do tej klasy.

-   **MonikerAttributeName**, który identyfikuje nazwa atrybutu XML w krótka nazwa. W tym fragmencie pliku serializacji użytkownika Autor języka specyficznego dla domeny zdefiniowane **MonikerElementName** jako "inPortMoniker" i **MonikerAttributeName** jako "path":

    ```
    <inPortMoniker path="//Component2/InPort1" />
    ```

### <a name="connectionbuilders"></a>ConnectionBuilders

Konstruktor połączenia jest zdefiniowana dla każdego narzędzia połączenia. Konstruktor każdego połączenia składa się z co najmniej jeden element LinkConnectDirective, z których każdy zawiera jeden lub więcej elementów SourceDirective i co najmniej jeden element TargetDirective. Po kliknięciu przycisku narzędzia połączenia, użytkownik może uruchomić połączenie z dowolnym kształcie zamapowane na element modelu, który pojawi się na liście elementów SourceDirective. Następnie można wykonać połączenia kształtu, który jest zamapowany do elementu, który pojawi się na liście elementów TargetDirective. Klasa relacji wystąpienia zależy od elementu LinkConnectDirective wskazywany przez gdzie połączenie zostało uruchomione.

### <a name="xmlpropertydata"></a>XmlPropertyData

A **DomainPropertyMoniker** atrybut określa właściwość, do którego odwołuje się dane. Ten atrybut musi być właściwością klasy otaczającej danych klas.

**XmlName** atrybutu daje z odpowiednią nazwą atrybutu, jak powinien wyglądać w pliku XML. Konwencja, ten ciąg jest taka sama jak nazwa właściwości z wyjątkiem pierwszej litery jest pisana małymi literami.

Domyślnie **reprezentacja** atrybut ma wartość atrybutu. Jeśli **reprezentacja** ustawiono Element podrzędny węzła jest tworzony w pliku XML. Jeśli **reprezentacja** jest ustawić wartość Ignore, właściwość nie jest serializowany.

**IsMonikerKey** i **IsMonikerQualifier** atrybuty przypisać właściwości rolę w identyfikacji wystąpienia klasy nadrzędnej. Można ustawić **IsMonikerKey** na wartość true dla jednej właściwości, która jest zdefiniowana w lub dziedziczone przez klasy. Ten atrybut identyfikuje poszczególne wystąpienia klasy nadrzędnej. Właściwość, której możesz ustawić `IsMonikerKey` jest zazwyczaj nazwą lub innego identyfikatora klucza. Na przykład `Name` właściwości ciągu jest kluczem moniker dla nazwanego i jej klas pochodnych. Gdy użytkownik zapisuje modelu do pliku, ten atrybut musi zawierać unikatowe wartości dla każdego wystąpienia między jego elementów równorzędnych w drzewie osadzenia relacji.

W pliku modelu serializacji pełne krótkiej nazwy elementu jest ścieżką z katalogu głównego modelu niżej na drzewie osadzenia relacje zamykający klucza krótkiej nazwy w każdym punkcie. Na przykład InPorts są osadzone w składnikach, które z kolei są osadzone w modelu głównym. Dlatego jest prawidłową krótką nazwę:

```
<inPortMoniker name="//Component2/InPort1" />
```

Można ustawić **IsMonikerQualifier** atrybutu dla właściwości ciągu i zapewnić dodatkowe sposób utworzyć pełną nazwę elementu. Na przykład w pliku DslDefinition.dsl **Namespace** jest kwalifikatora krótkiej nazwy.

### <a name="xmlrelationshipdata"></a>XmlRelationshipData

W pliku modelu serializacji łączy (osadzanie i odwołanie relacje) są reprezentowane przez węzły podrzędne końca źródłowego relacji. Do osadzenia relacje, węzeł podrzędny zawiera poddrzewo. W przypadku relacji odwołania węzeł podrzędny zawiera krótkiej nazwy, która odwołuje się do innej części drzewa.

**XmlRelationshipData** atrybutu w **XmlClassData** atrybut definiuje dokładnie, jak węzły podrzędne są zagnieżdżone w obrębie elementu źródła. Każdy relacji, który jest źródłem w klasie domeny ma jeden **XmlRelationshipData** atrybutu.

**DomainRelationshipMoniker** atrybut identyfikuje jednej z relacji powierzając jej ich konserwację w klasie.

**RoleElementName** atrybutu daje nazwie tagu XML, który umieszcza węzła podrzędnego w danych serializacji.

Na przykład plik DslDefinition.dsl zawiera:

```
<XmlClassData ElementName="component" ...>
  <DomainClassMoniker Name="Component" />
  <ElementData>
    <XmlRelationshipData RoleElementName="ports">
      <DomainRelationshipMoniker Name="ComponentHasPorts" />
    </XmlRelationshipData>
```

W związku z tym zawiera seryjnych pliku:

```
<component name="Component1"> <!-- parent ->
   <ports> <!-- role ->
     <outPort name="OutPort1"> <!-- child element ->
       ...
     </outPort>
   </ports> ...
```

Jeśli **UseFullForm** atrybut ma ustawioną wartość true, wprowadza dodatkową warstwę zagnieżdżenia. Ta warstwa reprezentuje samą relację. Ten atrybut musi mieć ustawioną wartość true, jeśli relacja ma właściwości.

```
<XmlClassData ElementName="outPort">
   <DomainClassMoniker Name="OutPort" />
   <ElementData>
     <XmlRelationshipData UseFullForm="true" RoleElementName="targets">
       <DomainRelationshipMoniker Name="Connection" />
     </XmlRelationshipData>
   </ElementData>
 </XmlClassData>
```

Zawiera seryjnych pliku:

```
<outPort name="OutPort1">  <!-- Parent ->
   <targets>  <!-- role ->
     <connection sourceRoleName="X">  <!-- relationship link ->
         <inPortMoniker name="//Component2/InPort1" /> <!-- child ->
     </connection>
    </targets>
  </outPort>
```

(Relacja połączenia ma własną klasy danych XML, co zapewnia jego nazw elementów i atrybutów).

Jeśli **OmitElement** atrybut jest ustawiony na wartość true, relacji nazwa roli jest pominięty, który wyświetla trzyliterowy skrót pliku serializacji i jest jednoznaczne, jeśli dwie klasy mieć nie więcej niż jedną relację. Na przykład:

```
<component name="Component3">
  <!-- only one relationship could get here: ->
  <outPort name="OutPort1">
     <targets> ...
```

### <a name="serialization-of-a-domain-specific-language-definition"></a>Serializacja definicji języka specyficznego dla domeny

Plik DslDefinition.dsl jest plikiem serializacji i jest zgodny z definicją języka specyficznego dla domeny. Oto kilka przykładów definicje serializacji XML:

-   **DSL** jest węzeł RootClass i klasa diagramu. DomainClass elementu DomainRelationship i inne elementy są osadzone w obszarze `Dsl`.

-   **Klasy** jest **RoleElementName** relacji między języka specyficznego dla domeny i DomainClass.

```
<Dsl Name="CmptDsl5" ...>
  <Classes>
    <DomainClass Name="NamedElement" InheritanceModifier="Abstract" ...
```

-   **XmlSerializationBehavior** atrybutu jest osadzony w obszarze `Dsl` atrybutu, ale **OmitElement** atrybut został ustawiony na Relacja osadzania. W związku z tym nie `RoleElementName` uczestniczyło atrybutu. Z kolei **danych klas** atrybutu `RoleElementName` atrybutu osadzania relacji między **XmlSerializationBehavior** atrybutu i **XmlClassData** atrybutu.

```
<Dsl Name="CmptDsl5" ...> ...
  <XmlSerializationBehavior Name="ComponentsSerializationBehavior" >
    <ClassData>
      <XmlClassData ...>...</XmlClassData>
      <XmlClassData ...>...</XmlClassData>
```

-   ConnectorHasDecorators jest relacja osadzania między `Connector` i `Decorator`. `UseFullForm` ustawiono tak, aby nazwa relacji pojawi się z listą właściwości dla każdego łącza z obiektu łącznika. Jednak `OmitElement` również została ustawiona, aby nie `RoleElementName` umieszcza wielu linki, które są osadzone wewnątrz `Connector`:

```
<Connector Name="AssociationLink" ...>
  <ConnectorHasDecorators Position="TargetTop" ...>
    <TextDecorator Name="TargetRoleName"   />
  </ConnectorHasDecorators>
  <ConnectorHasDecorators Position="SourceTop" ...>
    <TextDecorator Name="SourceRoleName"   />
  </ConnectorHasDecorators>
</Connector>
```

## <a name="shapes-and-connectors"></a>Kształty i łączniki

Definicje kształt i łącznika atrybuty i węzłów podrzędnych dziedziczyć klasy domeny, oprócz następujących czynności:

-   `Color` i `Line``Style` atrybutów.

-   **ExposesFillColorAsProperty** i kilku atrybutów podobne. Te atrybuty logiczne wprowadź odpowiednią zmienną właściwości przez użytkownika. Ogólnie rzecz biorąc, kliknięcie języka kształt na diagramie, właściwości wyświetlanych w **właściwości** okna są wystąpienia klasy domeny, do którego kształt jest zamapowany. Jeśli `ExposesFillColorAsProperty` ma wartość true, właściwość kształt pojawia się również.

-   **ShapeHasDecorators**. Wystąpienie tego atrybutu występuje dla każdego tekstu, ikony lub dekoratora Rozwiń/Zwiń. (W pliku DslDefinition.dsl `ShapeHasDecorators` relację z `UseFullForm` ustawioną na true.)

## <a name="shape-maps"></a>Kształt mapy

Mapy kształtu określają sposób wyświetlania wystąpienia klasy danej domeny na ekranie reprezentowany przez kształtu. Mapy zarówno kształtu, jak i łącznika są wyświetlane w obszarze `Diagram` sekcji pliku DslDefinition.dsl.

Jak w poniższym przykładzie `ShapeMap` elementy mają co najmniej, krótkiej nazwy klasy domeny, moniker kształtu, a `ParentElementPath` elementu:

```
<ShapeMap>
  <DomainClassMoniker Name="InPort" />
  <ParentElementPath>
    <DomainPath>ComponentHasPorts.Component/!Component</DomainPath>
  </ParentElementPath>
  <PortMoniker Name="InPortShape" />
</ShapeMap>
```

Podstawową funkcją `ParentElementPath` element jest tak, aby w tej samej klasy obiektów może pojawić się jako inny kształt w różnych kontekstach. Na przykład jeśli `InPort` można również osadzać w komentarzu, `InPort` może występować jako inny kształt do tego celu.

Po drugie ścieżka Określa, jak kształtu odnosi się do elementu nadrzędnego. Nie określono żadnych osadzania struktury między kształtów w pliku DslDefinition.dsl. Musi rozpoznać struktury z mapy kształtu. Element nadrzędny kształtu jest kształtu, który jest zamapowany do elementu domeny, który identyfikuje ścieżkę elementu nadrzędnego. W takim przypadku ścieżki identyfikuje składnika, do którego `InPort` należy. W innym mapy kształtu Klasa składnika jest mapowany na ComponentShape. W związku z tym nowy `InPort` kształtu staje się elementem podrzędnym kształt z jego składników `ComponentShape`.

Jeśli zamiast tego dołączonego portu podczerwieni kształtu do diagramu, ścieżka elementu nadrzędnego mają przyjąć kolejny krok do modelu składnika, który jest mapowany do diagramu:

```
ComponentHasPorts . Component / ! Component /    ComponentModelHasComponents . ComponentModel / ! ComponentModel
```

Katalogu głównego modelu nie ma mapy kształtu. Zamiast tego głównego odwołuje się bezpośrednio z diagramu, który ma `Class` elementu:

```
<Diagram Name="ComponentDiagram" >
    <Class>
      <DomainClassMoniker Name="ComponentModel" />
    </Class>...
```

### <a name="decorator-maps"></a>Dekoratora mapy

Mapa dekoratora kojarzy właściwości w klasie zmapowane do dekorator dla kształtu. Jeśli właściwość jest typu wyliczeniowego lub Boolean, jego wartość można określić, czy dekorator jest widoczny. Jeśli dekorator dekoratora tekstu, wartości właściwości mogą być wyświetlane, a użytkownik może go edytować.

### <a name="compartment-shape-maps"></a>Przedział kształtu mapy

Mapy kształtu Przedział są podtypów map kształtu.

## <a name="connector-maps"></a>Łącznik mapy

Mapa minimalnego łącznika odwołuje się łącznika i relacji:

```
<ConnectorMap>
  <ConnectorMoniker Name="CommentLink" />
  <DomainRelationshipMoniker Name="CommentsReferenceComponents" />
</ConnectorMap>
```

Łącznik maps może również zawierać dekoratora mapy.

## <a name="see-also"></a>Zobacz także

- [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
- [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md)