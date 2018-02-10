---
title: "Dodawanie poleceń i gestów do diagramów zależności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, adding custom commands
- dependency diagrams, adding custom gestures
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5a8f1a2ff8e5ffc95d885b847a17e6cc16965837
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="add-commands-and-gestures-to-dependency-diagrams"></a>Dodawanie poleceń i gestów do diagramów zależności
Można zdefiniować poleceń menu kontekstowego i gestów programów obsługi na wykresach zależności w Visual Studio. Rozszerzenia te można spakować do programu Visual Studio integracji rozszerzenia (VSIX) dystrybuowanej do innych użytkowników programu Visual Studio.  
  
 Jeśli chcesz można zdefiniować kilka programy obsługi poleceń i gestów w tym samym projekcie Visual Studio. Można także połączyć tych projektów w jednym pliku VSIX. Na przykład można zdefiniować pojedynczego VSIX, które zawiera polecenia warstwy i języka specyficznego dla domeny.  
  
> [!NOTE]
>  Można również dostosować walidacji architektury, użytkowników, których źródła kodu jest porównywany z diagramami zależności. Należy zdefiniować walidacji architektury w oddzielnych projektu programu Visual Studio. Można dodać go do tego samego pliku VSIX jako inne rozszerzenia. Aby uzyskać więcej informacji, zobacz [Dodawanie niestandardowej weryfikacji architektury do diagramów zależności](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).  
  
## <a name="requirements"></a>Wymagania  
 Zobacz [wymagania](../modeling/extend-layer-diagrams.md#prereqs).  
  
## <a name="defining-a-command-or-gesture-in-a-new-vsix"></a>Definiowanie polecenia lub gestu w nowego pliku VSIX  
 Tworzenie rozszerzenia najszybszą metodą jest należy użyć szablonu projektu. Kod i manifestu VSIX to umieszczenie w tym samym projekcie.  
  
#### <a name="to-define-an-extension-by-using-a-project-template"></a>Aby zdefiniować rozszerzenia za pomocą szablonu projektu  
  
1.  Tworzenie projektu na nowe rozwiązanie, za pomocą **nowy projekt** na **pliku** menu.  
  
2.  W **nowy projekt** okna dialogowego, w obszarze **projektów modelowania**, wybierz opcję **rozszerzenia poleceń projektanta warstwy** lub **rozszerzenia gestu projektanta warstwy** .  
  
     Szablon tworzy projekt, który zawiera krótki przykład pracy.  
  
3.  Aby przetestować rozszerzenia, naciśnij klawisz **CTRL + F5** lub **F5**.  
  
     Uruchamia eksperymentalne wystąpienie programu Visual Studio. W tym wystąpieniu Utwórz diagram zależności. Rozszerzenie polecenia lub gestu powinny działać na tym diagramie.  
  
4.  Zamknij eksperymentalne wystąpienie i zmodyfikować przykładowy kod. Aby uzyskać więcej informacji, zobacz [nawigowanie i aktualizowanie modeli w kodzie programu warstwy](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
5.  Możesz dodać więcej programy obsługi poleceń i gestów do tego samego projektu. Aby uzyskać więcej informacji zobacz jedną z następujących sekcji:  
  
     [Definiowanie polecenia Menu](#command)  
  
     [Definiowanie procedury obsługi gestów](#gesture)  
  
6.  Aby zainstalować rozszerzenie w głównym wystąpienie programu Visual Studio lub na innym komputerze, należy znaleźć **.vsix** w pliku **bin\\\***. Skopiuj go na komputerze, na którym chcesz zainstalować, a następnie kliknij go dwukrotnie. Aby go odinstalować, użyj **rozszerzenia i aktualizacje** na **narzędzia** menu.  
  
## <a name="adding-a-command-or-gesture-to-a-separate-vsix"></a>Dodawanie poleceń i gestów do oddzielnego pliku VSIX  
 Jeśli chcesz utworzyć jedną VSIX, które zawiera polecenia, warstwy modułów weryfikacji i inne rozszerzenia, zaleca się utworzenie jednego projektu do definiowania pliku VSIX i oddzielne projektów dla programów obsługi.
  
#### <a name="to-add-layer-extensions-to-a-separate-vsix"></a>Aby dodać warstwę rozszerzenia do oddzielnego pliku VSIX  
  
1.  Tworzenie projektu biblioteki klas w nowego lub istniejącego rozwiązania Visual Studio. W **nowy projekt** okno dialogowe, kliknij przycisk **Visual C#** , a następnie kliknij przycisk **biblioteki klas**. Ten projekt będzie zawierają polecenia lub gestu klasy programu obsługi.  
  
    > [!NOTE]
    >  Można zdefiniować więcej niż jedną klasę programu obsługi poleceń i gestów w bibliotece jedną klasę, ale należy zdefiniować warstwy sprawdzania poprawności klasy w bibliotece klas oddzielne.  
  
2.  Zidentyfikuj lub tworzenia projektu VSIX w rozwiązaniu. Projektu VSIX zawiera plik o nazwie **source.extension.vsixmanifest**. Aby dodać projektu VSIX:  
  
    1.  W **nowy projekt** okna dialogowego rozwiń **Visual C#**, następnie kliknij przycisk **rozszerzalności**, a następnie kliknij przycisk **projektu VSIX**.  
  
    2.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projektu VSIX, a następnie kliknij przycisk **Ustaw jako projekt startowy**.  
  
    3.  Kliknij przycisk **Wybierz wersje** i upewnij się, że **programu Visual Studio** jest zaznaczony.  
  
3.  W **source.extension.vsixmanifest**w obszarze **zasoby**, należy dodać polecenie lub gestu projektu obsługi jako składnik MEF.  
  
    1.  W **zasoby**TAB, wybierz **nowy**.  
  
    2.  W **typu**, wybierz pozycję **Microsoft.VisualStudio.MefComponent**.  
  
    3.  W **źródła**, wybierz pozycję **projekt w bieżącym rozwiązaniu** i wybierz nazwę polecenia lub gestu projektu programu obsługi.  
  
    4.  Zapisz plik.  
  
4.  Wróć do polecenia lub gestu projektu programu obsługi i dodaj następujące odwołania do projektu.  
  
|**Dokumentacja**|**Co to umożliwia**|  
|-------------------|------------------------------------|  
|Program Files\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Tworzenie i edytowanie warstwy|  
|Microsoft.VisualStudio.Uml.Interfaces|Tworzenie i edytowanie warstwy|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility|Modyfikowanie kształtów na diagramach|  
|System.ComponentModel.Composition|Zdefiniuj składników za pomocą Managed Extensibility Framework (MEF)|  
|Microsoft.VisualStudio.Modeling.Sdk.[version]|Zdefiniuj rozszerzenia modelowania|  
|Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]|Kształty aktualizacji i diagramów|  
  
1.  Przeprowadź edycję pliku klasy w C# projektu biblioteki klas zawiera kod dla rozszerzenia. Aby uzyskać więcej informacji zobacz jedną z następujących sekcji:  
  
     [Definiowanie polecenia Menu](#command)  
  
     [Definiowanie procedury obsługi gestów](#gesture)  
  
     Zobacz też [nawigowanie i aktualizowanie modeli w kodzie programu warstwy](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
2.  Aby przetestować funkcję, naciśnij kombinację klawiszy CTRL + F5 lub F5. Otwiera eksperymentalne wystąpienie programu Visual Studio. W tym wystąpieniu Utwórz lub Otwórz diagram zależności.  
  
3.  Aby zainstalować pliku VSIX w głównym wystąpienie programu Visual Studio lub na innym komputerze, należy znaleźć **.vsix** w pliku **bin** katalogu projektu VSIX. Skopiuj go na komputerze, na którym chcesz zainstalować pliku VSIX. Kliknij dwukrotnie plik VSIX w Eksploratorze Windows.  
  
     Aby go odinstalować, użyj **rozszerzenia i aktualizacje** na **narzędzia** menu.  
  
##  <a name="command"></a>Definiowanie polecenia Menu  
 Można dodać więcej definicji polecenia menu do istniejącego gestu lub polecenie projektu. Każde polecenie jest zdefiniowane przez klasę, która ma następującą charakterystykę:  
  
-   Klasa jest zadeklarowany w następujący sposób:  
  
     `[LayerDesignerExtension]`  
  
     `[Export(typeof(ICommandExtension))]`  
  
     `public class`  *MyLayerCommand*  `: ICommandExtension { ... }`  
  
-   Przestrzeń nazw i nazwę klasy nie są ważne.  
  
-   Metody, które implementują `ICommandExtension` są następujące:  
  
    -   `string Text {get;}`-Etykietę wyświetlaną w menu.  
  
    -   `void QueryStatus(IMenuCommand command)`-wywoływane, gdy użytkownik kliknie prawym przyciskiem myszy diagram i określa, czy polecenie powinno być widoczne i włączone dla użytkownika bieżącego zaznaczenia.  
  
    -   `void Execute(IMenuCommand command)`-wywoływana, gdy użytkownik wybierze polecenie.  
  
-   Aby sprawdzić bieżące zaznaczenie, można importować `IDiagramContext`:  
  
     `[Import]`  
  
     `public IDiagramContext DiagramContext { get; set; }`  
  
     `...`  
  
     `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`  
  
 Aby uzyskać więcej informacji, zobacz [nawigowanie i aktualizowanie modeli w kodzie programu warstwy](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
 Aby dodać nowe polecenie, Utwórz nowy plik kodu zawierający poniższy przykład. Następnie testować i go edytować.  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using System.ComponentModel.Composition;  
using System.Linq;  
  
namespace MyLayerExtension // Change to your preference.  
{  
  // This is a feature for dependency diagrams:  
  [LayerDesignerExtension]  
  // This feature is a menu command:  
  [Export(typeof(ICommandExtension))]  
  // Change the class name to your preference:  
  public class MyLayerCommand : ICommandExtension  
  {  
    [Import]  
    public IDiagramContext DiagramContext { get; set; }  
  
    [Import]  
    public ILinkedUndoContext LinkedUndoContext { get; set; }  
  
    // Menu command label:  
    public string Text  
    {  
      get { return "Duplicate layers"; }  
    }  
  
    // Called when the user right-clicks the diagram.  
    // Defines whether the command is visible and enabled.  
    public void QueryStatus(IMenuCommand command)  
    {   
      command.Visible =   
      command.Enabled = DiagramContext.CurrentDiagram  
        .SelectedShapes.Count() > 0;  
    }  
  
    // Called when the user selects the command.  
    public void Execute(IMenuCommand command)  
    {  
      // A selection of starting points:  
      IDiagram diagram = this.DiagramContext.CurrentDiagram;  
      ILayerModel lmodel = diagram.GetLayerModel();  
      foreach (ILayer layer in lmodel.Layers)  
      { // All layers in model.  
      }  
      // Updates should be performed in a transaction:  
      using (ILinkedUndoTransaction t =  
        LinkedUndoContext.BeginTransaction("copy selection"))  
      {  
        foreach (ILayer layer in   
          diagram.SelectedShapes  
            .Select(shape=>shape.GetLayerElement())  
            .Where(element => element is ILayer))  
        {  
          ILayer copy = lmodel.CreateLayer(layer.Name + "+");  
          // Position the shapes:  
          IShape originalShape = layer.GetShape();  
          copy.GetShape().Move(  
            originalShape.XPosition + originalShape.Width * 1.2,  
            originalShape.YPosition);  
        }  
        t.Commit();  
      }  
    }  
  }  
}  
```  
  
##  <a name="gesture"></a>Definiowanie procedury obsługi gestów  
 Procedury obsługi gestów reaguje, gdy użytkownik przeciąga elementów na diagramie zależności, a użytkownik kliknie dwukrotnie dowolne miejsce na diagramie.  
  
 Do istniejącego polecenia lub projektu VSIX procedury obsługi gestów można dodać pliku kodu, który definiuje procedury obsługi gestów:  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using System.ComponentModel.Composition;  
using System.Linq;  
namespace MyLayerExtensions // change to your preference  
{  
  [LayerDesignerExtension]  
  [Export(typeof(IGestureExtension))]  
  public class MyLayerGestureHandler : IGestureExtension  
  {  
  }  
}  
```  
  
 Zwróć uwagę następujące kwestie dotyczące obsługi gestów:  
  
-   Elementy członkowskie `IGestureExtension` są następujące:  
  
     **OnDoubleClick** -wywoływane, gdy użytkownik kliknie dwukrotnie dowolne miejsce na diagramie.  
  
     **CanDragDrop** — wywołane wielokrotnie, ponieważ użytkownik przesuwa wskaźnik myszy podczas przeciągania elementu na diagramie. Musi działać szybko.  
  
     **OnDragDrop** -wywoływane, gdy użytkownik porzuca elementu na diagramie.  
  
-   Pierwszy argument do każdej z metod jest `IShape`, z którego można uzyskać elementu warstwy. Na przykład:  
  
    ```  
    public void OnDragDrop(IShape target, IDataObject data)  
    {  
        ILayerElement element = target.GetLayerElement();  
        if (element is ILayer)  
        {  
            // ...  
        }  
    }  
    ```  
  
-   Programy obsługi dla niektórych typów przeciąganego elementu są już zdefiniowane. Na przykład użytkownik może przeciągnij elementy z Eksploratora rozwiązań diagram zależności. Nie można zdefiniować przeciągania obsługę tych typów elementów. W takich przypadkach z `DragDrop` metody nie zostaną wywołane.  
  
  
## <a name="see-also"></a>Zobacz też  
 [Nawigowanie i aktualizowanie modeli warstw w kodzie programu](../modeling/navigate-and-update-layer-models-in-program-code.md)   
 [Dodawanie niestandardowej walidacji architektury do diagramów zależności](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
