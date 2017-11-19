---
title: "Kontrolowanie kolor, styl linii i inne właściwości kształtu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c06d0066-24aa-4c65-b91c-c2089b81ec8d
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 1d2ed7170189ad48474a7cf8422386b6198ccc9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
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