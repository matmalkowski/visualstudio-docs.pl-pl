---
title: Osadzanie diagramu w formularzu systemu Windows | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa6cd040-7c88-4329-b9c3-2a80b312610f
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: a19aef7cc11e7db1e04a6f54e4438f74227a55ee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Osadzanie diagramu w formularzu systemu Windows
DSL diagram można osadzić w formancie systemu Windows, który jest wyświetlany w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] okna.  
  
## <a name="embedding-a-diagram"></a>Osadzanie diagramu  
  
#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Aby osadzić DSL diagram w formancie systemu Windows  
  
1.  Dodaj nową **kontrolki użytkownika** plik do projektu DslPackage.  
  
2.  Dodawanie formantu panelu do formantu użytkownika. Panel ten będzie zawierać DSL Diagram.  
  
     Dodać inne formanty, które są potrzebne.  
  
     Ustaw właściwości zakotwiczenia formantów.  
  
3.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy plik kontrolki użytkownika, a następnie kliknij przycisk **kod widoku**. Dodaj ten konstruktor i zmiennych w kodzie:  
  
    ```csharp  
  
    internal UserControl1(MyDSLDocView docView, Control content)  
      : this()  
    {  
      panel1.Controls.Add(content);  
      this.docView = docView;  
    }  
    private MyDSLDSLDocView docView;  
  
    ```  
  
4.  Dodaj nowy plik do projektu DslPackage o następującej treści:  
  
    ```  
    using System.Windows.Forms;  
    namespace Company.MyDSL  
    {  
      partial class MyDSLDocView  
      {  
        private UserControl1 container;  
        public override IWin32Window Window  
        {  
          get  
          {  
            if (container == null)  
            {  
              // Put our own form inside the DSL window:  
              container = new UserControl1(this,  
                (Control)base.Window);  
            }  
            return container;  
    } } } }  
  
    ```  
  
5.  Aby przetestować DSL, naciśnij klawisz F5 i Otwórz plik przykładowy model. Wyświetlany w formancie. Przybornika i inne funkcje działają normalnie.  
  
#### <a name="updating-the-form-using-store-events"></a>Aktualizowanie formularza przy użyciu magazynu  
  
1.  W projektancie formularzy dodać **ListBox** o nazwie `listBox1`. Spowoduje to wyświetlenie listy elementów w modelu. Zostaną zachowane w synchronism przy użyciu modelu *przechowywania zdarzeń*. Aby uzyskać więcej informacji, zobacz [obsługi Propaguj zmiany poza Model zdarzeń](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
2.  W pliku kodu niestandardowego Zastąp dodatkowe metody do klasy widok dokumentu:  
  
    ```  
  
    partial class MyDSLDocView  
    {  
     /// <summary>  
     /// Register store event listeners.  
     /// This method is called when the model and diagram    
     /// have completed loading.   
     /// </summary>  
     protected override bool LoadView()  
      {  
        bool result = base.LoadView();  
        Store store = this.DocData.Store;  
        EventManagerDirectory emd = store.EventManagerDirectory;  
        DomainClassInfo componentClass = store.DomainDataDirectory.FindDomainClass(typeof(ExampleElement));  
        emd.ElementAdded.Add(componentClass, new EventHandler<ElementAddedEventArgs>(AddElement));  
        emd.ElementDeleted.Add(componentClass, new EventHandler<ElementDeletedEventArgs>(RemoveElement));  
  
        // Do the initial parts list:  
        container.SetUpFormFromModel();  
        return result;  
      }  
     /// <summary>  
     /// Listener method called on creation of each instance of   
     /// the ExampleElement class or its subclasses.  
     /// </summary>  
     private void AddElement(object sender, ElementAddedEventArgs e)  
     {  
       container.Add(e.ModelElement as ExampleElement);  
     }  
     /// <summary>  
     /// Listener method called after deletion of each instance of   
     /// the ExampleElement class or its subclasses.  
     /// </summary>  
     private void RemoveElement(object sender, ElementDeletedEventArgs e)  
     {  
       container.Remove(e.ModelElement as ExampleElement);  
     }  
  
    ```  
  
3.  W kodzie kontrolki użytkownika Wstaw metod do nasłuchiwania elementy dodawane i usuwane:  
  
    ```  
  
          public partial class UserControl1 : UserControl { ...  
  
    private ExampleModel modelRoot;  
  
    internal void Add(ExampleElement e) { UpdatePartsList(); }  
    internal void Remove(ExampleElement e) { UpdatePartsList(); }  
  
    internal void SetUpFormFromModel()  
    {  
      modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;  
      UpdatePartsList();  
    }  
  
    private void UpdatePartsList()  
    {  
      StringBuilder builder = new StringBuilder();  
      listBox1.Items.Clear();  
      foreach (ExampleElement c in modelRoot.Elements)  
      {  
        listBox1.Items.Add(c.Name);  
      }  
    }  
  
    ```  
  
4.  Aby przetestować DSL, naciśnij klawisz F5 w eksperymentalne wystąpienie programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], otwórz plik przykładowy model.  
  
     Należy zauważyć, że pole listy zawiera listę elementów w modelu i czy jest poprawna po albo i po Cofnij i ponów.  
  
## <a name="see-also"></a>Zobacz też  
 [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)