---
title: 'Porady: dostęp i ograniczyć bieżące zaznaczenie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 278947fdb9851bdc54a80ea7f2d47d72deba300e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Porady: ograniczenie bieżącego wyboru i uzyskiwanie dostępu do niego
Podczas obsługi polecenia lub gestu pisania dla danego języka specyficznego dla domeny, należy określić element, jakie użytkownik kliknął prawym przyciskiem myszy. Można również uniemożliwić niektórych kształtów lub pola wybierane. Na przykład można rozmieścić, że gdy użytkownik kliknie ikonę dekoratora, kształtu, który go zawiera zamian zostanie wybrany. Zaznaczenie w ten sposób ograniczający zmniejsza liczbę obsługi, które trzeba zapisać. On również ułatwia dla użytkownika, który można kliknij w dowolnym miejscu w kształcie bez konieczności uniknąć dekorator.  
  
## <a name="accessing-the-current-selection-from-a-command-handler"></a>Uzyskiwanie dostępu do bieżącego zaznaczenia z programem obsługi  
 Klasy zestawu poleceń języka specyficznego dla domeny zawiera programy obsługi poleceń dla Twojego polecenia niestandardowych. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Klasy, z którego pochodzi klasy zestawu poleceń języka specyficznego dla domeny, udostępnia kilka elementów członkowskich do uzyskiwania dostępu do bieżącego zaznaczenia.  
  
 W zależności od tego polecenia program obsługi poleceń może być konieczne zaznaczenie w Projektancie modeli, Eksplorator modelu lub aktywne okno.  
  
#### <a name="to-access-selection-information"></a>Dostęp do informacji zaznaczenia  
  
1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Klasa definiuje następujące elementy członkowskie, które mogą służyć do bieżącego zaznaczenia.  
  
    |Element członkowski|Opis|  
    |------------|-----------------|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A> — Metoda|Zwraca `true` elementy wybrane w Projektancie modeli w przypadku kształtu przedział; w przeciwnym razie `false`.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A> — Metoda|Zwraca `true` Jeśli diagramu jest wybrane w Projektancie modelu; w przeciwnym razie `false`.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A> — Metoda|Zwraca `true` Jeśli dokładnie jeden element jest wybrany w Projektancie modelu; w przeciwnym razie `false`.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A> — Metoda|Zwraca `true` Jeśli dokładnie jeden element jest wybrany w aktywnym oknie; w przeciwnym razie `false`.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> Właściwość|Pobiera zbiór elementów wybrane w Projektancie modeli tylko do odczytu.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> Właściwość|Pobiera zbiór elementów wybrane w aktywnym oknie tylko do odczytu.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> Właściwość|Pobiera element podstawowy zaznaczenia w Projektancie modelu.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> Właściwość|Pobiera element podstawowy zaznaczenia w aktywnym oknie.|  
  
2.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> Właściwość <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> klasy zapewnia dostęp do <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> obiekt reprezentujący okno projektanta modelu i udostępnia dodatkowe wybrane elementy w Projektancie modelu.  
  
3.  Ponadto wygenerowany kod definiuje właściwość okna narzędzia Eksplorator i explorer właściwość zaznaczenia w poleceniu set — Klasa języka specyficznego dla domeny.  
  
    -   Właściwość okna narzędzia Eksplorator Zwraca wystąpienie klasy okna Eksploratora narzędzia języka specyficznego dla domeny. Pochodną klasy okna narzędzia Eksplorator <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> klasy i reprezentuje Eksplorator modelu dla języka specyficznego dla domeny.  
  
    -   `ExplorerSelection` Właściwość zwraca wybranego elementu w Eksploratorze modelu dla języka specyficznego dla domeny.  
  
## <a name="determining-which-window-is-active"></a>Określanie, które okno jest aktywne  
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Zawiera interfejs definiuje elementów członkowskich, które zapewniają dostęp do bieżącego stanu zaznaczenia w powłoce. Możesz uzyskać <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> obiekt z klasy pakietu lub klasy zestawu poleceń języka specyficznego dla domeny za pomocą `MonitorSelection` właściwość zdefiniowana w klasie podstawowej każdego z nich. Klasa pakiet pochodzi z <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> klasa i klasy zestawu poleceń pochodną <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> klasy.  
  
#### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Aby określić z programem obsługi, jakiego rodzaju okno jest aktywne  
  
1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> Właściwość <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> klasy zwraca <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> obiekt, który zapewnia dostęp do bieżącego stanu zaznaczenia w powłoce.  
  
2.  <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> Właściwość <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> interfejsu pobiera kontenera aktywnego zaznaczenia, który może różnić się od aktywnego okna.  
  
3.  Dodaj następujące właściwości do polecenia ustawiane klasy języka specyficznego dla domeny, aby ustalić, jakiego rodzaju okno jest aktywne.  
  
    ```csharp  
    // using Microsoft.VisualStudio.Modeling.Shell;  
  
    // Returns true if the model designer is the active selection container;  
    // otherwise, false.  
    protected bool IsDesignerActive  
    {  
        get  
        {  
            return (this.MonitorSelection.CurrentSelectionContainer  
                is DiagramDocView);  
        }  
    }  
  
    // Returns true if the model explorer is the active selection container;  
    // otherwise, false.  
    protected bool IsExplorerActive  
    {  
        get  
        {  
            return (this.MonitorSelection.CurrentSelectionContainer  
                is ModelExplorerToolWindow);  
        }  
    }  
    ```  
  
## <a name="constraining-the-selection"></a>Ograniczający zaznaczenia  
 Przez dodanie reguł wyboru, można kontrolować, które elementy są zaznaczone, po wybraniu elementu w modelu. Na przykład aby zezwolić użytkownikowi traktować jako pojedyncza jednostka liczba elementów, należy użyć reguły zaznaczenia.  
  
#### <a name="to-create-a-selection-rule"></a>Aby utworzyć regułę wyboru  
  
1.  Utwórz plik niestandardowego kodu w projekcie DSL  
  
2.  Definiowanie klasy reguły wyboru, która jest pochodną <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> klasy.  
  
3.  Zastąpienie <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> metody klasy reguły wyboru, aby zastosować kryteriów wyboru.  
  
4.  Dodaj definicję klasy częściowej klasy ClassDiagram do pliku kodu niestandardowego.  
  
     `ClassDiagram` Pochodną klasy <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> klasy i jest zdefiniowany w wygenerowanym pliku kodu, Diagram.cs, w projekcie DSL.  
  
5.  Zastąpienie <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> właściwość `ClassDiagram` służącą do zwracania reguły niestandardowe wyboru.  
  
     Domyślna implementacja <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> właściwości pobiera obiekt reguły wyboru, który nie modyfikuje zaznaczenie.  
  
### <a name="example"></a>Przykład  
 Następujący plik kodu tworzy regułę wyboru rozszerzanym w celu uwzględnienia wszystkich wystąpień każdej początkowo wybrane kształty domeny.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
namespace CompanyName.ProductName.GroupingDsl  
{  
    public class CustomSelectionRules : DiagramSelectionRules  
    {  
        protected Diagram diagram;  
        protected IElementDirectory elementDirectory;  
  
        public CustomSelectionRules(Diagram diagram)  
        {  
            if (diagram == null) throw new ArgumentNullException();  
  
            this.diagram = diagram;  
            this.elementDirectory = diagram.Store.ElementDirectory;  
        }  
  
        /// <summary>Called by the design surface to allow selection filtering.  
        /// </summary>  
        /// <param name="currentSelection">[in] The current selection before any  
        /// ShapeElements are added or removed.</param>  
        /// <param name="proposedItemsToAdd">[in/out] The proposed DiagramItems to  
        /// be added to the selection.</param>  
        /// <param name="proposedItemsToRemove">[in/out] The proposed DiagramItems  
        /// to be removed from the selection.</param>  
        /// <param name="primaryItem">[in/out] The proposed DiagramItem to become  
        /// the primary DiagramItem of the selection. A null value signifies that  
        /// the last DiagramItem in the resultant selection should be assumed as  
        /// the primary DiagramItem.</param>  
        /// <returns>true if some or all of the selection was accepted; false if  
        /// the entire selection proposal was rejected. If false, appropriate  
        /// feedback will be given to the user to indicate that the selection was  
        /// rejected.</returns>  
        public override bool GetCompliantSelection(  
            SelectedShapesCollection currentSelection,  
            DiagramItemCollection proposedItemsToAdd,  
            DiagramItemCollection proposedItemsToRemove,  
            DiagramItem primaryItem)  
        {  
            if (currentSelection.Count == 0 && proposedItemsToAdd.Count == 0) return true;  
  
            HashSet<DomainClassInfo> itemsToAdd = new HashSet<DomainClassInfo>();  
  
            foreach (DiagramItem item in proposedItemsToAdd)  
            {  
                if (item.Shape != null)  
                    itemsToAdd.Add(item.Shape.GetDomainClass());  
            }  
            proposedItemsToAdd.Clear();  
            foreach (DomainClassInfo classInfo in itemsToAdd)  
            {  
                foreach (ModelElement element  
                    in this.elementDirectory.FindElements(classInfo, false))  
                {  
                    if (element is ShapeElement)  
                    {  
                        proposedItemsToAdd.Add(  
                            new DiagramItem((ShapeElement)element));  
                    }  
                }  
            }  
  
            return true;  
        }  
    }  
  
    public partial class ClassDiagram  
    {  
        protected CustomSelectionRules customSelectionRules = null;  
  
        protected bool multipleSelectionMode = true;  
  
        public override DiagramSelectionRules SelectionRules  
        {  
            get  
            {  
                if (multipleSelectionMode)  
                {  
                    if (customSelectionRules == null)  
                    {  
                        customSelectionRules = new CustomSelectionRules(this);  
                    }  
                    return customSelectionRules;  
                }  
                else  
                {  
                    return base.SelectionRules;  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>