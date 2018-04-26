---
title: Nawigowanie i aktualizowanie modelu w kodzie programu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7e98be1dd16705be00f388419013686f861f3753
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="navigate-and-update-a-model-in-program-code"></a>Nawigowanie i aktualizowanie modelu w kodzie programu

Można napisać kod, aby tworzyć i usuwać elementy modelu, ustawiania ich właściwości, tworzenie i usuwanie łącza między elementami. Wszystkie zmiany muszą być wprowadzane w obrębie transakcji. Jeśli elementy są wyświetlane na diagramie, diagramu będzie je "poprawić" automatycznie po zakończeniu transakcji.

## <a name="in-this-topic"></a>W tym temacie
 [Przykład definicji DSL](#example)

 [Nawigowanie po modelu](#navigation)

 [Uzyskiwanie dostępu do informacji o klasie](#metadata)

 [Dokonać zmian w transakcji](#transaction)

 [Tworzenie elementów modelu](#elements)

 [Tworzenie relacji łączy](#links)

 [Usuwanie elementów](#deleteelements)

 [Usuwanie relacji łącza](#deletelinks)

 [Zmiana kolejności łączy relacji](#reorder)

 [Blokady](#locks)

 [Kopiowanie i wklejanie](#copy)

 [Nawigowanie i aktualizowanie diagramami](#diagrams)

 [Przechodzenie między kształtami i elementy](#views)

 [Właściwości łączników i kształtów](#shapeProperties)

 [Widok dokumentu i danych dokumentu](#docdata)

##  <a name="example"></a> Przykład definicji DSL
 To jest główna część DslDefinition.dsl przykłady w tym temacie:

 ![Diagram definicji DSL &#45; model drzewa rodziny](../modeling/media/familyt_person.png "FamilyT_Person")

 Ten model jest wystąpienie tego DSL:

 ![Model drzewa rodziny Tudorów](../modeling/media/tudor_familytreemodel.png "Tudor_FamilyTreeModel")

### <a name="references-and-namespaces"></a>Referencje i przestrzenie nazw
 Aby uruchomić kod w tym temacie, powinien odwoływać:

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 Kod użyje tej przestrzeni nazw:

 `using Microsoft.VisualStudio.Modeling;`

 Ponadto podczas pisania kodu w innym projekcie niż ten, w którym jest zdefiniowana z DSL, należy zaimportować zestaw jest konstruowany przez projekt Dsl.

##  <a name="navigation"></a> Nawigowanie po modelu

### <a name="properties"></a>Właściwości
 Właściwości domeny, które można zdefiniować w definicji DSL stają się właściwości, które są dostępne w kodzie programu:

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 Jeśli chcesz ustawić właściwość, należy to zrobić w [transakcji](#transaction):

 `henry.Name = "Henry VIII";`

 Jeśli w DSL definicji, właściwość **rodzaj** jest **obliczona**, nie można go ustawić. Aby uzyskać więcej informacji, zobacz [obliczona i właściwości magazynu niestandardowe](../modeling/calculated-and-custom-storage-properties.md).

### <a name="relationships"></a>Relacje
 Relacje domeny, które można zdefiniować w definicji DSL stają się pary właściwości jednej klasy na końcach relacji. Nazwy właściwości są wyświetlane na diagramie DslDefinition jako etykiety na ról na każdej stronie relacji. W zależności od Liczebność roli typ właściwości jest klasa na drugim końcu relacji lub kolekcji tej klasy.

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 Właściwości w przeciwną końców relacji są zawsze wzajemne. Po utworzeniu lub usunięciu łącze Właściwości roli na obu elementów są aktualizowane. Poniższe wyrażenie (który używa rozszerzeń `System.Linq`) zawsze ma wartość true dla relacji ParentsHaveChildren w przykładzie:

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**. Relacja również jest reprezentowany przez element modelu o nazwie *łącze*, który jest wystąpieniem typu relacji domeny. Łącze ma zawsze element jedno źródło i element docelowy jeden. Source element może być taka sama jak element docelowy.

 Uzyskać dostęp do łącza i jego właściwości:

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 Domyślnie nie więcej niż jedno wystąpienie relacji może połączyć jakiejkolwiek parze elementy modelu. Jednak jeśli w definicji DSL `Allow Duplicates` flaga ma wartość true dla tej relacji może istnieć więcej niż jednego połączenia i należy użyć `GetLinks`:

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 Istnieją także inne metody do uzyskiwania dostępu do łącza. Na przykład:

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **Ukryte ról.** Jeśli w definicji DSL **wygenerowaniu właściwości** jest **false** dla określonej roli, następnie właściwość nie jest generowany odpowiadający danej roli. Można nadal dostęp do łącza i przechodzenia łącza za pomocą metod relacji:

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 Przykład najczęściej używanych <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relacji, która łączy elementu modelu do kształtu, który wyświetla na diagramie:

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>Element katalogu
 Aby dostęp do wszystkich elementów w magazynie przy użyciu katalogu elementów:

 `store.ElementDirectory.AllElements`

 Dostępne są również metody wyszukiwania elementów, takich jak następujące:

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

##  <a name="metadata"></a> Uzyskiwanie dostępu do informacji o klasie
 Możesz uzyskać informacje dotyczące klas, relacje i innych aspektów definicji DSL. Na przykład:

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 Elementy modelu klas są następujące:

-   ModelElement — wszystkie elementy i relacje są ModelElements

-   ElementLink — wszystkie relacje są ElementLinks

##  <a name="transaction"></a> Dokonać zmian w transakcji
 Przy każdej zmianie kodu źródłowego w magazynie go zrobić wewnątrz transakcji. Dotyczy to wszystkich elementów modelu, relacje kształtów, diagramy i ich właściwości. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Modeling.Transaction>.

 Najwygodniejsza metoda zarządzania transakcji jest i `using` instrukcji ujęta w `try...catch` instrukcji:

```
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 Możesz wprowadzić dowolną liczbę zmian w jednej transakcji. Można otwierać nowych transakcji w aktywnej transakcji.

 Aby zmiany były trwałe, należy `Commit` transakcji przed jego usunięcia. Jeśli wystąpi wyjątek, który nie zawiera wewnątrz transakcji, magazynie zostaną zresetowane do stanu przed wprowadzeniem zmian.

##  <a name="elements"></a> Tworzenie elementów modelu
 W tym przykładzie dodaje element do istniejącego modelu:

```
FamilyTreeModel familyTree = ...; // The root of the model.
using (Transaction t =
    familyTree.Store.TransactionManager
    .BeginTransaction("update model"))
{
  // Create a new model element
  // in the same partition as the model root:
  Person edward = new Person(familyTree.Partition);
  // Set its embedding relationship:
  edward.FamilyTreeModel = familyTree;
          // same as: familyTree.People.Add(edward);
  // Set its properties:
  edward.Name = "Edward VII";
  t.Commit(); // Don't forget this!
}
```

 W tym przykładzie przedstawiono tych podstawowych punktów o tworzeniu elementu:

-   Tworzenie nowego elementu w określonej partycji magazynu. Dla elementów modeli i relacje, ale nie do kształtów zazwyczaj jest to partycja domyślne.

-   Utwórz element docelowy relacji osadzania. W DslDefinition w tym przykładzie każda osoba musi być elementem docelowym FamilyTreeHasPeople relacja osadzania. Można to osiągnąć, możemy ustawić właściwości roli FamilyTreeModel obiektu osoby lub Dodaj osobę do osób właściwości roli obiektu FamilyTreeModel.

-   Ustaw właściwości nowego elementu, szczególnie właściwości, dla którego `IsName` ma wartość true w DslDefinition. Ta flaga oznacza właściwość, która służy do identyfikowania elementu jednoznacznie wewnątrz jego właściciela. W takim przypadku właściwość Name ma tę flagę.

-   Definicja DSL tego DSL musi zostały załadowane do magazynu. Jeśli piszesz rozszerzenia, takie jak polecenie menu, zazwyczaj będzie już wartość true. W pozostałych przypadkach można jawnie załadować modelu do magazynu, lub użyj <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus> go załadować. Aby uzyskać więcej informacji, zobacz [porady: Otwieranie modelu z pliku w kodzie programu](../modeling/how-to-open-a-model-from-file-in-program-code.md).

 Po utworzeniu elementu w ten sposób kształt jest tworzony automatycznie (jeśli DSL ma diagramu). Prawdopodobnie jest automatycznie przypisywana lokalizację, z domyślnego kształtu, kolor i inne funkcje. Jeśli chcesz kontrolować jak i gdzie skojarzonego kształtu, zobacz [tworzenia elementu i jego kształtu](#merge).

##  <a name="links"></a> Tworzenie relacji łączy
 Istnieją dwie relacje zdefiniowane w tym przykładzie definicji DSL. Definiuje każdej relacji *właściwości roli* w klasie na końcach relacji.

 Istnieją trzy sposoby, w których można utworzyć wystąpienia relacji. Każda z tych trzech metod ma ten sam efekt:

-   Ustaw właściwość obiektu pełniącego rolę źródła. Na przykład:

    -   `familyTree.People.Add(edward);`

    -   `edward.Parents.Add(henry);`

-   Ustaw właściwość docelowego obiektu pełniącego rolę. Na przykład:

    -   `edward.familyTreeModel = familyTree;`

         Liczebność ta rola jest `1..1`, dlatego firma Microsoft przypisuje wartość.

    -   `henry.Children.Add(edward);`

         Liczebność ta rola jest `0..*`, więc dodania do kolekcji.

-   Jawnie utworzyć wystąpienia relacji. Na przykład:

    -   `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

    -   `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

 Ostatnia metoda jest przydatna, jeśli chcesz ustawić właściwości samą relację.

 Po utworzeniu elementu w ten sposób jest tworzony automatycznie łącznika na diagramie, ale ma ona domyślnego kształtu, kolor i inne funkcje. Aby kontrolować sposób tworzenia łącznika skojarzony, zobacz [tworzenia elementu i jego kształtu](#merge).

##  <a name="deleteelements"></a> Usuwanie elementów
 Usuń element przez wywołanie metody `Delete()`:

 `henry.Delete();`

 Ta operacja spowoduje również usunięcie:

-   Relacja łącza do i z elementu. Na przykład `edward.Parents` nie będą już miały `henry`.

-   Elementy w ról, dla którego `PropagatesDelete` flaga ma wartość true. Na przykład kształtu, który zawiera element zostaną usunięte.

 Domyślnie każdy relacja osadzania ma `PropagatesDelete` prawdziwe w roli docelowej. Usuwanie `henry` nie powoduje usunięcia `familyTree`, ale `familyTree.Delete()` spowoduje usunięcie wszystkich `Persons`. Aby uzyskać więcej informacji, zobacz [Dostosowywanie sposób usuwania](../modeling/customizing-deletion-behavior.md).

 Domyślnie `PropagatesDelete` nie jest spełniony dla ról relacji odwołania.

 Może spowodować reguły usuwania pominąć propagacji określonych podczas usuwania obiektu. Jest to przydatne, jeśli są podstawiając jednego elementu na inny. Należy podać identyfikator GUID jedną lub więcej ról, dla których należy nie propagowane usunięcia. Można uzyskać identyfikatora GUID z klasy relacji:

 `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

 (W tym przykładzie określonego czy nie mają wpływu, ponieważ `PropagatesDelete` jest `false` dla ról `ParentsHaveChildren` relacji.)

 W niektórych przypadkach usunięcie powiedzie się istnienie blokady, elementu lub w elemencie zostaną usunięte przez propagacji. Można użyć `element.CanDelete()` do sprawdzenia, czy element może zostać usunięte.

##  <a name="deletelinks"></a> Usuwanie relacji łącza
 Można usunąć relacji łącza przez usunięcie elementu z właściwością roli:

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 Można również jawnie usunąć łącza:

 `edwardHenryLink.Delete();`

 Te trzy metody wszystkie mają ten sam efekt. Należy użyć jednej z nich.

 Jeśli rola ma liczebność od 0 do 1 lub 1.. 1, można ją ustawić, `null`, lub z inną wartością:

 `edward.FamilyTreeModel = null;` lub:

 `edward.FamilyTreeModel = anotherFamilyTree;`

##  <a name="reorder"></a> Zmiana kolejności łączy relacji
 Łącza w określonej relacji powierzając jej ich konserwację lub celem elementu określonego modelu mają określonej kolejności. Pojawią się one w kolejności, w jakiej zostały dodane. Na przykład niniejszych zawsze da elementów podrzędnych w tej samej kolejności:

 `foreach (Person child in henry.Children) ...`

 Można zmienić kolejności łączy:

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

##  <a name="locks"></a> Blokady
 Zmiany może być niemożliwe przez blokady. Można ustawić blokady na poszczególne elementy, partycji i magazynu. Jeśli dowolne z tych poziomów blokada uniemożliwia rodzaju zmiany, które mają być, może być wyjątek przy próbie jego. Aby wykryć, czy blokady są skonfigurowane przy użyciu elementu. GetLocks(), czyli metody rozszerzenia, który jest zdefiniowany w przestrzeni nazw <xref:Microsoft.VisualStudio.Modeling.Immutability>.

 Aby uzyskać więcej informacji, zobacz [Definiowanie zasad blokowania do tworzenia segmentów tylko do odczytu](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).

##  <a name="copy"></a> Kopiowanie i wklejanie
 Można skopiować elementów lub grup elementów <xref:System.Windows.Forms.IDataObject>:

```
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 Elementy są przechowywane jako serializacji grupy elementów.

 Elementy z elementu IDataObject można scalić modelu:

```
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()` można zaakceptować albo `PresentationElement` lub `ModelElement`. Jeśli zostanie nadana `PresentationElement`, można również określić pozycji na diagramie docelowy jako trzeci parametr.

##  <a name="diagrams"></a> Nawigowanie i aktualizowanie diagramami
 W DSL element modelu domeny, który reprezentuje pojęcia, takie jak osoby lub utworu, różni się od elementu kształtu, który reprezentuje informacje wyświetlane na diagramie. Element modelu domeny przechowuje ważne właściwości i relacje pojęcia. Element kształtu przechowuje rozmiar, pozycja i kolor widok obiektu na diagramie, a układ jego składniki.

### <a name="presentation-elements"></a>Elementy prezentacji
 ![Diagram klas typów podstawowych kształt i element](../modeling/media/dslshapesandelements.png "DSLshapesAndElements")

 W definicji DSL każdy element, który określisz tworzy klasę, która jest określana na podstawie jednej z następujących klas standardowa.

|Rodzaj elementu|Klasa podstawowa|
|---------------------|----------------|
|Klasa domeny|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|Relacja domeny|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|Kształt|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|Łącznik|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|Diagram|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 Element na diagramie zazwyczaj reprezentuje elementu modelu. Zazwyczaj (ale nie zawsze) <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> reprezentuje wystąpienie klasy domeny, a <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> reprezentuje wystąpienie relacji domeny. <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> Relacji łączy kształt węzła lub łącze do elementu modelu, który reprezentuje.

 Należy co kształt węzła lub łącze do jeden diagram. Kształt łącze binarne łączy dwa kształty węzła.

 Kształty mogą mieć kształty podrzędne w dwóch zestawów. Kształt `NestedChildShapes` zestawu jest ograniczona do obwiedni jego elementu nadrzędnego. Kształt `RelativeChildShapes` listy może występować poza lub częściowo poza granicami nadrzędnego — na przykład etykieta lub portu. Nie ma diagramu `RelativeChildShapes` i nie `Parent`.

###  <a name="views"></a> Przechodzenie między kształtami i elementy
 Elementy modelu domeny i kształtu są powiązane przez <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relacji.

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 Tej samej relacji łączy relacje łączników na diagramie:

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 Ta relacja zawiera również linki katalogu głównego modelu do diagramu:

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 Aby uzyskać element modelu reprezentowanego przez kształtu, należy użyć:

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>Nawigowanie po wokół diagramu
 Ogólnie rzecz biorąc nie jest zalecane do przechodzenia między kształtami i łącznikami na diagramie. Warto nawigowanie po relacjach w modelu, przenoszenie między kształtami i łącznikami tylko wtedy, gdy jest to niezbędne do pracy nad wygląd diagramu. Te metody łączy łączniki do kształtów na końcach:

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 Wiele kształtów są kompozyty; składają się kształtu nadrzędnego i warstwy jeden lub więcej elementów podrzędnych. Kształty, które są pozycjonowane względem innego kształtu są określane jako jego *dzieci*. Gdy przesuwa kształtu nadrzędnego, elementy podrzędne są przenoszone wraz z nią.

 *Względne dzieci* może występować poza obwiednią kształtu nadrzędnego. *Zagnieżdżone* elementy podrzędne są wyświetlane wyłącznie wewnątrz granic elementu nadrzędnego.

 Aby uzyskać zestaw top kształtów na diagramie, należy użyć:

 `Diagram.NestedChildShapes`

 Klasy nadrzędnej kształtów i łączników są:

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *YourShape*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *YourConnector*

###  <a name="shapeProperties"></a> Właściwości łączników i kształtów
 W większości przypadków nie jest to niezbędne do zapewnienia jawne zmiany do kształtów. Zmiana elementów modelu reguły "Napraw" zaktualizować kształty i łączniki. Aby uzyskać więcej informacji, zobacz [reagowania na zagrożenia i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md).

 Jednak zaleca się zmianę niektórych jawnej kształtów we właściwościach, które są niezależne od elementów modelu. Na przykład można zmienić właściwości:

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A> -Określa wysokość i szerokość kształtu.

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> -pozycji względem kształtu nadrzędnego lub diagram

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A> -zestaw pióra i pędzle używany do rysowania kształtu lub łącznika

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A> -sprawia, że kształt jest niewidoczne

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A> -powoduje, że kształt jest widoczna po `Hide()`

###  <a name="merge"></a> Tworzenie elementu i jego kształtu
 Podczas tworzenia elementu i połączyć ją do drzewa relacji osadzenia, kształt jest automatycznie tworzone i skojarzonych z nim. Jest to realizowane przez reguły "naprawy", które są wykonywane po zakończeniu transakcji. Kształt pojawi się w lokalizacji automatycznie przypisywany i jego kształtu, kolor i inne funkcje będą mają przypisane wartości domyślne. Aby kontrolować sposób tworzenia kształtu, można użyć funkcji scalania. Najpierw dodaj elementy, które mają zostać dodane do elementu elementgroup przy, a następnie scalić grupy do diagramu.

 Tej metody:

-   Ustawia nazwę, jeśli przypisano właściwości jako nazwa elementu.

-   Stosuje wszelkie dyrektywy elementu scalania określone w definicji DSL.

 W tym przykładzie tworzy kształt na pozycji myszy, gdy użytkownik kliknie dwukrotnie diagramu. W definicji DSL dla tego przykładu `FillColor` właściwość `ExampleShape` zostały udostępnione.

```

using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
partial class MyDiagram
{
  public override void OnDoubleClick(DiagramPointEventArgs e)
  {
    base.OnDoubleClick(e);

    using (Transaction t = this.Store.TransactionManager
        .BeginTransaction("double click"))
    {
      ExampleElement element = new ExampleElement(this.Store);
      ElementGroup group = new ElementGroup(element);

      { // To use a shape of a default size and color, omit this block.
        ExampleShape shape = new ExampleShape(this.Partition);
        shape.ModelElement = element;
        shape.AbsoluteBounds = new RectangleD(0, 0, 1.5, 1.0);
        shape.FillColor = System.Drawing.Color.Azure;
        group.Add(shape);
      }

      this.ElementOperations.MergeElementGroupPrototype(
        this,
        group.CreatePrototype(),
        PointD.ToPointF(e.MousePosition));
      t.Commit();
    }
  }
}

```

 Jeśli podano więcej niż jeden kształt, należy ustawić ich położenia przy użyciu `AbsoluteBounds`.

 Można również ustawić, kolor i inne ujawnionych właściwości łączników, przy użyciu tej metody.

### <a name="use-transactions"></a>Użyj transakcji
 Kształty, łączniki i diagramy są podtypów <xref:Microsoft.VisualStudio.Modeling.ModelElement> i na żywo w magazynie. W związku z tym należy zmiany do nich tylko wewnątrz transakcji. Aby uzyskać więcej informacji, zobacz [porady: użycie transakcji do aktualizacji modelu](../modeling/how-to-use-transactions-to-update-the-model.md).

##  <a name="docdata"></a> Wyświetlanie dokumentów i danych dokumentu
 ![Diagram klas typów standardowe diagram](../modeling/media/dsldiagramsanddocs.png "DSLDiagramsandDocs")

## <a name="store-partitions"></a>Partycje magazynu
 Podczas ładowania modelu towarzyszący diagram został załadowany w tym samym czasie. Zazwyczaj modelu jest ładowany do Store.DefaultPartition, a zawartość diagramu zostanie załadowana do innej partycji. Zwykle zawartości każdej partycji jest załadowany i zapisane do pliku.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.Modeling.ModelElement>
- [Walidacja w języku specyficznym dla domeny](../modeling/validation-in-a-domain-specific-language.md)
- [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)
- [Instrukcje: Użycie transakcji do aktualizacji modelu](../modeling/how-to-use-transactions-to-update-the-model.md)
- [Integrowanie modeli za pomocą Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Odpowiadanie na zmiany i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md)
