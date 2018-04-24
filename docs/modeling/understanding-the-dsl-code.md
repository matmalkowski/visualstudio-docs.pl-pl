---
title: Znajomość kodu DSL
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, generated code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: ced29b2936f8bec00df3907ffaf54bd06c32ad80
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="understanding-the-dsl-code"></a>Znajomość kodu DSL
Interfejs API, który umożliwia odczytywanie i aktualizowanie wystąpień DSL w generuje rozwiązania języka specyficznego dla domeny (DSL) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Ten interfejs API jest zdefiniowana w kodzie, który jest generowany na podstawie definicji DSL. W tym temacie opisano wygenerowanego interfejsu API.

## <a name="the-example-solution-component-diagrams"></a>Przykładowe rozwiązanie: diagramy składników
 Aby utworzyć rozwiązanie, który jest źródłem Większość przykładów w tym temacie, należy utworzyć DSL z **modeli składnika** szablon rozwiązania. Jest to jedna z standardowych szablonów, które pojawia się podczas tworzenia nowego rozwiązania DSL.

> [!NOTE]
>  Szablon DSL diagramy składników nie jest powiązana z diagramy składników UML utworzone przy użyciu menu architektura programu Visual Studio. W **nowy projekt** okna dialogowego rozwiń **inne Types\Extensibility projektu** , a następnie kliknij przycisk **projektanta języka specyficznego dla domeny**.

 Naciśnij klawisz F5 i doświadczenia, jeśli nie masz doświadczenia z tym szablonem rozwiązania. Zwróć uwagę w szczególności utworzyć portów przeciągając narzędzie portu na składnika i że możesz połączyć portów.

 ![Składniki i portów połączonych](../modeling/media/componentsample.png "ComponentSample")

## <a name="the-structure-of-the-dsl-solution"></a>Struktura rozwiązania DSL
 **Dsl** projekt definiuje interfejs API dla Twojego DSL. **DslPackage** projekt definiuje sposobu integracji z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Można również dodać własne projekty, które również mogą zawierać kod wygenerowane na podstawie modelu.

### <a name="the-code-directories"></a>Katalogi kodu
 Większość kodu w każdym z tych projektów jest generowany na podstawie **Dsl\DslDefinition.dsl**. Wygenerowany kod znajduje się w **wygenerowany kod** folderu. Aby wyświetlić wygenerowany plik, kliknij przycisk **[+]** obok Generowanie **.TT —** pliku.

 Firma Microsoft zaleca sprawdzenie wygenerowany kod, aby lepiej zrozumieć DSL. Aby wyświetlić wygenerowanych plików, rozwiń pliki *.tt w Eksploratorze rozwiązań.

 \*.TT — pliki zawierają bardzo mało generowania kodu. Zamiast tego należy użyć `<#include>` dyrektywy dołączać pliki udostępnione szablonu. Udostępnione pliki znajdują się w **\Program Files\Microsoft programu Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates**

 Po dodaniu kodu źródłowego rozwiązania DSL, dodaj ją w osobnym pliku, znajduje się poza folderem wygenerowany kod. Należy utworzyć **kod niestandardowy** folderu. (Po dodaniu nowych plików kodu do folderu niestandardowego, pamiętaj, aby rozwiązać przestrzeń nazw w szkielet kodu początkowego.)

 Zdecydowanie zaleca się czy nie zmienisz wygenerowany kod bezpośrednio, ponieważ zmiany zostaną utracone podczas możesz ponownie skompiluj rozwiązanie. Zamiast tego aby dostosować Twojej DSL:

-   Dostosuj wiele parametrów w definicji DSL.

-   Zapisywać w plikach oddzielny kod klasy częściowe zastąpienie metody, które są zdefiniowane w lub dziedziczone przez wygenerowane klasy. W niektórych przypadkach należy ustawić **generuje podwójne pochodnych** opcji klasy w definicji DSL, aby można było zastąpić metodę wygenerowany.

-   Ustaw opcje w definicji DSL powodujące wygenerowany kod w celu zapewnienia 'punkty zaczepienia' swoim własnym kodem.

     Na przykład jeśli ustawisz **Konstruktor ma niestandardowy** opcji klasą domeny, a następnie Skompiluj rozwiązanie, zostanie wyświetlone komunikaty o błędach. Po dwukrotnym kliknięciu te komunikaty o błędach, zobaczysz komentarze, wyjaśniające, co powinno dostarczyć niestandardowy kod w wygenerowanym kodzie.

-   Napisać własne szablony tekstu, aby wygenerować kod specyficzne dla aplikacji. Użytkownik może Użyj zawierać pliki, aby udostępnić części szablonów, które są wspólne dla wielu projektów i tworzenia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] szablony do ustawiania projektów, które są inicjowane z strukturę pliku projektu.

## <a name="generated-files-in-dsl"></a>Pliki generowane Dsl
 Następujące pliki generowane są wyświetlane w **Dsl** projektu.

 *YourDsl* `Schema.xsd`

 Schemat dla plików, który zawiera wystąpień programu DSL. Ten plik jest kopiowany do kompilowania (**bin**) katalogu. Po zainstalowaniu programu DSL, możesz skopiować ten plik, aby **11.0\Xml\Schemas programu Visual Studio \Program Files\Microsoft** , dzięki czemu można zweryfikować pliki modelu. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązań języka specyficznego dla domeny](../modeling/deploying-domain-specific-language-solutions.md).

 Jeśli serializacji jest dostosowane przez ustawienie opcji w Eksploratorze DSL, schemat zostanie zmieniona. Jednak podczas pisania kodu serializacji, ten plik nie może reprezentować rzeczywistego schematu. Aby uzyskać więcej informacji, zobacz [dostosowywania magazynu plików i serializacja XML](../modeling/customizing-file-storage-and-xml-serialization.md).

 `ConnectionBuilders.cs`

 Konstruktor połączeń jest klasa, która umożliwia tworzenie relacji. Jest kod związany z narzędziem do połączenia. Ten plik zawiera pary klasy dla każdego narzędzia połączenia. Ich nazwy są uzyskiwane z nazw narzędzia połączenia i relacji domeny: *relacji*konstruktora, i *ConnectorTool*ConnectAction.

 (W tym przykładzie składnik rozwiązania nosi nazwę jednego z konstruktorów połączenia ConnectionBuilder, to zbieżność, dlatego relacja domeny nosi nazwę połączenie).

 Relacja jest tworzony w *relacji* `Builder.Connect()` metody. Wersja domyślna sprawdza, czy są dozwolone elementy modelu źródłowym i docelowym i tworzy wystąpienie relacji. Na przykład:

 `CommentReferencesSubject(sourceAccepted, targetAccepted);`

 Każda klasa Konstruktor jest generowana z węzła w **konstruktorów połączenia** sekcji w Eksploratorze DSL. Jeden `Connect` metody można utworzyć relacji między co najmniej jeden pary klas domeny. Każda para jest zdefiniowany przez dyrektywę połączyć Link, który można znaleźć w Eksploratorze DSL w węźle konstruktora.

 Można na przykład dodać do jednego konstruktora połączenia dyrektywy połączyć łącze, dla każdego z trzech rodzajów relacji w przykładowym DSL. Zapewni to użytkownika za pomocą narzędzia jednego połączenia. Typ relacji wystąpienia zależą od typów elementów źródłowych i docelowych wybrane przez użytkownika.  Aby dodać łącze dyrektywy połączenia, kliknij prawym przyciskiem myszy konstruktora w Eksploratorze DSL.

 Aby napisać kod niestandardowy, który jest uruchamiany, gdy jest tworzony dla określonego typu relacji domeny, wybierz odpowiednie dyrektywy połączyć łącze w węźle konstruktora. W oknie właściwości ustaw **niestandardowe korzysta z połączenia**. Ponownie skompiluj rozwiązanie, a następnie podaj kod, aby poprawić błędy wynikowy.

 Pisanie kodu niestandardowego, zawsze wtedy, gdy użytkownik korzysta z tego narzędzia połączenia, należy ustawić **jest niestandardowe** właściwości konstruktora połączenia. Możesz podać kod, który decyduje o tym, czy element źródłowy jest dozwolony, czy określona kombinacja źródła docelowy jest dozwolone i które aktualizacje powinny zostać wprowadzone do modelu po nawiązaniu połączenia. Na przykład można zezwolić na połączenia tylko wtedy, gdy nie spowoduje utworzenie pętli na diagramie. Zamiast łącze jednej relacji można utworzyć wystąpienia bardziej złożonym wzorcem kilka wzajemnie powiązanych elementów między źródłem a celem.

 `Connectors.cs`

 Zawiera klasy dla łączników, które są elementów diagramu, które zwykle odpowiadają relacji odwołania. Każda klasa jest generowany na podstawie jeden łącznik w definicji DSL. Każda klasa łącznika jest pochodną <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 Aby kolor i niektórych innych zmiennej funkcje stylu w czasie wykonywania, kliknij prawym przyciskiem myszy na diagramie DSL definicji klasy, a następnie wskaż **dodać widoczne**.

 Aby styl dodatkowe funkcje zmienną w czasie wykonywania, zobacz na przykład <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> i <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>.

 `Diagram.cs`

 Zawiera klasy, która definiuje diagramu. Jest pochodną <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>.

 Aby kolor i niektórych innych zmiennej funkcje stylu w czasie wykonywania, kliknij prawym przyciskiem myszy na diagramie DSL definicji klasy, a następnie wskaż **dodać widoczne**.

 Ponadto ten plik zawiera `FixupDiagram` reguły, która odpowiada po dodaniu nowego elementu do modelu. Reguła dodaje nowy kształt i łączy kształt z elementem modelu.

 `DirectiveProcessor.cs`

 Procesor dyrektywy ułatwia użytkownikom zapisu szablony tekstu, które odczytu wystąpienia użytkownika DSL. Procesor dyrektywy ładuje zestawy (dll) dla sieci DSL i efektywnie wstawia `using` instrukcje dla przestrzeni nazw. Dzięki temu kod w szablonach tekstowych do użycia klasy i relacje zdefiniowane w Twojej DSL.

 Aby uzyskać więcej informacji, zobacz [generowania kodu języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md) i [tworzenie procesory dyrektywy szablonu niestandardowego T4 tekstu](../modeling/creating-custom-t4-text-template-directive-processors.md).

 `DomainClasses.cs`

 Implementacje klasy domeny, które zostały zdefiniowane, łącznie z klasy abstrakcyjne i klasy głównym modelu. Są pochodnymi <xref:Microsoft.VisualStudio.Modeling.ModelElement>.

 Każda klasa domeny zawiera:

-   Definicja właściwości i klasy zagnieżdżonej obsługi dla każdej właściwości domeny. Można zastąpić OnValueChanging() i OnValueChanged(). Aby uzyskać więcej informacji, zobacz [obsługi zmiany wartości właściwości domeny](../modeling/domain-property-value-change-handlers.md).

     W przykładzie DSL `Comment` klasy zawiera właściwość `Text` i klasę programu obsługi `TextPropertyHandler`.

-   Metody dostępu właściwości relacji, w których uczestniczy klasy tej domeny. (Nie jest Brak zagnieżdżonej klasy dla właściwości roli).

     W przykładzie DSL `Comment` klasa ma metody dostępu, które uzyskują dostęp do swojego nadrzędnego modelu za pomocą relacja osadzania `ComponentModelHasComments`.

-   Konstruktory. Jeśli chcesz je zastąpić, ustaw **Konstruktor ma niestandardowy** klasy domeny.

-   Element metody obsługi grupy prototypu (EGP). Są one niezbędne, jeśli użytkownik może *scalania* (Dodaj) inny element na wystąpienie tej klasy. Zwykle ma to przeciągając je z narzędziem element lub innego kształtu lub wklejając.

     W tym przykładzie można scalić DSL, Port wejściowy lub Port wyjściowy na składnika. Ponadto na modelu można by scalić składników i komentarze. Program

     Metody obsługi EGP w klasie składnika zezwala na składnik do akceptowania portów, ale nie komentarze. Program obsługi EGP klasy głównym modelu akceptuje komentarze i składników, ale nie portów.

 `DomainModel.cs`

 Klasa, która reprezentuje modelu domeny. Jest pochodną <xref:Microsoft.VisualStudio.Modeling.DomainModel>.

> [!NOTE]
>  Nie jest taka sama jak klasa katalogu głównego modelu.

 Kopiuj i usunąć zamknięcia zdefiniować, co inne elementy powinny być uwzględnione, gdy element zostanie skopiowany lub usunięty. To zachowanie można kontrolować przez ustawienie **propaguje kopiowania** i **propaguje usunąć** właściwości ról na każdej stronie każdej relacji. Jeśli chcesz, aby wartości, które mają być określane dynamicznie, można napisać kod do przesłonięcia metody klasy zamknięcia.

 `DomainModelResx.resx`

 Zawiera parametry, takie jak opisy klasy i właściwości, nazwy właściwości etykiety przybornika, standardowe komunikaty i innych ciągów, które mogą być wyświetlane dla użytkownika. Zawiera także ikon narzędzi i obrazy kształtów obrazu.

 Ten plik jest powiązana w skompilowany zestaw i udostępnia domyślne wartości tych zasobów. Tworząc zestaw satelicki, zawierający zlokalizowanej wersji zasobów można lokalizować Twojej DSL. Tej wersji będą używane podczas DSL jest zainstalowany w odpowiadającym zlokalizowanych zasobów kultury. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązań języka specyficznego dla domeny](../modeling/deploying-domain-specific-language-solutions.md).

 `DomainRelationships.cs`

 Każde łącze między dwoma elementami modelu jest reprezentowany przez wystąpienie klasy relacji domeny. Wszystkie klasy relacji są uzyskiwane z <xref:Microsoft.VisualStudio.Modeling.ElementLink>, który z kolei jest określana na podstawie <xref:Microsoft.VisualStudio.Modeling.ModelElement>. Ponieważ jest elementem ModelElement wystąpienia relacji może mieć właściwości i może być źródłowa lub docelowa relacji.

 `HelpKeywordHelper.cs`

 Udostępnia funkcje, które są używane, gdy użytkownik naciśnie klawisz F1.

 `MultiplicityValidation.cs`

 W relacji ról, którym określić liczebność 1..1 lub 1.. *, użytkownik zostanie ostrzeżony tego co najmniej jedno wystąpienie relacji jest wymagana. Ten plik zawiera ograniczenia walidacji, które implementują tych ostrzeżeń. 1..1 łącze do osadzania nadrzędnego nie jest weryfikowany.

 Dla tych warunków ograniczających do wykonania musi być zainstalowany jeden z **używa...**  opcje w **Editor\Validation** węzła w Eksploratorze DSL. Aby uzyskać więcej informacji, zobacz [sprawdzania poprawności języka specyficznego dla domeny](../modeling/validation-in-a-domain-specific-language.md).

 `PropertiesGrid.cs`

 Ten plik zawiera kodu tylko wtedy, gdy deskryptora typu niestandardowego dołączono do właściwości domeny. Aby uzyskać więcej informacji, zobacz [dostosowywania okna właściwości](../modeling/customizing-the-properties-window.md).

 `SerializationHelper.cs`

-   Metody weryfikacji, aby upewnić się, że nie dwa elementy odwołuje się tej samej krótkiej nazwy. Aby uzyskać więcej informacji, zobacz [dostosowywania magazynu plików i serializacja XML](../modeling/customizing-file-storage-and-xml-serialization.md).

-   Klasa SerializationHelper zawiera funkcje, które używają wspólnych klas serializacji.

 `Serializer.cs`

 Klasa serializatora do każdej klasy domeny, relacja kształtu, łącznik, diagram i modelu.

 Wiele funkcji te klasy można sterować za pomocą ustawień w Eksploratorze DSL w obszarze **zachowanie serializacji Xml**.

 `Shapes.cs`

 Klasy dla każdej klasy kształtu w definicji DSL. Pochodne kształtów <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>. Aby uzyskać więcej informacji, zobacz [dostosowywania magazynu plików i serializacja XML](../modeling/customizing-file-storage-and-xml-serialization.md).

 Aby zastąpić metody wygenerowane z metody w klasie częściowej, ustaw **generuje podwójne pochodnych** dla łącznika w definicji DSL. Aby zastąpić konstruktora swoim własnym kodem, ustaw **Konstruktor ma niestandardowy**.

 Aby kolor i niektórych innych zmiennej funkcje stylu w czasie wykonywania, kliknij prawym przyciskiem myszy na diagramie DSL definicji klasy, a następnie wskaż **dodać widoczne**.

 Aby styl dodatkowe funkcje zmienną w czasie wykonywania, zobacz na przykład <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> i <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 `ToolboxHelper.cs`

 Konfiguruje przybornika poprzez zainstalowanie element grupy prototypy do narzędzia elementu. Kopie tych prototypy są scalane z elementów docelowych, jeśli użytkownik uruchamia narzędzie.

 Można zastąpić `CreateElementPrototype()` do definiowania elementu przybornika, który tworzy grupy kilka obiektów. Na przykład można zdefiniować elementu do reprezentowania obiektów, które składniki podrzędne. Po zmianie kod, zresetuj eksperymentalne wystąpienie programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aby wyczyścić pamięć podręczną przybornika.

## <a name="generated-files-in-the-dslpackage-project"></a>Wygenerowane pliki w projekcie DslPackage
 DslPackage couples modelu DSL do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] powłoki zarządzania polecenia Okno przybornika i menu. Większość klas jest podwójne pochodnych, dzięki czemu można przesłonić ich metod.

 `CommandSet.cs`

 Poleceń menu kontekstowego, które są widoczne na diagramie. Można dostosować lub dodać do tego zestawu. Ten plik zawiera kod dla polecenia. Lokalizacja poleceń menu jest określana przez plik Commands.vsct. Aby uzyskać więcej informacji, zobacz [pisma użytkownika poleceń i działań](../modeling/writing-user-commands-and-actions.md).

 `Constants.cs`

 GUIDs.

 `DocData.cs`

 *YourDsl* `DocData` zarządza ładowania i zapisywania modelu do pliku i tworzy wystąpienie magazynu.

 Na przykład, jeśli chcesz zapisać Twoje DSL w bazie danych, nie plikiem, można zastąpić `Load` i `Save` metody.

 `DocView.cs`

 *YourDsl* `DocView` zarządza okna, w której znajduje się diagramu. Na przykład można osadzić diagram wewnątrz formularza systemu windows:

 Dodaj plik kontrolki użytkownika do projektu DslPackage. Dodaj panelu, w którym można wyświetlić diagram. Dodawanie przycisków i innych kontrolek. W widoku kodu formularza Dodaj następujący kod, dopasowanie nazwy użytkownika DSL:

```
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Drawing;
using System.Data;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Shell;

namespace Company.EmbedInForm
{
  public partial class UserControl1 : UserControl
  {
    public UserControl1()
    {
      InitializeComponent();
    }

    private DiagramDocView docView;

    public UserControl1(DiagramDocView docView, Control content)
      : this()
    {
      this.docView = docView;
      panel1.Controls.Add(content);
    }

    private void button1_Click(object sender, EventArgs e)
    {
      ExampleModel modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;
      foreach (ExampleElement element in modelRoot.Elements)
      {
       listBox1.Items.Add(element.Name);
      }
    }
  }
  internal partial class EmbedInFormDocView
  {

    private ContainerControl container;

    /// <summary>
    /// Return a User Control instead of the DSL window.
    /// The user control will contain the DSL window.
    /// </summary>

    public override System.Windows.Forms.IWin32Window Window
    {
      get
      {
        if (container == null)
        {
          // Put the normal DSL Window inside our control
          container = new UserControl1(this, (Control)base.Window);
        }
        return container;
      }
    }
  }

}

```

 `EditorFactory.cs`

 Tworzy wystąpienie `DocData` i `DocView`. Spełnia ona standard interfejsu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] używa, aby otworzyć Edytor po uruchomieniu pakietu DSL. Odwołuje się do niego `ProvideEditorFactory` atrybutu w Package.cs

 `GeneratedVSCT.vsct`

 Lokalizuje standardowych poleceń menu, takich jak menu kontekstowego diagram **Edytuj** menu i tak dalej. Kod dla poleceń jest CommandSet.cs. Można przenosić lub modyfikować poleceń standardowych i mogą dodać własne polecenia. Aby uzyskać więcej informacji, zobacz [pisma użytkownika poleceń i działań](../modeling/writing-user-commands-and-actions.md).

 `ModelExplorer.cs`

 Definiuje Eksploratora modelu dla Twojego DSL. Jest to widok drzewa modelu, który użytkownik zobaczy równolegle z diagramu.

 Na przykład można zastąpić `InsertTreeView()` Aby zmienić kolejność wyświetlania elementów w Eksploratorze modelu.

 Aby zaznaczenie w Eksploratorze modelu, aby zachować zsynchronizowane z opcją diagramu, można użyć poniższego kodu:

```
protected override void OnSelectionChanged(global::System.EventArgs e)
{
base.OnSelectionChanged(e);
// get the selected element
DslModeling::ModelElement selectedElement =
this.PrimarySelection as DslModeling::ModelElement;
// Select in the model explorer
SelectInModelExplorer<YOURLANGUAGEExplorerToolWindow>(selectedElement);
}
private void SelectInModelExplorer<T>(DslModeling::ModelElement modelElement)
where T : DslShell.ModelExplorerToolWindow
{
DslShell::ModelingPackage package =
this.GetService(typeof(VSShell.Package)) as DslShell::ModelingPackage;

if (package != null)
{
// find the model explorer window
T explorerWindow = package.GetToolWindow(typeof(T), true) as T;
if (explorerWindow != null)
{
// get the tree container
DslShell.ModelExplorerTreeContainer treeContainer =
explorerWindow.TreeContainer;
// find the tree node
DslShell.ExplorerTreeNode treeNode =
treeContainer.FindNodeForElement(modelElement);
// select the node
explorerWindow.TreeContainer.ObjectModelBrowser.SelectedNode = treeNode;
}
}
}

```

 `ModelExplorerToolWindow.cs`

 Definiuje okna, w którym jest wyświetlany Eksploratora modelu. Obsługuje wyboru elementów w Eksploratorze.

 `Package.cs`

 Ten plik definiuje sposób integruje DSL [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Atrybuty klasy pakietu zarejestrować DSL jako programu obsługi plików z rozszerzeniem pliku, zdefiniuj jego przybornika oraz definiowanie sposobu Otwórz nowe okno. Jeden raz po pierwszym DSL jest ładowany do wywołania metody Initialize() [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wystąpienia.

 `Source.extension.vsixmanifest`

 Aby dostosować ten plik, Edytuj `.tt` pliku.

> [!WARNING]
>  Po zmodyfikowaniu pliku .TT —, aby uwzględnić zasobów, takich jak ikony lub obrazów, upewnij się, czy zasób jest uwzględniona w kompilacji pliku VSIX. W Eksploratorze rozwiązań wybierz plik, a następnie upewnij się, że **Include w pliku VSIX** jest właściwość `True`.

 Ten plik Określa, jak DSL jest spakowany w Visual Studio integracji rozszerzenia (VSIX). Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązań języka specyficznego dla domeny](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
- [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md)
- [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md)
- [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
