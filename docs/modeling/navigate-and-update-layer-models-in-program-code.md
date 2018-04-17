---
title: Nawigowanie i aktualizowanie modeli warstw w kodzie programu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8d827a77608efac4d08f2698d8c9b6519b0ec632
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Nawigowanie i aktualizowanie modeli warstw w kodzie programu
W tym temacie opisano elementów i relacji w modelach warstwy, których można nawigowanie i aktualizowanie przy użyciu kodu programu. Aby uzyskać więcej informacji o zależnościach diagramy z punktu widzenia użytkownika, zobacz [diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md) i [diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md).  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer> Model opisanych w tym temacie jest fasad na bardziej ogólnym <xref:Microsoft.VisualStudio.GraphModel> modelu. Jeśli piszesz [menu polecenie lub gestu rozszerzenie](../modeling/add-commands-and-gestures-to-layer-diagrams.md), użyj `Layer` modelu. Jeśli piszesz [warstwy sprawdzania poprawności rozszerzenia](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), łatwiej używać `GraphModel`.  
  
## <a name="transactions"></a>Transakcje  
 Podczas aktualizowania modelu, należy wziąć pod uwagę zmiany w załączonym `ILinkedUndoTransaction`. Grupuje zmiany w jednej transakcji. Jeśli zmiany zakończy się niepowodzeniem, cała transakcja będzie można wycofać. Jeśli użytkownik spowoduje cofnięcie zmian, wszystkie zmiany zostaną cofnięte razem.  
  
```  
using (ILinkedUndoTransaction t =  
        LinkedUndoContext.BeginTransaction("a name"))  
{   
    // Make changes here ....  
    t.Commit(); // Don't forget this!  
}  
```  
  
## <a name="containment"></a>Zawierania  
 ![ILayer i ILayerModel może zawierać ILayers. ] (../modeling/media/layerapi_containment.png "LayerApi_Containment")  
  
 Warstwy (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>) oraz model warstwy (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>) może zawierać komentarzy i warstwy.  
  
 Warstwy (`ILayer`) mogą być zawarte w modelu warstwy (`ILayerModel`) lub mogą być zagnieżdżone w innym `ILayer`.  
  
 Aby utworzyć komentarz lub warstwy, należy użyć metody tworzenia odpowiedniego kontenera.  
  
## <a name="dependency-links"></a>Łączy współzależności  
 Łącze zależności jest reprezentowana przez obiekt. Może zostać przesłane w żadnym kierunku:  
  
 ![An ILayerDependencyLink connects two ILayers.](../modeling/media/layerapi_dependency.png "LayerApi_Dependency")  
  
 Aby utworzyć łącze zależności, należy wywołać `source.CreateDependencyLink(target)`.  
  
## <a name="comments"></a>Komentarze  
 Komentarze może być zawarty wewnątrz warstwy lub modelu warstwy, a także może odnosić się do dowolnego elementu warstwy:  
  
 ![Komentarze można dołączyć do dowolnego elementu warstwy. ] (../modeling/media/layerapi_comments.png "LayerApi_Comments")  
  
 Komentarz może odnosić się do dowolnej liczby elementów, w tym none.  
  
 Aby uzyskać komentarze, które są dołączone do elementu warstwy, należy użyć:  
  
```csharp  
ILayerModel model = diagram.GetLayerModel();   
IEnumerable<ILayerComment> comments =   
   model.Comments.Where(comment =>   
      comment.Links.Any(link => link.Target == layerElement));  
  
```  
  
> [!CAUTION]
>  `Comments` Właściwość `ILayer` pobiera komentarze, które są zawarte w `ILayer`. Nie otrzymuje komentarze, które są z nim połączone.  
  
 Komentarz utworzyć przez wywołanie `CreateComment()` na odpowiedniego kontenera.  
  
 Utwórz łącze przy użyciu `CreateLink()` na komentarz.  
  
## <a name="layer-elements"></a>Elementy w warstwie  
 Wszystkie typy elementu, który może być zawarte w modelu są elementy warstwy:  
  
 ![Zawartość diagramu zależności są ILayerElements. ] (../modeling/media/layerapi_layerelements.png "LayerApi_LayerElements")  
  
## <a name="properties"></a>Właściwości  
 Każdy `ILayerElement` słownika ciągu o nazwie `Properties`. Można użyć tego słownika można dołączyć dowolnych informacji do dowolnego elementu warstwy.  
  
## <a name="artifact-references"></a>Odwołania do artefaktu  
 Odwołania do artefaktu (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>) reprezentuje łącze między warstwami elementu projektu, takie jak pliku, klasa lub folderu. Użytkownik tworzy artefakty podczas tworzenia warstwy lub Dodaj do niej, przeciągając elementy z Eksploratora rozwiązań, Widok klas lub przeglądarki obiektów na diagramie zależności. Dowolna liczba odwołań do artefaktu może być połączony do warstwy.  
  
 Każdy wiersz w Eksploratorze warstwy Wyświetla odwołania do artefaktu. Aby uzyskać więcej informacji, zobacz [tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md).  
  
 Główne typy i metody danych z odwołaniami do artefaktu są następujące:  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>. Właściwość kategorii wskazuje, jaki rodzaj artefaktu odwołuje się do, takich jak klasy, plik wykonywalny lub zestawu. Kategorie określa, jak identyfikator identyfikuje artefaktu docelowej.  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A> Tworzy odwołania do artefaktu z <xref:EnvDTE.Project> lub <xref:EnvDTE.ProjectItem>. To jest operacja asynchroniczna. W związku z tym zazwyczaj zawierają wywołania zwrotnego, która jest wywoływana po zakończeniu tworzenia.  
  
 Odwołania do artefaktu warstwa nie należy mylić z artefaktami w diagramy przypadków użycia.  
  
## <a name="shapes-and-diagrams"></a>Kształty i diagramów  
 Dwa obiekty są używane do reprezentowania każdego elementu w modelu warstwy: <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>i <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>. `IShape` Reprezentuje położenia i rozmiaru kształtu na diagramie. W modelach warstwy co `ILayerElement` ma jeden `IShape`i co `IShape` na zależność diagramu ma jeden `ILayerElement`. `IShape` Służy także do modeli UML. W związku z tym nie każdy `IShape` ma element warstwy.  
  
 W ten sam sposób <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel> jest wyświetlany na jednym <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram>.  
  
 W kodzie polecenia niestandardowych lub procedury obsługi gestów, można uzyskać bieżącego diagramu i bieżące zaznaczenie kształty z `DiagramContext` importowania:  
  
```  
public class ... {  
[Import]  
    public IDiagramContext DiagramContext { get; set; }  
...  
public void ... (...)   
{ IDiagram diagram = this.DiagramContext.CurrentDiagram;  
  ILayerModel model = diagram.GetLayerModel();  
  if (model != null)  
  { foreach (ILayer layer in model.Layers) { ... }}  
  foreach (IShape selected in diagram.SelectedShapes)  
  { ILayerElement element = selected.GetLayerElement();  
    if (element != null) ... }}  
```  
  
 ![Każdy ILayerElement jest przedstawiony przez IShape. ] (../modeling/media/layerapi_shapes.png "LayerApi_Shapes")  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> i <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> są również używane do wyświetlania modeli UML. 
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie poleceń i gestów do diagramów zależności](../modeling/add-commands-and-gestures-to-layer-diagrams.md)   
 [Dodawanie niestandardowej weryfikacji architektury do diagramów zależności](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
 [Dodawanie właściwości niestandardowych do diagramów zależności](../modeling/add-custom-properties-to-layer-diagrams.md)   
 [Diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md)   
 [Diagramy zależności: Wskazówki](../modeling/layer-diagrams-guidelines.md)   
