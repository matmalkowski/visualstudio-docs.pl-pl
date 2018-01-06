---
title: "Aktualizowanie łączników i kształtów w celu odzwierciedlenia modelu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51eb2af9-00e7-4725-a87d-62fb4f39f444
caps.latest.revision: "6"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 7c63d8e9d7da3c02259e557580c5d7cafa74d0b1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>Aktualizowanie kształtów i łączników, aby odzwierciedlały model
W języku specyficznego dla domeny, w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], możesz wprowadzić wygląd kształtu odzwierciedlają stan modelu źródłowego.  
  
 Przykłady kodu, w tym temacie powinny zostać dodane do `.cs` plików w sieci `Dsl` projektu. Te instrukcje w każdym pliku będą potrzebne:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
```  
  
## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Ustaw właściwości mapy kształt, aby kontrolować widoczność dekoratora  
 Widoczność dekoratora można kontrolować, bez konieczności pisania kodu programu, konfigurując mapowanie między kształt i klasy domeny w definicji DSL. Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md).
  
## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Udostępnianie kolorów i Styl kształtu jako właściwości  
 W definicji DSL, kliknij prawym przyciskiem myszy klasę kształtu, wskaż pozycję **dodać widoczne**i kliknij jeden z elementów takich jak **kolor wypełnienia**.  
  
 Kształt ma teraz właściwość domeny można ustawić w kodzie programu lub użytkownik. Na przykład aby ustawić ją w kodzie programu polecenia lub reguły, można napisać:  
  
 `shape.FillColor = System.Drawing.Color.Red;`  
  
 Jeśli chcesz ustaw dla zmiennej właściwość tylko pod kontrolą programu, a nie przez użytkownika, wybierz nową właściwość domeny takich jak **kolor wypełnienia** na diagramie definicji DSL. Następnie w oknie właściwości ustaw **jest można przeglądać** do `false` lub ustaw **jest tylko do odczytu w interfejsie użytkownika** do `true`.  
  
## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Zdefiniuj Zmień reguły koloru, stylu lub lokalizacji są zależne od właściwości elementu modelu  
 Można zdefiniować reguły, które aktualizują wygląd kształtu zależny od innych części modelu. Na przykład można zdefiniować reguły zmiany w elemencie modelu, który aktualizuje kolor kształtu zależna od właściwości elementu modelu. Aby uzyskać więcej informacji o regułach zmian, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Należy używać reguły tylko do aktualizacji właściwości, które są przechowywane w magazynie, ponieważ zasady nie są wywoływane po wykonaniu polecenia Cofnij. Dotyczy to niektóre funkcje graficzne, takie jak rozmiar i widoczność kształtu. Aby zaktualizować te funkcje kształtu, zobacz [funkcji aktualizowania graficznych bez magazynu](#OnAssociatedProperty).  
  
 W poniższym przykładzie założono, że zostały udostępnione `FillColor` jako właściwość domeny, zgodnie z opisem w poprzedniej sekcji.  
  
```csharp  
[RuleOn(typeof(ExampleElement))]  
  class ExampleElementPropertyRule : ChangeRule  
  {  
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)  
    {  
      base.ElementPropertyChanged(e);  
      ExampleElement element = e.ModelElement as ExampleElement;  
      // The rule is called for every property that is updated.  
      // Therefore, verify which property changed:  
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)  
      {  
        // There is usually only one shape:  
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))  
        {  
          ExampleShape shape = pel as ExampleShape;  
          // Replace this with a useful condition:  
          shape.FillColor = element.Name.EndsWith("3")   
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;  
        }  
      }  
    }  
  }  
  // The rule must be registered:  
  public partial class OnAssociatedPropertyExptDomainModel  
  {  
    protected override Type[] GetCustomDomainModelTypes()  
    {  
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
      types.Add(typeof(ExampleElementPropertyRule));  
      // If you add more rules, list them here.   
      return types.ToArray();  
    }  
  }  
  
```  
  
## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Użyj OnChildConfigured można zainicjować właściwości kształtu  
 Można ustawić właściwości kształtu przy pierwszym utworzone, zastąpienie `OnChildConfigured()` w definicji częściowej klasy diagramu. Diagram jest określona w definicji DSL i wygenerowany kod znajduje się w **Dsl\Generated Code\Diagram.cs**. Na przykład:  
  
```csharp  
partial class MyLanguageDiagram  
{  
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)  
  {  
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);  
    ExampleShape shape = child as ExampleShape;  
    if (shape != null)   
    {  
      if (!createdDuringViewFixup) return; // Ignore load from file.  
      ExampleElement element = shape.ModelElement as ExampleElement;  
      // Replace with a useful condition:  
      shape.FillColor = element.Name.EndsWith("3")   
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;  
    }  
    // else deal with other types of shapes and connectors.  
  }  
}  
  
```  
  
 Tej metody można użyć zarówno dla właściwości domeny i z systemem innym niż magazynu funkcji, takich jak rozmiaru kształtu.  
  
##  <a name="OnAssociatedProperty"></a>Użyj AssociateValueWith(), aby zaktualizować innych funkcji kształtu  
 W przypadku niektórych funkcji kształtu, np. czy ma cień lub Styl strzałki łącznika nie istnieje wbudowana metoda ujawnienia funkcji jako właściwość domeny.  Zmiany tych funkcji nie są pod kontrolą systemu transakcji. W związku z tym nie jest odpowiedni je zaktualizować przy użyciu reguł, ponieważ zasady nie są wywoływane, gdy użytkownik wykonuje polecenie Undo.  
  
 Jednak takie funkcje można zaktualizować przy użyciu <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>. W poniższym przykładzie Styl strzałki łącznika jest kontrolowany przez wartość właściwości domeny w relacji, która wyświetla łącznika:  
  
```  
public partial class ArrowConnector // My connector class.   
{  
   /// <summary>  
    /// Called whenever a registered property changes in the associated model element.  
    /// </summary>  
    /// <param name="e"></param>  
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)  
    {  
      base.OnAssociatedPropertyChanged(e);  
      // Can be called for any property change. Therefore,  
      // Verify that this is the property we're interested in:  
      if ("IsDirected".Equals(e.PropertyName))  
      {  
        if (e.NewValue.Equals(true))  
        { // Update the shape's built-in Decorator feature:  
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;  
        }  
        else  
        {  
          this.DecoratorTo = null; // No arrowhead.  
        }  
      }  
    }  
    // OnAssociatedPropertyChanged is called only for properties  
    // that have been registered using AssociateValueWith().  
    // InitializeResources is a convenient place to call this.  
    // This method is invoked only once per class, even though  
    // it is an instance method.   
    protected override void InitializeResources(StyleSet classStyleSet)  
    {  
      base.InitializeResources(classStyleSet);  
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);  
      // Add other properties here.  
    }  
}  
  
```  
  
 `AssociateValueWith()`powinna być wywoływana raz dla każdej właściwości domeny, który chcesz zarejestrować. Po została wywołana, zmiany wprowadzone w określonej właściwości wywoła `OnAssociatedPropertyChanged()` w kształtów, które są dostępne właściwości elementu modelu.  
  
 Nie jest konieczne do wywołania `AssociateValueWith()` dla każdego wystąpienia. Mimo że InitializeResources metody wystąpienia, jest wywoływana tylko jeden raz dla każdej klasy kształtu.
