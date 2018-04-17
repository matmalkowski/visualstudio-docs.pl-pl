---
title: 'Wskazówki: Pierwszy WPF pulpitu aplikację | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- csharp
- vb
ms.workload:
- multiple
ms.openlocfilehash: 26ab7672095c518c0204491472695e1e04a2dcdb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Wskazówki: Pierwszy WPF pulpitu aplikację

Ten przewodnik zawiera wprowadzenie do rozwoju Windows Presentation Foundation (WPF). Utworzysz Podstawowa aplikacja, która zawiera elementy, które są wspólne dla większości aplikacji klasycznych WPF: XAML znaczników, związane z kodem definicji aplikacji, kontrolki, układ, powiązania danych i style.

## <a name="creating-the-application-project"></a>Tworzenie projektu aplikacji

W tej sekcji utworzysz infrastruktury aplikacji, które zawiera projekt i okna głównego lub formularza.

### <a name="to-create-the-project"></a>Aby utworzyć projekt

1. Na pasku menu wybierz **pliku** > **nowy** > **projektu**.

1. W **nowy projekt** okna dialogowego, rozwiń pozycję **Visual C#** lub **Visual Basic** węzła i wybierz polecenie **Windows** węzeł, a następnie rozwiń węzeł **Windows** węzeł i wybierz polecenie **klasyczny pulpit** węzła.

1. Na liście szablonów wybierz **aplikacji WPF** szablonu.

1. W **nazwa** wprowadź pole tekstowe `ExpenseIt`, a następnie wybierz pozycję **OK** przycisku.

    Projekt zostanie utworzony i pliki projektu zostaną dodane do **Eksploratora rozwiązań**i Projektant dla domyślnego okna aplikacji o nazwie **MainWindow.xaml** jest wyświetlany.

### <a name="to-modify-the-main-window"></a>Aby zmodyfikować okna głównego

1. W projektancie, wybierz **MainWindow.xaml** karcie, jeśli nie jest jeszcze aktywne Karta konstruktora.

1. Jeśli używasz programu C#, wyszukaj wiersz `<Window x:Class="ExpenseIt.MainWindow"` i zastąpić go ciągiem `<NavigationWindow x:Class="ExpenseIt.MainWindow"`.

     Jeśli używasz programu Visual Basic, wyszukaj wiersz `<Window x:Class=" MainWindow"` i zastąpić go ciągiem `<NavigationWindow x:Class="MainWindow"`.

     Zwróć uwagę, że jeśli zmienisz `<Window` znacznika `<NavigationWindow`, IntelliSense automatycznie zmieni tag zamykający do `</NavigationWindow>` również.

    > [!NOTE]
    >  Po zmianie znacznika, jeśli **listy błędów** jest otwarte okno mogą pojawić się kilka błędów. Nie martw się, zmiany wprowadzane w ciągu następnych kilku kroków spowoduje, że te Przejdź optymalizacji.

1. Wybierz `<Grid>` i `</Grid>` znaczniki i usuń je.

     A **NavigationWindow** nie może zawierać inne elementy interfejsu użytkownika, takich jak **siatki**.

1. W **właściwości** okna, rozwiń węzeł **typowe** węzła kategorii i wybierz polecenie **tytuł** właściwości, a następnie wprowadź `ExpenseIt` i naciśnij klawisz **Enter**  klucza.

     Zwróć uwagę, że **tytuł** atrybut w XAML okna zmiany aby pasowała do nowej wartości. Można zmodyfikować właściwości XAML w oknie XAML lub **właściwości** okna, a zmiany są synchronizowane.

1. W oknie XAML, ustaw wartość **wysokość** elementu `375`i ustaw wartość **szerokość** właściwości `500`.

     Tych elementów odpowiadają **wysokość** i **szerokość** właściwości znalezionych w **układu** kategorii w **właściwości** okna.

     Twoje **MainWindow.xaml** pliku powinna wyglądać tak jak to w języku C#:

    ```xaml
    <NavigationWindow x:Class="ExpenseIt.MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            xmlns:local="clr-namespace:ExpenseIt"
            mc:Ignorable="d"
            Title="ExpenseIt" Height="375" Width="500">
    </NavigationWindow>
    ```

    Lub podobny do tego w języku Visual Basic:

    ```xaml
    <NavigationWindow x:Class="MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            xmlns:local="clr-namespace:ExpenseIt"
            mc:Ignorable="d"
            Title="ExpenseIt" Height="375" Width="500">
    </NavigationWindow>
    ```

### <a name="to-modify-the-code-behind-file-c"></a>Aby zmodyfikować plik CodeBehind (C#)

1. W **Eksploratora rozwiązań**, rozwiń węzeł **MainWindow.xaml** węzła i Otwórz **MainWindow.xaml.cs** pliku.

1. Znajdź wiersz `public partial class MainWindow : Window` i zastąpić go ciągiem `public partial class MainWindow : NavigationWindow`.

    Spowoduje to zmianę `MainWindow` pochodzi od klasy `NavigationWindow`. W języku Visual Basic odbywa się to automatycznie po zmianie okna w języku XAML, więc zmiany w kodzie nie są niezbędne.

## <a name="adding-files-to-the-application"></a>Dodawanie plików do aplikacji

W tej sekcji dodasz dwie strony i obraz do aplikacji.

### <a name="to-add-a-home-screen"></a>Aby dodać ekranu głównego

1. W **Eksploratora rozwiązań**, otwórz menu skrótów **programu ExpenseIt** węzeł i wybierz polecenie **Dodaj** > **strony**.

1. W **Dodaj nowy element** okno dialogowe, wybierz **nazwa** tekstu i wpisz `ExpenseItHome`, a następnie wybierz pozycję **Dodaj** przycisku.

     Ta strona jest pierwszym oknie, która jest wyświetlana, gdy aplikacja jest uruchamiana.

1. W projektancie, wybierz **ExpenseItHome.xaml** karcie, jeśli nie jest jeszcze aktywne Karta konstruktora.

1. Wybierz `Title` atrybutu i zmień wartość na **programu ExpenseIt — strona główna**.

     Twoje **ExpenseItHome.xaml** pliku powinna wyglądać tak jak to w języku C#:

    ```xaml
    <Page x:Class="ExpenseIt.ExpenseItHome"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - Home">
        <Grid>

        </Grid>
    </Page>
    ```

    W języku Visual Basic pierwszego wiersza mogą być nieco inne:

    ```xaml
    <Page x:Class="ExpenseItHome"
    ```

1. W projektancie, wybierz **MainWindow.xaml** kartę.

1. Znajdź wiersz `Title="ExpenseIt" Height="375" Width="500">` element i Dodaj `Source="ExpenseItHome.xaml"` właściwości.

     To ustawienie **ExpenseItHome.xaml** się na pierwszej stronie otwarty podczas uruchamiania aplikacji. Twoje **MainWindow.xaml** pliku powinna wyglądać tak jak to w języku C#:

    ```xaml
    <NavigationWindow x:Class="ExpenseIt.MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            xmlns:local="clr-namespace:ExpenseIt"
            mc:Ignorable="d"
            Title="ExpenseIt" Height="375" Width="500" Source="ExpenseItHome.xaml">
    </NavigationWindow>
    ```

    W języku Visual Basic pierwszego wiersza mogą być nieco inne:

    ```xaml
    <NavigationWindow x:Class="MainWindow"
    ```

     Ponieważ z właściwości, które można ustawić wcześniej, można ustawiono `Source` właściwości w **różne** kategorii **właściwości** okna.

### <a name="to-add-a-details-window"></a>Aby dodać okno Szczegóły

1. W **Eksploratora rozwiązań**, otwórz menu skrótów **programu ExpenseIt** węzeł i wybierz polecenie **Dodaj** > **strony**.

1. W **Dodaj nowy element** okno dialogowe, wybierz **nazwa** tekstu i wpisz `ExpenseReportPage`, a następnie wybierz pozycję **Dodaj** przycisku.

     To okno wyświetli raport poszczególnych wydatków.

1. W projektancie, wybierz **ExpenseReportPage.xaml** karcie, jeśli nie jest jeszcze aktywne Karta konstruktora.

1. Wybierz `Title` atrybutu i zmień wartość na **programu ExpenseIt — widok wydatków**.

     Plik ExpenseReportPage.xaml powinna wyglądać tak jak to w języku C#:

    ```xaml
    <Page x:Class="ExpenseIt.ExpenseReportPage"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - View Expense">
        <Grid>

        </Grid>
    </Page>
    ```

    W języku Visual Basic pierwszego wiersza mogą być nieco inne:

    ```xaml
    <Page x:Class="ExpenseReportPage"
    ```

1. Na pasku menu wybierz **debugowania** > **Rozpocznij debugowanie** (lub naciśnij klawisz **F5**) do uruchomienia aplikacji.

     Na poniższej ilustracji przedstawiono aplikację z przycisków nawigacji okna.

     ![Zrzut ekranu przedstawiający przykładowy programu ExpenseIt](../designers/media/gettingstartedfigure1.png "GettingStartedFigure1")

1. Zamknij aplikację, aby powrócić do trybu projektowania.

## <a name="creating-the-user-interface"></a>Tworzenie interfejsu użytkownika

Układ zapewnia uporządkowanej sposób umieszczania elementów, a także zarządza rozmiar i położenie tych elementów, gdy zmieniany jest rozmiar formularza. W tej sekcji utworzysz siatki pojedynczej kolumny z trzech wierszy. Będzie dodawanie formantów do dwie strony, Dodaj kod i na koniec zdefiniuj wielokrotnego użytku style formantów.

### <a name="to-create-the-layout"></a>Aby utworzyć układ

1. Otwórz **ExpenseItHome.xaml** i wybierz polecenie `<Grid>` elementu.

1. W **właściwości** okna, rozwiń węzeł **układu** węzła kategorii i zestawu **margines** wartości do `10`, `10`, `0`i `10`, które odpowiada lewo, prawo, górny i dolny marginesy.

     Element `Margin="10,0,10,10"` jest dodawany do `<Grid>` elementu w pliku XAML. Ponownie, może wprowadzono te wartości bezpośrednio w kodzie XAML, zamiast w **właściwości** okna z takiego samego wyniku.

1. Dodaj następujący kod XAML, aby `Grid` element do tworzenia definicji wierszy i kolumn:

    ```xaml
    <Grid.ColumnDefinitions>
        <ColumnDefinition />
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition />
        <RowDefinition Height="Auto"/>
    </Grid.RowDefinitions>
    ```

### <a name="to-add-controls"></a>Do dodawania formantów

1. Otwórz **ExpenseItHome.xaml**.

1. Dodaj następujący kod XAML tylko powyżej `</Grid>` tag, aby utworzyć `Border`, `ListBox` i `Button` kontrolki:

    ```xaml
    <!-- People list -->
      <Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">
          <Label VerticalAlignment="Center" Foreground="White">Names</Label>
      </Border>
      <ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1">
          <ListBoxItem>Mike</ListBoxItem>
          <ListBoxItem>Lisa</ListBoxItem>
          <ListBoxItem>John</ListBoxItem>
          <ListBoxItem>Mary</ListBoxItem>
      </ListBox>

      <!-- View report button -->
      <Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right">View</Button>
    ```

     Należy zauważyć, że kontrolki są wyświetlane w oknie projektowania. Można również utworzono formanty przeciągając je z **przybornika** okna na okno projektowania i ustawiania ich właściwości **właściwości** okna.

1. Skompiluj i uruchom aplikację. Na poniższej ilustracji przedstawiono wyglądu w czasie wykonywania formantów, które zostały utworzone przy użyciu języka XAML w tej procedurze.

     ![Zrzut ekranu przedstawiający przykładowy programu ExpenseIt](../designers/media/gettingstartedfigure2.png "GettingStartedFigure2")

1. Zamknij aplikację, aby powrócić do trybu projektowania.

### <a name="to-add-a-background-image"></a>Aby dodać obraz tła

1. Wybierz następujące obrazu i zapisz go jako `watermark.png`.

     ![Obraz znaku wodnego przewodnik](../designers/media/wpf_watermark.png "znaku wodnego")

    > [!NOTE]
    >  Można utworzyć własny obraz i zapisz go jako `watermark.png`.

1. W **Eksploratora rozwiązań**, otwórz menu skrótów **programu ExpenseIt** węzeł i wybierz polecenie **Dodaj** > **istniejący element**.

1. W **Dodaj istniejący element** okna dialogowego, Znajdź **watermark.png** obrazu, który właśnie został dodany, wybierz go, a następnie wybierz pozycję **Dodaj** przycisku.

    > [!NOTE]
    >  Konieczne może być rozwiń **typów plików** listę i wybierz **pliki obrazów**.

1. Otwórz **ExpenseItHome.xaml** pliku i Dodaj następujący kod XAML tylko powyżej `</Grid>` tag, aby utworzyć obraz tła:

    ```xaml
    <Grid.Background>
        <ImageBrush ImageSource="watermark.png"/>
    </Grid.Background>
    ```

### <a name="to-add-a-title"></a>Aby dodać tytuł

1. Otwórz **ExpenseItHome.xaml**.

1. Znajdź wiersz `<Grid.ColumnDefinitions>` i dodaj następujące po prostu poniżej:

    ```xaml
    <ColumnDefinition Width="230" />
    ```

    Spowoduje to utworzenie dodatkową kolumnę z lewej strony innych kolumn o stałej szerokości 230 pikseli.

1. Znajdź wiersz `<Grid.RowDefinitions>` i dodaj następujące po prostu poniżej:

    ```xaml
    <RowDefinition />
    ```

    Spowoduje to dodanie wiersza do początku siatki.

1. Przenieś formanty do drugiej kolumny przez ustawienie `Grid.Column` do wartości 1. Przenieś każdego formantu w dół wiersza, zwiększając każdego `Grid.Row` wartość 1.

    1. Znajdź wiersz `<Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">`. Zmień `Grid.Column="0"` do `Grid.Column="1"` i zmienić `Grid.Row="0"` do `Grid.Row="1"`.

    1. Znajdź wiersz `<ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1"`. Zmień `Grid.Column="0"` do `Grid.Column="1"` i zmienić `Grid.Row="1"` do `Grid.Row="2"`.

    1. Znajdź wiersz `<Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"`. Zmień `Grid.Column="0"` do `Grid.Column="1"` i zmienić `Grid.Row="2"` do `Grid.Row="3"`.

1. Tuż przed `<Border` elementu, Dodaj następujący kod XAML, aby wyświetlić tytuł:

    ```xaml
    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">
        View Expense Report
    </Label>
    ```

     Zawartość **ExpenseItHome.xaml** powinna wyglądać tak jak to w języku C#:

    ```xaml
    <Page x:Class="ExpenseIt.ExpenseItHome"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - Home">
        <Grid Margin="10,0,10,10">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="230" />
                <ColumnDefinition />
            </Grid.ColumnDefinitions>
            <Grid.RowDefinitions>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
            </Grid.RowDefinitions>
            <Border Grid.Column="1" Grid.Row="1" Height="35" Padding="5" Background="#4E87D4">
                <Label VerticalAlignment="Center" Foreground="White">Names</Label>
            </Border>
            <!-- People list -->
            <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">
                View Expense Report
            </Label>
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">
                <ListBoxItem>Mike</ListBoxItem>
                <ListBoxItem>Lisa</ListBoxItem>
                <ListBoxItem>John</ListBoxItem>
                <ListBoxItem>Mary</ListBoxItem>
            </ListBox>

            <!-- View report button -->
            <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right">View</Button>
            <Grid.Background>
                <ImageBrush ImageSource="watermark.png"/>
            </Grid.Background>
        </Grid>
    </Page>
    ```

    W języku Visual Basic pierwszego wiersza mogą być nieco inne:

    ```xaml
    <Page x:Class="ExpenseItHome"
    ```

1. Jeśli skompilować i uruchomić aplikację w tym momencie, powinien wyglądać jak na poniższej ilustracji:

     ![Zrzut ekranu przedstawiający przykładowy programu ExpenseIt](../designers/media/gettingstartedfigure3.png "GettingStartedFigure3")

### <a name="to-add-code-to-the-button"></a>Aby dodać kod do przycisku

1. Otwórz **ExpenseItHome.xaml**.

1. Wybierz `Button` element i Dodaj następujący kod XAML natychmiast po `HorizontalAlignment="Right"` element: `Click="Button_Click"`.

     Spowoduje to dodanie obsługi zdarzeń dla przycisku `Click` zdarzeń. **Przycisk** element kod powinien teraz wyglądać następująco:

    ```xaml
    <!-- View report button -->
      <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right" Click="Button_Click">View</Button>
    ```

1. Otwórz **ExpenseItHome.xaml.cs** lub **ExpenseItHome.xaml.vb** pliku.

1. Dodaj następujący kod do `ExpenseItHome` klasy:

   ```csharp
   private void Button_Click(object sender, RoutedEventArgs e)
   {
       // View Expense Report
       ExpenseReportPage expenseReportPage = new ExpenseReportPage();
       this.NavigationService.Navigate(expenseReportPage);
   }
   ```

   ```vb
   Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
       ' View Expense Report
       Dim expenseReportPage As New ExpenseReportPage()
   Me.NavigationService.Navigate(expenseReportPage)
   End Sub
   ```

    Ten program obsługi zdarzeń otwiera stronę raportu wydatków, po kliknięciu przycisku.

### <a name="to-create-the-ui-for-the-report-page"></a>Aby utworzyć interfejsu użytkownika dla strony raportu

1. Otwórz **ExpenseReportPage.xaml**.

    Ta strona wyświetla raport wydatków dla osoby, która jest zaznaczona na stronie głównej.

1. Dodaj następujący kod XAML między `<Grid>` i `</Grid>` tagów:

    ```xaml
    <Grid.Background>
        <ImageBrush ImageSource="watermark.png" />
    </Grid.Background>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="230" />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto" />
        <RowDefinition />
    </Grid.RowDefinitions>

    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
    FontWeight="Bold" FontSize="18" Foreground="#0066cc">
        Expense Report For:
    </Label>
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">

        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto" />
            <RowDefinition Height="Auto" />
            <RowDefinition />
        </Grid.RowDefinitions>

        <!-- Name -->
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">
            <Label Margin="0,0,0,5" FontWeight="Bold">Name:</Label>
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>
        </StackPanel>

        <!-- Department -->
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">
            <Label Margin="0,0,0,5" FontWeight="Bold">Department:</Label>
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>
        </StackPanel>

        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"
              HorizontalAlignment="Left">
            <!-- Expense type and Amount table -->
            <DataGrid  AutoGenerateColumns="False" RowHeaderWidth="0" >
                <DataGrid.ColumnHeaderStyle>
                    <Style TargetType="{x:Type DataGridColumnHeader}">
                        <Setter Property="Height" Value="35" />
                        <Setter Property="Padding" Value="5" />
                        <Setter Property="Background" Value="#4E87D4" />
                        <Setter Property="Foreground" Value="White" />
                    </Style>
                </DataGrid.ColumnHeaderStyle>
                <DataGrid.Columns>
                    <DataGridTextColumn Header="ExpenseType" />
                    <DataGridTextColumn Header="Amount"  />
                </DataGrid.Columns>
            </DataGrid>
        </Grid>
    </Grid>
    ```

     Interfejs ten jest podobny do interfejsu użytkownika dla strony głównej tworzony, ale dane raportu są wyświetlane w **DataGrid** formantu.

1. Skompiluj i uruchom aplikację.

1. Wybierz **widoku** przycisku.

     Zostanie wyświetlona strona raportu wydatków.

     Na poniższej ilustracji przedstawiono wydatków strony raportu. Zwróć uwagę, że jest włączony przycisk nawigacji Wstecz.

     ![Zrzut ekranu przedstawiający przykładowy programu ExpenseIt](../designers/media/gettingstartedfigure4.png "GettingStartedFigure4")

### <a name="to-style-controls"></a>Style formantów

1. Otwórz **App.xaml** pliku (C#) lub **Application.xaml** pliku (Visual Basic).

1. Dodaj następujące XAML między `<Application.Resources>` i `</Application.Resources>` tagów:

    ```xaml
    <!-- Header text style -->
    <Style x:Key="headerTextStyle">
        <Setter Property="Label.VerticalAlignment" Value="Center"></Setter>
        <Setter Property="Label.FontFamily" Value="Trebuchet MS"></Setter>
        <Setter Property="Label.FontWeight" Value="Bold"></Setter>
        <Setter Property="Label.FontSize" Value="18"></Setter>
        <Setter Property="Label.Foreground" Value="#0066cc"></Setter>
    </Style>

    <!-- Label style -->
    <Style x:Key="labelStyle" TargetType="{x:Type Label}">
        <Setter Property="VerticalAlignment" Value="Top" />
        <Setter Property="HorizontalAlignment" Value="Left" />
        <Setter Property="FontWeight" Value="Bold" />
        <Setter Property="Margin" Value="0,0,0,5" />
    </Style>

    <!-- DataGrid header style -->
    <Style x:Key="columnHeaderStyle" TargetType="{x:Type DataGridColumnHeader}">
        <Setter Property="Height" Value="35" />
        <Setter Property="Padding" Value="5" />
        <Setter Property="Background" Value="#4E87D4" />
        <Setter Property="Foreground" Value="White" />
    </Style>

    <!-- List header style -->
    <Style x:Key="listHeaderStyle" TargetType="{x:Type Border}">
        <Setter Property="Height" Value="35" />
        <Setter Property="Padding" Value="5" />
        <Setter Property="Background" Value="#4E87D4" />
    </Style>

    <!-- List header text style -->
    <Style x:Key="listHeaderTextStyle" TargetType="{x:Type Label}">
        <Setter Property="Foreground" Value="White" />
        <Setter Property="VerticalAlignment" Value="Center" />
        <Setter Property="HorizontalAlignment" Value="Left" />
    </Style>

    <!-- Button style -->
    <Style x:Key="buttonStyle" TargetType="{x:Type Button}">
        <Setter Property="Width" Value="125" />
        <Setter Property="Height" Value="25" />
        <Setter Property="Margin" Value="0,10,0,0" />
        <Setter Property="HorizontalAlignment" Value="Right" />
    </Style>
    ```

     Ta XAML dodaje następujące style:

    -   `headerTextStyle`: Aby sformatować tytuł strony `Label`.

    -   `labelStyle`: Do formatowania `Label` kontrolki.

    -   `columnHeaderStyle`: Do formatowania `DataGridColumnHeader`.

    -   `listHeaderStyle`: Do formatowania nagłówków `Border` kontrolki.

    -   `listHeaderTextStyle`: Do formatowania nagłówków **etykiety**.

    -   `buttonStyle`: Do formatowania `Button` na **ExpenseItHome.xaml** strony.

1. Otwórz **ExpenseItHome.xaml** i Zastąp wszystko pomiędzy `<Grid>` i `</Grid>` elementy o następujących XAML:

    ```xaml
    <Grid.ColumnDefinitions>
                <ColumnDefinition Width="230" />
                <ColumnDefinition />
            </Grid.ColumnDefinitions>

            <Grid.RowDefinitions>
                <RowDefinition/>
                <RowDefinition Height="Auto"/>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
            </Grid.RowDefinitions>
            <Label Grid.Column="1" Style="{StaticResource headerTextStyle}" >
                View Expense Report
            </Label>
            <!-- People list -->
                  <Border Grid.Column="1" Grid.Row="1" Style="{StaticResource listHeaderStyle}">
                <Label Style="{StaticResource listHeaderTextStyle}">Names</Label>
            </Border>
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">
                <ListBoxItem>Mike</ListBoxItem>
                <ListBoxItem>Lisa</ListBoxItem>
                <ListBoxItem>John</ListBoxItem>
                <ListBoxItem>Mary</ListBoxItem>
            </ListBox>

            <!-- View report button -->
            <Button Grid.Column="1" Grid.Row="3" Click="Button_Click" Style="{StaticResource buttonStyle}">View</Button>
            <Grid.Background>
                <ImageBrush ImageSource="watermark.png"  />
            </Grid.Background>
    ```

     Właściwości, takie jak `VerticalAlignment` i `FontFamily` definiujących wygląd każdej kontrolki usunięty i zastąpiony, stosując style.

1. Otwórz **ExpenseReportPage.xaml** i Zastąp wszystko pomiędzy `<Grid>` i końcowych `</Grid>` elementy o następujących XAML:

    ```xaml
    <Grid.Background>
        <ImageBrush ImageSource="watermark.png" />
    </Grid.Background>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="230" />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto" />
        <RowDefinition />
    </Grid.RowDefinitions>
    <Label Grid.Column="1" Style="{StaticResource headerTextStyle}">
        Expense Report For:
    </Label>
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto" />
            <RowDefinition Height="Auto" />
            <RowDefinition />
        </Grid.RowDefinitions>

        <!-- Name -->
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">
            <Label Style="{StaticResource labelStyle}">Name:</Label>
            <Label Style="{StaticResource labelStyle}"></Label>
        </StackPanel>

        <!-- Department -->
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1"
    Orientation="Horizontal">
            <Label Style="{StaticResource labelStyle}">Department:</Label>
            <Label Style="{StaticResource labelStyle}"></Label>
        </StackPanel>

        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"
              HorizontalAlignment="Left">
            <!-- Expense type and Amount table -->
            <DataGrid ColumnHeaderStyle="{StaticResource columnHeaderStyle}"
                      AutoGenerateColumns="False" RowHeaderWidth="0" >
                <DataGrid.Columns>
                    <DataGridTextColumn Header="ExpenseType" />
                    <DataGridTextColumn Header="Amount"  />
                </DataGrid.Columns>
            </DataGrid>
        </Grid>
    </Grid>
    ```

     Spowoduje to dodanie stylów `<Label>` i `<Border>` elementy.

## <a name="connecting-to-data"></a>Łączenie z danymi
 W tej sekcji będzie utworzyć dostawcę danych i szablon danych, a następnie połącz służy do wyświetlania danych.

### <a name="to-bind-data-to-a-control"></a>Wiązanie danych do formantu

1. Otwórz **ExpenseItHome.xaml** i wybierz polecenie `<Grid>` elementu.

1. Dodaj następujący kod XAML:

    ```xaml
    <Grid.Resources>
    <!-- Expense Report Data -->
    <XmlDataProvider x:Key="ExpenseDataSource" XPath="Expenses">
        <x:XData>
            <Expenses xmlns="">
                <Person Name="Mike" Department="Legal">
                    <Expense ExpenseType="Lunch" ExpenseAmount="50" />
                    <Expense ExpenseType="Transportation" ExpenseAmount="50" />
                </Person>
                <Person Name="Lisa" Department="Marketing">
                    <Expense ExpenseType="Document printing"
          ExpenseAmount="50"/>
                    <Expense ExpenseType="Gift" ExpenseAmount="125" />
                </Person>
                <Person Name="John" Department="Engineering">
                    <Expense ExpenseType="Magazine subscription"
         ExpenseAmount="50"/>
                    <Expense ExpenseType="New machine" ExpenseAmount="600" />
                    <Expense ExpenseType="Software" ExpenseAmount="500" />
                </Person>
                <Person Name="Mary" Department="Finance">
                    <Expense ExpenseType="Dinner" ExpenseAmount="100" />
                </Person>
            </Expenses>
        </x:XData>
    </XmlDataProvider>
    </Grid.Resources>
    ```

     Ten kod tworzy `XmlDataProvider` klasy, która zawiera dane dla każdej osoby. Zwykle będzie to być ładowane jako plik, ale dla uproszczenia dane są dodawane wbudowanego.

1. Wewnątrz `<Grid.Resources>` elementu, Dodaj następujący kod XAML:

    ```xaml
    <!-- Name item template -->
    <DataTemplate x:Key="nameItemTemplate">
        <Label Content="{Binding XPath=@Name}"/>
    </DataTemplate>
    ```

     Spowoduje to dodanie `Data Template` definiujący sposób wyświetlania danych w **ListBox**.

1. Zastąp istniejące `<ListBox>` elementu o następujących XAML:

    ```xaml
    <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2"
             ItemsSource="{Binding Source={StaticResource ExpenseDataSource}, XPath=Person}"
             ItemTemplate="{StaticResource nameItemTemplate}">
    </ListBox>
    ```

     Ten kod wiąże `ItemsSource` właściwość `ListBox` ze źródłem danych i stosuje szablon danych jako `ItemTemplate`.

### <a name="to-connect-data-to-controls"></a>Aby połączyć dane do formantów

1. Otwórz **ExpenseReportPage.xaml.vb** lub **ExpenseReportPage.xaml.cs**.

1. W języku C#, Dodaj następujący Konstruktor do **ExpenseReportPage** klasy lub w języku Visual Basic Zastąp istniejące klasy następującym kodem:

   ```csharp
   // Custom constructor to pass expense report data
   public ExpenseReportPage(object data):this()
   {
       // Bind to expense report data.
       this.DataContext = data;
   }
   ```

   ```vb
   Partial Public Class ExpenseReportPage
   Inherits Page
       Public Sub New()
       InitializeComponent()
       End Sub

       ' Custom constructor to pass expense report data
       Public Sub New(ByVal data As Object)
           Me.New()
           ' Bind to expense report data.
           Me.DataContext = data
       End Sub
   End Class
   ```

   Ten konstruktor przyjmuje obiekt danych jako parametr. W takim przypadku obiekt danych będzie zawierać nazwę wybranego użytkownika.

1. Otwórz **ExpenseItHome.xaml.vb** lub **ExpenseItHome.xaml.cs**.

1. Zastąp `Click` kod obsługi zdarzenia z następujących czynności:

   ```csharp
   private void Button_Click(object sender, RoutedEventArgs e)
   {
       // View Expense Report
       ExpenseReportPage expenseReportPage = new ExpenseReportPage(this.peopleListBox.SelectedItem);
       this.NavigationService.Navigate(expenseReportPage);
   }
   ```

   ```vb
   Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
       ' View Expense Report
       Dim expenseReportPage As New ExpenseReportPage(Me.peopleListBox.SelectedItem)
       Me.NavigationService.Navigate(expenseReportPage)
   End Sub
   ```

   Ten kod wywołuje nowego konstruktora.

### <a name="to-update-the-ui-with-data-templates"></a>Aby zaktualizować interfejsu użytkownika z szablonami danych

1. Otwórz **ExpenseReportPage.xaml**.

1. Zastąp kod XAML **nazwa** i **działu** `<StackPanel` elementy z następujących czynności:

    ```xaml
    <!-- Name -->
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">
        <Label Style="{StaticResource labelStyle}">Name:</Label>
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Name}"></Label>
    </StackPanel>

    <!-- Department -->
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">
        <Label Style="{StaticResource labelStyle}">Department:</Label>
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Department}"></Label>
    </StackPanel>
    ```

     Powoduje to powiązanie **etykiety** formantów do właściwości źródła danych.

1. Dodaj następujący kod XAML wewnątrz `<Grid>` elementu:

    ```xaml
    <!--Templates to display expense report data-->
    <Grid.Resources>
        <!-- Reason item template -->
        <DataTemplate x:Key="typeItemTemplate">
            <Label Content="{Binding XPath=@ExpenseType}"/>
        </DataTemplate>
        <!-- Amount item template -->
        <DataTemplate x:Key="amountItemTemplate">
            <Label Content="{Binding XPath=@ExpenseAmount}"/>
        </DataTemplate>
    </Grid.Resources>
    ```

     Definiuje sposób wyświetlania danych raportu wydatków.

1. Zastąp `<DataGrid>` element z następujących czynności:

    ```xaml
    <!-- Expense type and Amount table -->
    <DataGrid ItemsSource="{Binding XPath=Expense}" ColumnHeaderStyle="{StaticResource columnHeaderStyle}" AutoGenerateColumns="False" RowHeaderWidth="0" >

        <DataGrid.Columns>
            <DataGridTextColumn Header="ExpenseType" Binding="{Binding XPath=@ExpenseType}"  />
            <DataGridTextColumn Header="Amount" Binding="{Binding XPath=@ExpenseAmount}" />
        </DataGrid.Columns>

    </DataGrid>
    ```

     Spowoduje to dodanie **ItemSource** i definiuje powiązania elementów wydatków.

1. Skompiluj i uruchom aplikację.

1. Wybierz osoby, a następnie wybierz **widoku** przycisku.

     Na poniższej ilustracji przedstawiono obie strony aplikacji programu ExpenseIt z formantami, układ, style, powiązania danych i zastosować szablony danych.

     ![Zrzuty ekranu programu ExpenseIt](../designers/media/gettingstartedfigure5.png "GettingStartedFigure5")

## <a name="best-practices"></a>Najlepsze praktyki

W tym przykładzie przedstawiono podstawowe informacje o WPF i w związku z tym, nie jest zgodna z najlepszych rozwiązań tworzenia aplikacji. Dla kompleksowym WPF i .NET Framework aplikacji programowanie najlepszych rozwiązań zobacz następujące tematy, zależnie od potrzeb:

-   Dostępność — [najlepsze praktyki dotyczące ułatwień dostępu](/dotnet/framework/ui-automation/accessibility-best-practices)

-   Zabezpieczenia — [zabezpieczeń w systemie Windows Presentation Foundation](/dotnet/framework/wpf/security-wpf)

-   Lokalizacja — [omówienie lokalizacja i globalizacja WPF](/dotnet/framework/wpf/advanced/wpf-globalization-and-localization-overview)

-   Wydajność — [optymalizacji wydajności aplikacji WPF](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)

## <a name="whats-next"></a>Co to jest dalej

Masz teraz szereg technik dyspozycji użytkownika służący do tworzenia klasycznych aplikacji przy użyciu WPF. Powinny teraz mieć podstawową wiedzę na temat tworzenia bloków aplikacji WPF z danymi. W tym temacie w żadnym wypadku nie jest wyczerpująca, ale miejmy nadzieję, że użytkownik ma teraz również w pewnym sensie niektóre możliwości, które można wykryć samodzielnie poza technik w tym temacie.

Aby uzyskać więcej informacji o modelach programowanie i architektura WPF zobacz następujące tematy:

-   [Architektura WPF](/dotnet/framework/wpf/advanced/wpf-architecture)

-   [XAML — omówienie](/dotnet/framework/wpf/advanced/xaml-overview-wpf)

-   [Przegląd właściwości zależności](/dotnet/framework/wpf/advanced/dependency-properties-overview)

-   [Układ systemu](/dotnet/framework/wpf/advanced/layout)

-   [Style i szablony](/dotnet/framework/wpf/controls/styles-and-templates)

Aby uzyskać więcej informacji o tworzeniu aplikacji zobacz następujące tematy:

-   [Omówienie tworzenia aplikacji](/dotnet/framework/wpf/app-development/index)

-   [Informacje o formantach](/dotnet/framework/wpf/controls/index)

-   [Powiązanie danych — omówienie](/dotnet/framework/wpf/data/data-binding-overview)

-   [Omówienie nośnika, animacji i WPF grafikę](/dotnet/framework/wpf/graphics-multimedia/index)

-   [Dokumenty w WPF](/dotnet/framework/wpf/advanced/documents-in-wpf)

## <a name="see-also"></a>Zobacz także

[Tworzenie nowoczesnych aplikacji klasycznych przy użyciu platformy Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)
