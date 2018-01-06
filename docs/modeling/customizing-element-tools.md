---
title: "Dostosowywanie narzędzia elementu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: "6"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 2571fd137875a0971b7a9e4364849a3105ca220a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-element-tools"></a>Narzędzia dostosowywania elementów
W niektórych definicjach DSL jednej koncepcji reprezentowały grupę elementów. Na przykład w przypadku utworzenia modelu, w którym składnik ma ustalony zbiór portów, zawsze ma portów należy utworzyć w tym samym czasie jako składnik ich nadrzędnego. W związku z tym należy dostosować narzędzie do tworzenia elementu tak, aby tworzy grupę elementów, a nie tylko jednego. Aby to osiągnąć, można dostosować, jak narzędzie do tworzenia elementu został zainicjowany.  
  
 Można również zastąpić, co się dzieje, gdy narzędzie jest przeciągnięto diagramu lub elementu.  
  
## <a name="customizing-the-content-of-an-element-tool"></a>Dostosowywanie narzędzia Element zawartości  
 Każdy element narzędzie przechowuje wystąpienia <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), który zawiera wersja po serializacji elementów modelu oraz łącza. Domyślnie EGP narzędzia element zawiera jedno wystąpienie klasy określonym dla narzędzia. Można to zmienić przez zastąpienie *YourLanguage*`ToolboxHelper.CreateElementToolPrototype`. Ta metoda jest wywoływana po załadowaniu pakietu DSL.  
  
 Parametr metody jest identyfikator klasy określony w definicji DSL. Po wywołaniu metody w klasie myślisz, możesz dodać dodatkowe elementy do EGP.  
  
 EGP musi zawierać osadzanie łącza z jednego elementu głównego do elementów pomocniczych. Może również obejmować linki odwołań.  
  
 Poniższy przykład tworzy main element i dwa elementy osadzone. Klasy głównym jest nazywany rezystor i ma dwie relacje osadzania elementy o nazwie terminalu. Osadzanie właściwości roli są nazywane Terminal1 i Terminal2 i mają liczebność 1..1.  
  
```  
using Microsoft.VisualStudio.Modeling; ...    
public partial class CircuitDiagramToolboxHelper  
{  
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)  
  {  
    // A case for each tool to customize:    
    if (domainClassId == Resistor.DomainClassId)  
    {  
      // Set up the prototype elements and links:  
      Resistor resistor = new Resistor(store);  
      resistor.Terminal1 = new Terminal(store);   
      resistor.Terminal2 = new Terminal(store);  
      resistor.Terminal1.Name = "T1"; // embedding  
      resistor.Terminal2.Name = "T2"; // embedding  
      // We could also set up reference links.  
  
      // Create an element group prototype for the toolbox:  
      ElementGroup egp = new ElementGroup(store.DefaultPartition);  
      egp.AddGraph(resistor, true);  
      // We do not have to explicitly include embedded children.  
      return egp.CreatePrototype();  
    }  
    // Element tools for other classes:  
    else  
      return base.CreateElementToolPrototype(store, domainClassId);  
  }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie tworzenia i przesuwania elementu](../modeling/customizing-element-creation-and-movement.md)