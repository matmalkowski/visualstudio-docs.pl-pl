---
title: Wprowadzenie do WPF
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- csharp
- vb
ms.workload:
- multiple
ms.openlocfilehash: 96855f9050eda640b0f5dc9c44dbc67a3ec6b328
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="introduction-to-wpf"></a>Wprowadzenie do WPF

Windows Presentation Foundation (WPF) umożliwia tworzenie klienta stacjonarnego aplikacji dla systemu Windows z wizualnie ogłuszania wrażenia użytkowników.

 ![Przykładowy interfejs użytkownika opieki zdrowotnej firmy Contoso](../designers/media/wpfintrofigure24.png)

 Podstawowe WPF jest aparat renderowania niezależne od rozdzielczości i wektorowej, który korzysta z wbudowanej wykorzystać grafiki nowoczesnych urządzeń. WPF rozszerza podstawową z użyciem kompleksowego zestawu funkcji tworzenia aplikacji, które obejmują Extensible Application Markup Language (XAML), kontrolek, powiązanie danych, układu, grafiki 2W i 3W, animacji, style, szablony, dokumentów, nośnika, tekst, a typografii. WPF znajduje się w programie .NET Framework, można tworzyć aplikacje, które inne elementy bibliotece klas programu .NET Framework.

 To omówienie jest przeznaczony dla nowych osób i opisano najważniejsze funkcje i koncepcje WPF.

## <a name="program-with-wpf"></a>Program z użyciem WPF

WPF istnieje jako podzbiór typów .NET Framework, które w większości przypadków znajdują się w <xref:System.Windows> przestrzeni nazw. Jeśli aplikacje zostały wcześniejsza kompilacja platformy .NET Framework za pomocą technologii zarządzanych, takich jak ASP.NET i formularze systemu Windows, WPF podstawowych, środowisko programowania w języku, należy się zapoznać; Możesz utworzyć wystąpienia klasy, ustaw właściwości, metody wywołania i uchwyt zdarzenia, wszystkie przy użyciu programu .NET ulubiony język programowania, na przykład C# lub Visual Basic.

WPF obejmuje dodatkowych narzędzi programistycznych, które podnoszą właściwości i zdarzenia: [właściwości zależności](/dotnet/framework/wpf/advanced/dependency-properties-overview) i [zdarzenia rozsyłane](/dotnet/framework/wpf/advanced/routed-events-overview).

## <a name="markup-and-code-behind"></a>Znaczniki i związane z kodem

WPF umożliwia tworzenie aplikacji przy użyciu zarówno *znacznika* i *CodeBehind*, środowisko, które deweloperów platformy ASP.NET, należy się zapoznać z. Ogólnie rzecz biorąc przy użyciu znaczników XAML wyglądu aplikacji podczas używania zarządzanego języków programowania (code-behind) do zaimplementowania jego zachowania. To oddzielenie wygląd i zachowanie ma następujące zalety:

- Projektowanie i utrzymanie koszty są obniżona, ponieważ specyficzne dla wyglądu znacznika nie jest ściśle powiązane ze zachowanie unikatowy kod.

- Programowanie jest bardziej wydajne, ponieważ projektantów można zaimplementować wygląd aplikacji jednocześnie deweloperom, którzy wdrażania zachowania aplikacji.

- [Lokalizacja i globalizacja](/dotnet/framework/wpf/advanced/wpf-globalization-and-localization-overview) dla WPF została uproszczona w aplikacji.

### <a name="markup"></a>Kod znaczników

XAML jest oparte na języku XML język używany do wdrożenia aplikacji wygląd deklaratywnie. Zwykle służy do tworzenia systemu windows, okna dialogowe, stron i kontrolek użytkownika i wypełnić je z formantami, kształtów i grafiki.

 W poniższym przykładzie użyto XAML, aby zaimplementować wygląd okna, który zawiera jeden przycisk.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

 W szczególności ten XAML definiuje okna i przycisk przy użyciu `Window` i `Button` elementów, odpowiednio. Każdy element jest skonfigurowany z atrybutów, takich jak `Window` elementu `Title` atrybutu na określanie tekstu pasek tytułu okna. W czasie wykonywania WPF konwertuje elementów i atrybutów, które są zdefiniowane w znaczniku można instancji klasy WPF. Na przykład `Window` element jest konwertowana na wystąpienie <xref:System.Windows.Window> klasy, których <xref:System.Windows.Window.Title%2A> właściwość ma wartość `Title` atrybutu.

 Na poniższej ilustracji przedstawiono interfejs użytkownika (UI), który jest zdefiniowany w języku XAML w poprzednim przykładzie.

 ![Okno zawierające przycisk](../designers/media/wpfintrofigure10.png "WPFIntroFigure10")

 Ponieważ XAML jest oparte na języku XML, budowy interfejsu użytkownika, które tworzą z nią w hierarchii elementów zagnieżdżonych znany jako [element drzewa](/dotnet/framework/wpf/advanced/trees-in-wpf). Element drzewa zapewnia logiczne i intuicyjne sposób tworzenia i zarządzania nimi UI.

### <a name="code-behind"></a>Związane z kodem

Główne zachowanie aplikacji jest zaimplementowanie funkcji, które odpowiada interakcji użytkownika, w tym obsługa zdarzeń (na przykład, klikając pozycję menu, paska narzędzi lub przycisku) i wywoływania logika biznesowa i logika dostępu do danych w odpowiedzi. Na platformie WPF to zachowanie jest zaimplementowana w kodzie, który jest skojarzony z kodu znaczników. Ten typ kodu jest nazywany związane z kodem. W poniższym przykładzie przedstawiono zaktualizowane znaczników z poprzedniego przykładu i CodeBehind.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.AWindow"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button" Click="button_Click">Click Me!</Button>

</Window>
```

```csharp
using System.Windows; // Window, RoutedEventArgs, MessageBox 

namespace SDKSample
{
    public partial class AWindow : Window
    {
        public AWindow()
        {
            // InitializeComponent call is required to merge the UI 
            // that is defined in markup with this class, including  
            // setting properties and registering event handlers
            InitializeComponent();
        }

        void button_Click(object sender, RoutedEventArgs e)
        {
            // Show message box when button is clicked
            MessageBox.Show("Hello, Windows Presentation Foundation!");
        }
    }
}
```

```vb
Namespace SDKSample

    Partial Public Class AWindow
        Inherits System.Windows.Window

        Public Sub New()

            ' InitializeComponent call is required to merge the UI 
            ' that is defined in markup with this class, including  
            ' setting properties and registering event handlers
            InitializeComponent()

        End Sub 

        Private Sub button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)

            ' Show message box when button is clicked
            MessageBox.Show("Hello, Windows Presentation Foundation!")

        End Sub 

    End Class 

End Namespace
```

W tym przykładzie kodu powiązanego implementuje klasy, która jest pochodną <xref:System.Windows.Window> klasy. `x:Class` Atrybut służy do skojarzenia z klasą związane z kodem znaczników. `InitializeComponent` jest wywoływana z konstruktora klasy kodu powiązanego do scalenia interfejsu użytkownika, który jest zdefiniowany w znaczniku przy użyciu klasy związane z kodem. (`InitializeComponent` jest generowany automatycznie podczas tworzenia aplikacji, dlatego nie trzeba ręcznie zaimplementować.) Kombinacja `x:Class` i `InitializeComponent` upewnij się, że wdrożenie jest poprawnie zainicjować zawsze, gdy jest tworzona. Klasy związane z kodem zawiera implementację programu obsługi zdarzeń dla przycisku <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń. Po kliknięciu przycisku program obsługi zdarzeń pokazuje okno komunikatu przez wywołanie metody <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> metody.

Na poniższej ilustracji przedstawiono wyniku, gdy przycisk zostanie kliknięty.

![Element MessageBox](../designers/media/wpfintrofigure25.png)

## <a name="controls"></a>Formanty

Środowiska użytkownika, które są dostarczane przez model aplikacji są skonstruowane formanty. Na platformie WPF "control" jest ogólny termin, która ma zastosowanie do kategorii WPF klas, które znajdują się w oknie lub strony sieci, interfejs użytkownika i zaimplementować niektórych zachowanie.

Aby uzyskać więcej informacji, zobacz [formanty](/dotnet/framework/wpf/controls/index).

### <a name="wpf-controls-by-function"></a>Formanty WPF według kategorii

Poniżej przedstawiono wbudowane formantów WPF.

- **Przyciski**: <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.Primitives.RepeatButton>.

- **Wyświetlanie danych**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>, i <xref:System.Windows.Controls.TreeView>.

- **Data wyświetlania i wybór**: <xref:System.Windows.Controls.Calendar> i <xref:System.Windows.Controls.DatePicker>.

- **Okna dialogowe**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>, i <xref:Microsoft.Win32.SaveFileDialog>.

- **Elektroniczne pismo odręczne**: <xref:System.Windows.Controls.InkCanvas> i <xref:System.Windows.Controls.InkPresenter>.

- **Dokumenty**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, i <xref:System.Windows.Controls.StickyNoteControl>.

- **Dane wejściowe**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, i <xref:System.Windows.Controls.PasswordBox>.

- **Układ**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>, i <xref:System.Windows.Controls.WrapPanel>.

- **Nośnik**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>, i <xref:System.Windows.Controls.SoundPlayerAction>.

- **Menu**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>, i <xref:System.Windows.Controls.ToolBar>.

- **Nawigacji**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, i <xref:System.Windows.Controls.TabControl>.

- **Wybór**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, i <xref:System.Windows.Controls.Slider>.

- **Informacje o użytkowniku**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>, i <xref:System.Windows.Controls.ToolTip>.

## <a name="input-and-commands"></a>Dane wejściowe i poleceń

Formanty najczęściej wykrywania i odpowiadać na dane wejściowe użytkownika. [System wprowadzania WPF](/dotnet/framework/wpf/advanced/input-overview) używa zdarzenia zarówno bezpośrednio, jak i kierowanego do obsługi wprowadzania tekstu, funkcje zarządzania i położenie myszy.

Aplikacje mają często złożonych wymagania wprowadzania. Udostępnia WPF [polecenia systemu](/dotnet/framework/wpf/advanced/commanding-overview) oddzielający akcje wejściowych użytkownika z kodu, które odpowiada te akcje.

## <a name="layout"></a>Układ

Podczas tworzenia interfejsu użytkownika rozmieszczania formanty według lokalizacji i rozmiaru do utworzenia układu. Decydujące znaczenie żadnych układu jest dostosowania do zmiany rozmiaru okna i ustawienia wyświetlania. Zamiast wymuszania można napisać kod do dostosowania układu w takiej sytuacji, WPF zapewnia system najwyższej jakości, rozszerzalne układu dla Ciebie.

Podstawy systemu układ jest względne położenie, co zwiększa możliwość dostosowanie do zmieniających się okna i warunki wyświetlania. Ponadto system układu zarządza negocjacji między formantami do określania układu. Negocjowanie jest procesem dwuetapowym: najpierw formantu informuje jego elementu nadrzędnego, jakie lokalizacja i rozmiar wymaga; Po drugie nadrzędny informuje formantu miejsca, jakie może mieć.

Układ systemu jest widoczne dla formantów podrzędnych za pomocą klas podstawowych WPF. W przypadku typowych układów, takich jak siatki, zestawianie i dokowanie WPF zawiera kilka formantów układu:

- <xref:System.Windows.Controls.Canvas>: Formanty podrzędne Podaj własne układu.

- <xref:System.Windows.Controls.DockPanel>: Formanty podrzędne są wyrównane do krawędzi panelu.

- <xref:System.Windows.Controls.Grid>: Formanty podrzędne będą umieszczane według wierszy i kolumn.

- <xref:System.Windows.Controls.StackPanel>: Formanty podrzędne są ułożone w pionie lub poziomie.

- <xref:System.Windows.Controls.VirtualizingStackPanel>: Formanty podrzędne jest Zwirtualizowana i nie ułożone w pojedynczej linii o orientacji poziomej lub pionowej.

- <xref:System.Windows.Controls.WrapPanel>: Formanty podrzędne są rozmieszczone w kolejności od lewej do prawej i zawijany do następnego wiersza, gdy istnieją formanty więcej w bieżącym wierszu, niż pozwala miejsca.

W poniższym przykładzie użyto <xref:System.Windows.Controls.DockPanel> do określania układu kilka <xref:System.Windows.Controls.TextBox> kontrolki.

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_1.xaml)]

<xref:System.Windows.Controls.DockPanel> Umożliwia podrzędne <xref:System.Windows.Controls.TextBox> formantów zostanie wstrzymana do rozmieszczenia. Aby to zrobić, <xref:System.Windows.Controls.DockPanel> implementuje `Dock` dołączona właściwość, która jest widoczna do formantów podrzędnych, aby umożliwić każdej z nich, aby określić styl dokowania.

> [!NOTE]
> Właściwość, która jest zaimplementowana przez formant nadrzędny konstrukcję WPF jest używany przez formanty podrzędne o nazwie [dołączona właściwość](/dotnet/framework/wpf/advanced/attached-properties-overview).

Na poniższej ilustracji przedstawiono wynik znaczników XAML w poprzednim przykładzie.

![Strona DockPanel](../designers/media/wpfintrofigure11.png)

## <a name="data-binding"></a>Powiązanie danych

Większość aplikacji są tworzone może udostępnić użytkownikowi środki do wyświetlania i edytowania danych. W przypadku aplikacji WPF pracy przechowywania i uzyskiwania dostępu do danych jest już udostępniane na potrzeby technologii, takich jak SQL Server oraz obiektów ADO .NET. Po jest dostęp do danych i ładowane do aplikacji zarządzanych obiektów, rozpocznie się praca aplikacji WPF. Obejmuje to zasadniczo dwie czynności:

1.  Kopiowanie danych z zarządzanych obiektów w formantach, gdzie można wyświetlić i edytować danych.

2.  Zapewnienie, że zmiany wprowadzone w danych za pomocą formantów są kopiowane do obiektów zarządzanych.

Aby ułatwić projektowanie aplikacji, WPF zawiera aparat wiązania danych, aby automatycznie wykonać te czynności. Jednostka core aparat wiązania danych jest <xref:System.Windows.Data.Binding> klasy, którego zadaniem jest powiązanie formantu (cel wiązania) na obiekt danych (źródło powiązania). Ta relacja jest zilustrowane poniższej ilustracji:

![Diagram podstawowego powiązania danych](../designers/media/databindingmostbasic.png)

Kolejnym przykładzie pokazano, jak można powiązać <xref:System.Windows.Controls.TextBox> do wystąpienia niestandardowego `Person` obiektu. `Person` Implementacji przedstawiono w poniższym kodzie:

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](../designers/codesnippet/VisualBasic/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](../designers/codesnippet/CSharp/introduction-to-wpf_2.cs)]

Następujący kod znaczników wiąże <xref:System.Windows.Controls.TextBox> do wystąpienia niestandardowego `Person` obiektu.

 ```xaml
 <Window
     xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
     xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
     x:Class="SDKSample.DataBindingWindow">

   <!-- Bind the TextBox to the data source (TextBox.Text to Person.Name) -->
   <TextBox Name="personNameTextBox" Text="{Binding Path=Name}" />

 </Window>
 ```

[!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_6.vb)]
[!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_6.cs)]

W tym przykładzie `Person` klasa zostanie uruchomiony w CodeBehind i jest ustawiony jako kontekst danych `DataBindingWindow`. W znaczniku <xref:System.Windows.Controls.TextBox.Text%2A> właściwość <xref:System.Windows.Controls.TextBox> jest powiązany z `Person.Name` właściwości (przy użyciu "`{Binding ... }`" składni języka XAML). Ten XAML informuje WPF powiązać <xref:System.Windows.Controls.TextBox> formant `Person` obiekt, który jest przechowywany w <xref:System.Windows.FrameworkElement.DataContext%2A> właściwość okna.

Aparat powiązanie danych WPF zapewnia dodatkową pomoc, który obejmuje weryfikację, sortowanie, filtrowanie i grupowanie. Ponadto powiązań danych obsługuje korzystanie z szablonów danych można utworzyć niestandardowego interfejsu użytkownika dla powiązania danych, gdy interfejs użytkownika, wyświetlane przez standardowych formantów WPF nie jest odpowiedni.

Aby uzyskać więcej informacji, zobacz [omówienie powiązania danych](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="graphics"></a>Grafika

WPF wprowadza szeroką gamę, skalowalnych i elastycznych zestaw funkcji grafiki, które mają następujące korzyści:

- **Niezależne od rozdzielczości i urządzenia grafiki**. Podstawowa jednostka miary w systemie WPF grafikę jest piksela niezależnych od urządzenia ma wartość 1/96 cala, niezależnie od rzeczywistej rozdzielczość ekranu i stanowi podstawę do renderowania niezależne od rozdzielczości i urządzenia. Każdego piksela niezależnych od urządzenia jest automatycznie skalowany zgodne z ustawieniem punktów na cal (dpi) używanego systemu renderowania na.

- **Ulepszone dokładności**. System współrzędnych WPF jest mierzony z liczby zmiennoprzecinkowe podwójnej precyzji zamiast pojedynczej precyzji. Przekształcenia i wartości nieprzezroczystość również są wyrażane jako podwójnej precyzji. WPF również obsługuje gama kolor dwubajtowe (scRGB) i zapewnia obsługę zintegrowane zarządzanie danych wejściowych z różnych przestrzeni kolorów.

- **Zaawansowana obsługa grafiki i animacji**. WPF upraszcza programowanie grafiki, zarządzając sceny animacji dla Ciebie; nie istnieje potrzeba martwić się o przetwarzania sceny, pętle renderowania i Dwuliniowa interpolacji. Ponadto WPF zapewnia testowanie trafień oraz alfa składania pomocy technicznej.

- **Przyspieszanie sprzętowe**. System WPF grafikę wykorzystuje grafiki sprzętu w celu zminimalizowania użycia procesora CPU.

### <a name="2d-shapes"></a>2D kształtów

WPF zawiera bibliotekę typowych rysowane wektor 2D kształtów, takich jak prostokąty i wielokropek, które są wyświetlane na poniższej ilustracji:

![Elipsy i prostokąty](../designers/media/wpfintrofigure4.PNG)

Interesujące możliwość kształtów jest, że nie są one tylko do wyświetlania; kształty implementuje wiele funkcji, których można się spodziewać po formantów, w tym klawiatury i myszy. W poniższym przykładzie przedstawiono <xref:System.Windows.UIElement.MouseUp> zdarzenie <xref:System.Windows.Shapes.Ellipse> obsługiwane.

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_8.cs)]

Na poniższej ilustracji przedstawiono, co jest generowany przez poprzedni kod.

![Okno z tekstem "kliknięto przycisk wielokropka&#33;"](../designers/media/wpfintrofigure12.png)

Aby uzyskać więcej informacji, zobacz [kształtów i podstawowe rysunek w omówieniu WPF](/dotnet/framework/wpf/data/data-binding-overview).

### <a name="2d-geometries"></a>2D mają geometrię

Kształty 2D podał WPF obejmują standardowy zestaw kształty podstawowe. Jednak należy utworzyć kształty niestandardowe, aby ułatwić projektowanie interfejsu użytkownika. W tym celu WPF zawiera mają geometrię. Na poniższym rysunku pokazano użycie geometrii, tworząc niestandardowe kształtu, który może być narysowana bezpośrednio, używane jako Pędzel lub używana należy przyciąć innych kształtów i formantów.

<xref:System.Windows.Shapes.Path> obiekty może służyć do rysowania kształty zamknięte lub otwarte, wielu kształtów i nawet zakrzywioną kształtów.

<xref:System.Windows.Media.Geometry> obiekty można wycinka, testowanie trafień i 2D danych graficzne renderowania.

![Różnych zastosowań ścieżki](../designers/media/wpfintrofigure5.PNG "WPFIntroFigure5")

Aby uzyskać więcej informacji, zobacz [omówienie geometrii](/dotnet/framework/wpf/graphics-multimedia/geometry-overview).

### <a name="2d-effects"></a>Efekty 2D

Podzestaw możliwości 2D WPF zawiera efekty wizualne, takie jak gradienty, mapy bitowe, rysunki malowanie wideo, obracanie, skalowanie i pochylanie. Te są wszystkie osiągnięty przy pędzle; na poniższej ilustracji przedstawiono kilka przykładów.

![Ilustracja różnych pędzli](../designers/media/wpfintrofigure6.PNG "WPFIntroFigure6")

Aby uzyskać więcej informacji, zobacz [omówienie pędzle WPF](/dotnet/framework/wpf/graphics-multimedia/wpf-brushes-overview).

### <a name="3d-rendering"></a>Renderowania 3W

WPF zawiera również funkcje renderowania 3W, które zintegrować z grafiki 2-d, aby umożliwić tworzenie atrakcyjnych i bardziej interesującego interfejsów użytkownika. Na przykład na poniższej ilustracji przedstawiono obrazów 2D renderowane kształtów 3D.

![Zrzut ekranu przedstawiający przykładowy Visual3D](../designers/media/wpfintrofigure13.png "WPFIntroFigure13")

Aby uzyskać więcej informacji, zobacz [Przegląd grafiki 3D](/dotnet/framework/wpf/graphics-multimedia/3-d-graphics-overview).

## <a name="animation"></a>Animacja

Umożliwia obsługę animacji WPF, wprowadzone kontrolki powiększania, potrząsanie, pokrętła i zanikania, aby utworzyć interesujące strony przejścia i inne. Można animować większość klas WPF, nawet klas niestandardowych. Na poniższej ilustracji przedstawiono prosty animacji w akcji.

![Obrazy modułu animowany](../designers/media/wpfintrofigure7.png "WPFIntroFigure7")

Aby uzyskać więcej informacji, zobacz [omówienie animacja](/dotnet/framework/wpf/graphics-multimedia/animation-overview).

## <a name="media"></a>Nośnik

Jest jednym ze sposobów przekazywać zawartość sformatowanego przy użyciu nośnika audiowizualnych. WPF obsługuje specjalnych obrazów, wideo i audio.

### <a name="images"></a>Obrazy

Obrazy są wspólne dla większości aplikacji i WPF udostępnia kilka sposobów korzystania z nich. Na poniższej ilustracji przedstawiono interfejs użytkownika z pola listy, który zawiera obrazy miniatur. Po wybraniu miniaturę obrazu jest wyświetlany w pełnym rozmiarze.

![Obrazy miniatur i pełne&#45;rozmiar obrazu](../designers/media/wpfintrofigure8.PNG "WPFIntroFigure8")

Aby uzyskać więcej informacji, zobacz [Imaging omówienie](/dotnet/framework/wpf/graphics-multimedia/imaging-overview).

### <a name="video-and-audio"></a>Audio i wideo

<xref:System.Windows.Controls.MediaElement> Formantu ma możliwość odtwarzania audio i wideo i jest wystarczająco elastyczny, aby stanowić podstawę do odtwarzacza multimedialnego niestandardowych. Następujący kod XAML implementuje odtwarzacza multimedialnego.

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_9.xaml)]

Okna na poniższy rysunek przedstawia <xref:System.Windows.Controls.MediaElement> kontroli w akcji.

![Formant MediaElement z obsługą audio i wideo](../designers/media/wpfintrofigure1.png "WPFIntroFigure1")

Aby uzyskać więcej informacji, zobacz [grafiki i Multimedia](/dotnet/framework/wpf/graphics-multimedia).

## <a name="text-and-typography"></a>Tekst i typografii

W celu ułatwienia renderowanie tekstu wysokiej jakości, WPF oferuje następujące funkcje:

- Obsługa czcionek OpenType.

- Ulepszenia ClearType.

- Wysoka wydajność, wykorzystującego przyspieszanie sprzętowe.

- Integracja tekstu z nośnika, grafiki i animacji.

- Międzynarodowe czcionki mechanizmów obsługi i powrotu.

Jako pokaz tekst integracji z grafiki na poniższej ilustracji przedstawiono stosowanie dekoracji tekstu.

![Tekst z różnych dekoracji tekstu](../designers/media/wpfintrofigure23.png)

Aby uzyskać więcej informacji, zobacz [typografii w systemie Windows Presentation Foundation](/dotnet/framework/wpf/advanced/typography-in-wpf).

## <a name="customize-wpf-apps"></a>Dostosowywanie aplikacji WPF

Do tego momentu przedstawiono podstawowe bloki konstrukcyjne WPF do tworzenia aplikacji. Model aplikacji umożliwia hostowanie i dostarczania zawartości aplikacji, która składa się głównie z formantów. Aby uprościć rozmieszczenie kontrolek w interfejsie użytkownika i aby upewnij się, że rozmieszczenia jest obsługiwany w wypadku zmiany rozmiaru okna i wyświetlić ustawienia, należy użyć systemu układu WPF. Ponieważ większość aplikacji zezwala użytkownikom na interakcję z danymi, umożliwia powiązanie danych Zmniejsz ilość pracy integracji interfejsu użytkownika z danymi. Aby poprawić wygląd aplikacji, należy użyć kompleksowego zakresu Obsługa grafiki, animacji i multimediów w WPF.

Często jednak podstawy nie są wystarczająco do tworzenia i zarządzania nimi naprawdę różne wizualne ogłuszania środowisko użytkownika. Standardowych formantów WPF nie może zintegrować z wygląd żądanej aplikacji. Dane mogą być niewidoczne w najbardziej efektywny sposób. Środowisko użytkownika ogólną aplikacji może nie być odpowiednie do domyślnego wyglądu i działania kompozycji systemu Windows. Na wiele sposobów technologii prezentacji musi rozszerzalności programu visual jak każdy inny rodzaj rozszerzalności.

Z tego powodu WPF zapewnia różne mechanizmy do tworzenia środowiska unikatowych użytkowników, tym sformatowanego modelu zawartości dla formantów, wyzwalaczy, sterowania i szablony danych, style, zasoby interfejsu użytkownika i kompozycje i karnacji.

### <a name="content-model"></a>Model zawartości

Głównym celem większości formantów WPF jest do wyświetlania zawartości. Na platformie WPF, typ i liczbę elementów, które mogą stanowić zawartość formantu jest nazywane formantu *modelu zawartości*. Niektóre formanty mogą zawierać jeden element i typu zawartości; na przykład zawartość <xref:System.Windows.Controls.TextBox> jest wartość ciągu, która jest przypisana do <xref:System.Windows.Controls.TextBox.Text%2A> właściwości. Poniższy przykład przedstawia zawartość <xref:System.Windows.Controls.TextBox>.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

Na poniższej ilustracji przedstawiono wynik.

![Kontrolki pola tekstowego, który zawiera tekst](../designers/media/wpfintrofigure21.png "WPFIntroFigure21")

Inne formanty, jednak może zawierać wielu elementów różnych typów zawartości; zawartość <xref:System.Windows.Controls.Button>, określony przez <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości, może zawierać wiele elementów w tym formantów układu, tekst, obrazy i kształtów. W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Button> z zawartością, która obejmuje <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Border>, a <xref:System.Windows.Controls.MediaElement>.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ButtonContentWindow"
    Title="Button Content">

  <Button Margin="20">
    <!-- Button Content -->
    <DockPanel Width="200" Height="180">
      <Label DockPanel.Dock="Top" HorizontalAlignment="Center">Click Me!</Label>
      <Border Background="Black" BorderBrush="Yellow" BorderThickness="2"
        CornerRadius="2" Margin="5">
        <MediaElement Source="media/wpf.wmv" Stretch="Fill" />
      </Border>
    </DockPanel>
  </Button>
</Window>
```

Na poniższej ilustracji przedstawiono zawartości tego przycisku.

![Przycisk zawierający wiele typów zawartości](../designers/media/wpfintrofigure22.png "WPFIntroFigure22")

Aby uzyskać więcej informacji na typy zawartości, która jest obsługiwana przez różnych formantów, zobacz [modelu zawartości WPF](/dotnet/framework/wpf/controls/wpf-content-model).

### <a name="triggers"></a>Wyzwalacze

Mimo że głównym celem znaczników XAML do zaimplementowania wygląd aplikacji, umożliwia także XAML do wykonania niektórych aspektów zachowanie aplikacji. Przykładem jest użycie wyzwalaczy, aby zmienić wygląd aplikacji na podstawie interakcji użytkownika. Aby uzyskać więcej informacji, zobacz [stylami i tworzenia szablonów](/dotnet/framework/wpf/controls/styling-and-templating).

### <a name="control-templates"></a>Szablony formantu

Domyślne interfejsów użytkownika dla formantów WPF są zwykle tworzone na podstawie innych kontrolek i kształtów. Na przykład <xref:System.Windows.Controls.Button> składa się z obu <xref:Microsoft.Windows.Themes.ButtonChrome> i <xref:System.Windows.Controls.ContentPresenter> kontrolki. <xref:Microsoft.Windows.Themes.ButtonChrome> Zapewnia wygląd przycisku standardowe podczas <xref:System.Windows.Controls.ContentPresenter> Wyświetla zawartości przycisku, zgodnie z <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości.

Czasami może być incongruent z ogólny wygląd aplikacji domyślny wygląd formantu. W takim przypadku można użyć <xref:System.Windows.Controls.ControlTemplate> Aby zmienić wygląd formantu interfejsu użytkownika bez modyfikowania jej zawartości i zachowania.

Na przykład w poniższym przykładzie pokazano, jak zmienić wygląd <xref:System.Windows.Controls.Button> przy użyciu <xref:System.Windows.Controls.ControlTemplate>.

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_17.vb)]

W tym przykładzie został zastąpiony przycisk domyślny interfejs <xref:System.Windows.Shapes.Ellipse> ciemny obramowaniem niebieska i jest wypełniana przy użyciu <xref:System.Windows.Media.RadialGradientBrush>. <xref:System.Windows.Controls.ContentPresenter> Kontroli Wyświetla zawartość <xref:System.Windows.Controls.Button>, "Kliknij mnie!" Gdy <xref:System.Windows.Controls.Button> zostanie kliknięty <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie jest zgłaszane, nadal jako część <xref:System.Windows.Controls.Button> formantu domyślne zachowanie. Wynik jest wyświetlany na poniższej ilustracji:

![Przycisk eliptycznej i drugie okno](../designers/media/wpfintrofigure2.png)

### <a name="data-templates"></a>Szablony danych

Natomiast szablon formantu umożliwia określenie wyglądu formantu, szablon danych umożliwia określenie wyglądu formantu zawartości. Szablony danych są często używane w celu zwiększenia sposób powiązania danych jest wyświetlany. Na poniższej ilustracji przedstawiono wygląd domyślny <xref:System.Windows.Controls.ListBox> który jest powiązany z kolekcją `Task` obiektów, gdzie każde zadanie ma nazwę, opis i priorytet.

![Pola listy z wyglądem domyślnym](../designers/media/wpfintrofigure18.png "WPFIntroFigure18")

Wygląd domyślny to, czego można oczekiwać, od <xref:System.Windows.Controls.ListBox>. Wygląd domyślny każdego zadania zawiera jednak tylko nazwa zadania. Aby wyświetlić nazwę zadania, opis i priorytet, domyślny wygląd <xref:System.Windows.Controls.ListBox> formantu powiązanego listy elementów należy zmienić przy użyciu <xref:System.Windows.DataTemplate>. Definiuje następujące XAML, takie <xref:System.Windows.DataTemplate>, których są stosowane do każdego zadania przy użyciu <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> atrybutu.

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="SDKSample.DataTemplateWindow"
  Title="With a Data Template">
  <Window.Resources>
    <!-- Data Template (applied to each bound task item in the task collection) -->
    <DataTemplate x:Key="myTaskTemplate">
      <Border Name="border" BorderBrush="DarkSlateBlue" BorderThickness="2"
        CornerRadius="2" Padding="5" Margin="5">
        <Grid>
          <Grid.RowDefinitions>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
          </Grid.RowDefinitions>
          <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition />
          </Grid.ColumnDefinitions>
          <TextBlock Grid.Row="0" Grid.Column="0" Padding="0,0,5,0" Text="Task Name:"/>
          <TextBlock Grid.Row="0" Grid.Column="1" Text="{Binding Path=TaskName}"/>
          <TextBlock Grid.Row="1" Grid.Column="0" Padding="0,0,5,0" Text="Description:"/>
          <TextBlock Grid.Row="1" Grid.Column="1" Text="{Binding Path=Description}"/>
          <TextBlock Grid.Row="2" Grid.Column="0" Padding="0,0,5,0" Text="Priority:"/>
          <TextBlock Grid.Row="2" Grid.Column="1" Text="{Binding Path=Priority}"/>
        </Grid>
      </Border>
    </DataTemplate>
  </Window.Resources>

  <!-- UI -->
  <DockPanel>
    <!-- Title -->
    <Label DockPanel.Dock="Top" FontSize="18" Margin="5" Content="My Task List:"/>

    <!-- Data template is specified by the ItemTemplate attribute -->
    <ListBox
      ItemsSource="{Binding}"
      ItemTemplate="{StaticResource myTaskTemplate}"
      HorizontalContentAlignment="Stretch"
      IsSynchronizedWithCurrentItem="True"
      Margin="5,0,5,5" />

 </DockPanel>
</Window>
```

Na poniższej ilustracji przedstawiono wpływu tego kodu.

![Pola listy, która używa szablonu danych](../designers/media/wpfintrofigure19.png)

Należy pamiętać, że <xref:System.Windows.Controls.ListBox> zachował jego działanie i wygląd; zmienił się tylko na wygląd zawartości będzie wyświetlany w polu listy.

Aby uzyskać więcej informacji, zobacz [omówienie tworzenia szablonów danych](/dotnet/framework/wpf/data/data-templating-overview).

### <a name="styles"></a>Style

Style Włącz deweloperów i projektantów normalizacji w szczególności wygląd ich produktu. WPF udostępnia model strong style, jest podstawą <xref:System.Windows.Style> elementu. Poniższy przykład tworzy styl, który ustawia kolor tła dla każdego <xref:System.Windows.Controls.Button> na okno, aby `Orange`.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.StyleWindow"
    Title="Styles">
  <!-- Style that will be applied to all buttons -->
  <Style TargetType="{x:Type Button}">
    <Setter Property="Background" Value="Orange" />
    <Setter Property="BorderBrush" Value="Crimson" />
    <Setter Property="FontSize" Value="20" />
    <Setter Property="FontWeight" Value="Bold" />
    <Setter Property="Margin" Value="5" />
  </Style>
  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>

  <!-- This label will not have the style applied to it -->
  <Label>Don't Click Me!</Label>

  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>
</Window>
```

Ponieważ ten styl jest przeznaczony dla wszystkich <xref:System.Windows.Controls.Button> formantów, stylów jest automatycznie stosowane do wszystkich przyciski w oknie, jak pokazano na poniższej ilustracji:

![Dwa pomarańczowe przyciski](../designers/media/wpfintrofigure20.png)

Aby uzyskać więcej informacji, zobacz [stylami i tworzenia szablonów](/dotnet/framework/wpf/controls/styling-and-templating).

### <a name="resources"></a>Zasoby

Formanty w aplikacji powinny współużytkować tego samego wygląd mogą obejmować z czcionki i kolory tła sterowania szablonów, szablony danych i style. Obsługa WPF w zasoby interfejsu użytkownika umożliwia hermetyzować zasoby w jednej lokalizacji do ponownego użycia.

W poniższym przykładzie zdefiniowano wspólnej kolor tła, który jest współużytkowany przez <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.Label>.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ResourcesWindow"
    Title="Resources Window">

  <!-- Define window-scoped background color resource -->
  <Window.Resources>
    <SolidColorBrush x:Key="defaultBackground" Color="Red" />
  </Window.Resources>

  <!-- Button background is defined by window-scoped resource -->
  <Button Background="{StaticResource defaultBackground}">One Button</Button>

  <!-- Label background is defined by window-scoped resource -->
  <Label Background="{StaticResource defaultBackground}">One Label</Label>
</Window>
```

W tym przykładzie implementuje zasób koloru tła przy użyciu `Window.Resources` elementu właściwości. Ten zasób jest dostępny dla wszystkich obiektów podrzędnych <xref:System.Windows.Window>. Istnieje wiele zasobów zakresów, takie jak, wymienione w kolejności, w których są one rozpoznane:

1.  Poszczególnych kontrolek (przy użyciu dziedziczonego <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> właściwości).

2.  A <xref:System.Windows.Window> lub <xref:System.Windows.Controls.Page> (także za pomocą dziedziczonego <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> właściwości).

3.  <xref:System.Windows.Application> (Przy użyciu <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> właściwości).

Różne zakresy zapewnia elastyczność w odniesieniu do sposobu, w którym można zdefiniować i udostępnianie zasobów.

Alternatywą wobec bezpośrednio kojarzenie zasobów z określonego zakresu można spakować jeden lub więcej zasobów przy użyciu oddzielnej <xref:System.Windows.ResourceDictionary> który może być przywoływany w innych częściach aplikacji. Na przykład w poniższym przykładzie zdefiniowano domyślny kolor tła ze słownika zasobów.

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

 Poniższy przykład odwołuje się do słownika zasobów zdefiniowane w poprzednim przykładzie, dzięki czemu są one udostępniane przez aplikację.

```xaml
<Application
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.App">

  <Application.Resources>
    <ResourceDictionary>
      <ResourceDictionary.MergedDictionaries>
        <ResourceDictionary Source="BackgroundColorResources.xaml"/>
      </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
  </Application.Resources>
</Application>
```

Zasoby i słowniki zasobów są podstawę obsługę WPF kompozycje i karnacji.

Aby uzyskać więcej informacji, zobacz [zasobów](/dotnet/framework/wpf/advanced/xaml-resources).

### <a name="custom-controls"></a>Formanty niestandardowe

Chociaż hosta obsługi dostosowywania WPF, mogą wystąpić sytuacje, w którym istniejących formantów WPF nie spełniają potrzeb aplikacji lub jej użytkowników. Taka sytuacja może wystąpić podczas:

- Nie można utworzyć interfejsu użytkownika, która jest wymagana przez dostosowanie wyglądu i działania z istniejącymi implementacjami WPF.

- Zachowanie, która jest wymagana jest nie jest obsługiwana lub nie jest obsługiwane przez istniejącymi implementacjami WPF.

W tym momencie, możesz można korzystać z jednego z trzech modeli WPF do utworzenia nowego formantu. Każdy model jest przeznaczony dla konkretnego scenariusza i wymaga formantu niestandardowego do pochodzi od konkretnej klasy podstawowej WPF. Poniżej przedstawiono trzy modele:

- **Model kontroli użytkownika**. Formant niestandardowy jest pochodną <xref:System.Windows.Controls.UserControl> i składa się z co najmniej jeden formant.

- **Model sterowania**. Formant niestandardowy jest pochodną <xref:System.Windows.Controls.Control> i jest używany do tworzenia wdrożenia, Rozdziel ich zachowanie z ich wygląd za pomocą szablonów, podobnie jak w większości formantów WPF. Wyprowadzanie z <xref:System.Windows.Controls.Control> umożliwia większą swobodę tworzenia niestandardowego interfejsu użytkownika niż kontrolki użytkownika, ale może wymagać więcej wysiłku.

- **Model elementu Framework**. Formant niestandardowy jest pochodną <xref:System.Windows.FrameworkElement> po jego wygląd jest zdefiniowany przez logikę niestandardowe renderowanie (nie szablonów).

W poniższym przykładzie przedstawiono niestandardowego liczbowe w górę/dół formantu, która jest pochodną <xref:System.Windows.Controls.UserControl>.

 [!code-xaml[IntroToWPFSnippets#UserControlMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_33.xaml)]

 [!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](../designers/codesnippet/CSharp/introduction-to-wpf_34.cs)]
 [!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](../designers/codesnippet/VisualBasic/introduction-to-wpf_34.vb)]

 Następnym przykładzie przedstawiono wymagane uwzględnienie kontrolki użytkownika w pliku XAML <xref:System.Windows.Window>.

 [!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](../designers/codesnippet/Xaml/introduction-to-wpf_37.xaml)]

 Poniższy rysunek pokazuje `NumericUpDown` kontroli hostowanych w <xref:System.Windows.Window>.

 ![Niestandardowe UserControl](../designers/media/wpfintrofigure3.png "WPFIntroFigure3")

Aby uzyskać więcej informacji na formantów niestandardowych, zobacz [informacje o formancie tworzenia](/dotnet/framework/wpf/controls/control-authoring-overview).

## <a name="wpf-best-practices"></a>Najlepsze rozwiązania w zakresie WPF

Podobnie jak w przypadku dowolnej platformie programowanie WPF można na wiele sposobów, aby osiągnąć pożądany wynik. Sposób zapewnienia, że Twoje WPF aplikacje zapewnić środowisko użytkownika wymagane i zazwyczaj spełnienia wymagań odbiorców, są zalecane najlepsze rozwiązania dotyczące ułatwień dostępu, lokalizacja i globalizacja i wydajności. Aby uzyskać więcej informacji, zobacz:

- [Ułatwienia dostępu](/dotnet/framework/ui-automation/accessibility-best-practices)
- [Lokalizacja i globalizacja WPF](/dotnet/framework/wpf/advanced/wpf-globalization-and-localization-overview)
- [Wydajność aplikacji WPF](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)
- [Zabezpieczenia WPF](/dotnet/framework/wpf/security-wpf)

## <a name="next-steps"></a>Następne kroki

Analizujemy Ciebie najważniejsze funkcje WPF. Teraz nadszedł czas, tworzenie pierwszej aplikacji WPF.

> [!div class="nextstepaction"]
> [Wskazówki: Mój pierwszy pulpitu aplikacja WPF](/dotnet/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application)

## <a name="see-also"></a>Zobacz także

- [Rozpoczynanie pracy z użyciem WPF](../designers/getting-started-with-wpf.md)
- [Windows Presentation Foundation](/dotnet/framework/wpf/index)
- [Zasoby społeczności WPF](/dotnet/framework/wpf/getting-started/community-feedback)
