---
title: "Dodawanie do okna narzędzia wyszukiwania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
caps.latest.revision: "38"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4f30c28b7255769be97ba6063e7c1ce435dfbe9f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="adding-search-to-a-tool-window"></a>Dodawanie do okna narzędzia wyszukiwania
Podczas tworzenia lub aktualizowania okna narzędzia w rozszerzenie, można dodać te same funkcje wyszukiwania, która pojawia się w innym miejscu w programie Visual Studio. Ta funkcja oferuje następujące funkcje:  
  
-   Pole wyszukiwania znajduje się zawsze w obszarze niestandardowego paska narzędzi.  
  
-   Wskaźnik postępu, który jest umieszczenia na samo pole wyszukiwania.  
  
-   Możliwość Pokaż wyniki, jak wprowadzasz każdego znaku (szybkie wyszukiwanie) lub tylko po wybraniu klawisza Enter (wyszukiwania na żądanie).  
  
-   Lista zawiera warunki, dla których wyszukaniu ostatnio.  
  
-   Możliwość filtrowania wyszukuje według określonych pól lub aspektów docelowe wyszukiwania.  
  
 Wykonując tego przewodnika, dowiesz się, jak można wykonywać następujące zadania:  
  
1.  Utwórz projekt pakiet VSPackage.  
  
2.  Utworzyć okna narzędzia, która zawiera UserControl z pola tekstowego tylko do odczytu.  
  
3.  Dodaj pole wyszukiwania do okna narzędzia.  
  
4.  Dodaj implementację wyszukiwania.  
  
5.  Włącz szybkie wyszukiwanie i Wyświetl pasek postępu.  
  
6.  Dodaj **wielkość liter** opcji.  
  
7.  Dodaj **wyszukiwanie tylko wiersze nawet** filtru.  
  
## <a name="to-create-a-vsix-project"></a>Do tworzenia projektu VSIX  
  
1.  Tworzenie projektu VSIX o nazwie `TestToolWindowSearch` z okna narzędzia o nazwie **TestSearch**. Jeśli potrzebujesz pomocy w ten sposób, zobacz [Tworzenie rozszerzenia z okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="to-create-a-tool-window"></a>Można utworzyć okna narzędzia  
  
1.  W `TestToolWindowSearch` projektu, otwórz plik TestSearchControl.xaml.  
  
2.  Zastąp istniejące `<StackPanel>` blok następujący blok, który dodaje tylko do odczytu <xref:System.Windows.Controls.TextBox> do <xref:System.Windows.Controls.UserControl> w oknie narzędzia.  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3.  W pliku TestSearchControl.xaml.cs, dodaj następującą instrukcję using:  
  
    ```csharp  
    using System.Text;  
    ```  
  
4.  Usuń `button1_Click()` metody.  
  
     W **TestSearchControl** klasy, Dodaj następujący kod.  
  
     Ten kod dodaje publiczny <xref:System.Windows.Controls.TextBox> właściwości o nazwie **SearchResultsTextBox** i właściwości publicznej ciągu o nazwie **SearchContent**. W Konstruktorze SearchResultsTextBox ma ustawioną wartość pola tekstowego, a SearchContent jest ustawiana na zestaw ciągów rozdzielone znakami nowego wiersza. Zawartość pola tekstowego również jest ustawiana na zestaw parametrów.  
  
    ```csharp  
    public partial class TestSearchControl : UserControl  
    {  
        public TextBox SearchResultsTextBox { get; set; }  
        public string SearchContent { get; set; }  
  
        public TestSearchControl()  
        {  
            InitializeComponent();  
  
            this.SearchResultsTextBox = resultsTextBox;  
            this.SearchContent = BuildContent();  
  
            this.SearchResultsTextBox.Text = this.SearchContent;  
        }  
  
        private string BuildContent()  
        {  
            StringBuilder sb = new StringBuilder();  
            sb.AppendLine("1 go");  
            sb.AppendLine("2 good");  
            sb.AppendLine("3 Go");  
            sb.AppendLine("4 Good");  
            sb.AppendLine("5 goodbye");  
            sb.AppendLine("6 Goodbye");  
  
            return sb.ToString();  
        }  
    }  
    ```  
  
     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]  
  
5.  Skompiluj projekt i Rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie programu Visual Studio.  
  
6.  Na pasku menu wybierz **widoku**, **inne okna**, **TestSearch**.  
  
     Zostanie wyświetlone okno narzędzia, ale kontrolka wyszukiwania nie jest jeszcze wyświetlane.  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>Aby dodać pole wyszukiwania do okna narzędzi  
  
1.  W pliku TestSearch.cs, Dodaj następujący kod do `TestSearch` klasy. Ten kod zastępuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> właściwości, aby metody dostępu get zwraca `true`.  
  
     Aby włączyć wyszukiwanie, należy zastąpić <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> właściwości. <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> Klasa implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> i udostępnia domyślną implementację, które nie umożliwiają wyszukiwania.  
  
    ```csharp  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  Skompiluj projekt i Rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie.  
  
3.  Eksperymentalne wystąpienie programu Visual Studio, otwórz **TestSearch**.  
  
     Formant wyszukiwania pojawi się w górnej części okna narzędzia, z **wyszukiwania** ikona szkła powiększanie i znak wodny. Jednak wyszukiwania nie działa jeszcze, ponieważ proces wyszukiwania nie została zaimplementowana.  
  
## <a name="to-add-the-search-implementation"></a>Aby dodać implementację wyszukiwania  
 Po włączeniu wyszukiwania na <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, tak jak w poprzedniej procedurze okna narzędzia tworzy hosta wyszukiwania. Ten host konfiguruje i zarządza procesami wyszukiwania, które są zawsze wykonywane dla wątku w tle. Ponieważ <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> klasa zarządza utworzenia hosta wyszukiwania i ustawienie wyszukiwania, należy tylko utworzenia zadania wyszukiwania i podaj metody search. Proces wyszukiwania wątku w tle, a wywołania do formantu okna narzędzia występować w wątku interfejsu użytkownika. W związku z tym należy użyć <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A> metoda zarządzania wszelkie wprowadzone w obsłudze formantu wywołania.  
  
1.  W pliku TestSearch.cs, Dodaj następujący `using` instrukcji:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Runtime.InteropServices;  
    using System.Text;  
    using System.Windows.Controls;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
2.  W `TestSearch` klasy, Dodaj następujący kod, który wykonuje następujące czynności:  
  
    -   Zastępuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> metodę w celu utworzenia zadania wyszukiwania.  
  
    -   Zastępuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> metody w celu przywrócenia stanu pola tekstowego. Ta metoda jest wywoływana, gdy użytkownik anuluje zadania wyszukiwania i kiedy użytkownik ustawia lub unsets opcji lub filtrów. Zarówno <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> są wywoływane w wątku interfejsu użytkownika. W związku z tym nie trzeba uzyskać dostępu do pola tekstowego za pomocą klasy <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A> metody.  
  
    -   Tworzy klasę o nazwie `TestSearchTask` dziedziczący po <xref:Microsoft.VisualStudio.Shell.VsSearchTask>, który udostępnia domyślną implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.  
  
         W `TestSearchTask`, konstruktora ustawia pole prywatne, który odwołuje się do okna narzędzia. Zapewnienie metody search zastąpienie <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> i <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> metody. <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> Metoda jest, gdzie zaimplementować proces wyszukiwania. Proces ten obejmuje wyszukiwania, wyświetlania wyników wyszukiwania w polu tekstowym i wywołanie implementacji klasy podstawowej tej metody, aby zgłosić ukończeniu wyszukiwania.  
  
    ```csharp  
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)  
    {  
        if (pSearchQuery == null || pSearchCallback == null)  
            return null;  
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);  
    }  
  
    public override void ClearSearch()  
    {  
        TestSearchControl control = (TestSearchControl)this.Content;  
        control.SearchResultsTextBox.Text = control.SearchContent;  
    }  
  
    internal class TestSearchTask : VsSearchTask  
    {  
        private TestSearch m_toolWindow;  
  
        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)  
            : base(dwCookie, pSearchQuery, pSearchCallback)  
        {  
            m_toolWindow = toolwindow;  
        }  
  
        protected override void OnStartSearch()  
        {  
            // Use the original content of the text box as the target of the search.   
            var separator = new string[] { Environment.NewLine };  
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;  
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);  
  
            // Get the search option.   
            bool matchCase = false;  
            // matchCase = m_toolWindow.MatchCaseOption.Value;   
  
                // Set variables that are used in the finally block.  
                StringBuilder sb = new StringBuilder("");  
                uint resultCount = 0;  
                this.ErrorCode = VSConstants.S_OK;  
  
                try  
                {  
                    string searchString = this.SearchQuery.SearchString;  
  
                    // Determine the results.   
                    uint progress = 0;  
                    foreach (string line in contentArr)  
                    {  
                        if (matchCase == true)  
                        {  
                            if (line.Contains(searchString))  
                            {  
                                sb.AppendLine(line);  
                                resultCount++;  
                            }  
                        }  
                        else  
                            {  
                                if (line.ToLower().Contains(searchString.ToLower()))  
                                {  
                                    sb.AppendLine(line);  
                                    resultCount++;  
                                }  
                            }  
  
                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));   
  
                            // Uncomment the following line to demonstrate the progress bar.   
                            // System.Threading.Thread.Sleep(100);  
                        }  
                    }  
                    catch (Exception e)  
                    {  
                        this.ErrorCode = VSConstants.E_FAIL;  
                    }  
                    finally  
                    {  
                        ThreadHelper.Generic.Invoke(() =>  
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });  
  
                        this.SearchResults = resultCount;  
                    }  
  
            // Call the implementation of this method in the base class.   
            // This sets the task status to complete and reports task completion.   
            base.OnStartSearch();  
        }  
  
        protected override void OnStopSearch()  
        {  
            this.SearchResults = 0;  
        }  
    }  
    ```  
  
3.  Testowania implementacji wyszukiwania, wykonując następujące czynności:  
  
    1.  Ponownie skompilować projekt i Rozpocznij debugowanie.  
  
    2.  W eksperymentalnym wystąpieniu programu Visual Studio Otwórz ponownie okno narzędzia, wprowadź tekst wyszukiwania w oknie wyszukiwania i naciśnij klawisz ENTER.  
  
         Powinna zostać wyświetlona poprawnych wyników.  
  
## <a name="to-customize-the-search-behavior"></a>Aby dostosować zachowanie wyszukiwania  
 Zmiana ustawień wyszukiwania, możesz wprowadzić różnych zmian w sposób wyświetlania formantu wyszukiwania i jak wyszukiwanie jest przeprowadzane. Na przykład można zmienić znaku wodnego (domyślny tekst wyświetlany w polu wyszukiwania), minimalna i maksymalną szerokość formantu wyszukiwania oraz czy ma być wyświetlany pasek postępu. Można również zmienić punkt, w których wyniki wyszukiwania Uruchom (na żądanie lub wyszukaj) i czy ma być wyświetlana lista warunków, dla których ostatnio Przeszukano. Pełną listę ustawień w można znaleźć <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> klasy.  
  
1.  W pliku TestSearch.cs, Dodaj następujący kod do `TestSearch` klasy. Ten kod umożliwia szybkie wyszukiwanie zamiast wyszukiwania na żądanie (co oznacza, że użytkownik nie ma naciśnij klawisz ENTER). Ten kod zastępuje `ProvideSearchSettings` metoda `TestSearch` klasy, które są niezbędne do zmiany ustawień domyślnych.  
  
    ```csharp  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  Testowanie nowe ustawienie ponownie skompilować rozwiązanie i uruchamiając ponownie debuger.  
  
     Wyniki wyszukiwania wyświetlany za każdym razem wprowadzać znaku w polu wyszukiwania.  
  
3.  W `ProvideSearchSettings` metody, Dodaj następujący wiersz, który umożliwia wyświetlanie pasek postępu.  
  
    ```csharp  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,   
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);  
    }  
    ```  
  
     Pasek postępu się pojawiać należy podać postęp. Aby zgłosić postęp, usuń znaczniki komentarza następujący kod w `OnStartSearch` metody `TestSearchTask` klasy:  
  
    ```csharp  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  Aby zwolnić przetwarzania wystarczająco postęp pasek jest widoczny, usuń znaczniki komentarza następujący wiersz w `OnStartSearch` metody `TestSearchTask` klasy:  
  
    ```csharp  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  Przetestuj nowe ustawienia, ponownie skompilować rozwiązanie i rozpoczyna debugb.  
  
     Pasek postępu postać w oknie wyszukiwania (niebieska linia poniżej pola tekstowego wyszukiwania) zawsze czy wyszukiwania.  
  
## <a name="to-enable-users-to-refine-their-searches"></a>Aby umożliwić użytkownikom zawęzić kryteria wyszukiwania ich  
 Można zezwolić użytkownikom zawęzić kryteria wyszukiwania ich za pomocą opcji takich jak **wielkość liter** lub **Uwzględnij całe wyrazy**. Opcje można boolean, które występują jako pola wyboru lub polecenia, które są wyświetlane jako przyciski. W ramach tego przewodnika utworzysz opcja boolean.  
  
1.  W pliku TestSearch.cs, Dodaj następujący kod do `TestSearch` klasy. Ten kod zastępuje `SearchOptionsEnum` metodę, która umożliwia implementacji wyszukiwania do wykrywania, czy opcja danego lub wyłączyć. Kod w `SearchOptionsEnum` dodaje opcję uwzględnianie wielkości liter na <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> modułu wyliczającego. Opcję, aby wielkość liter jest również dostępny jako `MatchCaseOption` właściwości.  
  
    ```csharp  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
    {  
        get  
        {  
            if (m_optionsEnum == null)  
            {  
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();  
  
                list.Add(this.MatchCaseOption);  
  
                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;  
            }  
            return m_optionsEnum;  
        }  
    }  
  
    private WindowSearchBooleanOption m_matchCaseOption;  
    public WindowSearchBooleanOption MatchCaseOption  
    {  
        get  
        {  
            if (m_matchCaseOption == null)  
            {  
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);  
            }  
            return m_matchCaseOption;  
        }  
    }  
    ```  
  
2.  W `TestSearchTask` klasy, usuń znaczniki komentarza matchCase wiersza w `OnStartSearch` metody:  
  
    ```csharp  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
    {  
        get  
        {  
            if (m_optionsEnum == null)  
            {  
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();  
  
                list.Add(this.MatchCaseOption);  
  
                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;  
            }  
            return m_optionsEnum;  
        }  
    }  
  
    private WindowSearchBooleanOption m_matchCaseOption;  
    public WindowSearchBooleanOption MatchCaseOption  
    {  
        get  
         {  
            if (m_matchCaseOption == null)  
            {  
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);  
            }  
            return m_matchCaseOption;  
        }  
    }  
    ```  
  
3.  Przetestuj opcji:  
  
    1.  Skompiluj projekt i Rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie.  
  
    2.  W oknie Narzędzia wybierz Strzałka w dół po prawej stronie pola tekstowego.  
  
         **Wielkość liter** zostanie wyświetlone pole wyboru.  
  
    3.  Wybierz **wielkość liter** pole wyboru, a następnie wykonać niektóre wyszukiwania.  
  
## <a name="to-add-a-search-filter"></a>Aby dodać filtr wyszukiwania  
 Możesz dodać filtry wyszukiwania, które umożliwiają użytkownikom zaktualizowania zestawu elementów docelowych wyszukiwania. Na przykład można filtrować pliki w Eksploratorze plików według daty, na których ich modyfikacji ostatnio i ich rozszerzeń nazw plików. W tym przewodniku będzie dodać filtr tylko nawet wierszy. Po wybraniu tego filtru wyszukiwania dodaje ciągów, które można określić zapytania wyszukiwania. Można zidentyfikować te ciągi wewnątrz metodę wyszukiwania i odpowiednio filtrować elementy docelowe wyszukiwania.  
  
1.  W pliku TestSearch.cs, Dodaj następujący kod do `TestSearch` klasy. Implementuje kod `SearchFiltersEnum` przez dodanie <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> Określa, aby filtrować wyniki wyszukiwania będą wyświetlane tylko nawet wierszy.  
  
    ```csharp  
    public override IVsEnumWindowSearchFilters SearchFiltersEnum  
    {  
        get  
        {  
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();  
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));  
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;  
        }  
    }  
  
    ```  
  
     Teraz formant wyszukiwania Wyświetla filtr wyszukiwania `Search even lines only`. Gdy użytkownik wybierze filtr ciąg `lines:"even"` jest wyświetlana w polu wyszukiwania. Kryteria wyszukiwania może się znajdować w tym samym czasie jako filtr. Ciągi wyszukiwania może pojawić się przed filtru, po filtr lub oba.  
  
2.  W pliku TestSearch.cs, Dodaj następujące metody umożliwiające `TestSearchTask` klasy, która znajduje się w `TestSearch` klasy. Te metody obsługują `OnStartSearch` metodę, która będzie zmodyfikować w następnym kroku.  
  
    ```csharp  
    private string RemoveFromString(string origString, string stringToRemove)  
    {  
        int index = origString.IndexOf(stringToRemove);  
        if (index == -1)  
            return origString;  
        else   
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();  
    }  
  
    private string[] GetEvenItems(string[] contentArr)  
    {  
        int length = contentArr.Length / 2;  
        string[] evenContentArr = new string[length];  
  
        int indexB = 0;  
        for (int index = 1; index < contentArr.Length; index += 2)  
        {  
            evenContentArr[indexB] = contentArr[index];  
            indexB++;  
        }  
  
        return evenContentArr;  
    }  
    ```  
  
3.  W `TestSearchTask` klasy, zaktualizuj `OnStartSearch` metodę z następującym kodem. Ta zmiana aktualizuje kodu do obsługi filtra.  
  
    ```csharp  
    protected override void OnStartSearch()  
    {  
        // Use the original content of the text box as the target of the search.   
        var separator = new string[] { Environment.NewLine };  
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);  
  
        // Get the search option.   
        bool matchCase = false;  
        matchCase = m_toolWindow.MatchCaseOption.Value;  
  
        // Set variables that are used in the finally block.  
        StringBuilder sb = new StringBuilder("");  
        uint resultCount = 0;  
        this.ErrorCode = VSConstants.S_OK;  
  
        try  
        {  
            string searchString = this.SearchQuery.SearchString;  
  
            // If the search string contains the filter string, filter the content array.   
            string filterString = "lines:\"even\"";  
  
            if (this.SearchQuery.SearchString.Contains(filterString))  
            {  
                // Retain only the even items in the array.  
                contentArr = GetEvenItems(contentArr);  
  
                // Remove 'lines:"even"' from the search string.  
                searchString = RemoveFromString(searchString, filterString);  
            }  
  
            // Determine the results.   
            uint progress = 0;  
            foreach (string line in contentArr)  
            {  
                if (matchCase == true)  
                {  
                    if (line.Contains(searchString))  
                    {  
                        sb.AppendLine(line);  
                        resultCount++;  
                    }  
                }  
                else  
                {  
                    if (line.ToLower().Contains(searchString.ToLower()))  
                    {  
                        sb.AppendLine(line);  
                        resultCount++;  
                    }  
                }  
  
                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
  
                // Uncomment the following line to demonstrate the progress bar.   
                // System.Threading.Thread.Sleep(100);  
            }  
        }  
        catch (Exception e)  
        {  
            this.ErrorCode = VSConstants.E_FAIL;  
        }  
        finally  
        {  
            ThreadHelper.Generic.Invoke(() =>  
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });  
  
            this.SearchResults = resultCount;  
        }  
  
        // Call the implementation of this method in the base class.   
        // This sets the task status to complete and reports task completion.   
        base.OnStartSearch();  
    }  
    ```  
  
4.  Testowanie kodu.  
  
5.  Skompiluj projekt i Rozpocznij debugowanie. W eksperymentalnym wystąpieniu programu Visual Studio Otwórz okno narzędzia, a następnie wybierz Strzałka w dół w formancie wyszukiwania.  
  
     **Wielkość liter** pole wyboru i **wyszukiwanie tylko wiersze nawet** filtru są wyświetlane.  
  
6.  Wybierz filtr.  
  
     Zawiera pole wyszukiwania **wiersze: "nawet"**, i są wyświetlane następujące wyniki:  
  
     dobrym 2  
  
     Dobra 4  
  
     Praktyczny brak jakichkolwiek 6  
  
7.  Usuń `lines:"even"` w polu wyszukiwania wybierz **wielkość liter** pole wyboru, a następnie wprowadź `g` w polu wyszukiwania.  
  
     Zostaną wyświetlone następujące wyniki:  
  
     Przejdź 1  
  
     dobrym 2  
  
     praktyczny brak jakichkolwiek 5  
  
8.  Wybierz X po prawej stronie pola wyszukiwania.  
  
     Wyszukiwanie jest wyczyszczone i pojawi się zawartość oryginalnego. Jednak **wielkość liter** nadal jest zaznaczone pole wyboru.