---
title: Dostosowywanie przechowywania plików i serializacji XML
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: d9722bed4bcf20fbdba322bea7cd3aab4328fa7e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31954155"
---
# <a name="customize-file-storage-and-xml-serialization"></a>Dostosowywanie magazynu plików i serializacja XML

Gdy użytkownik zapisuje wystąpienia, lub *modelu*, języka specyficznego dla domeny (DSL) w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], pliku XML jest tworzony lub aktualizowany. Plik można załadować ponownie, aby odtworzyć modelu w magazynie.

Schemat serializacji można dostosować, zmieniając ustawienia w obszarze **zachowanie serializacji Xml** w Eksploratorze DSL. Istnieje węzeł w węźle **zachowanie serializacji Xml** dla każdej domeny klasy, właściwości i relacji. Relacje znajdują się w ich klasy źródłowej. Istnieją również węzły odpowiadających kształtu, łącznik i diagramu klas.

Można również napisać kod programu do bardziej zaawansowanych dostosowania.

> [!NOTE]
> Jeśli chcesz zapisać modelu w określonym formacie, ale nie trzeba załadować go ponownie z tego formularza, należy wziąć pod uwagę przy użyciu szablonów tekstowych do generowania danych wyjściowych z modelu, zamiast schematu niestandardowej serializacji. Aby uzyskać więcej informacji, zobacz [generowania kodu języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="model-and-diagram-files"></a>Model i pliki diagramu

Każdy model jest zwykle zapisywane w dwa pliki:

-   Plik modelu ma nazwę **Model1.mydsl**. Przechowuje elementy modelu oraz relacji i ich właściwości. Rozszerzenie pliku, takich jak **.mydsl** jest określany przez **FileExtension** właściwość **edytor** węzła w definicji DSL.

-   Plik diagramu ma nazwę **Model1.mydsl.diagram**. Przechowuje kształtów, łączniki i ich pozycje, kolory, grubości linii i inne szczegóły wygląd diagramu. Jeśli użytkownik usunie **.diagram** pliku, ważne informacje w modelu nie są tracone. Układ diagramu zostaną utracone. Po otwarciu pliku modelu domyślnego zestawu kształtów oraz łączniki zostanie utworzony.

### <a name="to-change-the-file-extension-of-a-dsl"></a>Aby zmienić rozszerzenie pliku DSL

1.  Otwórz definicję DSL. W Eksploratorze DSL kliknij węzeł edytora.

2.  W oknie Właściwości Edytuj **FileExtension** właściwości. Nie dołączaj wstępnego "." rozszerzenie nazwy pliku.

3.  W Eksploratorze rozwiązań, Zmień nazwę elementu dwa pliki szablonów w **DslPackage\ProjectItemTemplates**. Te pliki mają nazwy, które odpowiada temu formatowi:

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>Domyślny schemat serializacji

Aby utworzyć przykład w tym temacie, użyto następującej definicji DSL.

![Diagram definicji DSL &#45; rodziny drzewa modelu](../modeling/media/familyt_person.png)

Ten DSL została użyta do utworzenia modelu, który ma następujące wygląd na ekranie.

![Diagram drzewa rodziny, przybornika i explorer](../modeling/media/familyt_instance.png)

Ten model został zapisany i ponownym otwarciu w edytorze tekstu XML:

```xml
<?xml version="1.0" encoding="utf-8"?>
<familyTreeModel xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="f817b728-e920-458e-bb99-98edc469d78f" xmlns="http://schemas.microsoft.com/dsltools/FamilyTree">
  <people>
    <person name="Henry VIII" birthYear="1491" deathYear="1547" age="519">
      <children>
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Mary" />
      </children>
    </person>
    <person name="Elizabeth I" birthYear="1533" deathYear="1603" age="477" />
    <person name="Mary" birthYear="1515" deathYear="1558" age="495" />
  </people>
</familyTreeModel>
```

Zwróć uwagę następujące kwestie dotyczące modelu serializacji:

-   Każdy węzeł XML ma nazwę, która jest taka sama jak nazwa klasy domeny, z wyjątkiem tego, że początkowej litery jest pisana małymi literami. Na przykład `familyTreeModel` i `person`.

-   Właściwości domeny, takie jak nazwa i rokurodzenia są serializowane jako atrybuty w węzłach XML. Ponownie początkowy znak nazwy właściwości jest konwertowany na małe litery.

-   Każdej relacji jest szeregowana jako węzeł XML zagnieżdżone w obrębie końca źródłowego relacji. Węzeł ma taką samą nazwę jako właściwość roli źródła, ale początkowej małe litery.

     Na przykład w definicji DSL, rolę o nazwie **osób** są uzyskiwane na **FamilyTree** klasy.  W pliku XML, to jest reprezentowany przez węzeł o nazwie `people` zagnieżdżone wewnątrz `familyTreeModel` węzła.

-   Docelowe zakończenie każda relacja osadzania jest szeregowana jako węzeł zagnieżdżony w relacji. Na przykład `people` węzła zawiera kilka `person` węzłów.

-   Docelowe zakończenie każdej relacji jest szeregowana jako *moniker*, który koduje odwołanie do elementu docelowego.

     Na przykład w obszarze `person` węzła, może być `children` relacji. Ten węzeł zawiera krótkie, takie jak:

    ```xml
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understand-monikers"></a>Zrozumienie monikerów

Monikery są używane do reprezentowania odsyłacze między poszczególnymi częściami plików modelu i diagramu. Są one również używane w `.diagram` pliku do odwoływania się do węzłów w pliku modelu. Istnieją dwie formy krótkiej nazwy:

-   *Monikery identyfikator* oferta identyfikator GUID elementu docelowego. Na przykład:

    ```xml
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />
    ```

-   *Kwalifikowana monikerów klucza* zidentyfikować elementu docelowego na podstawie wartości właściwości wyznaczoną domeną nazywany kluczem krótkiej nazwy. Prefiks krótkiej nazwy elementu docelowego krótkiej nazwy elementu nadrzędnego w drzewie osadzenia relacji.

     Poniższe przykłady są pobierane z DSL w którym jest klasą domeny o nazwie albumu, którego relacja osadzania do domeny klasy o nazwie utworu:

    ```xml
    <albumMoniker title="/My Favorites/Jazz after Teatime" />
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
    ```

     Kwalifikowana monikerów klucza zostaną użyte, jeśli Klasa docelowa ma właściwość domeny, dla którego opcję **jest klucz Moniker** ma ustawioną wartość `true` w **zachowanie serializacji Xml**. W tym przykładzie ta opcja jest ustawiona dla właściwości domeny o nazwie "Title" w klasach domeny "Album" i "Utworu".

Kwalifikowana monikerów klucza są bardziej czytelny niż monikerów identyfikator. Jeśli planujesz XML plików modelu do odczytania przez różne osoby, należy rozważyć użycie kwalifikowaną monikerów klucza. Jest jednak użytkownik może ustawić więcej niż jeden element ma ten sam klucz krótkiej nazwy. Zduplikowane klucze spowodować, że pliku nie można poprawnie załadować ponownie. W związku z tym po zdefiniowaniu klasy domeny, do którego odwołuje się przy użyciu kwalifikowanej monikerów klucza, należy rozważyć sposoby uniemożliwia użytkownikowi zapisywanie pliku, który ma zduplikowane monikerów.

### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Aby ustawić odwoływać się monikerów identyfikator klasy domeny

1.  Upewnij się, że **jest klucz Moniker** jest `false` dla każdej właściwości domeny w klasie i jej klas podstawowych.

    1.  W Eksploratorze DSL rozwiń **danych Behavior\Class szeregowanie Xml\\\<klasy domeny > \Element danych**.

    2.  Sprawdź, czy **jest klucz Moniker** jest `false` dla każdej właściwości domeny.

    3.  Jeśli klasa domeny ma klasy podstawowej, powtórz procedurę przez tę klasę.

2.  Ustaw **serializować identyfikator**  =  `true` dla klasy domeny.

     Tej właściwości można znaleźć w **zachowanie serializacji Xml**.

### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Aby ustawić klasę domeny, aby odwoływać się kwalifikowaną monikerów klucza

-   Ustaw **jest klucz Moniker** domeny właściwości istniejącej klasy domeny. Typ właściwości musi być `string`.

    1.  W Eksploratorze DSL rozwiń **danych Behavior\Class szeregowanie Xml\\\<klasy domeny > \Element danych**, a następnie wybierz właściwość domeny.

    2.  W oknie właściwości ustaw **jest klucz Moniker** do `true`.

-   \- lub -

     Tworzenie nowej klasy domeny, przy użyciu **klasy o nazwie domeny** narzędzia.

     To narzędzie tworzy nową klasę, który ma właściwość domeny o nazwie Name. **Jest nazwa elementu** i **jest klucz Moniker** właściwości tej właściwości domeny są inicjowane na `true`.

-   \- lub -

     Utwórz relację dziedziczenia z klasy domeny do innej klasy, która ma właściwość klucza krótkiej nazwy.

### <a name="avoid-duplicate-monikers"></a>Unikaj zduplikowanych monikerów

Jeśli używasz kwalifikowaną monikerów klucza, istnieje możliwość dwa elementy w modelu użytkownika mają taką samą wartość właściwości klucza. Na przykład jeśli Twoje DSL ma klasę osoby, która ma właściwość Name, użytkownika można ustawić nazwy dwa elementy te same. Mimo że modelu może być zapisany do pliku, jego czy nie zostanie odświeżona poprawnie.

Istnieje kilka metod, które pomagają uniknąć tej sytuacji:

-   Ustaw **jest nazwa elementu**  =  `true` dla właściwości klucza domeny. Wybierz właściwość domeny na diagramie DSL definicji, a następnie ustaw wartość w oknie właściwości.

     Gdy użytkownik tworzy nowe wystąpienie klasy, wartość ta powoduje, że właściwość domeny można automatycznie przypisać inną wartość. Domyślne zachowanie dodaje numer na końcu nazwy klasy. To nie uniemożliwia użytkownikowi zmianę duplikat nazwy, ale pomaga w przypadku, gdy użytkownik nie ustawiono wartość przed zapisaniem modelu.

-   Włącz weryfikację DSL. W Eksploratorze DSL wybierz Editor\Validation i ustaw **używa...**  właściwości `true`.

     Brak metody weryfikacji generowane automatycznie sprawdza dla niejednoznaczności. Metoda ta jest `Load` sprawdzania poprawności kategorii. Dzięki temu się upewnić, że użytkownik zostanie poinformowany o czy może nie być możliwe do ponownego otwarcia pliku.

     Aby uzyskać więcej informacji, zobacz [sprawdzania poprawności języka specyficznego dla domeny](../modeling/validation-in-a-domain-specific-language.md).

### <a name="moniker-paths-and-qualifiers"></a>Kwalifikatory i krótkiej nazwy ścieżek

Kwalifikowana moniker klucza kończy się wraz z kluczem krótkiej nazwy, a jest prefiksem moniker jego elementu nadrzędnego w drzewie osadzania. Na przykład, jeśli jest moniker albumu:

```xml
<albumMoniker title="/My Favorites/Jazz after Teatime" />
```

Następnie utworów muzycznych, w tym albumu może być:

```xml
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

Jednak jeśli albumów odwołuje się identyfikator zamiast tego, następnie krótkie, należy w następujący sposób:

```xml
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

Zwróć uwagę, że identyfikator GUID jest unikatowy, jego nigdy nie prefiks moniker jego elementu nadrzędnego.

Jeśli wiesz, czy właściwość konkretnej domeny zawsze będą mieć unikatową wartość w modelu, możesz ustawić **jest kwalifikator Moniker** do `true` dla tej właściwości. To spowoduje ona zostać użyta jako kwalifikator, bez użycia krótkiej nazwy elementu nadrzędnego. Na przykład, jeśli wartość **jest kwalifikator krótkiej nazwy** i **jest klucz Moniker** dla właściwości domeny tytuł albumu klasy, nazwy lub identyfikatora modelu nie jest używany w monikerów albumu i jego osadzonych elementy podrzędne:

```xml
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />
```

## <a name="customize-the-structure-of-the-xml"></a>Dostosowywanie struktury XML

Aby wprowadzić następujące modyfikacje, rozwiń węzeł **zachowanie serializacji Xml** węzła w Eksploratorze DSL. W obszarze klasą domeny rozwiń węzeł elementu danych, aby zapoznać się z listą właściwości i relacje, które biorą się w tej klasie. Wybierz relację i Dostosuj opcje w oknie właściwości.

-   Ustaw **pominąć Element** wartość "prawda", aby pominąć węzeł roli źródła, pozostawiając tylko na liście elementów docelowych. Nie należy ustawiać tej opcji, jeśli istnieje więcej niż jedną relację między klas źródłowych i docelowych.

    ```xml
    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>
    ```

-   Ustaw **użyj pełnej formy** do osadzenia węzły docelowe w węzłach reprezentujący wystąpienia relacji. Ta opcja jest ustawiany automatycznie podczas dodawania właściwości domeny do relacji domeny.

    ```xml
    <familyTreeModel ...>
      <people>
        <!-- The following node is inserted by using Use Full Form: -->
        <familyTreeModelHasPeople myRelationshipProperty="x1">
          <person name="Henry VIII" .../>
        </familyTreeModelHasPeople>
        <familyTreeModelHasPeople myRelationshipProperty="x2">
          <person name="Elizabeth I" .../>
        </familyTreeModelHasPeople>
      </people>
    </familyTreeModel>
    ```

-   Ustaw **reprezentacja** = **elementu** mieć właściwość domeny, zapisany jako element zamiast jako wartość atrybutu.

    ```xml
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

-   Aby zmienić kolejność serializacji atrybutów oraz relacji, kliknij prawym przyciskiem myszy element w obszarze danych elementu, a następnie użyj **Przenieś w górę** lub **Przenieś w dół** poleceń menu.

## <a name="major-customization-using-program-code"></a>Główne dostosowywania za pomocą kodu programu

Można zastąpić część lub całość algorytmów serializacji.

Zaleca się Przestudiowanie kod w **Dsl\Generated Code\Serializer.cs** i **SerializationHelper.cs**.

### <a name="to-customize-the-serialization-of-a-particular-class"></a>Aby dostosować serializacji konkretnej klasy

1.  Ustaw **jest niestandardowa** w węźle dla tej klasy w obszarze **zachowanie serializacji Xml**.

2.  Przekształć wszystkie szablony, Skompiluj rozwiązanie i zbadaj zwrócone błędy kompilacji. Komentarze niemal każdego błędu wyjaśnić kodu, jakie należy podać.

### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Aby podać własne serializacji dla całego modelu.

1.  Przesłaniaj metody w Dsl\GeneratedCode\SerializationHelper.cs

## <a name="options-in-xml-serialization-behavior"></a>Opcje w zachowaniu serializacji Xml

W Eksploratorze DSL węzeł zachowanie serializacji Xml zawiera węzeł podrzędny dla każdej klasy domeny, relacji, kształtu, łącznik i diagramu klas. W każdej z tych węzłów znajduje się lista właściwości i relacje powierzając jej ich konserwację, w tym elemencie. Relacje są reprezentowane zarówno we własnym imieniu, jak i w klasach ich źródła.

W poniższej tabeli przedstawiono opcje, które można ustawić w tej sekcji definicji DSL. W każdym przypadku wybierz element w Eksploratorze DSL i ustaw opcje w oknie właściwości.

### <a name="xml-class-data"></a>Dane XML — klasa

Te elementy znajdują się w Eksploratorze DSL w obszarze **danych Behavior\Class szeregowanie Xml**.

|||
|-|-|
|Właściwość|Opis|
|Ma schematu elementu niestandardowego|W przypadku wartości PRAWDA oznacza, że klasa domeny ma schematu elementu niestandardowego|
|Jest niestandardowe|Ustaw tę wartość na **True** Aby napisać własny kod serializacji i deserializacji dla tej klasy domeny.<br /><br /> Skompiluj rozwiązanie i zbadaj błędy, aby odnaleźć szczegółowe instrukcje.|
|Klasa domeny|Klasa domeny, którego dotyczy ten węzeł danych klasy. Tylko do odczytu.|
|Nazwa elementu|Nazwa węzła XML dla elementów tej klasy. Wartość domyślna to małe wersji nazwy klasy domeny.|
|Nazwa atrybutu krótkiej nazwy|Nazwa atrybutu używanego w elementach moniker zawiera odwołanie. Jeżeli pole pozostanie puste, nazwa właściwości klucza lub identyfikator jest używany.<br /><br /> W tym przykładzie jest "name":  `<personMoniker name="/Mike Nash"/>`|
|Nazwa elementu krótkiej nazwy|Nazwa elementu xml używane do krótkie, które odwołują się do elementów tej klasy.<br /><br /> Wartość domyślna to małe wersji z "Moniker" sufiksem nazwy klasy. Na przykład `personMoniker`.|
|Nazwa typu krótkiej nazwy|Nazwa typu xsd wygenerowany dla monikerów elementy tej klasy. Trwa XSD **kod Dsl\Generated\\\*Schema.xsd**|
|Identyfikator serializacji|Jeśli PRAWDA, identyfikatora GUID elementu znajduje się w pliku. Musi to być wartość true, jeśli nie ma właściwości, który jest oznaczony jako **jest klucz Moniker** i DSL definiuje relacji odwołania do tej klasy.|
|Nazwa typu|Nazwa typu xml wygenerowanych w xsd z klasy wyznaczoną domeną.|
|Uwagi|Nieformalne informacje skojarzone z tym elementem|

### <a name="xml-property-data"></a>Dane XML właściwości

Właściwości XML węzły znajdują się w węzłach klasy.

|||
|-|-|
|Właściwość|Opis|
|Właściwość domeny|Właściwość, którego dotyczy dane konfiguracji serializacji xml. Tylko do odczytu.|
|Krótka nazwa klucza|Jeśli PRAWDA, właściwość jest używana jako klucz służący do tworzenia krótkie, które odwołują się do wystąpienia tej klasy domeny.|
|Jest kwalifikator krótkiej nazwy|Jeśli PRAWDA, właściwość jest używana do tworzenia w monikerów kwalifikator. Jeśli ma wartość FAŁSZ, a nie jest spełniony dla tej klasy domeny SerializeId, monikerów jest kwalifikowana krótkiej nazwy elementu nadrzędnego w drzewie osadzania.|
|Reprezentacja wartości|Jeśli atrybut, właściwość jest szeregowana jako atrybut xml; Jeśli Element jest serializowany jako element; Jeśli Ignoruj, nie jest serializowany.|
|Nazwa XML|Nazwa atrybutu xml lub element reprezentujący właściwość. Domyślnie jest to wersja małe nazwy właściwości domeny.|
|Uwagi|Nieformalne informacje skojarzone z tym elementem|

### <a name="xml-role-data"></a>Dane XML roli

Węzły danych roli znajdują się w węzłach klasy źródłowej.

|Właściwość|Opis|
|--------------|-----------------|
|Ma Moniker niestandardowych|Ustaw na true, jeśli chcesz udostępnić własny kod do generowania i rozpoznawania monikerów przechodzących przez tę relację.<br /><br /> Aby uzyskać szczegółowe instrukcje Skompiluj rozwiązanie, a następnie kliknij dwukrotnie komunikaty o błędach.|
|Relacja domeny|Określa relację, do którego te opcje są stosowane. Tylko do odczytu.|
|Pomiń — Element|Jeśli PRAWDA, węzeł XML, który odpowiada roli źródłowej została pominięta ze schematu.<br /><br /> Jeśli istnieje więcej niż jedną relację między klas źródłowych i docelowych, ten węzeł roli rozróżnia linki, które należą do dwie relacje. Dlatego zaleca się, że nie ustawisz tę opcję, w tym przypadku.|
|Nazwa elementu w roli|Określa nazwę elementu XML, który jest określana na podstawie roli źródłowej. Wartość domyślna to nazwa właściwości roli.|
|Użyj pełnej formy|Jeśli PRAWDA, każdego elementu docelowego lub krótkiej nazwy jest ujęta w węźle XML reprezentujący relacji. To powinno ustawioną wartość true, jeśli relacja ma właściwości domeny.|

## <a name="see-also"></a>Zobacz też

- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)