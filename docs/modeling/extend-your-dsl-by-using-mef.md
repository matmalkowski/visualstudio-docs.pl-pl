---
title: Rozszerzanie DSL za pomocą MEF
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8cc48c70cd6fe8bd45ed65b96732d3db31a386e2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="extend-your-dsl-by-using-mef"></a>Rozszerzanie DSL za pomocą MEF
Języka specyficznego dla domeny (DSL) można rozszerzyć za pomocą Managed Extensibility Framework (MEF). Użytkownik lub inni deweloperzy będą mogli zapisać rozszerzenia DSL bez zmiany definicji DSL i kod programu. Takie rozszerzenia obejmują poleceń menu, przeciągnij i upuść programów obsługi i sprawdzania poprawności. Użytkownicy będą mogli do zainstalowania programu DSL, a następnie opcjonalnie zainstalować rozszerzenia dla niego.

 Ponadto po włączeniu MEF w Twojej DSL, może być łatwiejsze do pisania niektóre funkcje programu DSL, nawet jeśli zostały one wszystkie utworzone wraz z DSL.

 Aby uzyskać więcej informacji na temat MEF, zobacz [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>Aby włączyć Twojej DSL rozszerzyć o MEF

1.  Utwórz nowy folder o nazwie **MefExtension** wewnątrz **DslPackage** projektu. Dodaj następujące pliki do niej:

     Nazwa pliku: `CommandExtensionVSCT.tt`

    > [!IMPORTANT]
    >  Ustaw identyfikator GUID w tym pliku, aby być taka sama jak CommandSetId identyfikator GUID, który jest zdefiniowany w DslPackage\GeneratedCode\Constants.tt

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#
    // CmdSet Guid must be defined before master template is included
    // This Guid must be kept synchronized with the CommandSetId Guid in Constants.tt
    Guid guidCmdSet = new Guid ("00000000-0000-0000-0000-000000000000");
    string menuidCommandsExtensionBaseId="0x4000";
    #>
    <#@ include file="DslPackage\CommandExtensionVSCT.tt" #>
    ```

     Nazwa pliku: `CommandExtensionRegistrar.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>
    ```

     Nazwa pliku: `ValidationExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>
    ```

     Nazwa pliku: `ValidationExtensionRegistrar.tt`

     Jeśli dodasz ten plik, należy włączyć sprawdzanie poprawności w Twojej DSL przy użyciu co najmniej jednego z przełączników w **EditorValidation** w Eksploratorze DSL.

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
    ```

     Nazwa pliku: `PackageExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
    ```

2.  Utwórz nowy folder o nazwie **MefExtension** wewnątrz **Dsl** projektu. Dodaj następujące pliki do niej:

     Nazwa pliku: `DesignerExtensionMetaDataAttribute.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>
    ```

     Nazwa pliku: `GestureExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionEnablement.tt" #>
    ```

     Nazwa pliku: `GestureExtensionController.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionController.tt" #>
    ```

3.  Dodaj następujący wiersz do istniejącego pliku o nazwie **DslPackage\Commands.vsct**:

    ```
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
    ```

     Wstaw wiersz po istniejącej `<Include>` dyrektywy.

4.  `Open DslDefinition.dsl.`

5.  W Eksploratorze DSL wybierz **Editor\Validation**.

6.  W oknie właściwości, upewnij się, że co najmniej jedna z właściwości o nazwie **używa...**  jest `true`.

7.  Na pasku narzędzi Eksplorator rozwiązań, kliknij przycisk **Przekształć wszystkie szablony**.

     Pliki pomocnicze są wyświetlane poniżej każdy z plików, które zostały dodane.

8.  Tworzenie i uruchamianie rozwiązania, aby zweryfikować, że nadal działa.

 Twoje DSL jest teraz włączone MEF. Polecenia menu, procedury obsługi gestów i ograniczenia sprawdzania poprawności można napisać jako MEF rozszerzenia. Te rozszerzenia można pisać w rozwiązaniu DSL wraz z innymi kodu niestandardowego. Ponadto możesz lub innymi deweloperami może zapisywać oddzielnych [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Twojego DSL rozszerzeń.

## <a name="creating-an-extension-for-a-mef-enabled-dsl"></a>Tworzenie rozszerzenia dla DSL włączone MEF
 Jeśli masz dostęp do włączone MEF DSL, utworzony przez siebie lub innej osoby, może zapisać rozszerzeń dla niego. Rozszerzenia umożliwia dodawanie polecenia menu, procedury obsługi gestów lub ograniczenia sprawdzania poprawności. Aby tworzyć te rozszerzenia, należy użyć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania rozszerzenia (VSIX). Rozwiązanie ma dwie części: projektu biblioteki klas, która tworzy zestaw kodu i projektu VSIX, który zestaw pakietów.

#### <a name="to-create-a-dsl-extension-vsix"></a>Aby utworzyć rozszerzenie VSIX DSL

1.  Tworzenie nowego projektu biblioteki klas. Aby to zrobić, w **nowy projekt** okno dialogowe, wybierz opcję **Visual Basic** lub **Visual C#** , a następnie wybierz **biblioteki klas**.

2.  W nowym projekcie biblioteki klasy Dodaj odwołanie do zestawu DSL.

    -   Ten zestaw ma zazwyczaj nazwę, która kończy się wyrazem ". DSL.dll".

    -   Jeśli masz dostęp do projektu DSL, można znaleźć pliku zestawu w katalogu **Dsl\bin\\\***

    -   Jeśli masz dostęp do pliku DSL VSIX, zmieniając rozszerzenie nazwy pliku w pliku VSIX "zip" można znaleźć zestawu. Dekompresja pliku zip.

3.  Dodaj odwołania do następujących zestawów platformy .NET:

    -   Microsoft.VisualStudio.Modeling.Sdk.11.0.dll

    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll

    -   Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll

    -   System.ComponentModel.Composition.dll

    -   System.Windows.Forms.dll

4.  Tworzenie projektu VSIX na tym samym rozwiązaniu. W tym, w **nowy projekt** okna dialogowego rozwiń **Visual Basic** lub **Visual C#**, kliknij przycisk **rozszerzalności**, a następnie wybierz  **Projektu VSIX**.

5.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projektu VSIX, a następnie kliknij przycisk **Ustaw jako projekt startowy**.

6.  W nowym projekcie, otwórz **source.extension.vsixmanifest**.

7.  Kliknij przycisk **dodać zawartość**. W oknie dialogowym Ustaw **typu zawartości** do **składników MEF**, i **projekt źródłowy** do projektu biblioteki klas.

8.  Dodaj odwołanie do DSL VSIX.

    1.  W **source.extension.vsixmanifest**, kliknij przycisk **Dodaj odwołanie**

    2.  W oknie dialogowym kliknij **dodać ładunku** , a następnie zlokalizuj plik VSIX DSL. Plik VSIX jest wbudowana w rozwiązanie DSL w **DslPackage\bin\\\***.

         Umożliwia to użytkownikom instalowanie DSL i rozszerzenie w tym samym czasie. Jeśli użytkownik zainstalował już DSL, zostanie zainstalowana tylko na Twoje rozszerzenie.

9. Przeglądu i aktualizowania innych pól **source.extension.vsixmanifest**. Kliknij przycisk **Wybierz wersje** i upewnij się, że zostały prawidłowo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wersje są ustawione.

10. Dodaj kod do projektu biblioteki klas. Użyj przykładów w następnej sekcji jako przewodnika.

     Możesz dodać dowolną liczbę polecenia gestu, klasy i sprawdzania poprawności.

11. Aby przetestować rozszerzenia, naciśnij klawisz **F5**. W eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], utworzyć lub otworzyć przykładowy plik DSL.

## <a name="writing-mef-extensions-for-dsls"></a>Pisanie rozszerzenia MEF dla DSLs
 Można napisać rozszerzeń w projekcie kodu zestawu oddzielnym rozwiązaniu rozszerzenia DSL. Umożliwia także MEF w projekcie DslPackage to wygodny sposób można zapisać jako część DSL poleceń, gestów i kodu walidacji.

### <a name="menu-commands"></a>Polecenia menu
 Aby napisać polecenia menu, Definiowanie klasy, która implementuje <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> i prefiksu klasę atrybutem, który jest zdefiniowany w DSL o nazwie *YourDsl*`CommandExtension`. Można zapisać więcej niż jedną klasę polecenia menu.

 `QueryStatus()` jest wywoływana, gdy użytkownik kliknie prawym przyciskiem myszy diagramu. Należy sprawdzić bieżące zaznaczenie i ustaw `command.Enabled` wskaż, jeśli polecenie ma zastosowanie.

```
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl; // My DSL
using Company.MyDsl.ExtensionEnablement; // My DSL
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement; // IVsSelectionContext
using Microsoft.VisualStudio.Modeling.ExtensionEnablement; // ICommandExtension

namespace MyMefExtension
{
  // Defined in Dsl\MefExtension\DesignerExtensionMetaDataAttribute.cs:
  [MyDslCommandExtension]
  public class MyCommandClass : ICommandExtension
  {
    /// <summary>
    /// Provides access to current document and selection.
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Called when the user selects this command.
    /// </summary>
    /// <param name="command"></param>
    public void Execute(IMenuCommand command)
    {
      // Transaction is required if you want to update elements.
      using (Transaction t = SelectionContext.CurrentStore
              .TransactionManager.BeginTransaction("fix names"))
      {
        foreach (ExampleShape shape in SelectionContext.CurrentSelection)
        {
          ExampleElement element = shape.ModelElement as ExampleElement;
          element.Name = element.Name + " !";
        }
        t.Commit();
      }
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines whether the command should appear.
    /// This method should set command.Enabled and command.Visible.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled =
        command.Visible = (SelectionContext.CurrentSelection.OfType<ExampleShape>().Count() > 0);
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines the text of the command in the menu.
    /// </summary>
    public string Text
    {
      get { return "My menu command"; }
    }
  }
}

```

### <a name="gesture-handlers"></a>Programy obsługi gestów
 Procedury obsługi gestów mogą dotyczyć obiektów przeciągnięto diagramu z dowolnego miejsca, wewnątrz lub na zewnątrz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Poniższy przykład umożliwia użytkownikowi przeciągnij pliki z Eksploratora Windows na diagramie. Tworzy on elementy, które zawierają nazwy plików.

 Można podczas pisania obsług radzenia sobie z drags z innymi modelami DSL i modeli UML. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md).

```

using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace MefExtension
{
  [MyDslGestureExtension]
  class MyGestureExtension : IGestureExtension
  {
    public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
    {
      System.Windows.Forms.MessageBox.Show("double click!");
    }

    /// <summary>
    /// Called when the user drags anything over the diagram.
    /// Return true if the dragged object can be dropped on the current target.
    /// </summary>
    /// <param name="targetMergeElement">The shape or diagram that the mouse is currently over</param>
    /// <param name="diagramDragEventArgs">Data about the dragged element.</param>
    /// <returns></returns>
    public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      // This handler only allows items to be dropped onto the diagram:
      return targetMergeElement is MefDsl2Diagram &&
      // And only accepts files dragged from Windows Explorer:
        diagramDragEventArgs.Data.GetFormats().Contains("FileNameW");
    }

    /// <summary>
    /// Called when the user drops an item onto the diagram.
    /// </summary>
    /// <param name="targetDropElement"></param>
    /// <param name="diagramDragEventArgs"></param>
    public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      MefDsl2Diagram diagram = targetDropElement as MefDsl2Diagram;
      if (diagram == null) return;

      // This handler only accepts files dragged from Windows Explorer:
      string[] draggedFileNames = diagramDragEventArgs.Data.GetData("FileNameW") as string[];
      if (draggedFileNames == null || draggedFileNames.Length == 0) return;

      using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("file names"))
      {
        // Create an element to represent each file:
        foreach (string fileName in draggedFileNames)
        {
          ExampleElement element = new ExampleElement(diagram.ModelElement.Partition);
          element.Name = fileName;

          // This method of adding the new element allows the position
          // of the shape to be specified:
          ElementGroup group = new ElementGroup(element);
          diagram.ElementOperations.MergeElementGroupPrototype(
            diagram, group.CreatePrototype(), PointD.ToPointF(diagramDragEventArgs.MousePosition));
        }
        t.Commit();
      }
    }
  }
}

```

### <a name="validation-constraints"></a>Ograniczenia walidacji
 Sprawdzanie poprawności metody są oznaczane `ValidationExtension` atrybut, który jest generowany przez DSL, a także przez <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute>. Metoda może występować w dowolnej klasy, która nie jest oznaczona przez atrybut.

 Aby uzyskać więcej informacji, zobacz [sprawdzania poprawności języka specyficznego dla domeny](../modeling/validation-in-a-domain-specific-language.md).

```
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.Validation;

namespace MefExtension
{
  class MyValidationExtension // Can be any class.
  {
    // SAMPLE VALIDATION METHOD.
    // All validation methods have the following attributes.

    // Specific to the extended DSL:
    [MyDslValidationExtension]

    // Determines when validation is applied:
    [ValidationMethod(
       ValidationCategories.Save
     | ValidationCategories.Open
     | ValidationCategories.Menu)]

    /// <summary>
    /// When validation is executed, this method is invoked
    /// for every element in the model that is an instance
    /// of the second parameter type.
    /// </summary>
    /// <param name="context">For reporting errors</param>
    /// <param name="elementToValidate"></param>
    private void ValidateClassNames
      (ValidationContext context,
       // Type determines to what elements this will be applied:
       ExampleElement elementToValidate)
    {
      // Write code here to test values and links.
      if (elementToValidate.Name.IndexOf(' ') >= 0)
      {
        // Log any unacceptable values:
        context.LogError(
          // Description:
          "Name must not contain spaces"
          // Error code unique to this type of error:
          , "MyDsl001"
          // Element to highlight when user double-clicks error:
          , elementToValidate);
} } } }

```

## <a name="see-also"></a>Zobacz też

- [Dostarczanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)
- [Instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Walidacja w języku specyficznym dla domeny](../modeling/validation-in-a-domain-specific-language.md)