---
title: "Rozszerzanie właściwości, lista zadań, danych wyjściowych i opcje Windows | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
caps.latest.revision: "37"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 631c336d0350fdf8a43d747eb6bda7b01e9d1eba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-properties-task-list-output-and-options-windows"></a>Rozszerzanie właściwości, lista zadań, danych wyjściowych i opcje systemu Windows
Można uzyskać dostępu do dowolnego okna narzędzia w programie Visual Studio. W tym przewodniku pokazano, jak zintegrować informacji na temat okna narzędzia nowy **opcje** strony i nowe ustawienie na **właściwości** strony, a także zapisać **listy zadań** i **dane wyjściowe** systemu windows.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-an-extension-with-a-tool-window"></a>Tworzenie rozszerzenia z okna narzędzia  
  
1.  Tworzenie projektu o nazwie **TodoList** przy użyciu szablonu VSIX, a następnie dodaj niestandardowe narzędzie szablon elementu okna o nazwie **TodoWindow**.  
  
    > [!NOTE]
    >  Aby uzyskać więcej informacji o tworzeniu rozszerzenie z okna narzędzia, zobacz [Tworzenie rozszerzenia z okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="set-up-the-tool-window"></a>Konfigurowanie okna narzędzi  
 Dodaj pole tekstowe, w którym można wpisać nowe zadanie do wykonania, przycisk, aby dodać nowy element do listy, a listy do wyświetlenia elementów na liście.  
  
1.  W TodoWindow.xaml należy usunąć kontrolki przycisku, pola tekstowego i Panel stosu z UserControl.  
  
    > [!NOTE]
    >  To nie powoduje usunięcia **button1_Click** obsługi zdarzeń, który będzie używany w kolejnym kroku.  
  
2.  Z **wszystkich kontrolek WPF** sekcji **przybornika**, przeciągnij **kanwy** formant do siatki.  
  
3.  Przeciągnij **pole tekstowe**, **przycisk**, a **ListBox** do obszaru roboczego. Rozmieść elementy w polu tekstowym i przycisk znajdują się na tym samym poziomie, a element ListBox wypełnia pozostałe okna znajdującą się pod nimi, tak jak na ilustracji poniżej.  
  
     ![Zakończono okna narzędzia](../extensibility/media/t5-toolwindow.png "T5 ToolWindow")  
  
4.  W okienku XAML Znajdź przycisk i ustaw dla właściwości zawartości **Dodaj**. Połącz ponownie program obsługi zdarzeń przycisk formantu przycisku przez dodanie `Click="button1_Click"` atrybutu. Blok obszaru roboczego powinien wyglądać następująco:  
  
    ```xml  
    <Canvas HorizontalAlignment="Left" Width="306">  
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>  
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>  
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>  
    </Canvas>  
    ```  
  
#### <a name="customize-the-constructor"></a>Dostosowywanie konstruktora  
  
1.  W pliku TodoWindowControl.xaml.cs, dodaj następującą instrukcję using:  
  
    ```csharp  
    using System;  
    ```  
  
2.  Dodaj publiczny odwołanie do TodoWindow i mieć konstruktora TodoWindowControl mieć parametr TodoWindow. Kod powinien wyglądać następująco:  
  
    ```csharp  
    public TodoWindow parent;  
  
    public TodoWindowControl(TodoWindow window)  
    {  
        InitializeComponent();  
        parent = window;  
    }  
    ```  
  
3.  W TodoWindow.cs Zmień konstruktora TodoWindowControl dodać parametr TodoWindow. Kod powinien wyglądać następująco:  
  
    ```csharp  
    public TodoWindow() : base(null)  
    {  
        this.Caption = "TodoWindow";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
  
         this.Content = new TodoWindowControl(this);  
    }  
    ```  
  
## <a name="create-an-options-page"></a>Utwórz stronę opcji  
 Możesz podać strony w **opcje** okna dialogowego, dzięki czemu użytkownicy będą mogli zmieniać ustawienia dla okna narzędzia. Tworzenie stron opcje wymaga zarówno klasę, która opisuje opcje i wpis w pliku TodoListPackage.cs lub TodoListPackage.vb.  
  
1.  Dodaj klasę o nazwie `ToolsOptions.cs`. Zmień klasę ToolsOptions dziedziczyć <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```csharp  
    class ToolsOptions : DialogPage  
    {  
    }  
    ```  
  
2.  Dodaj następującą instrukcję using:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
3.  Strona opcji, w tym przewodniku zawiera tylko jedną opcję o nazwie DaysAhead. Dodaj pole prywatne o nazwie **daysAhead** i właściwość o nazwie **DaysAhead** do klasy ToolsOptions:  
  
    ```csharp  
    private double daysAhead;  
  
    public double DaysAhead  
    {  
        get { return daysAhead; }  
        set { daysAhead = value; }  
    }  
    ```  
  
 Teraz należy projekt o tej stronie opcje.  
  
#### <a name="make-the-options-page-available-to-users"></a>Udostępnienie użytkownikom strona Opcje  
  
1.  W TodoWindowPackage.cs, Dodaj <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> do klasy TodoWindowPackage:  
  
    ```csharp  
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]  
    ```  
  
2.  Pierwszy parametr do konstruktora ProvideOptionPage jest typ klasy ToolsOptions, który został utworzony wcześniej. Drugi parametr "ToDo" jest nazwą kategorii w **opcje** okno dialogowe. Trzeci parametr "Ogólne" jest nazwą Podkategoria **opcje** okno dialogowe, w którym strona opcje będą dostępne. Następne dwa parametry są identyfikatorów zasobów ciągów; Pierwsza to nazwa kategorii, a drugi to nazwa podkategorii. Ostatni parametr określa, czy ta strona jest dostępna przy użyciu automatyzacji.  
  
     Gdy użytkownik otwiera stronę opcje, powinien on przypominać następujące obrazu.  
  
     ![Strona opcji](../extensibility/media/t5optionspage.gif "T5OptionsPage")  
  
     Zwróć uwagę, Kategoria **ToDo** i podkategorii **ogólne**.  
  
## <a name="make-data-available-to-the-properties-window"></a>Udostępnienie danych w oknie właściwości  
 Aby wykonać informacje o liście można udostępnić, tworząc klasę o nazwie TodoItem, która przechowuje informacje dotyczące poszczególnych elementów listy ToDo.  
  
1.  Dodaj klasę o nazwie `TodoItem.cs`.  
  
     Jeśli okna narzędzia są dostępne dla użytkowników, elementy na liście będą reprezentowane przez TodoItems. Gdy użytkownik wybierze jeden z tych elementów w kontrolce ListBox, **właściwości** oknie będą wyświetlane informacje o elemencie.  
  
     Aby udostępnić dane w **właściwości** okna, możesz przekształcić w danych właściwości publicznych, które mają dwa atrybuty specjalne, `Description` i `Category`. `Description`tekst wyświetlany w dolnej części jest **właściwości** okna. `Category`Określa, gdzie właściwość powinna występować, jeśli **właściwości** okno jest wyświetlane w **według kategorii** widoku. Na poniższej ilustracji **właściwości** okno **według kategorii** widoku **nazwa** właściwości w **pól ToDo** kategoria jest zaznaczone oraz opis **nazwa** właściwości są wyświetlane u dołu okna.  
  
     ![Okno właściwości](../extensibility/media/t5properties.png "T5Properties")  
  
2.  Dodaj następujące instrukcje using TodoItem.cs pliku.  
  
    ```csharp  
    using System.ComponentModel;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Dodaj `public` modyfikator dostępu do deklaracji klasy.  
  
    ```csharp  
    public class TodoItem  
    {  
    }  
    ```  
  
     Dodaj dwie właściwości, nazwy i Data ukończenia. Robimy UpdateList() i CheckForErrors() później.  
  
    ```csharp  
    public class TodoItem  
    {  
        private TodoWindowControl parent;  
        private string name;  
        [Description("Name of the ToDo item")]  
        [Category("ToDo Fields")]  
        public string Name  
        {  
            get { return name; }  
            set  
            {  
                name = value;  
                parent.UpdateList(this);  
            }  
        }  
  
        private DateTime dueDate;  
        [Description("Due date of the ToDo item")]  
        [Category("ToDo Fields")]  
        public DateTime DueDate  
        {  
            get { return dueDate; }  
            set  
            {  
                dueDate = value;  
                parent.UpdateList(this);  
                parent.CheckForErrors();  
            }  
        }  
    }  
    ```  
  
4.  Dodaj odwołanie prywatnych do kontrolki użytkownika. Dodaj konstruktora, który przyjmuje nazwę dla tego elementu ToDo i kontroli użytkownika. Aby znaleźć wartość daysAhead, pobiera właściwość strony opcji.  
  
    ```csharp  
    private TodoWindowControl parent;  
  
    public TodoItem(TodoWindowControl control, string itemName)  
    {  
        parent = control;  
        name = itemName;  
        dueDate = DateTime.Now;  
  
        double daysAhead = 0;  
        IVsPackage package = parent.parent.Package as IVsPackage;  
        if (package != null)  
        {  
            object obj;  
            package.GetAutomationObject("ToDo.General", out obj);  
  
            ToolsOptions options = obj as ToolsOptions;  
            if (options != null)  
            {  
                daysAhead = options.DaysAhead;  
            }  
        }  
  
        dueDate = dueDate.AddDays(daysAhead);  
    }  
    ```  
  
5.  Ponieważ wystąpień `TodoItem` klasy będzie przechowywana w polu listy i element ListBox wywoła `ToString` funkcji, należy przeciążyć `ToString` funkcji. Dodaj następujący kod do TodoItem.cs, po konstruktora, a przed zakończeniem klasy.  
  
    ```csharp  
    public override string ToString()  
    {  
        return name + " Due: " + dueDate.ToShortDateString();  
    }  
    ```  
  
6.  W TodoWindowControl.xaml.cs, Dodaj metody klasy zastępczej do klasy TodoWindowControl dla `CheckForError` i `UpdateList` metody. Umieść je po ProcessDialogChar i przed końcem pliku.  
  
    ```csharp  
    public void CheckForErrors()  
    {  
    }  
    public void UpdateList(TodoItem item)  
    {  
    }  
    ```  
  
     `CheckForError` Metoda wywoła metodę, która ma taką samą nazwę w obiekcie nadrzędnym, a metoda sprawdzi, czy błędy wystąpiły i obsługiwać je poprawnie. `UpdateList` Metody spowoduje zaktualizowanie ListBox formantu nadrzędnego; metoda wywoływana, gdy `Name` i `DueDate` właściwości w przypadku zmiany tej klasy. Będą one prowadzone później.  
  
## <a name="integrate-into-the-properties-window"></a>Integrowanie okno właściwości  
 Teraz pisania kodu, który zarządza ListBox, który zostanie powiązany **właściwości** okna.  
  
 Należy zmienić przycisku kliknij program obsługi odczyt pole tekstowe, tworzenie zadania do wykonania i dodaje go do listy.  
  
1.  Zastąp istniejące `button1_Click` funkcji z kodu, który tworzy nowy TodoItem i dodaje go do listy. Wywołuje TrackSelection(), który zostanie zdefiniowany później.  
  
    ```csharp  
    private void button1_Click(object sender, RoutedEventArgs e)  
    {  
        if (textBox.Text.Length > 0)  
        {  
            var item = new TodoItem(this, textBox.Text);  
            listBox.Items.Add(item);  
            TrackSelection();  
            CheckForErrors();  
        }  
    }  
    ```  
  
2.  W widoku projektu i wybierz kontrolkę ListBox. W **właściwości** kliknij **procedury obsługi zdarzeń** przycisk i Znajdź zdarzenie SelectionChanged. Wypełnij pole tekstowe z **listBox_SelectionChanged**. W ten sposób dodaje stub obsługi SelectionChanged i przypisuje go do zdarzenia.  
  
3.  Implementuje metody TrackSelection(). Ponieważ musisz pobrać <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> usługi, należy wprowadzić <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> dostępny za pomocą TodoWindowControl. Dodaj następującą metodę do klasy TodoWindow:  
  
    ```  
    internal object GetVsService(Type service)  
    {  
        return GetService(service);  
    }  
    ```  
  
4.  Dodaj następujące instrukcje using do TodoWindowControl.xaml.cs:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  Wypełnij obsługi SelectionChanged w następujący sposób:  
  
    ```  
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)  
    {  
        TrackSelection();  
    }  
    ```  
  
6.  Teraz, wypełnij funkcję TrackSelection, która zapewnia integrację z **właściwości** okna. Ta funkcja jest wywoływana, gdy użytkownik dodaje element do listy lub kliknie pozycję na liście. Dodaje zawartość elementu ListBox do SelectionContainer i przekazuje SelectionContainer do **właściwości** okna <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> obsługi zdarzeń. Usługa TrackSelection śledzi wybranych obiektów w interfejsie użytkownika (UI) i wyświetla ich właściwości  
  
    ```csharp  
    private SelectionContainer mySelContainer;  
    private System.Collections.ArrayList mySelItems;  
    private IVsWindowFrame frame = null;  
  
    private void TrackSelection()  
    {  
        if (frame == null)  
        {  
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;  
            if (shell != null)  
            {  
                var guidPropertyBrowser = new  
                Guid(ToolWindowGuids.PropertyBrowser);  
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,  
                ref guidPropertyBrowser, out frame);  
            }  
        }  
        if (frame != null)  
            {  
                frame.Show();  
            }  
        if (mySelContainer == null)  
        {  
            mySelContainer = new SelectionContainer();  
        }  
  
        mySelItems = new System.Collections.ArrayList();  
  
        var selected = listBox.SelectedItem as TodoItem;  
        if (selected != null)  
        {  
            mySelItems.Add(selected);  
        }  
  
        mySelContainer.SelectedObjects = mySelItems;  
  
        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))  
                                as ITrackSelection;  
        if (track != null)  
        {  
            track.OnSelectChange(mySelContainer);  
        }  
    }  
    ```  
  
     Teraz, po klasie który **właściwości** okna można użyć, możesz też zintegrować **właściwości** okna z okna narzędzia. Po kliknięciu elementu na liście w oknie narzędzia **właściwości** okna powinien być odpowiednio aktualizowany. Podobnie, gdy użytkownik zmieni elementu ToDo **właściwości** okna, skojarzony element powinien zostać zaktualizowany.  
  
7.  Teraz Dodaj pozostałe kod funkcji UpdateList w TodoWindowControl.xaml.cs. Powinien usunąć i ponownie dodać TodoItem zmodyfikowane w polu listy.  
  
    ```csharp  
    public void UpdateList(TodoItem item)  
    {  
        var index = listBox.SelectedIndex;  
        listBox.Items.RemoveAt(index);  
        listBox.Items.Insert(index, item);  
        listBox.SelectedItem = index;  
    }  
    ```  
  
8.  Testowanie kodu. Skompiluj projekt i Rozpocznij debugowanie. Eksperymentalne wystąpienie powinny być wyświetlane.  
  
9. Otwórz **narzędzia / Opcje** stron. Powinny pojawić się kategorii ToDo w okienku po lewej stronie. Kategorie są wyświetlane w alfabetyczne, dlatego Sprawdź w obszarze usług terminalowych.  
  
10. Na stronie opcji Todo powinna zostać wyświetlona ustawioną właściwość DaysAhead **0**. Zmień, aby **2**.  
  
11. W widoku / menu inne okna, otwórz **TodoWindow**. Typ **EndDate** w polu tekstowym i kliknij **Dodaj**.  
  
12. W polu listy powinny być widoczne dwa dni później niż bieżąca data.  
  
## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Dodawanie tekstu do okna dane wyjściowe oraz elementów do listy zadań  
 Dla **listy zadań**, Utwórz nowy obiekt typu zadania, a następnie dodaj ten obiekt zadania, aby **listy zadań** przez wywołanie jego metody Add. Można zapisać do **dane wyjściowe** , wywołaj jej metodę GetPane, aby uzyskać obiekt okienka, a następnie wywołaj metodę OutputString obiektu okienka.  
  
1.  W TodoWindowControl.xaml.cs w `button1_Click` metody, Dodaj kod, aby pobrać **ogólne** okienku **dane wyjściowe** okna (która jest wartością domyślną) i zapisywać do niego. Metoda powinna wyglądać następująco:  
  
    ```csharp  
    private void button1_Click(object sender, EventArgs e)  
    {  
        if (textBox.Text.Length > 0)  
        {  
            var item = new TodoItem(this, textBox.Text);  
            listBox.Items.Add(item);  
  
            var outputWindow = parent.GetVsService(  
                typeof(SVsOutputWindow)) as IVsOutputWindow;  
            IVsOutputWindowPane pane;  
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;  
            outputWindow.GetPane(ref guidGeneralPane, out pane);  
            if (pane != null)  
            {  
                 pane.OutputString(string.Format(  
                    "To Do item created: {0}\r\n",  
                 item.ToString()));  
        }  
            TrackSelection();  
            CheckForErrors();  
        }  
    }  
    ```  
  
2.  Aby dodać elementy do listy zadań, należy dodać do klasy TodoWindowControl zagnieżdżona klasa. Klasy zagnieżdżone musi pochodzić od <xref:Microsoft.VisualStudio.Shell.TaskProvider>. Dodaj następujący kod na końcu klasy TodoWindowControl.  
  
    ```csharp  
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]  
    public class TodoWindowTaskProvider : TaskProvider  
    {  
        public TodoWindowTaskProvider(IServiceProvider sp)  
            : base(sp)  
        {  
        }  
    }  
    ```  
  
3.  Następnie dodać do klasy TodoWindowControl prywatnej odwołanie do TodoTaskProvider, a także metodę CreateProvider(). Kod powinien wyglądać następująco:  
  
    ```csharp  
    private TodoWindowTaskProvider taskProvider;  
    private void CreateProvider()  
    {  
        if (taskProvider == null)  
        {  
            taskProvider = new TodoWindowTaskProvider(parent);  
            taskProvider.ProviderName = "To Do";  
        }  
    }  
    ```  
  
4.  Dodaj ClearError(), co spowoduje wyczyszczenie listy zadań, a ReportError(), który dodaje wpis do listy zadań, do klasy TodoWindowControl.  
  
    ```csharp  
    private void ClearError()  
    {  
        CreateProvider();  
        taskProvider.Tasks.Clear();  
    }  
    private void ReportError(string p)  
    {  
        CreateProvider();  
        var errorTask = new Task();  
        errorTask.CanDelete = false;  
        errorTask.Category = TaskCategory.Comments;  
        errorTask.Text = p;  
  
        taskProvider.Tasks.Add(errorTask);  
  
        taskProvider.Show();  
  
        var taskList = parent.GetVsService(typeof(SVsTaskList))  
            as IVsTaskList2;  
        if (taskList == null)  
        {  
            return;  
        }  
  
        var guidProvider = typeof(TodoWindowTaskProvider).GUID;  
         taskList.SetActiveProvider(ref guidProvider);  
    }  
    ```  
  
5.  Implementuje metody CheckForErrors teraz w następujący sposób.  
  
    ```csharp  
    public void CheckForErrors()  
    {  
        foreach (TodoItem item in listBox.Items)  
        {  
            if (item.DueDate < DateTime.Now)  
            {  
                ReportError("To Do Item is out of date: "  
                    + item.ToString());  
            }  
        }  
    }  
    ```  
  
## <a name="trying-it-out"></a>Testuje ją  
  
1.  Skompiluj projekt i Rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie.  
  
2.  Otwórz TodoWindow (**widoku / innych okien / TodoWindow**).  
  
3.  Typ elementu w polu tekstowym, a następnie kliknij przycisk **Dodaj**.  
  
     Termin 2 dni od dziś zostanie dodany do listy. Nie powodują generowania błędów i **listy zadań** (**wyświetlić / zadań listy**) powinien mieć żadnych wpisów.  
  
4.  Teraz Zmień ustawienie na **narzędzia / Opcje / ToDo** strony z **2** do **0**.  
  
5.  Typ innych obiektów w **TodoWindow** , a następnie kliknij przycisk **Dodaj** ponownie. Powoduje błąd, a także do wpisu w **listy zadań**.  
  
     Podczas dodawania elementów Data początkowa wynosi teraz plus 2 dni.  
  
6.  Na **widoku** menu, kliknij przycisk **dane wyjściowe** otworzyć **dane wyjściowe** okna.  
  
     Zwróć uwagę, że zawsze czy Dodawanie elementu, zostanie wyświetlony komunikat w **listy zadań** okienka.  
  
7.  Kliknij jeden z elementów w kontrolce ListBox.  
  
     **Właściwości** wyświetlane dwie właściwości elementu.  
  
8.  Zmień jedną z właściwości, a następnie naciśnij klawisz ENTER.  
  
     Element jest aktualizowany w kontrolce ListBox.