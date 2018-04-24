---
title: Dostosowywanie zachowania dotyczącego kopiowania
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 603f66a6f9966aaab8758771a345a211feebe8ad
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="customizing-copy-behavior"></a>Dostosowywanie zachowania dotyczącego kopiowania
W języku specyficznego dla domeny (DSL) utworzone za pomocą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wizualizacji i modelowania SDK, można zmienić, co się dzieje, gdy użytkownik kopiuje i wkleja elementów.

## <a name="standard-copy-and-paste-behavior"></a>Standardowe kopiowania i wklejania zachowania
 Aby włączyć kopiowanie, ustaw **Włącz kopiowania/wklejania** właściwość **edytor** węzła w Eksploratorze DSL.

 Domyślnie gdy użytkownik kopiuje elementy do Schowka, następujące elementy są również kopiowane:

-   Osadzone obiekty podrzędne wybrane elementy. (Oznacza to, elementy, które są elementy docelowe osadzenia relacje, które biorą się na skopiowane elementy).

-   Łącza relacji między skopiowane elementy.

 Ta reguła dotyczy rekursywnie skopiowane elementy i łącza.

 ![Skopiować i wkleić elementy](../modeling/media/dslcopypastedefault.png "DslCopyPasteDefault")

 Skopiowane elementy i łącza są serializowane i przechowywane w <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), który znajduje się w Schowku.

 Obraz skopiowane elementy również znajduje się w Schowku. Dzięki temu użytkownikowi na wklejanie w innych aplikacjach, takich jak Word.

 Użytkownik może Wklej skopiowane elementy do obiektu docelowego, który może zaakceptować elementy zgodnie z definicją DSL. Na przykład w DSL, wygenerowane z szablonu rozwiązania składników, użytkownik wkleić porty na składniki, ale nie na diagram; i wkleić składników na diagramie, ale nie do innych składników.

## <a name="customizing-copy-and-paste-behavior"></a>Dostosowywanie kopiowania i wklejania zachowanie
 Aby uzyskać więcej informacji dotyczących dostosowywania modelu przy użyciu kodu programu, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

 **Włącz lub Wyłącz kopiowanie, wycinanie i wklejanie.**
W Eksploratorze DSL ustawić **Włącz kopiowania/wklejania** właściwość **edytor** węzła.

 **Skopiuj łącza do tego samego obiektu docelowego.** Na przykład do pole Komentarz skopiowane połączone z tego samego elementu podmiotu.
Ustaw **propaguje kopiowania** właściwości roli do **propagację kopiowania, aby połączyć tylko**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie zachowania Kopiuj Link](#customizeLinks).

 Skopiuj połączonych elementów. Na przykład podczas kopiowania nowego elementu kopie pól połączonego komentarz stają się również.
Ustaw **propaguje kopiowania** właściwości roli do **propagację kopiowania do łącza i przeciwne obiektu pełniącego rolę**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie zachowania Kopiuj Link](#customizeLinks).

 **Przez kopiowanie i wklejanie szybko zduplikowane elementy.** Zwykły element, który został skopiowany nadal jest zaznaczone, a nie można wkleić ten sam typ elementu na niego.
Dodaj Element scalania dyrektywy do klasy domeny i ustaw ją do scalenia do przodu do klasy nadrzędnej. Będzie to mieć ten sam efekt operacji przeciągania. Aby uzyskać więcej informacji, zobacz [Dostosowywanie Element tworzenia i przepływu](../modeling/customizing-element-creation-and-movement.md).

 \- lub -

 Wybierz diagram przed wklejeniem elementów, przez zastąpienie `ClipboardCommandSet.ProcessOnPasteCommand()`. Dodaj ten kod w pliku użytkownika projektu DslPackage:

```csharp
namespace Company.MyDsl {
using System.Linq;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Shell;
partial class MyDslClipboardCommandSet
{
  protected override void ProcessOnMenuPasteCommand()
  {
 // Deselect the current selection after copying:
 Diagram diagram = (this.CurrentModelingDocView as SingleDiagramDocView).Diagram;
    this.CurrentModelingDocView
     .SelectObjects(1, new object[] { diagram }, 0);
  }
} }

```

 **Utwórz dodatkowe łącza, gdy użytkownik wkleja na wybranego celu.** Na przykład pole komentarza wklejeniu na element, łącze się między nimi.
Dodaj dyrektywę scalania Element do klasy docelowej domeny i ustaw ją do przetworzenia przez dodawanie łączy scalania. Będzie to mieć ten sam efekt operacji przeciągania. Aby uzyskać więcej informacji, zobacz [Dostosowywanie Element tworzenia i przepływu](../modeling/customizing-element-creation-and-movement.md).

 \- lub -

 Zastąpienie `ClipboardCommandSet.ProcessOnPasteCommand()` utworzyć dodatkowe linki po wywołaniu metody podstawowej.

 **Dostosowywanie formatów, w których mogą zostać skopiowane elementy** do aplikacji zewnętrznych — na przykład, aby dodać obramowanie do formularza mapy bitowej.
Zastąpienie *MyDsl* `ClipboardCommandSet.ProcessOnMenuCopyCommand()` w projekcie DslPackage.

 **Dostosowywanie, jak są kopiowane elementy do Schowka za pomocą polecenia kopiowania, ale nie w operacji przeciągania.**
Zastąpienie *MyDsl* `ClipboardCommandSet.CopyModelElementsIntoElementGroupPrototype()` w projekcie DslPackage.

 **Zachowaj układ kształt za pomocą kopiowania i wklejania.**
Gdy użytkownik kopiuje wielu kształtów, gdy zostaną wklejone można zachować ich położenia. Ta technika jest przedstawiona na przykładzie na [VMSDK: Przykładowe schematy obwodów](http://go.microsoft.com/fwlink/?LinkId=213879).

 Osiągnąć, Dodaj kształty i łączniki do ElementGroupPrototype skopiowane. Jak najdogodniejszy metody do przesłonięcia jest ElementOperations.CreateElementGroupPrototype(). Aby to zrobić, Dodaj następujący kod do projektu Dsl:

```csharp

public class MyElementOperations : DesignSurfaceElementOperations
{
  // Create an EGP to add to the clipboard.
  // Called when the elements to be copied have been
  // collected into an ElementGroup.
 protected override ElementGroupPrototype CreateElementGroupPrototype(ElementGroup elementGroup, ICollection<ModelElement> elements, ClosureType closureType)
  {
 // Add the shapes and connectors:
 // Get the elements already in the group:
    ModelElement[] mels = elementGroup.ModelElements
        .Concat(elementGroup.ElementLinks) // Omit if the paste target is not the diagram.
        .ToArray();
 // Get their shapes:
    IEnumerable<PresentationElement> shapes =
       mels.SelectMany(mel =>
            PresentationViewsSubject.GetPresentation(mel));
    elementGroup.AddRange(shapes);

 return base.CreateElementGroupPrototype
           (elementGroup, elements, closureType);
  }

 public MyElementOperations(IServiceProvider serviceProvider, ElementOps1Diagram diagram)
      : base(serviceProvider, diagram)
  { }
}

// Replace the standard ElementOperations
// singleton with your own:
partial class MyDslDiagram // EDIT NAME
{
 /// <summary>
 /// Singleton ElementOperations attached to this diagram.
 /// </summary>
 public override DesignSurfaceElementOperations ElementOperations
  {
 get
    {
 if (singleton == null)
      {
        singleton = new MyElementOperations(this.Store as IServiceProvider, this);
      }
 return singleton;
    }
  }
 private MyElementOperations singleton = null;
}

```

 **Wklejanie kształtów w wybranej lokalizacji, np. w bieżącej pozycji kursora.**
Gdy użytkownik kopiuje wielu kształtów, gdy zostaną wklejone można zachować ich położenia. Ta technika jest przedstawiona na przykładzie na [VMSDK: Przykładowe schematy obwodów](http://go.microsoft.com/fwlink/?LinkId=213879).

 Aby uzyskać ten efekt, Przesłoń `ClipboardCommandSet.ProcessOnMenuPasteCommand()` Aby użyć lokalizacji określonej wersji `ElementOperations.Merge()`. Aby to zrobić, Dodaj następujący kod w projekcie DslPackage:

```csharp

partial class MyDslClipboardCommandSet // EDIT NAME
{
   /// <summary>
    /// This method assumes we only want to paste things onto the diagram
    /// - not onto anything contained in the diagram.
    /// The base method pastes in a free space on the diagram.
    /// But if the menu was used to invoke paste, we want to paste in the cursor position.
    /// </summary>
    protected override void ProcessOnMenuPasteCommand()
    {

  NestedShapesSampleDocView docView = this.CurrentModelingDocView as NestedShapesSampleDocView;

      // Retrieve data from clipboard:
      System.Windows.Forms.IDataObject data = System.Windows.Forms.Clipboard.GetDataObject();

      Diagram diagram = docView.CurrentDiagram;
      if (diagram == null) return;

      if (!docView.IsContextMenuShowing)
      {
        // User hit CTRL+V - just use base method.

        // Deselect anything that's selected, otherwise
        // pasted item will be incompatible:
        if (!this.IsDiagramSelected())
        {
          docView.SelectObjects(1, new object[] { diagram }, 0);
        }

        // Paste into a convenient spare space on diagram:
    base.ProcessOnMenuPasteCommand();
      }
      else
      {
        // User right-clicked - paste at mouse position.

        // Utility class:
        DesignSurfaceElementOperations op = diagram.ElementOperations;

        ShapeElement pasteTarget = diagram;

        // Check whether what's in the paste buffer is acceptable on the target.
        if (pasteTarget != null && op.CanMerge(pasteTarget, data))
        {

        // Although op.Merge would be a no-op if CanMerge failed, we check CanMerge first
          // so that we don't create an empty transaction (after which Undo would be no-op).
          using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("paste"))
          {
            PointD place = docView.ContextMenuMousePosition;
            op.Merge(pasteTarget, data, PointD.ToPointF(place));
            t.Commit();
          }
        }
      }
    }
  }
```

 **Umożliwia użytkownikowi na przeciąganie i upuszczanie elementów.**
Zobacz [porady: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md).

##  <a name="customizeLinks"></a> Dostosowywanie zachowania Kopiuj Link
 Gdy użytkownik kopiuje element, standardowe zachowanie jest wszelkie elementy osadzone są również kopiowane. Można zmodyfikować standard kopiowanie zachowanie. W definicji DSL, wybierz rolę po jednej stronie relacji i w zestawie okna właściwości **propaguje kopiowania** wartość.

 ![Propaguje właściwości kopii roli domeny](../modeling/media/dslpropagatescopy.png "DslPropagatesCopy")

 Istnieją trzy wartości:

-   Nie propagację kopiowania

-   Propagacja kopiowania, aby powiązać tylko — po wklejeniu grupy, nową kopię tego łącza odnoszą się do istniejącego elementu na drugim końcu łącza.

-   Propagacja kopiowania, aby połączyć i przeciwne obiektu pełniącego rolę - skopiowane grupa zawiera kopię elementu na drugim końcu łącza.

 ![Efekt kopiowania z PropagateCopyToLinkOnly](../modeling/media/dslpropagatecopy.png "DslPropagateCopy")

 Wprowadzane zmiany będzie miało wpływ na zarówno elementy, jak i obraz, który jest skopiowany.

## <a name="programming-copy-and-paste-behavior"></a>Programowanie kopiowania i wklejania zachowanie
 Wiele aspektów DSL zachowanie w odniesieniu do kopiowania, wklejania, tworzenie i usuwanie obiektów są regulowane przez wystąpienie <xref:Microsoft.VisualStudio.Modeling.ElementOperations> który jest sprzężona do diagramu. Można zmodyfikować zachowanie użytkownika DSL wyprowadzanie klasy z <xref:Microsoft.VisualStudio.Modeling.ElementOperations> i zastępowanie <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.ElementOperations%2A> właściwości klasy diagramu.

> [!TIP]
>  Aby uzyskać więcej informacji dotyczących dostosowywania modelu przy użyciu kodu programu, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

 ![Diagram sekwencji dla operacji kopiowania](../modeling/media/dslcopyseqdiagram.png "dslCopySeqDiagram")

 ![Diagram sekwencji operacji wklejania](../modeling/media/dslpasteseqdiagram.png "dslPasteSeqDiagram")

#### <a name="to-define-your-own-elementoperations"></a>Aby zdefiniować własny ElementOperations

1.  W nowym pliku w projekcie DSL, Utwórz klasę, która jest pochodną <xref:Microsoft.VisualStudio.Modeling.Diagrams.DesignSurfaceElementOperations>.

2.  Dodaj definicję klasy częściowej dla klasy diagramu. Nazwa tej klasy można znaleźć w **Dsl\GeneratedCode\Diagrams.cs**.

     W klasie diagram zastąpienie <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.ElementOperations%2A> można zwrócić wystąpienia podklasa ElementOperations użytkownika. Powinien zwrócić tego samego wystąpienia przy każdym wywołaniu.

 Dodaj ten kod w pliku kodu niestandardowego, w projekcie DslPackage:

```csharp

using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;

  public partial class MyDslDiagram
  {
    public override DesignSurfaceElementOperations ElementOperations
    {
      get
      {
        if (this.elementOperations == null)
        {
          this.elementOperations = new MyElementOperations(this.Store as IServiceProvider, this);
        }
        return this.elementOperations;
      }
    }
    private MyElementOperations elementOperations = null;
  }

  public class MyElementOperations : DesignSurfaceElementOperations
  {
    public MyElementOperations(IServiceProvider serviceProvider, MyDslDiagram diagram)
      : base(serviceProvider, diagram)
    { }
    // Overridden methods follow
  }

```

## <a name="receiving-items-dragged-from-other-models"></a>Odbieranie elementów przeciągnięte z innymi modelami
 ElementOperations mogą służyć do definiowania zachowania kopiowania, przenoszenia, usuwania i przeciągania i upuszczania. Jako pokaz Użyj ElementOperations przykładzie podanym w tym miejscu definiuje niestandardowe zachowanie przeciągania i upuszczania. Jednak w tym celu należy rozważyć alternatywne podejście opisane w [porady: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md), co jest bardziej extensible.

 Zdefiniuj dwie metody w klasie ElementOperations:

-   `CanMerge(ModelElement targetElement, System.Windows.Forms.IDataObject data)` która określa, czy element źródła może być przeciągnięto docelowego kształtu, łącznik lub diagram.

-   `MergeElementGroupPrototype(ModelElement targetElement, ElementGroupPrototype sourcePrototype)` które łączy elementu źródłowego do docelowego.

### <a name="canmerge"></a>CanMerge()
 `CanMerge()` jest wywołana w celu określenia uwag, które należy do użytkownika jako wskaźnik myszy porusza się na diagramie. Parametry metody są element, w którym znajduje się wskaźnik myszy, a dane dotyczące źródła, z którego wykonano operację przeciągania. Użytkownika można przeciągnąć z dowolnego miejsca na ekranie. W związku z tym obiekt źródłowy może mieć wiele różnych typów i mogą być zserializowane w różnych formatach. Jeśli źródło jest modelu DSL lub UML, parametr danych jest serializacji <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>. Operacje przeciągania, kopiowania i przybornika używa ElementGroupPrototypes do reprezentowania fragmenty modeli.

 Element prototypu grupy może zawierać dowolną liczbę elementów i łącza. Typy elementów można zidentyfikować według ich identyfikatorów. Identyfikator GUID jest kształtu, który został przeciągnięty nie odpowiedniego elementu modelu. W poniższym przykładzie `CanMerge()` zwraca wartość true, jeśli klasa kształt z UML diagram zostanie przeciągnięty na tym diagramie.

```csharp
public override bool CanMerge(ModelElement targetShape, System.Windows.Forms.IDataObject data)
 {
  // Extract the element prototype from the data.
  ElementGroupPrototype prototype = ElementOperations.GetElementGroupPrototype(this.ServiceProvider, data);
  if (targetShape is MyTargetShape && prototype != null &&
        prototype.RootProtoElements.Any(rootElement =>
          rootElement.DomainClassId.ToString()
          ==  "3866d10c-cc4e-438b-b46f-bb24380e1678")) // Guid of UML Class shapes
          // or SourceClass.DomainClassId
        return true;
   return base.CanMerge(targetShape, data);
 }

```

## <a name="mergeelementgroupprototype"></a>MergeElementGroupPrototype()
 Ta metoda jest wywoływana, gdy użytkownik porzuca elementu na diagramie, kształtu lub łącznika. Należy go scalić zawartości przeciąganego elementu docelowego. W tym przykładzie kodu Określa, czy rozpoznaje kombinację typów prototypu i docelowe. Jeśli tak, metoda konwertuje elementów przeciąganych prototyp elementów, które mają zostać dodane do modelu. Podstawowa metoda jest wywoływana przeprowadzić scalania, albo przekonwertowanego lub nieprzekonwertowane elementów.

```csharp
public override void MergeElementGroupPrototype(ModelElement targetShape, ElementGroupPrototype sourcePrototype)
{
  ElementGroupPrototype prototypeToMerge = sourcePrototype;
  MyTargetShape pel = targetShape as MyTargetShape;
  if (pel != null)
  {
    prototypeToMerge = ConvertDraggedTypeToLocal(pel, sourcePrototype);
  }
  if (prototypeToMerge != null)
    base.MergeElementGroupPrototype(targetShape, prototypeToMerge);
}

```

 Ten przykład dotyczy elementów klasy UML przeciągnięte z diagramu klas UML. DSL nie jest przeznaczony do przechowywania klas UML bezpośrednio, ale zamiast tego, utworzymy element DSL dla każdego przeciąganego klasy UML. Powinien to być przydatne na przykład, jeśli DSL jest diagram wystąpienia. Użytkownika można przeciągnięcie klasy do na diagramie, aby utworzyć wystąpień tych klas.

```csharp

private ElementGroupPrototype ConvertDraggedTypeToLocal (MyTargetShape snapshot, ElementGroupPrototype prototype)
{
  // Find the UML project:
  EnvDTE.DTE dte = snapshot.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
  foreach (EnvDTE.Project project in dte.Solution.Projects)
  {
    IModelingProject modelingProject = project as IModelingProject;
    if (modelingProject == null) continue; // not a modeling project
    IModelStore store = modelingProject.Store;
    if (store == null) continue;
    // Look for the shape that was dragged:
    foreach (IDiagram umlDiagram in store.Diagrams())
    {
      // Get modeling diagram that implements UML diagram:
      Diagram diagram = umlDiagram.GetObject<Diagram>();
      Guid elementId = prototype.SourceRootElementIds.FirstOrDefault();
      ShapeElement shape = diagram.Partition.ElementDirectory.FindElement(elementId) as ShapeElement;
      if (shape == null) continue;
      IClass classElement = shape.ModelElement as IClass;
      if (classElement == null) continue;

      // Create a prototype of elements in my DSL, based on the UML element:
      Instance instance = new Instance(snapshot.Store);
      instance.Type = classElement.Name;
      // Pack them into a prototype:
      ElementGroup group = new ElementGroup(instance);
      return group.CreatePrototype();
    }
  }
  return null;
}

```

## <a name="standard-copy-behavior"></a>Zachowanie kopia Standard
 Kod w tej sekcji przedstawiono przesłonić metody, które można zmienić zachowanie kopiowania. Aby poznać sposób uzyskać własne dostosowania, ta sekcja zawiera kod, który zastępuje metody objętego kopiowania, ale nie zmienić standardowe zachowanie.

 Gdy użytkownik naciśnie klawisze CTRL + C lub używa polecenia menu kopiowania, Metoda <xref:Microsoft.VisualStudio.Modeling.Shell.ClipboardCommandSet.ProcessOnMenuCopyCommand%2A> jest wywoływana. Widać to konfiguracji **DslPackage\Generated Code\CommandSet.cs**. Aby uzyskać więcej informacji dotyczących sposobu konfigurowania przez polecenia, zobacz [porady: Dodawanie polecenia do Menu skrótów](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

 Można zastąpić ProcessOnMenuCopyCommand przez dodanie definicji klasy częściowej *MyDsl* `ClipboardCommandSet` w projekcie DslPackage.

```csharp
using System.Collections.Generic;
using System.Drawing;
using System.Windows.Forms;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

partial class MyDslClipboardCommandSet
{
  /// <summary>
  /// Override ProcessOnMenuCopyCommand() to copy elements to the
  /// clipboard in different formats, or to perform additional tasks
  /// before or after copying - for example deselect the copied elements.
  /// </summary>
  protected override void ProcessOnMenuCopyCommand()
  {
    IList<ModelElement> selectedModelElements = this.SelectedElements;
    if (selectedModelElements.Count == 0) return;

    // System container for clipboard data.
    // The IDataObject can contain data in several formats.
    IDataObject dataObject = new DataObject();

    Bitmap bitmap = null; // For export to other programs.
    try
    {
      #region Create EGP for copying to a DSL.
      this.CopyModelElementsIntoElementGroupPrototype
                     (dataObject, selectedModelElements);
      #endregion

      #region Create bitmap for copying to another application.
      // Find all the shapes associated with this selection:
      List<ShapeElement> shapes = new List<ShapeElement>(
        this.ResolveExportedShapesForClipboardImages
              (dataObject, selectedModelElements));

      bitmap = this.CreateBitmapForClipboard(shapes);
      if (bitmap != null)
      {
        dataObject.SetData(DataFormats.Bitmap, bitmap);
      }
      #endregion

      // Add the data to the clipboard:
      Clipboard.SetDataObject(dataObject, true, 5, 100);
    }
    finally
    {
      // Dispose bitmap after SetDataObject:
      if (bitmap != null) bitmap.Dispose();
    }
  }
/// <summary>
/// Override this to customize the element group that is copied to the clipboard.
/// </summary>
protected override void CopyModelElementsIntoElementGroupPrototype(IDataObject dataObject, IList<ModelElement> selectedModelElements)
{
  return this.ElementOperations.Copy(dataObject, selectedModelElements);
}
}
```

 Każdy diagram zawiera pojedyncze wystąpienie ElementOperations. Możesz podać własne zależnych. Ten plik, który można umieścić w projekcie DSL, czy działają tak samo jako kod, który zastępuje ona:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace Company.MyDsl
{
  partial class MyDslDiagram
  {
    /// <summary>
    /// Singleton ElementOperations attached to this diagram.
    /// </summary>
    public override DesignSurfaceElementOperations ElementOperations
    {
      get
      {
        if (this.elementOperations == null)
        {
          this.elementOperations = new MyElementOperations(this.Store as IServiceProvider, this);
        }
        return this.elementOperations;
      }
    }
    private MyElementOperations elementOperations = null;
  }

  // Our own version of ElementOperations so that we can override:
  public class MyElementOperations : DesignSurfaceElementOperations
  {
    public MyElementOperations(IServiceProvider serviceProvider, ElementOps1Diagram diagram)
      : base(serviceProvider, diagram)
    { }

    /// <summary>
    /// Copy elements to the clipboard data.
    /// Provides a hook for adding custom data.
    /// </summary>
    public override void Copy(System.Windows.Forms.IDataObject data,
      ICollection<ModelElement> elements,
      ClosureType closureType,
      System.Drawing.PointF sourcePosition)
    {
      if (CanAddElementGroupFormat(elements, closureType))
      {
        AddElementGroupFormat(data, elements, closureType);
      }

      // Override these to store additional data:
      if (CanAddCustomFormat(elements, closureType))
      {
        AddCustomFormat(data, elements, closureType, sourcePosition);
      }
    }

    protected override void AddElementGroupFormat(System.Windows.Forms.IDataObject data, ICollection<ModelElement> elements, ClosureType closureType)
    {
      // Add the selected elements and those implied by the propagate copy rules:
      ElementGroup elementGroup = this.CreateElementGroup(elements, closureType);

      // Mark all the elements that are not embedded under other elements:
      this.MarkRootElements(elementGroup, elements, closureType);

      // Store in the clipboard data:
      ElementGroupPrototype elementGroupPrototype = this.CreateElementGroupPrototype(elementGroup, elements, closureType);
      data.SetData(ElementGroupPrototype.DefaultDataFormatName, elementGroupPrototype);
    }

    /// <summary>
    /// Override this to store additional elements in the element group:
    /// </summary>
    protected override ElementGroupPrototype CreateElementGroupPrototype(ElementGroup elementGroup, ICollection<ModelElement> elements, ClosureType closureType)
    {
      ElementGroupPrototype prototype = new ElementGroupPrototype(this.Partition, elementGroup.RootElements, elementGroup);
      return prototype;
    }

    /// <summary>
    /// Create an element group from the given starting elements, using the
    /// copy propagation rules specified in the DSL Definition.
    /// By default, this includes all the embedded descendants of the starting elements,
    /// and also includes reference links where both ends are already included.
    /// </summary>
    /// <param name="startElements">model elements to copy</param>
    /// <param name="closureType"></param>
    /// <returns></returns>
    protected override ElementGroup CreateElementGroup(ICollection<ModelElement> startElements, ClosureType closureType)
    {
      // ElementClosureWalker finds all the connected elements,
      // according to the propagate copy rules specified in the DSL Definition:
      ElementClosureWalker walker = new ElementClosureWalker(this.Partition,
        closureType, // Normally ClosureType.CopyClosure
        startElements,
        true, // Do not load other models.
        null, // Optional list of domain roles not to traverse.
        true); // Include relationship links where both ends are already included.

      walker.Traverse(startElements);
      IList<ModelElement> closureList = walker.ClosureList;
      Dictionary<object, object> closureContext = walker.Context;

      // create a group for this closure
      ElementGroup group = new ElementGroup(this.Partition);
      group.AddRange(closureList, false);

      // create the element group prototype for the group
      foreach (object key in closureContext.Keys)
      {
        group.SourceContext.ContextInfo[key] = closureContext[key];
      }

      return group;
    }
  }
}

```

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie tworzenia i przesuwania elementu](../modeling/customizing-element-creation-and-movement.md)
- [Instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Dostosowywanie zachowania dotyczącego usuwania](../modeling/customizing-deletion-behavior.md)
- [Przykład: Diagramy obwodu VMSDK próbki](http://go.microsoft.com/fwlink/?LinkId=213879)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]