---
title: Tworzenie dodatku Visual Studio dla przeglądarki wyników testu wydajności sieci Web | Dokumentacja firmy Microsoft
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, Visual Studio Add-in
- Visual Studio Add-in, Web performance tests
ms.assetid: 1118c604-4b1b-4b21-a04e-45995b676fa8
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: aa163381415060d189899e7defd64a8935c4ea94
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-visual-studio-add-in-for-the-web-performance-test-results-viewer"></a>Porady: tworzenie dodatku Visual Studio dla przeglądarki wyników testu wydajności sieci Web

Rozszerzenie z interfejsu użytkownika dla przeglądarki wyników testu wydajności sieci Web, korzystając z następujących przestrzeni nazw:

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting>

-   <xref:Microsoft.VisualStudio.TestTools.WebTesting>

Ponadto musisz dodać odwołanie do biblioteki DLL LoadTestPackage, który znajduje się w *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies* folderu.

-   Aby rozszerzyć przeglądarka wyników testu wydajności sieci Web interfejsu użytkownika, należy utworzyć dodatku programu Visual Studio i kontrolki użytkownika. W poniższych procedurach opisano sposób tworzenia dodatku, kontrolki użytkownika i implementowania klas należy rozszerzyć przeglądarka wyników testu wydajności sieci Web interfejsu użytkownika.

## <a name="create-or-open-a-solution-that-contains-an-aspnet-web-application-and-a-web-performance-and-load-test-project"></a>Utwórz lub Otwórz rozwiązanie, które zawiera aplikacji sieci Web ASP.NET i wydajności sieci Web i projektu testu obciążenia

### <a name="to-prepare-for-extending-the-web-performance-test-results-viewer"></a>Aby przygotować się do rozszerzania przeglądarka wyników testu wydajności sieci Web

Należy utworzyć lub otworzyć rozwiązanie nieprodukcyjnych, że możesz eksperymentować z zawierającą aplikację sieci Web ASP.NET i wydajności sieci Web i obciążenia projekt testowy z jednego lub więcej testów wydajności sieci Web dla aplikacji sieci Web ASP.NET.

> [!NOTE]
> Można utworzyć aplikację sieci Web ASP.NET i wydajności sieci Web i testów obciążenia projekt zawierający testy wydajności sieci Web zgodnie z instrukcjami opisanymi w [porady: tworzenie testów usług sieci Web](../test/how-to-create-a-web-service-test.md) i [Generowanie i uruchamianie kodowanego sieci web test wydajności](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="create-a-visual-studio-add-in"></a>Tworzenie dodatku Visual Studio

Dodatek jest skompilowanej biblioteki DLL, która działa w programie Visual Studio zintegrowane środowisko programistyczne (IDE). Kompilacja pomaga w ochronie własności intelektualnej i zwiększa wydajność. Mimo że można tworzyć ręcznie dodatków, użytkownik może ułatwić za pomocą kreatora Add-In. Ten kreator tworzy funkcjonalności, ale podstawowe dodatku uruchomienia natychmiast po jego utworzeniu. Po Kreator dodatku generuje program podstawowe, możesz Dodaj kod, aby go i dostosować go.

 Kreator dodatków pozwala podać nazwę wyświetlaną i opis dla dodatku. Będzie znajdować się w **Menedżera dodatków**. Opcjonalnie, masz kod Generuj kreatora, który dodaje do **narzędzia** menu polecenie, aby otworzyć dodatku. Można również wyświetlić niestandardowego **o** okno dialogowe dla dodatku. Po zakończeniu działania kreatora, masz nowy projekt, który ma tylko jedną klasę, która implementuje dodatku. Tej klasy, nosi nazwę połączenia.

 Użyjesz **Menedżera dodatków** na końcu tego tematu.

### <a name="to-create-an-add-in-by-using-the-add-in-wizard"></a>Aby utworzyć dodatku za pomocą Kreatora dodatku

1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy rozwiązanie, wybierz **Dodaj** , a następnie wybierz **nowy projekt**.

     Zostanie wyświetlone okno dialogowe Nowy projekt.

2.  W obszarze **zainstalowane szablony**, rozwiń węzeł **inne typy projektów** i wybierz **rozszerzalności**.

3.  Na liście szablonów wybierz **dodatku Visual Studio**.

4.  W obszarze Nazwa wpisz nazwę dla dodatku. Na przykład **WebPerfTestResultsViewerAddin**.

5.  Wybierz **OK**.

     Zostanie uruchomiony Kreator dodatku Visual Studio.

6.  Wybierz **dalej**.

7.  Na **wybierz język programowania** wybierz język programowania, którego chcesz użyć, aby zapisać dodatku.

    > [!NOTE]
    > W tym temacie używa języka Visual C# przykładowy kod.

8.  Na **wybierz hosta aplikacji** wybierz **programu Visual Studio** i wyczyść **programu Visual Studio makra**.

9. Wybierz **dalej**.

10. Wpisz nazwę i opis dla dodatku na **wprowadź nazwę i opis** strony.

     Po dodatku, jego nazwa i opis są wyświetlane w **dostępne dodatki** na liście **Menedżera dodatków**. Dodaj wystarczającej liczby szczegółów Opis dodatku, dzięki czemu użytkownicy mogą dowiedzieć się, jakie dodatek nie, jak działa i tak dalej.

11. Wybierz **dalej**.

12. Na **wybierz dodatku opcje** wybierz pozycję **chcę Moje dodatku załadować podczas uruchamiania aplikacji hosta**.

13. Usuń zaznaczenie pola wyboru pozostałych.

14. Na **Wybieranie pomocy o informacje** strony, możesz można określić, czy informacje o dodatek mają być wyświetlane w **o** okno dialogowe. Informacje do wyświetlenia, zaznacz **tak, chcę Moje dodatku do zaoferowania "Informacje" pole** pole wyboru.

     Informacje, które mogą być dodawane do programu Visual Studio **o** okno dialogowe zawiera numer wersji, szczegóły dotyczące obsługi danych licencyjnych i tak dalej.

15. Wybierz **dalej**.

16. Wybrane opcje są wyświetlane na **Podsumowanie** strony możesz się zapoznać. Jeśli masz pewność, wybierz **Zakończ** można utworzyć dodatku. Jeśli chcesz zmienić, wybierz **ponownie** przycisku.

     Tworzenia nowego rozwiązania i projektu i pliku Connect.cs nowego dodatku jest wyświetlany w edytorze kodu.

     Dodasz kod do pliku Connect.cs po następującej procedury, która tworzy kontrolkę użytkownika, który będzie się odwoływać ten projekt WebPerfTestResultsViewerAddin.

 Po dodatku został utworzony, musi być zarejestrowany z programem Visual Studio przed aktywowaniem w **Menedżera dodatków**. Można to zrobić przy użyciu pliku XML, który ma rozszerzenie nazwy pliku .addin.

 Plik .addin zawiera opis informacji Visual Studio wymaga, aby wyświetlić w dodatku **Menedżera dodatków**. Po uruchomieniu programu Visual Studio wygląda w lokalizacji plików .addin żadnych plików .addin dostępne. Jeśli znajdzie żadnego odczytuje plik XML i daje **Menedżera dodatków** informacje, które wymaga, aby uruchomić dodatek po kliknięciu.

 Plik .addin jest tworzona automatycznie podczas tworzenia dodatku za pomocą Kreatora dodatku.

### <a name="add-in-file-locations"></a>Lokalizacje plików dodatku

Dwie kopie plików .addin są tworzone automatycznie przez kreatora dodatku w następujący sposób:

|**. Lokalizacja pliku dodatku**|**Opis**|
|------------------------------|----------------------------|---------------------|
|Folder główny projektu|Używane do wdrażania projektu dodatku. Dołączony do projektu w celu ułatwienia edycji i ma ścieżkę lokalną na potrzeby wdrażania XCopy stylu.|
|Dodaj w folderze|Używane do uruchamiania dodatku w środowisku debugowania. Zawsze powinna wskazywać ścieżka wyjściowa bieżącej konfiguracji kompilacji.|

## <a name="create-a-windows-form-control-library-project"></a>Tworzenie projektu biblioteki kontrolki formularza systemu Windows

Visual Studio dodatek utworzony w poprzedniej procedurze odwołuje się do projektu Biblioteka formantów formularzy systemu Windows, aby utworzyć wystąpienie <xref:System.Windows.Forms.UserControl> klasy.

### <a name="to-create-a-control-to-be-used-in-the-web-test-results-viewer"></a>Aby utworzyć formant do użycia w przeglądarce wyników testu sieci Web

1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy rozwiązanie, wybierz **Dodaj** , a następnie wybierz **nowy projekt**.

     **Nowy projekt** zostanie wyświetlone okno dialogowe.

2.  W obszarze **zainstalowane szablony**, rozwiń węzeł **albo Visual Basic** lub **Visual C#** i wybierz **Windows**.

    > [!NOTE]
    > W tym temacie używa języka Visual C# przykładowy kod.

3.  Na liście szablonów wybierz **Biblioteka formantów formularzy systemu Windows**.

4.  W obszarze **nazwa**, wpisz nazwę dla dodatku. Na przykład **WebPerfTestResultsViewerControl**.

5.  Wybierz **OK**.

     Projektu biblioteki formantu formularzy systemu Windows, dodane w Eksploratorze rozwiązań i UserControl1.cs WebPerfTestResultsViewerControl jest wyświetlany w trybie projektowania.

6.  Przeciągnij z przybornika, <xref:System.Windows.Forms.DataGridView> na powierzchnię userControl1.

7.  Kliknij akcję symbolu tagu (![symbol tagu inteligentnego](../test/media/vs_winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> i wykonaj następujące czynności:

    1.  Wybierz **Zadokuj w kontenerze nadrzędnym**.

    2.  Usuń zaznaczenie pól wyboru dla **Włącz dodawanie**, **Włącz edytowanie**, **Włącz usuwanie** i **Włączanie zmiany układu kolumn**.

    3.  Wybierz **dodać kolumny**.

         **Dodaj kolumnę** zostanie wyświetlone okno dialogowe.

    4.  W **typu** listy rozwijanej wybierz **DataGridViewTextBoxColumn**.

    5.  Usuń wartość tekstową "Kolumna1" w **tekst nagłówka**.

    6.  Wybierz **dodać**.

    7.  Wybierz **Zamknij**.

8.  W oknie Właściwości zmień **(nazwa)** właściwość <xref:System.Windows.Forms.DataGridView> do **resultControlDataGridView**.

9. Kliknij prawym przyciskiem myszy projekt powierzchni i wybierz pozycję **kod widoku**.

     Plik UserControl1.cs jest wyświetlany w edytorze kodu.

10. Zmiana nazwy wystąpień <xref:System.Windows.Forms.UserControl> klasy z UserContro1 resultControl:

    ```csharp
    namespace WebPerfTestResultsViewerControl
    {
        public partial class resultControl : UserControl
        {
            public resultControl()
            {
                InitializeComponent();
            }
    ```

     W następnej procedurze kodu zostaną dodane do projektu WebPerfTestResultsViewerAddin Connect.cs pliku, który będzie odwoływać się do klasy resultControl.

     Dodasz dodatkowy kod do pliku Connect.cs później.

## <a name="add-code-to-the-webperftestresultsvieweraddin"></a>Dodaj kod, aby WebPerfTestResultsViewerAddin

### <a name="to-add-code-to-the-visual-studio-add-in-to-extend-the-web-test-results-viewer"></a>Aby dodać kod do dodatku Visual Studio Aby rozszerzyć przeglądarka wyników testu sieci Web

1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **odwołania** węzeł w WebPerfTestResultsViewerAddin projektu i wybierz **Dodaj odwołanie**.

2.  W **Dodaj odwołanie** oknie dialogowym wybierz **.NET** kartę.

3.  Przewiń w dół i wybierz **Microsoft.VisualStudio.QualityTools.WebTestFramework** i **System.Windows.Forms**.

4.  Wybierz **OK**.

5.  Kliknij prawym przyciskiem myszy **odwołania** ponownie, a następnie wybierz węzeł **Dodaj odwołanie**.

6.  W **Dodaj odwołanie** oknie dialogowym wybierz **Przeglądaj** kartę.

7.  Wybierz z listy rozwijanej dla **Szukaj w** i przejdź do % ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies i wybierz Microsoft.VisualStudio.QualityTools.LoadTestPackage.dll plik.

8.  Wybierz **OK**.

9. Kliknij prawym przyciskiem myszy węzeł projektu WebPerfTestResultsViewerAddin, a następnie wybierz **Dodaj odwołanie**.

10. W **Dodaj odwołanie** oknie dialogowym wybierz **projekty** kartę.

11. W obszarze **Nazwa projektu**, wybierz pozycję **WebPerfTestResultsViewerControl** projekt i wybierz pozycję **OK**.

12. Jeśli plik Connect.cs nie jest jeszcze otwarty, w Eksploratorze rozwiązań, kliknij prawym przyciskiem myszy **Connect.cs** pliku w projekcie WebPerfTestResultsViewerAddin i wybierz **kod widoku**.

13. W pliku Connect.cs Dodaj następujące instrukcje Using:

    ```csharp
    using System.IO;
    using System.Windows.Forms;
    using System.Collections.Generic;
    using Microsoft.VisualStudio.TestTools.LoadTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using WebPerfTestResultsViewerControl;
    ```

14. Przewiń w dół pliku Connect.cs. Należy dodać listę identyfikatorów GUID dla <xref:System.Windows.Forms.UserControl> w przypadku więcej niż jedno wystąpienie przeglądarka wyników testu wydajności sieci Web jest otwarty. Należy dodać później kod, który używa tej listy.

     Listę drugi ciąg jest używany w metodzie OnDiscconection, który zostanie później kodem.

    ```csharp
    private DTE2 _applicationObject;
    private AddIn _addInInstance;

    private Dictionary<Guid, List<UserControl>> m_controls = new Dictionary<Guid, List<UserControl>>();        private List<string> temporaryFilePaths = new List<string>();
    ```

15. Plik Connect.cs tworzy wystąpienie klasy o nazwie Połącz z <xref:Extensibility.IDTExtensibility2> klasy, a także niektóre metody wdrażania dodatku Visual Studio. Jedną z metod jest metody OnConnection, która otrzymuje powiadomienie, że dodatek jest ładowany. W metodzie OnConnection klasy LoadTestPackageExt użyje do utworzenia pakietu rozszerzeń dla przeglądarki wyników testu wydajności sieci Web. Dodaj następujący kod do metody OnConnection:

    ```csharp
    public void OnConnection(object application, ext_ConnectMode connectMode, object addInInst, ref Array custom)
                {
                _applicationObject = (DTE2)application;
                _addInInstance = (AddIn)addInInst;

                // Create a load test packge extensibility class.            LoadTestPackageExt loadTestPackageExt = _applicationObject.GetObject("Microsoft.VisualStudio.TestTools.LoadTesting.LoadTestPackageExt") as LoadTestPackageExt;            // Process open windows.            foreach (WebTestResultViewer webTestResultViewer in loadTestPackageExt.WebTestResultViewerExt.ResultWindows)            {                WindowCreated(webTestResultViewer);            }            // Create event handlers.            loadTestPackageExt.WebTestResultViewerExt.WindowCreated += new EventHandler<WebTestResultViewerExt.WindowCreatedEventArgs>(WebTestResultViewerExt_WindowCreated);            loadTestPackageExt.WebTestResultViewerExt.WindowClosed += new EventHandler<WebTestResultViewerExt.WindowClosedEventArgs>(WebTesResultViewer_WindowClosed);            loadTestPackageExt.WebTestResultViewerExt.SelectionChanged += new EventHandler<WebTestResultViewerExt.SelectionChangedEventArgs>(WebTestResultViewer_SelectedChanged);
            }
    ```

16. Dodaj następujący kod do klasy connect można utworzyć metody WebTestResultViewerExt_WindowCreated dla programu obsługi zdarzeń loadTestPackageExt.WebTestResultViewerExt.WindowCreated, które zostały dodane w metodzie OnConnection i metody WindowCreated który WebTestResultViewerExt_WindowCreated wywołania metody.

    ```csharp
            void WebTestResultViewerExt_WindowCreated(object sender, WebTestResultViewerExt.WindowCreatedEventArgs e)
            {
                // New control added to new result viewer window.
                WindowCreated(e.WebTestResultViewer);
            }

    private void WindowCreated(WebTestResultViewer viewer)        {            // Instantiate an instance of the resultControl referenced in the WebPerfTestResultsViewerControl project.
                resultControl resultControl = new resultControl();            // Add to the dictionary of open playback windows.            System.Diagnostics.Debug.Assert(!m_controls.ContainsKey(viewer.TestResultId));            List<UserControl> userControls = new List<UserControl>();            userControls.Add(resultControl);            // Add Guid to the m_control List to manage Result viewers and controls.            m_controls.Add(viewer.TestResultId, userControls);            // Add tabs to the playback control.            resultControl.Dock = DockStyle.Fill;            viewer.AddResultPage(new Guid(), "Sample", resultControl);        }
    ```

17. Dodaj następujący kod do klasy connect można utworzyć metody WebTestResultViewer_SelectedChanged obsługi zdarzeń loadTestPackageExt.WebTestResultViewerExt.SelectionChanged dodanych w metodzie OnConnection:

    ```csharp
    void WebTestResultViewer_SelectedChanged(object sender, WebTestResultViewerExt.SelectionChangedEventArgs e)
    {
        foreach (UserControl userControl in m_controls[e.TestResultId])            {                // Update the userControl in each result viewer.                resultControl resultControl = userControl as resultControl;                if (resultControl != null)                    // Call the resultControl's Update method (This will be added in the next procedure).                    resultControl.Update(e.WebTestRequestResult);            }
    }
    ```

18. Dodaj następujący kod do klasy connect można utworzyć metody WebTesResultViewer_WindowClosed dla programu obsługi zdarzeń dla loadTestPackageExt.WebTestResultViewerExt.WindowClosed, dodanego w metodzie OnConnection:

    ```csharp
    void WebTesResultViewer_WindowClosed(object sender, WebTestResultViewerExt.WindowClosedEventArgs e)
    {
        if (m_controls.ContainsKey(e.WebTestResultViewer.TestResultId))
        {
            m_controls.Remove(e.WebTestResultViewer.TestResultId);
        }
    }
    ```

     Teraz, kod zakończenia dodatku Visual Studio, konieczne jest dodanie metody aktualizacji do resultControl w w projekcie WebPerfTestResultsViewerControl.

## <a name="add-code-to-the-webperftestresultsviewercontrol"></a>Dodaj kod, aby WebPerfTestResultsViewerControl

### <a name="to-add-code-to-the-user-control"></a>Aby dodać kod do kontrolki użytkownika

1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu WebPerfTestResultsViewerControl i wybierz **właściwości**.

2.  Wybierz **aplikacji** karcie, a następnie wybierz pozycję **platformy docelowej** listy rozwijanej i wybierz **.NET Framework 4** i zamknij właściwości.

     Jest to wymagane w celu zapewnienia obsługi odwołania do biblioteki DLL, które są wymagane przez rozszerzenie przeglądarka wyników testu wydajności sieci Web.

3.  W Eksploratorze rozwiązań w projekcie WebPerfTestResultsViewerControl, kliknij prawym przyciskiem myszy **odwołania** a następnie wybierz węzeł **Dodaj odwołanie**.

4.  W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET** kartę.

5.  Przewiń w dół i wybierz **Microsoft.VisualStudio.QualityTools.WebTestFramework**.

6.  Wybierz **OK**.

7.  W pliku UserControl1.cs Dodaj następujące instrukcje Using:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting.Rules;
    ```

8.  Dodaj metodę aktualizacji, która jest wywoływana przekazany WebTestRequestResult z metody WebPerfTestResultsViewerAddin WebTestResultViewer_SelectedChanged w pliku Connect.cs. Metoda aktualizacji wypełnia różne właściwości przekazany do niego WebTestRequestResult formantu DataGridView.

    ```csharp
    public void Update(WebTestRequestResult WebTestResults)
            {
                // Clear the DataGridView when a request is selected.
                resultControlDataGridView.Rows.Clear();
                // Populate the DataGridControl with properties from the WebTestResults.
                this.resultControlDataGridView.Rows.Add("Request: " + WebTestResults.Request.Url.ToString());
                this.resultControlDataGridView.Rows.Add("Response: " + WebTestResults.Response.ResponseUri.ToString());
                foreach (RuleResult ruleResult in WebTestResults.ExtractionRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Extraction rule results: " + ruleResult.Message.ToString());
                }
                foreach (RuleResult ruleResult in WebTestResults.ValidationRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Validation rule results: " + ruleResult.Message.ToString());
                }
                foreach (WebTestError webTestError in WebTestResults.Errors)
                {
                    this.resultControlDataGridView.Rows.Add("Error: " + webTestError.ErrorType.ToString() + " " + webTestError.ErrorSubtype.ToString() + " " + webTestError.ExceptionText.ToString());
                }
            }
    ```

## <a name="build-the-webperftestresultsvieweraddin-solution"></a>Skompiluj rozwiązanie WebPerfTestResultsViewerAddin

### <a name="to-build-the-solution"></a>Tworzenie rozwiązania

-   Na **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.

## <a name="register-the-webperftestresultsvieweraddin-add-in"></a>Zarejestruj dodatek WebPerfTestResultsViewerAddin

### <a name="to-register-the-add-in-using-the-add-in-manager"></a>Aby zarejestrować dodatek przy użyciu Menedżera dodatków

1.  Na **narzędzia** menu, wybierz opcję **Menedżera dodatków**.

2.  **Menedżera dodatków** zostanie wyświetlone okno dialogowe.

3.  Zaznacz pole wyboru dodatku WebPerfTestResultsViewerAddin w **dostępne dodatki** kolumny i wyczyść zaznaczenie pola wyboru poniżej **uruchamiania** i **wiersza polecenia**kolumn.

4.  Wybierz **OK**.

## <a name="run-the-web-performance-test-using-the-build-the-webperftestresultsvieweraddin-add-in"></a>Uruchamianie testu wydajności sieci Web przy użyciu dodatku WebPerfTestResultsViewerAddin

### <a name="to-run-the-new-vs-add-in-for-the-web-test-results-viewer"></a>Aby uruchomić nowe dodatku VS dla przeglądarki wyników testu sieci Web

1.  Uruchamianie testu wydajności sieci Web i będzie wyświetlany WebPerfTestResultsViewerAddin dodatku nową kartę zatytułowany przykładowe wyświetlane w wydajności sieci Web testów Podgląd wyników.

2.  Wybierz kartę, aby wyświetlić właściwości przedstawionych w formancie DataGridView.

## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework

Aby poprawić bezpieczeństwo przez złośliwe dodatki uniemożliwia automatyczne aktywowanie, program Visual Studio udostępnia ustawienia w **opcje narzędzia** stronę o nazwie **Dodaj w/makra zabezpieczeń**.

Ta strona Opcje pozwala dodatkowo określić foldery, w których wyszukiwania Visual Studio. Pliki rejestracji dodatku. Zwiększa to zabezpieczeń, umożliwiając ograniczyć lokalizacje gdzie. Dodatek rejestracji pliki mogą być odczytywane. Pomaga to zapobiec złośliwe. Pliki addIn przypadkowo używane.

 **Ustawienia zabezpieczeń dodatku**

 Ustawienia na stronie opcji dla dodatku zabezpieczeń są następujące:

-   **Zezwalaj na składniki dodatku do załadowania.** Domyślnie zaznaczone. Po wybraniu dodatków mogą ładować w programie Visual Studio. Nie wybrano dodatki są zabronione obciążenia w programie Visual Studio.

-   **Zezwalaj na składniki dodatku załadować z adresu URL.** Nie są wybrane domyślnie. Po wybraniu dodatków mogą zostać załadowane z zewnętrznych witryn sieci Web. Nie wybrano zdalnego dodatki są zabronione obciążenia w programie Visual Studio. Jeśli z jakiegoś powodu nie można załadować dodatku, następnie go nie można załadować z sieci Web. To ustawienie określa tylko podczas ładowania biblioteki DLL dodatku. . Pliki rejestracji AddIn zawsze musi znajdować się w systemie lokalnym.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.UserControl>
- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.DataGrid>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)