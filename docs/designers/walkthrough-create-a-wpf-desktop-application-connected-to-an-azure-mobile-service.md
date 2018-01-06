---
redirect_url: /azure/app-service-mobile/app-service-mobile-windows-store-dotnet-get-started
title: "Wskazówki: Tworzenie aplikacji dla komputerów osobistych WPF podłączone do usługi mobilnej Azure | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d42620f-553b-4b04-a38b-f6b306d73a50
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- csharp
- vb
ms.workload: azure
ms.openlocfilehash: f3fd548234dbd7f02be4abfab77a22d3efd9b34a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service"></a>Wskazówki: Tworzenie aplikacji dla komputerów osobistych WPF podłączone do usługi mobilnej Azure
Windows Presentation Foundation (WPF) umożliwia szybkie tworzenie nowoczesnych aplikacji pulpitu, która używa usługi mobilnej Azure do przechowywania i dostarczania danych.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
Potrzebne są następujące czynności w tym przewodniku:  
  
-   Visual Studio 2017 lub w dowolnej wersji, która obsługuje programowanie WPF.  
  
-   Aktywne konto Microsoft Azure.  
  
    -   Użytkownik może Załóż bezpłatne konto próbne [tutaj](http://azure.microsoft.com/en-us/pricing/free-trial/).  
  
    -   Może aktywować [korzyści dla subskrybentów MSDN](https://azure.microsoft.com/en-us/pricing/member-offers/msdn-benefits-details/?WT.mc_id=A261C142F). Subskrypcja MSDN otrzymasz kredyt, co miesiąc, używanego programu płatnych usług Azure.  
  
## <a name="create-a-project-and-add-references"></a>Tworzenie projektu i dodawanie odwołania  
 Pierwszym krokiem jest utworzenie projektu WPF i dodanie pakietu NuGet, które umożliwia połączenie z usług Azure Mobile Services.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  W **nowy projekt** okna dialogowego, rozwiń pozycję **Visual C#** lub **Visual Basic** węzeł i wybierz polecenie **Windows Desktop klasycznego** węzła.  
  
3.  Na liście szablonów wybierz **WPF aplikacji (.NET Framework)** szablonu.  
  
4.  W **nazwa** wprowadź pole tekstowe `WPFQuickStart`, a następnie wybierz pozycję **OK** przycisku.  
  
     Projekt zostanie utworzony i pliki projektu zostaną dodane do **Eksploratora rozwiązań**. Projektant dla domyślnego okna aplikacji o nazwie **MainWindow.xaml** jest wyświetlany.  
  
#### <a name="to-add-a-reference-to-the-windows-azure-mobile-services-sdk"></a>Aby dodać odwołanie do zestawu SDK usług mobilnych Azure systemu Windows  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **odwołania** węzeł i wybierz polecenie **Zarządzaj pakietami NuGet...** .  
  
2.  W **Menedżera pakietów NuGet**, wybierz **Przeglądaj** u góry, wprowadź `mobileservices` w polu wyszukiwania.  
  
3.  W okienku po lewej stronie wybierz **WindowsAzure.MobileServices**, a następnie w okienku po prawej stronie wybierz **zainstalować** przycisku.  
  
    > [!NOTE]
    >  Jeśli **Podgląd** zostanie wyświetlone okno dialogowe, przejrzyj proponowanych zmian, a następnie wybierz pozycję **OK** przycisku.  
  
4.  W **akceptacji licencji** okno dialogowe, przejrzyj licencji definicje terminów i zaakceptuj je, wybierając **akceptuję** przycisku.  
  
     Niezbędne odwołania zostaną dodane do **Eksploratora rozwiązań**.  
  
    > [!NOTE]
    >  Jeśli nie akceptujesz postanowień licencyjnych, wybierz **odrzucam** przycisku. Nie można zakończyć rest tego przewodnika.  
  
## <a name="create-the-user-interface"></a>Tworzenie interfejsu użytkownika  
Następnym krokiem jest tworzenie interfejsu użytkownika dla aplikacji. Najpierw utworzysz formant użytkownika wielokrotnego użytku, który wyświetla układu standardowe okienku dwóch side-by-side. Użytkownik będzie Dodaj kontrolkę użytkownika w oknie głównym aplikacji i Dodaj formanty do wprowadzania i wyświetlania danych, a następnie napisanie kodu, zdefiniuj interakcji z zapleczem usługi mobilnej.  
  
#### <a name="to-add-a-user-control"></a>Aby dodać kontrolkę użytkownika  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **WPFQuickStart** węzeł i wybierz polecenie **Dodaj**, **nowy Folder**.  
  
2.  Nazwa folderu `Common`.  
  
3.  Otwórz menu skrótów **typowe** folder i wybierz polecenie **Dodaj**, **kontrolki użytkownika**.  
  
4.  W **Dodaj nowy element** okno dialogowe, wybierz pole nazwy, a następnie wprowadź `QuickStartTask`, a następnie wybierz pozycję **Dodaj** przycisku.  
  
     Kontrola użytkownika zostanie dodane do projektu i **QuickStartTask.xaml** plik zostanie otwarty w projektancie.  
  
5.  W dolnym okienku projektanta, wybierz `<Grid>` i `</Grid>` znaczniki i Zamień poniższy kod XAML:  
  
    ```xaml  
    <Grid VerticalAlignment="Top">
        <StackPanel Orientation="Horizontal">
            <Border BorderThickness="0,0,1,0" BorderBrush="DarkGray" Margin="0,10" MinWidth="70">
                <TextBlock Text="{Binding Number}" FontSize="45" Foreground="DarkGray" Margin="20,0"/>
            </Border>
            <StackPanel>
                <TextBlock Text="{Binding Title}" Margin="10,10,0,0" FontSize="16" FontWeight="Bold" />
                <TextBlock Text="{Binding Description}" Margin="10,0,0,0" TextWrapping="Wrap" MaxWidth="500" />
            </StackPanel>
        </StackPanel>
    </Grid>  
    ```  
  
     Ten kod XAML tworzy układu wielokrotnego użytku z symbole zastępcze pola numer, tytuł i opis. W czasie wykonywania można zastąpić symbole zastępcze tekstem jak pokazano na poniższej ilustracji.  
  
     ![Kontrola użytkownika QuickStartTask](../designers/media/wpfquickstart1.PNG "WPFQuickStart1")  
  
6.  W **Eksploratora rozwiązań**, rozwiń węzeł **QuickStartTask.xaml** węzła i Otwórz **QuickStartTask.xaml.cs** lub **QuickStartTask.xaml.vb**pliku.  
  
7.  W edytorze kodu Zastąp `namespace WPFQuickStart.Common` przestrzeni nazw (C#) lub `Public Class QuickStartTask` klasy (VB) z następującym kodem:  
  
    ```csharp  
    namespace WPFQuickStart.Common  
    {  
        /// <summary>  
        /// Interaction logic for QuickStartTask.xaml  
        /// </summary>  
        public partial class QuickStartTask : UserControl  
        {  
            public QuickStartTask()  
            {  
                this.InitializeComponent();  
                this.DataContext = this;  
            }  
  
            public int Number  
            {  
                get { return (int)GetValue(NumberProperty); }  
                set { SetValue(NumberProperty, value); }  
            }  
  
            // Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...  
            public static readonly DependencyProperty NumberProperty =  
                DependencyProperty.Register("Number", typeof(int), typeof(QuickStartTask), new PropertyMetadata(0));  
  
            public string Title  
            {  
                get { return (string)GetValue(TitleProperty); }  
                set { SetValue(TitleProperty, value); }  
            }  
  
            // Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...  
            public static readonly DependencyProperty TitleProperty =  
                DependencyProperty.Register("Title", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));  
  
            public string Description  
            {  
                get { return (string)GetValue(DescriptionProperty); }  
                set { SetValue(DescriptionProperty, value); }  
            }  
  
            // Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...  
            public static readonly DependencyProperty DescriptionProperty =  
                DependencyProperty.Register("Description", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));  
        }  
    }  
    ```  
  
    ```vb  
    Partial Public Class QuickStartTask  
            Inherits UserControl  
  
            Public Sub New()  
                Me.InitializeComponent()  
                Me.DataContext = Me  
            End Sub  
  
            Public Property Number() As Integer  
                Get  
                    Return CInt(Fix(GetValue(NumberProperty)))  
                End Get  
                Set(ByVal value As Integer)  
                    SetValue(NumberProperty, value)  
                End Set  
            End Property  
  
            ' Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...  
            Public Shared ReadOnly NumberProperty As DependencyProperty = DependencyProperty.Register("Number", GetType(Integer), GetType(QuickStartTask), New PropertyMetadata(0))  
  
            Public Property Title() As String  
                Get  
                    Return CStr(GetValue(TitleProperty))  
                End Get  
                Set(ByVal value As String)  
                    SetValue(TitleProperty, value)  
                End Set  
            End Property  
  
            ' Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...  
            Public Shared ReadOnly TitleProperty As DependencyProperty = DependencyProperty.Register("Title", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))  
  
            Public Property Description() As String  
                Get  
                    Return CStr(GetValue(DescriptionProperty))  
                End Get  
                Set(ByVal value As String)  
                    SetValue(DescriptionProperty, value)  
                End Set  
            End Property  
  
            ' Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...  
            Public Shared ReadOnly DescriptionProperty As DependencyProperty = DependencyProperty.Register("Description", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))  
        End Class  
    ```  
  
     Ten kod używa właściwości zależności można ustawić wartości w polach numer, tytuł i opis w czasie wykonywania.  
  
8.  Na pasku menu wybierz **kompilacji**, **kompilacji WPFQuickStart** tworzenie kontrolki użytkownika.  
  
#### <a name="to-create-and-modify-the-main-window"></a>Do tworzenia i modyfikowania okna głównego  
  
1.  W **Eksploratora rozwiązań**, otwórz **MainWindow.xaml** pliku.  
  
2.  **Ważne**. Ten krok jest tylko dla C#. Jeśli używasz programu Visual Basic, przejdź do następnego kroku. W dolnym okienku projektanta, odszukaj wiersz `xmlns:local="clr-namespace:WPFQuickStart"` i zastąp go następującym kodem XAML:  
  
    ```xaml  
    xmlns:local="clr-namespace:WPFQuickStart.Common"  
    ```  
  
3.  W **właściwości** okna, rozwiń węzeł **typowe** węzła kategorii i wybierz polecenie **tytuł** właściwości, a następnie wprowadź `WPF Todo List` i naciśnij klawisz **Enter**  klucza.  
  
     Zwróć uwagę, że **tytuł** zmiany elementu w oknie XAML aby pasowała do nowej wartości. Można zmodyfikować właściwości XAML w oknie XAML lub **właściwości** okna, a zmiany są synchronizowane.  
  
4.  W oknie XAML, ustaw wartość **wysokość** elementu `768`i ustaw wartość **szerokość** właściwości `1280`.  
  
     Tych elementów odpowiadają **wysokość** i **szerokość** właściwości znalezionych w **układu** kategorii w **właściwości** okna.  
  
5.  Wybierz `<Grid>` i `</Grid>` znaczniki i Zamień poniższy kod XAML:  
  
    ```xaml  
    <Grid>
        <Grid Margin="50,50,10,10">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="*" />
                <ColumnDefinition Width="*" />
            </Grid.ColumnDefinitions>
            <Grid.RowDefinitions>
                <RowDefinition Height="Auto" />
                <RowDefinition Height="*" />
            </Grid.RowDefinitions>
            <Grid Grid.Row="0" Grid.ColumnSpan="2" Margin="0,0,0,20">
                <StackPanel>
                    <TextBlock Foreground="#0094ff" FontFamily="Segoe UI Light" Margin="0,0,0,6">MICROSOFT AZURE MOBILE SERVICES</TextBlock>
                    <TextBlock Foreground="Gray" FontFamily="Segoe UI Light" FontSize="45" ><Run Text="My Todo List"/></TextBlock>
                </StackPanel>
            </Grid>
            <Grid Grid.Row="1">
                <StackPanel>
                    <local:QuickStartTask Number="1" Title="Insert a TodoItem" Description="Enter some text below and click Save to insert a new todo item into the list." />
                    <StackPanel Orientation="Horizontal" Margin="72,0,0,0">
                        <TextBox x:Name="TodoInput" Margin="5" MinWidth="300"/>
                        <Button x:Name="ButtonSave" Click="ButtonSave_Click" Content="Save"/>
                    </StackPanel>
                </StackPanel>
            </Grid>
            <Grid Grid.Row="1" Grid.Column="1">
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto" />
                    <RowDefinition />
                </Grid.RowDefinitions>
                <StackPanel>
                    <local:QuickStartTask Number="2" Title="Query and Update Data" Description="Click the Refresh button to load the unfinished TodoItems from the Azure Mobile Service. Select the checkbox to mark a ToDo item as complete and update the list." />
                    <Button Margin="72,0,0,0" Name="ButtonRefresh" Click="ButtonRefresh_Click">Refresh</Button>
                </StackPanel>
                <ListView Name="ListItems" Margin="62,10,0,0" Grid.Row="1">
                    <ListView.ItemTemplate>
                        <DataTemplate>
                            <StackPanel Orientation="Horizontal">
                                <CheckBox Name="CheckBoxComplete" IsChecked="{Binding Complete, Mode=TwoWay}" Checked="CheckBoxComplete_Checked" Content="{Binding Text}" Margin="10,5" VerticalAlignment="Center"/>
                            </StackPanel>
                        </DataTemplate>
                    </ListView.ItemTemplate>
                </ListView>
            </Grid>
        </Grid>
    </Grid>  
    ```  
  
     Należy zauważyć, że zmiany są widoczne w oknie projektowania. Ponownie, również można zdefiniowano interfejsu użytkownika przez dodawanie formantów z **przybornika** okno i ustawianie właściwości w **właściwości** okna. Wszystko, co można zrobić w Projektancie może odbywać się w kodzie XAML i na odwrót.  
  
     W tym momencie projektu powinna wyglądać podobnie do poniższej ilustracji.  
  
     ![Właściwości MainWindow w Projektancie](../designers/media/wpfquickstart2.PNG "WPFQuickStart2")  
  
    > [!NOTE]
    >  Podczas następnej procedury kilka może pojawiać się błędy w **listy błędów** Jeśli jest on otwarty. Nie martw się; te błędy zniknie po ukończeniu procedury pozostałych.  
  
6.  W **Eksploratora rozwiązań**, rozwiń węzeł **MainWindow.xaml** węzła i Otwórz **MainWindow.xaml.cs** lub **MainWindow.xaml.vb** pliku.  
  
7.  W edytorze kodu, Dodaj następujący `using` lub `Imports` dyrektywy na początku pliku:  
  
    ```csharp  
    using Microsoft.WindowsAzure.MobileServices;  
    using Newtonsoft.Json;   
    ```  
  
    ```vb  
    Imports Microsoft.WindowsAzure.MobileServices  
    Imports Newtonsoft.Json  
    ```  
  
8.  Zastąp cały kod w **WPFQuickStart** przestrzeń nazw (C#) lub **klasy okna głównego** klasy (VB) z następującym kodem:  
  
    ```csharp  
    namespace WPFQuickStart  
    {  
        /// <summary>  
        /// Interaction logic for MainWindow.xaml  
        /// </summary>  
        public class TodoItem  
        {  
            public string Id { get; set; }  
  
            [JsonProperty(PropertyName = "text")]  
            public string Text { get; set; }  
  
            [JsonProperty(PropertyName = "complete")]  
            public bool Complete { get; set; }  
        }  
  
        public partial class MainWindow : Window  
        {  
            private MobileServiceCollection<TodoItem, TodoItem> items;  
            private IMobileServiceTable<TodoItem> todoTable = App.MobileService.GetTable<TodoItem>();  
  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
  
            private async void InsertTodoItem(TodoItem todoItem)  
            {  
                // This code inserts a new TodoItem into the database. When the operation completes  
                // and Mobile Services has assigned an Id, the item is added to the CollectionView  
                await todoTable.InsertAsync(todoItem);  
                items.Add(todoItem);  
            }  
  
            private async void RefreshTodoItems()  
            {  
                try  
                {  
                    // This code refreshes the entries in the list view by querying the TodoItem table.  
                    // The query excludes completed TodoItems  
                    items = await todoTable  
                        .Where(todoItem => todoItem.Complete == false)  
                        .ToCollectionAsync();  
                    ListItems.ItemsSource = items;  
                }  
                catch (MobileServiceInvalidOperationException e)  
                {  
                    MessageBox.Show(e.Message, "Error loading items");  
                }  
            }  
  
            private async void UpdateCheckedTodoItem(TodoItem item)  
            {  
                // This code takes a freshly completed TodoItem and updates the database. When the MobileService   
                // responds, the item is removed from the list   
                await todoTable.UpdateAsync(item);  
                items.Remove(item);  
            }  
  
            private void ButtonRefresh_Click(object sender, RoutedEventArgs e)  
            {  
                RefreshTodoItems();  
            }  
  
            private void ButtonSave_Click(object sender, RoutedEventArgs e)  
            {  
                var todoItem = new TodoItem { Text = TodoInput.Text };  
                InsertTodoItem(todoItem);  
                TodoInput.Text = "";  
            }  
  
            private void CheckBoxComplete_Checked(object sender, RoutedEventArgs e)  
            {  
                CheckBox cb = (CheckBox)sender;  
                TodoItem item = cb.DataContext as TodoItem;  
                UpdateCheckedTodoItem(item);  
            }  
  
            protected override void OnActivated(EventArgs e)  
            {  
                RefreshTodoItems();  
            }  
        }  
  
    }  
    ```  
  
    ```vb  
    Public Class TodoItem  
        Public Property Id() As String  
  
        <JsonProperty(PropertyName:="text")>  
        Public Property Text() As String  
  
        <JsonProperty(PropertyName:="complete")>  
        Public Property Complete() As Boolean  
    End Class  
  
    Partial Public Class MainWindow  
        Inherits Window  
  
        Private items As MobileServiceCollection(Of TodoItem, TodoItem)  
        Private todoTable As IMobileServiceTable(Of TodoItem) = Application.MobileService.GetTable(Of TodoItem)()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        Private Async Sub InsertTodoItem(ByVal todoItem As TodoItem)  
            ' This code inserts a new TodoItem into the database. When the operation completes  
            ' and Mobile Services has assigned an Id, the item is added to the CollectionView  
            Await todoTable.InsertAsync(todoItem)  
            items.Add(todoItem)  
        End Sub  
  
        Private Async Sub RefreshTodoItems()  
            Dim exception As MobileServiceInvalidOperationException = Nothing  
            Try  
                ' This code refreshes the entries in the list view by querying the TodoItem table.  
                ' The query excludes completed TodoItems  
                items = Await todoTable.Where(Function(todoItem) todoItem.Complete = False).ToCollectionAsync()  
            Catch e As MobileServiceInvalidOperationException  
                exception = e  
            End Try  
  
            If exception IsNot Nothing Then  
                MessageBox.Show(exception.Message, "Error loading items")  
            Else  
                ListItems.ItemsSource = items  
            End If  
        End Sub  
  
        Private Async Sub UpdateCheckedTodoItem(ByVal item As TodoItem)  
            ' This code takes a freshly completed TodoItem and updates the database. When the MobileService   
            ' responds, the item is removed from the list   
            Await todoTable.UpdateAsync(item)  
            items.Remove(item)  
        End Sub  
  
        Private Sub ButtonRefresh_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
            RefreshTodoItems()  
        End Sub  
  
        Private Sub ButtonSave_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
            Dim todoItem = New TodoItem With {.Text = TodoInput.Text}  
            InsertTodoItem(todoItem)  
            TodoInput.Text = ""  
        End Sub  
  
        Private Sub CheckBoxComplete_Checked(ByVal sender As Object, ByVal e As RoutedEventArgs)  
            Dim cb As CheckBox = DirectCast(sender, CheckBox)  
            Dim item As TodoItem = TryCast(cb.DataContext, TodoItem)  
            UpdateCheckedTodoItem(item)  
        End Sub  
  
        Protected Overrides Sub OnActivated(ByVal e As EventArgs)  
            RefreshTodoItems()  
        End Sub  
    End Class  
    ```  
  
     Ten kod definiuje interakcji między interfejsu użytkownika i bazę danych w usłudze mobilnej przy użyciu metod asynchronicznych.  
  
## <a name="create-the-azure-mobile-service"></a>Tworzenie usługi mobilnej Azure  
 Ostatnim krokiem jest utworzenie usługi mobilnej na platformie Microsoft Azure Dodaj tabelę do przechowywania danych, a następnie odwoływać się do wystąpienia usługi z aplikacji.  
  
#### <a name="to-create-a-mobile-service"></a>Aby utworzyć usługę mobilną  
  
1.  Otwórz przeglądarkę sieci web i zaloguj się do portalu usługi Microsoft Azure, a następnie wybierz **usług MOBILE SERVICES** kartę.  
  
2.  Wybierz **nowy** przycisk, a następnie w wyświetlonym oknie dialogowym wybierz **OBLICZENIOWE**, **usługi MOBILNEJ, Utwórz**.  
  
3.  W **nową usługę MOBILNĄ** okno dialogowe, wybierz **adres URL** pola tekstowego, a następnie wprowadź `wpfquickstart01`.  
  
    > [!NOTE]
    >  Może być konieczna zmiana liczbową część adresu URL. Microsoft Azure wymaga unikatowego adresu URL dla każdej usługi mobilnej.  
  
    To ustawia adres URL usługi do *https://wpfquickstart01.azure-mobile.net/*.  
  
4.  W **bazy danych** listy, wybierz opcję bazy danych. Ponieważ jest to prawdopodobnie nie będzie otrzymywał partii użycia aplikacji, należy wybrać **Utwórz bezpłatną bazę danych SQL 20MB** opcji lub wybierz bezpłatną bazę danych, już skojarzony z subskrypcją.  
  
5.  W **REGION** wybierz centrum danych, w której chcesz wdrożyć usługę mobilną, a następnie wybierz pozycję **dalej** przycisk (Strzałka w prawo).  
  
    > [!NOTE]
    >  Dla tej usługi użyje domyślnej **ZAPLECZA** ustawienie **JavaScript**.  
  
6.  W przypadku tworzenia nowej bazy danych na **Określ ustawienia bazy danych** strony w **serwera** listy wybierz **serwera bazy danych SQL nowe**, wprowadź użytkownika **logowania SQL Nazwa** i **hasło**, a następnie wybierz pozycję **Complete** przycisk (znacznikiem wyboru).  
  
7.  W przypadku wybrania istniejącej bazy danych na **ustawienia bazy danych** wprowadź Twojej **hasło logowania** , a następnie wybierz **Complete** przycisk (znacznikiem wyboru).  
  
     Rozpocznie się proces tworzenia usługi mobilnej. Po zakończeniu procesu stan zmieni się na **gotowe** i możesz przejść do następnego kroku.  
  
8.  W portalu, wybierz nowo utworzony usługi mobilnej, a następnie wybierz pozycję **Zarządzanie KLUCZAMI** przycisku.  
  
9. W **Zarządzaj kluczami dostępu** okno dialogowe, kopiowania **klucz aplikacji**.  
  
     Służy to w następnej procedurze.  
  
#### <a name="to-create-a-table"></a>Aby utworzyć tabelę  
  
1.  W portalu Microsoft Azure, wybierz strzałkę w prawo, obok nazwy usługi mobilnej, a na pasku menu, wybierz **danych**, a następnie wybierz pozycję **dodawania tabeli A** łącza.  
  
2.  W **Utwórz nową tabelę** okna dialogowego, w **nazwy tabeli** polu tekstowym wprowadź `TodoItem`, a następnie wybierz pozycję **Complete** przycisk (znacznikiem wyboru).  
  
     Poczekaj, aż do utworzenia tabeli, a następnie przejdź do procedury końcowe.  
  
#### <a name="to-add-a-declaration-for-the-mobile-service"></a>Aby dodać deklaracji dla usługi mobilnej  
  
1.  Wróć do programu Visual Studio. W **Eksploratora rozwiązań**, rozwiń węzeł **App.xaml** (C#) lub **Application.xaml** węzła (Visual Basic) i Otwórz **App.xaml.cs** lub  **App.XAML.VB** pliku.  
  
2.  W edytorze kodu, Dodaj następujący `using` lub **importów** dyrektywy na początku pliku:  
  
    ```csharp  
    using Microsoft.WindowsAzure.MobileServices;  
    ```  
  
    ```vb  
    Imports Microsoft.WindowsAzure.MobileServices  
    ```  
  
3.  Dodaj następujące oświadczenie do klasy, zastępując *YOUR SERVICE_HERE* o nazwie adresu URL dla usługi i zastępowanie *YOUR klucz tutaj* skopiowany w poprzednim kluczem aplikacji procedury:  
  
    ```csharp  
    public static MobileServiceClient MobileService = new MobileServiceClient(  
                 "https://YOUR-SERVICE-HERE.azure-mobile.net/",  
                 "YOUR-KEY-HERE"  
             );  
    ```  
  
    ```vb  
    Public Shared MobileService As New MobileServiceClient("https://YOUR-SERVICE-HERE.azure-mobile.net/", "YOUR-KEY-HERE")  
    ```  
  
     Ten kod umożliwia aplikacji dostęp do usługi mobilnej uruchomiony w systemie Microsoft Azure.  
  
## <a name="test-the-application"></a>Testowanie aplikacji  
 To wszystko — po utworzeniu WPF aplikacja komputerowa, która uzyskuje dostęp do usługi mobilnej Azure. Teraz pozostało jest uruchomienie aplikacji i zobaczyć ją w akcji.  
  
#### <a name="to-run-the-application"></a>Aby uruchomić aplikację  
  
1.  Na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie** (lub naciśnij klawisz **F5**).  
  
2.  W **Wstaw czynność do wykonania** pole tekstowe, wprowadź `Do something`, a następnie wybierz pozycję **zapisać** przycisku.  
  
3.  Wprowadź `Do something else`, a następnie wybierz pozycję **zapisać** przycisk ponownie.  
  
     Należy zauważyć, że dwa wpisy są dodawane do **zapytań i aktualizacji danych** listy, jak pokazano na poniższej ilustracji.  
  
     ![Elementy Todo są dodawane do listy. ] (../designers/media/wpfquickstart3.PNG "WPFQuickStart3")  
  
4.  Zaznacz pole wyboru **czegoś innego** wpis na liście.  
  
     Powoduje to wywołanie **UpdateCheckedTodoItem** — metoda i usuwa element z listy i bazy danych.  
  
## <a name="next-steps"></a>Następne kroki  
 Zakończono jest dość simplistic przykład aplikacja WPF z wewnętrznej bazy danych Azure. Oczywiście rzeczywistej aplikacji jest prawdopodobnie bardziej złożonej, ale zastosowanie tego samego podstawowe pojęcia. Zobacz [WPF w programie .NET Framework](https://msdn.microsoft.com/en-us/library/ms754130).  
  
 Możesz wprowadzić interfejsu użytkownika bardziej atrakcyjny przez dodanie kolorów, kształtów grafiki i nawet animacji. Zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML w programie Visual Studio](creating-a-ui-by-using-xaml-designer-in-visual-studio.md) i [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](creating-a-ui-by-using-blend-for-visual-studio.md). Aby uzyskać porównanie narzędzi, zobacz [projektowania XAML w programie Visual Studio i Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md).  

 Można połączyć z istniejących baz danych lub innych źródeł danych przy użyciu usług Azure Mobile Services. Zobacz [dokumentacji usług Mobile Services](http://azure.microsoft.com/en-us/services/app-service/mobile/).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Pierwszy WPF pulpitu aplikację](../designers/walkthrough-my-first-wpf-desktop-application2.md)   
 [Tworzenie nowoczesnych aplikacji klasycznych przy użyciu platformy Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)