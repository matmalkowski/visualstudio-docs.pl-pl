---
title: Kontrolowanie koloru, stylu linii i innych właściwości kształtu
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 710e4a20d0b9cc60a32786836fda7716a70f86e5
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Kontrolowanie koloru, stylu linii i innych właściwości kształtu
Niektóre właściwości kształtu, takie jak kolor może być "widoczne" - oznacza to, połączony z właściwością domeny kształtu. Inne muszą być kontrolowane bezpośrednio.

## <a name="exposing-a-property"></a>Udostępnianie właściwości
 Niektóre właściwości kształtu, takie jak kolor można powiązać wartości właściwości domeny.

 W definicji DSL wybierz kształt, łącznik lub diagramu klas. Menu kontekstowe, wybierz **dodać widoczne**, a następnie wybierz pozycję Właściwości, takie jak kolor wypełnienia.

 Kształt ma teraz właściwość domeny można ustawić w kodzie programu lub użytkownik.

## <a name="dynamically-updating-an-exposed-property"></a>Dynamiczne aktualizowanie ujawnionych właściwości
 Zazwyczaj mają być zależna od innej właściwości ujawnionych właściwości. Można na przykład shape do czerwony, gdy właściwość określonej domeny jest mniejsza od zera. Aby ta zależność, Utwórz [reguły](../modeling/rules-propagate-changes-within-the-model.md). Na przykład:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
namespace ExampleNamespace
{
 // Attribute associates the rule with class:
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class CarShapeAddRule : AddRule
 {
 // Override the abstract method:
 public override void ElementAdded(ElementAddedEventArgs e)
 {
 base.ElementAdded(e);
 CarShape shape = e.ModelElement as CarShape;
 Store store = shape.Store;
 // Ignore this call if we're currently loading a model:
 if (store.TransactionManager.CurrentTransaction.IsSerializing)
  return;
 Car car = shape.ModelElement as Car;
 // Code here propagates change as required - for example:
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;
 }
}
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
 protected override Type[] GetCustomDomainModelTypes()
 {
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
  types.Add(typeof(CarShapeAddRule));
  // If you add more rules, list them here.
  return types.ToArray();
 }
 }
}
```