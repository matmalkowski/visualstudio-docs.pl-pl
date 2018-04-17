---
title: Usługa języka i punkty rozszerzenia Edytora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d3c253ba52da1fd6bb9133e44ba6858e8f1a4151
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="language-service-and-editor-extension-points"></a>Usługa języka i punkty rozszerzenia Edytora
Edytor umożliwia punktów rozszerzenia, które można rozszerzyć jako części Managed Extensibility Framework (MEF), w tym większości funkcji usługi języka. Są to kategorie punktu rozszerzenia główne:  
  
-   Typy zawartości  
  
-   Klasyfikacja typy i formaty klasyfikacji  
  
-   Marginesy i paski przewijania  
  
-   Znaczniki  
  
-   Skojarzenia  
  
-   Procesory myszy  
  
-   Programy obsługi upuszczania  
  
-   Opcje  
  
-   IntelliSense  
  
## <a name="extending-content-types"></a>Rozwijanie typów zawartości  
 Typy zawartości są definicje typów tekstu obsługiwane przez edytor, na przykład, "text", "kod" lub "CSharp". Zdefiniuj nowy typ zawartości przez deklarowanie zmiennej typu <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> podając unikatową nazwę nowego typu zawartości. Aby zarejestrować typ zawartości w edytorze, należy go wyeksportować wraz z następującymi atrybutami:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute> jest nazwa typu zawartości.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> jest nazwa typu zawartości, z którego pochodzi ten typ zawartości. Typ zawartości może dziedziczyć po wielu innych typów zawartości.  
  
 Ponieważ <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> klasy jest zapieczętowany, możesz wyeksportować go z ma parametru typu.  
  
 W poniższym przykładzie przedstawiono atrybuty eksportu w definicji typu zawartości.  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 Typy zawartości mogą być oparte na zero lub więcej istniejące typy zawartości. Są to typy wbudowane:  
  
-   Dowolny: podstawowy typ zawartości. Element nadrzędny innych typów zawartości.  
  
-   Tekst: podstawowy typ zawartości z systemem innym niż projekcji. Dziedziczy po "dowolne".  
  
-   W postaci zwykłego tekstu: dla tekstu z systemem innym niż kodu. Dziedziczy po "text".  
  
-   Kod: dla kodu wszelkiego rodzaju. Dziedziczy po "text".  
  
-   Obojętny: tekst umieszczony z jakiejkolwiek obsługi. Tekst tego typu zawartości nigdy nie będą miały dowolnego rozszerzenia zastosować dla niego.  
  
-   Projekcja: dla zawartość buforów projekcji. Dziedziczy po "dowolne".  
  
-   IntelliSense: dla zawartości IntelliSense. Dziedziczy po "text".  
  
-   Sighelp: podpis pomocy. Dziedziczy po "intellisense".  
  
-   Sighelp-doc: podpis dokumentacji pomocy. Dziedziczy po "intellisense".  
  
 Poniżej przedstawiono niektóre typy zawartości, które są zdefiniowane przez program Visual Studio i niektóre języki, które są hostowane w programie Visual Studio:  
  
-   Podstawowy  
  
-   C/C++  
  
-   ConsoleOutput  
  
-   CSharp  
  
-   CSS  
  
-   KODERA  
  
-   FindResults  
  
-   F#  
  
-   HTML  
  
-   JScript  
  
-   XAML  
  
-   XML  
  
 Aby zobaczyć listę dostępnych typów zawartości, należy zaimportować <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, która przechowuje kolekcję typów zawartości edytora. Poniższy kod importuje tej usługi jako właściwość.  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 Aby skojarzyć typu zawartości z rozszerzeniem nazwy pliku, użyj <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>.  
  
> [!NOTE]
>  W programie Visual Studio, rozszerzenia nazw plików są rejestrowane przy użyciu <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> w pakiecie usługi języka. <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> Kojarzy MEF typu zawartości z rozszerzeniem nazwy pliku, który został zarejestrowany w ten sposób.  
  
 Aby wyeksportować dane rozszerzenie nazwy pliku do definicji typu zawartości, należy uwzględnić następujące atrybuty:  
  
-   <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: Określa rozszerzenie nazwy pliku.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: Określa typ zawartości.  
  
 Ponieważ <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> klasy jest zapieczętowany, możesz wyeksportować go z ma parametru typu.  
  
 W poniższym przykładzie przedstawiono atrybuty eksportu na rozszerzenie nazwy pliku do definicji typu zawartości.  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> Zarządza skojarzenia rozszerzeń nazw plików i typy zawartości.  
  
## <a name="extending-classification-types-and-classification-formats"></a>Rozszerzanie typów klasyfikacji i klasyfikacji formatów  
 Aby zdefiniować rodzaje tekstu, dla którego chcesz podać inną obsługi (na przykład kolorowania niebieski tekst "— słowo kluczowe" i "comment" tekst zielony), można użyć typów klasyfikacji. Zdefiniuj nowy typ klasyfikacji przez deklarowanie zmiennej typu <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> i nadanie mu unikatową nazwę.  
  
 Aby zarejestrować typ klasyfikacji w edytorze, należy go wyeksportować wraz z następującymi atrybutami:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Nazwa typu klasyfikacji.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: Nazwa typu klasyfikacji, po którym dziedziczy ten typ klasyfikacji. Wszystkie typy klasyfikacji dziedziczą "text", a typ klasyfikacji może dziedziczyć po wielu innych typów klasyfikacji.  
  
 Ponieważ <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> klasy jest zapieczętowany, możesz wyeksportować go z ma parametru typu.  
  
 W poniższym przykładzie przedstawiono atrybuty eksportu w definicji typu klasyfikacji.  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> Zapewnia dostęp do standardowych klasyfikacji. Klasyfikacja wbudowane typy te:  
  
-   "tekst"  
  
-   "języka naturalnego" (pochodzi od "text")  
  
-   "język formalne" (pochodzi od "text")  
  
-   "string" (pochodzi od "literal")  
  
-   "character" (pochodzi od "literal")  
  
-   "numeryczne" (pochodzi od "literal")  
  
 Zestaw typów inny błąd dziedziczyć <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>. Obejmują one następujące typy błędów:  
  
-   "Błąd składni"  
  
-   "błąd kompilatora"  
  
-   "inny błąd"  
  
-   "ostrzeżenie"  
  
 Aby zobaczyć listę dostępnych typów klasyfikacji, należy zaimportować <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, która przechowuje kolekcję typów klasyfikacji edytora. Poniższy kod importuje tej usługi jako właściwość.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 Definicja formatu klasyfikacji można zdefiniować nowego typu klasyfikacji. Klasa wyprowadzona z <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> i wyeksportować go z typem <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>, wraz z następującymi atrybutami:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: nazwa formatu.  
  
-   <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: Nazwa wyświetlana w formacie.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Określa, czy format jest wyświetlany na **czcionki i kolory** strony **opcje** okno dialogowe.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: priorytet format. Prawidłowe są wartości od <xref:Microsoft.VisualStudio.Text.Classification.Priority>.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: wpisz nazwę klasyfikacji do której ten format jest zamapowany.  
  
 W poniższym przykładzie przedstawiono atrybuty eksportu w definicji formatu klasyfikacji.  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 Aby zobaczyć listę dostępnych formatów, należy zaimportować <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, która przechowuje kolekcję formatów edytora. Poniższy kod importuje tej usługi jako właściwość.  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## <a name="extending-margins-and-scrollbars"></a>Rozszerzanie marginesy i paski przewijania  
 Marginesy i pasków przewijania są elementami Widok główny edytora oprócz samego widoku tekstu. Możesz podać dowolną liczbę marginesy oprócz standardowych marginesy otaczających widoku tekstu.  
  
 Implementowanie <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> interfejs do definiowania margines. Musi implementować też <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interfejs do tworzenia margines.  
  
 Aby zarejestrować dostawcę margines w edytorze, należy wyeksportować dostawcy wraz z następującymi atrybutami:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Nazwa marginesu.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kolejność, w którym jest wyświetlany margines, względem inne marginesy.  
  
     Są to wbudowane marginesy:  
  
    -   "Wpf poziomy pasek przewijania"  
  
    -   "Wpf pionowy pasek przewijania"  
  
    -   "Margines numer wiersza Wpf"  
  
     Marginesy poziomy, które mają atrybut kolejności `After="Wpf Horizontal Scrollbar"` są wyświetlone poniżej margines wbudowanych i poziomy marginesy, które mają atrybut kolejności `Before ="Wpf Horizontal Scrollbar"` są wyświetlane powyżej wbudowanych margines. Kliknij prawym przyciskiem myszy marginesów pionowych, które mają atrybut kolejności `After="Wpf Vertical Scrollbar"` są wyświetlane z prawej strony paska przewijania. LEFT marginesów pionowych, które mają atrybut kolejności `After="Wpf Line Number Margin"` są wyświetlane na lewym marginesie numer wiersza (jeśli jest on widoczny).  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: rodzaj margines (lewo, prawo, top lub bottom).  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "code"), dla którego Twojej marginesu jest prawidłowy.  
  
 W poniższym przykładzie przedstawiono atrybuty eksportu przez dostawcę margines dla margines, który pojawia się po prawej stronie margines numeru wiersza.  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## <a name="extending-tags"></a>Rozszerzenie znaczników  
 Tagi to sposób kojarzenia danych z różnych rodzajów tekstu. W wielu przypadkach skojarzone dane są wyświetlane jako efektem, ale nie wszystkie tagi ma wizualną prezentację. Można zdefiniować własny rodzaj tagu zaimplementowanie <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Musi implementować też <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> zapewnienie tagi dla danego zestawu obejmuje tekst i <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> zapewnienie modułu znakowania. Należy wyeksportować dostawcy modułu znakowania wraz z następującymi atrybutami:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "code"), dla którego oznakowanie jest prawidłowy.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: rodzaj tagu.  
  
 W poniższym przykładzie przedstawiono atrybuty eksportu przez dostawcę modułu znakowania.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 Wbudowane są następujące rodzaje tagu:  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: skojarzony z <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: skojarzony z błędami.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: skojarzony z ozdób.  
  
    > [!NOTE]
    >  Przykład <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, patrz definicja HighlightWordTag w [wskazówki: wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md).  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: skojarzony z regionów, które mogą być rozwinięte lub zwinięte w obramowanie.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: definiuje miejsca zajmuje ozdób w widoku tekstu. Aby uzyskać więcej informacji na temat negocjowania miejsca skojarzenia Zobacz sekcję poniżej.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: zawiera automatyczne odstępy i zmianę rozmiaru dla ozdób.  
  
 Aby odnaleźć i użyć tagów dla buforów i widoków, zaimportuj <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> lub <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, które dają <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> żądanego typu. Poniższy kod importuje tej usługi jako właściwość.  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### <a name="tags-and-markerformatdefinitions"></a>Znaczniki i MarkerFormatDefinitions  
 Można rozszerzyć <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> klasy do określenia jej wyglądu znacznika. Należy wyeksportować klasie (jako <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>) z następującymi atrybutami:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Nazwa używana do utworzenia odwołania tego formatu  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: powoduje formatu, które mają być widoczne w Interfejsie użytkownika  
  
 W Konstruktorze można zdefiniować nazwę wyświetlaną i wyglądu znacznika. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> Określa kolor wypełnienia i <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> Określa kolor obramowania. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> Jest nazwą Lokalizowalny Definicja formatu.  
  
 Oto przykład definicji formatu:  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
[UserVisible(true)]  
internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
{  
    public HighlightWordFormatDefinition()  
    {  
        this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";   
        this.ZOrder = 5;  
    }  
}  
  
```  
  
 Aby zastosować to Definicja formatu tag, odwoływać się do nazwy, ustawione w atrybucie nazwy klasy (nie nazwę wyświetlaną).  
  
> [!NOTE]
>  Przykład <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, zobacz klasę HighlightWordFormatDefinition w [wskazówki: wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md).  
  
## <a name="extending-adornments"></a>Rozszerzenie skojarzenia  
 Skojarzenia zdefiniuj efektów wizualnych, które można dodać do tekst, który jest wyświetlany w widoku tekstu lub w tekście wyświetlić sam. Możesz zdefiniować własny ozdób dowolnego typu <xref:System.Windows.UIElement>.  
  
 W klasie ozdób należy zadeklarować <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>. Aby zarejestrować warstwą ozdób, należy go wyeksportować wraz z następującymi atrybutami:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Nazwa ozdób.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: porządkowanie ozdób względem innych warstw ozdób. Klasa <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> definiuje cztery warstwy domyślne: wybór, tworzenie konspektu karetki i tekst.  
  
 W poniższym przykładzie przedstawiono atrybuty eksportu w definicji warstwy ozdób.  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 Należy utworzyć drugiej klasy, która implementuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> i obsługi jej <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> zdarzeń przy uruchamianiu ozdób. Należy wyeksportować tej klasy wraz z następującymi atrybutami:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "code"), dla którego ozdób jest prawidłowy.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: rodzaj widoku tekstu, dla którego ten ozdób jest prawidłowy. Klasa <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> ma ustawioną tekstu wstępnie zdefiniowanego widoku ról. Na przykład <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> jest używany głównie dla tekstu widoki plików. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> Służy do widoków tekstu, czy użytkownik może edytować lub przejść za pomocą myszy i klawiatury. Przykłady <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> widoki są widoku edytora tekstu i **dane wyjściowe** okna.  
  
 W poniższym przykładzie przedstawiono atrybuty eksportu dla dostawcy ozdób.  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 Ozdób negocjowania miejsca to taki, który zajmuje miejsca na tym samym poziomie jako tekst. Aby utworzyć tego rodzaju ozdób, należy zdefiniować klasy tag, który dziedziczy z <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, która określa ilość miejsca zajmuje ozdób.  
  
 Podobnie jak w przypadku wszystkich skojarzenia, należy wyeksportować definicji warstwy ozdób.  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 Można utworzyć wystąpienia ozdób negocjowania miejsca, należy utworzyć klasę implementującą <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, oprócz klasy, która implementuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (tak jak inne rodzaje skojarzenia).  
  
 Aby zarejestrować dostawcę modułu znakowania, należy go wyeksportować wraz z następującymi atrybutami:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "code"), dla którego ozdób użytkownika jest prawidłowy.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: rodzaj widoku tekstu, dla których ten tag lub ozdób są prawidłowe. Klasa <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> ma ustawioną tekstu wstępnie zdefiniowanego widoku ról. Na przykład <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> jest używany głównie dla tekstu widoki plików. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> Służy do widoków tekstu, czy użytkownik może edytować lub przejść za pomocą myszy i klawiatury. Przykłady <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> widoki są widoku edytora tekstu i **dane wyjściowe** okna.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: rodzaj tagu lub ozdób zdefiniowanej przez użytkownika. Należy dodać drugi <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> dla <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>.  
  
 W poniższym przykładzie przedstawiono atrybuty eksportu dla dostawcy modułu znakowania tagu ozdób negocjowania miejsca.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## <a name="extending-mouse-processors"></a>Rozszerzanie procesorów myszy  
 Możesz dodać specjalnej obsługi dla myszą. Utwórz klasę, która dziedziczy po klasie <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> i Zastąp zdarzenia myszy na dane mają być obsługiwane. Musi implementować też <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> w drugiej klasy i wyeksportować go razem z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> , który określa rodzaj zawartości (na przykład "text" lub "code"), dla którego programu obsługi myszy jest prawidłowy.  
  
 W poniższym przykładzie przedstawiono atrybuty eksportu przez dostawcę procesora myszy.  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## <a name="extending-drop-handlers"></a>Rozszerzanie listy programów obsługi  
 Można dostosować zachowanie programów obsługi upuszczania dla określonych rodzajów tekstu, tworząc klasę, która implementuje <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> i drugiej klasy, która implementuje <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> do utworzenia programu obsługi upuszczania. Należy wyeksportować obsługi upuszczania wraz z następującymi atrybutami:  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: format tekstu, dla którego ten program obsługi upuszczania jest prawidłowa. Następujące formaty są obsługiwane w kolejności priorytetu z najwyższym do najniższego:  
  
    1.  Wszelkie formatu niestandardowego  
  
    2.  FileDrop  
  
    3.  EnhancedMetafile  
  
    4.  WaveAudio  
  
    5.  RIFF  
  
    6.  DIF  
  
    7.  Regionalne  
  
    8.  Palety  
  
    9. PenData  
  
    10. Możliwy do serializacji  
  
    11. SymbolicLink  
  
    12. XAML  
  
    13. XamlPackage  
  
    14. TIFF  
  
    15. Mapy bitowej  
  
    16. Dib  
  
    17. MetafilePicture  
  
    18. CSV  
  
    19. System.String  
  
    20. HTML Format  
  
    21. UnicodeText  
  
    22. OEMText  
  
    23. Tekst  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Nazwa obsługi upuszczania.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: porządkowanie obsługi upuszczania przed lub po listy domyślny program obsługi. Upuść domyślny program obsługi dla programu Visual Studio ma nazwę "DefaultFileDropHandler".  
  
 W poniższym przykładzie przedstawiono atrybuty eksportu przez dostawcę obsługi upuszczania.  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## <a name="extending-editor-options"></a>Rozszerzanie Opcje edytora  
 Można zdefiniować opcje, aby identyfikator był prawidłowy tylko w niektórych zakresu, na przykład w widoku tekstu. Edytor umożliwia ten zestaw wstępnie zdefiniowanych opcji: Opcje edytora, opcje wyświetlania i opcje wyświetlania Windows Presentation Foundation (WPF). Te opcje można znaleźć w <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>, i <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>.  
  
 Aby dodać nową opcję, wyprowadzenia klasy z jednej z tych opcji definicji klas:  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
 Poniższy przykład przedstawia sposób eksportowania definicji opcji, która ma wartość logiczną.  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## <a name="extending-intellisense"></a>Rozszerzenie IntelliSense  
 IntelliSense jest ogólny termin grupy funkcje, które zawierają informacje o strukturze tekstu i uzupełniania instrukcji dla niego. Te funkcje obejmują uzupełniania instrukcji, pomocy podpisu szybkie informacje i żarówki. Uzupełnianie ułatwia użytkownikom poprawnie wpisz nazwę elementu członkowskiego lub słowo kluczowe języka. Podpis pomocy Wyświetla podpisu lub sygnatury dla metody, które użytkownik ma wpisane. Szybkie informacje wyświetla podpis pełną nazwę typu lub elementu członkowskiego, gdy wskaźnik myszy opiera się na nim. Żarówki zapewniają dodatkowe akcje dla niektórych identyfikatorów w niektórych kontekstach, na przykład zmiana nazwy wszystkie wystąpienia zmiennej po zmianie nazwy wystąpienia.  
  
 Projekt funkcji IntelliSense jest znacznie sama we wszystkich przypadkach:  
  
-   IntelliSense *brokera* jest odpowiedzialny za cały proces.  
  
-   IntelliSense *sesji* reprezentuje sekwencję zdarzeń między wyzwolenie prezenterze i committal lub anulowanie zaznaczenia. Sesja jest zwykle wyzwalane przez niektóre gestu użytkownika.  
  
-   IntelliSense *kontrolera* jest odpowiedzialny za decyzje czas rozpoczęcia i zakończenia sesji. Decyduje również gdy informacje powinny być zatwierdzone i podczas sesji powinien zostać anulowany.  
  
-   IntelliSense *źródła* udostępnia zawartość i decyduje o najlepsze dopasowanie.  
  
-   IntelliSense *prezenterze* odpowiada za wyświetlanie zawartości.  
  
 W większości przypadków zaleca się podanie co najmniej źródłem a kontrolerem. Można też podać prezenterze, jeśli chcesz dostosować wyświetlanie.  
  
### <a name="implementing-an-intellisense-source"></a>Implementowanie źródłowego IntelliSense  
 Aby dostosować źródła, należy zaimplementować jeden (lub więcej) z następujących interfejsów źródła:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> przestarzała uzyskać <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
 Ponadto należy zaimplementować dostawcę tego samego typu:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> przestarzała uzyskać <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.  
  
 Należy wyeksportować dostawcy wraz z następującymi atrybutami:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Nazwa źródła.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "code"), którego dotyczy źródła.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kolejność źródła powinna wyświetlania (w odniesieniu do innych źródeł).  
  
-   W poniższym przykładzie przedstawiono atrybuty eksportu przez dostawcę źródła ukończenia.  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 Aby uzyskać więcej informacji o implementacji źródeł IntelliSense zobacz następujące wskazówki:  
  
 [Przewodnik: wyświetlanie etykietek narzędzi SzybkieInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Przewodnik: wyświetlanie pomocy dotyczącej sygnatur](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Przewodnik: wyświetlanie uzupełniania instrukcji](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### <a name="implementing-an-intellisense-controller"></a>Wdrażanie kontrolera IntelliSense  
 Aby dostosować kontrolera, należy zaimplementować <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> interfejsu. Ponadto należy zaimplementować dostawcę kontrolera wraz z następującymi atrybutami:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Nazwa kontrolera.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: rodzaj zawartości (na przykład "text" lub "code"), którego dotyczy kontrolera.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kolejność kontroler powinien wyświetlania (w odniesieniu do innych kontrolerów).  
  
 W poniższym przykładzie przedstawiono atrybuty eksportu przez dostawcę kontrolera ukończenia.  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 Aby uzyskać więcej informacji o korzystaniu z funkcji IntelliSense kontrolerów zobacz następujące wskazówki:  
  
 [Przewodnik: wyświetlanie etykietek narzędzi SzybkieInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)