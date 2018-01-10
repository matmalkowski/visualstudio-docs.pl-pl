---
title: "Wskazówki: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 1ca2e83bab05c336f4b4ed37a13271c636b457dc
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="walkthrough-creating-editing-and-maintaining-a-coded-ui-test"></a>Wskazówki: tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika
Podręcznik pozwala utworzyć prostą aplikację Windows Presentation Foundation (WPF) do przedstawienia sposobu tworzenia, edytowania i utrzymywania kodowanego testu interfejsu użytkownika. Dostarcza on rozwiązania do korekcji testów, które zostały uszkodzone przez różne problemy związane z czasem i refaktoryzacją kontroli.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Oprócz przewodnika potrzeba:  
  
-   Visual Studio Enterprise  
  
### <a name="create-a-simple-wpf-application"></a>Tworzenie prostej aplikacji WPF  
  
1.  Na **pliku** menu wskaż **nowy**, a następnie wybierz **projektu**.  
  
     **Nowy projekt** zostanie wyświetlone okno dialogowe.  
  
2.  W **zainstalowana** okienku rozwiń **Visual C#**, a następnie wybierz **pulpitu systemu Windows**.  
  
3.  Nad środkowym okienku, sprawdź, czy na liście rozwijanej framework docelowy jest ustawiony na **.NET Framework 4.5**.  
  
4.  W środkowym okienku wybierz **aplikacji WPF** szablonu.  
  
5.  W **nazwa** polu tekstowym **SimpleWPFApp**.  
  
6.  Wybierz folder, w którym zapiszesz projekt. W **lokalizacji** tekstu wpisz nazwę folderu.  
  
7.  Wybierz **OK**.  
  
     Zostanie otwarty program The WPF Designer for Visual Studio i pojawi się główne okno projektu.  
  
8.  Jeśli przybornik nie jest otwarty, otwórz go. Wybierz **WIDOKU** menu, a następnie wybierz pozycję **przybornika**.  
  
9. W obszarze **wszystkich kontrolek WPF** sekcji, przeciągnij **przycisk**, **wyboru** i **ProgressBar** formant na właściwości MainWindow w projekcie powierzchni.  
  
10. Zaznacz formant przycisku. W oknie Właściwości zmień wartość atrybutu **nazwa** właściwość z \<bez nazwy > Aby button1. Następnie zmień wartość atrybutu **zawartości** właściwości z przycisk Start.  
  
11. Zaznacz formant paska postępu. W oknie Właściwości zmień wartość dla **nazwa** właściwość z \<bez nazwy > Aby progressBar1. Następnie zmień wartość atrybutu **maksymalna** właściwość z **100** do **10000**.  
  
12. Zaznacz formant pola wyboru. W oknie Właściwości zmień wartość atrybutu **nazwa** właściwość z \<bez nazwy > pole wyboru 1 i wyczyść **IsEnabled** właściwości.  
  
     ![Aplikacja WPF proste](../test/media/codedui_wpfapp.png "CodedUI_WPFApp")  
  
13. Kliknij dwukrotnie dodać obsługi zdarzeń kliknięcia formantu przycisku.  
  
     MainWindow.xmal.cs jest wyświetlany w edytorze kodu, z kursorem w nowej metodzie button1_Click.  
  
14. W górnej części klasy MainWindow dodaj delegata. Delegat będzie używany dla paska postępu. Aby dodać delegata, dodaj następujący kod:  
  
    ```csharp  
    public partial class MainWindow : Window  
    {  
            private delegate void ProgressBarDelegate(System.Windows.DependencyProperty dp, Object value);          
  
        public MainWindow()  
        {  
  
            InitializeComponent();  
        }  
  
    ```  
  
15. W metodzie button1_Click dodaj następujący kod:  
  
    ```csharp  
    private void button1_Click(object sender, RoutedEventArgs e)  
    {  
        double progress = 0;  
  
        ProgressBarDelegate updatePbDelegate =  
            new ProgressBarDelegate(progressBar1.SetValue);  
  
        do  
        {  
            progress ++;  
  
            Dispatcher.Invoke(updatePbDelegate,  
                System.Windows.Threading.DispatcherPriority.Background,  
                new object[] { ProgressBar.ValueProperty, progress });  
            progressBar1.Value = progress;  
        }  
        while (progressBar1.Value != progressBar1.Maximum);  
  
        checkBox1.IsEnabled = true;  
    }  
  
    ```  
  
16. Zapisz plik.  
  
### <a name="verify-the-wpf-application-runs-correctly"></a>Weryfikowanie prawidłowego uruchamiania aplikacji WPF  
  
1.  Na **debugowania** menu, wybierz opcję **Rozpocznij debugowanie** lub naciśnij klawisz **F5**.  
  
2.  Zwróć uwagę, że kontrolka pola wyboru jest wyłączona. Wybierz **Start**.  
  
     W ciągu kilku sekund pasek postępu powinien być zapełniony w 100%.  
  
3.  Możesz teraz wybrać kontrolkę pola wyboru.  
  
4.  Zamknij aplikację SimpleWPFApp.  
  
### <a name="create-and-run-a-coded-ui-test-for-simplewpfapp"></a>Tworzenie i uruchamianie kodowanego testu interfejsu użytkownika dla aplikacji SimpleWPFApp  
  
1.  Zlokalizuj aplikacji SimpleWPFApp, który został utworzony wcześniej. Domyślnie aplikacja będzie znajdować się w lokalizacji C:\Users\\< nazwa_użytkownika\>\Documents\Visual Studio \<wersji > \Projects\SimpleWPFApp\SimpleWPFApp\bin\Debug\SimpleWPFApp.exe  
  
2.  Utwórz na pulpicie skrót do aplikacji SimpleWPFApp. Kliknij prawym przyciskiem myszy SimpleWPFApp.exe i wybierz polecenie **kopiowania**. Na pulpicie kliknij prawym przyciskiem myszy i wybierz polecenie **Wklej skrót**.  
  
    > [!TIP]
    >  Skrót do aplikacji ułatwia dodawanie lub modyfikowanie kodowanych testów interfejsu użytkownika dla aplikacji, ponieważ pozwala to na szybkie uruchamianie aplikacji.  
  
3.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy rozwiązanie, wybierz **Dodaj** , a następnie wybierz **nowy projekt**.  
  
     **Dodawanie nowego projektu** zostanie wyświetlone okno dialogowe.  
  
4.  W **zainstalowana** okienku rozwiń **Visual C#**, a następnie wybierz **testu**.  
  
5.  W środkowym okienku wybierz **kodowanego interfejsu użytkownika projektu testowego** szablonu.  
  
6.  Wybierz **OK**.  
  
     W Eksploratorze rozwiązań, nowe kodowanego interfejsu użytkownika testu projektu o nazwie **CodedUITestProject1** zostanie dodany do rozwiązania.  
  
     **Generuj kod dla kodowanego testu interfejsu użytkownika** zostanie wyświetlone okno dialogowe.  
  
7.  Wybierz **Rejestruj akcje, Edytuj mapę interfejsu użytkownika lub Dodaj asercje** opcję i wybierz polecenie **OK**.  
  
     UIMap — Konstruktor kodowanego testu interfejsu użytkownika zostanie wyświetlony, a okno programu Visual Studio jest zminimalizowany.  
  
     Aby uzyskać więcej informacji na temat opcji w oknie dialogowym, zobacz [tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
8.  Wybierz **Rozpocznij rejestrowanie** na UIMap - kodowanego testu interfejsu użytkownika.  
  
     ![Rozpocznij nagrywanie](../test/media/cuit_builder_record.png "CUIT_Builder_Record")  
  
     Można wstrzymać rejestrowania, jeśli to konieczne, na przykład jeśli masz radzenia sobie z poczty przychodzącej.  
  
     ![Wstrzymanie nagrywania](../test/media/cuit_.png "CUIT_")  
  
    > [!WARNING]
    >  Wszystkie akcje wykonywane na pulpicie będą rejestrowane. Wstrzymanie nagrywania, wykonywania działań, które mogą prowadzić do włączenia rejestrowania danych poufnych.  
  
9. Uruchom SimpleWPFApp za pomocą skrótu na pulpicie.  
  
     Jak wcześniej Zwróć uwagę, że kontrolkę pola wyboru jest wyłączona.  
  
10. Na SimpleWPFApp, wybierz **Start**.  
  
     W ciągu kilku sekund pasek postępu powinien być zapełniony w 100%.  
  
11. Zaznacz kontrolkę pola wyboru, która jest teraz włączony.  
  
12. Zamknij aplikację SimpleWPFApp.  
  
13. Na UIMap — Konstruktor kodowanego testu interfejsu użytkownika, wybierz **Generuj kod**.  
  
14. W polu wpisz nazwę metody **SimpleAppTest** i wybierz polecenie **Dodaj i Generuj**. W ciągu kilku sekund Kodowany test interfejsu użytkownika pojawi się i będzie dodany do rozwiązania.  
  
15. Zamknij UIMap - kodowanego testu interfejsu użytkownika.  
  
     Plik CodedUITest1.cs pojawi się w edytorze kodu.  
  
16. Zapisz projekt.  
  
### <a name="run-the-coded-ui-test"></a>Uruchamianie kodowanego testu interfejsu użytkownika.  
  
1.  Z **testu** menu, wybierz **Windows** , a następnie wybierz **Eksploratora testów**.  
  
2.  Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.  
  
3.  W pliku CodedUITest1.cs Znajdź **CodedUITestMethod** metody, kliknij prawym przyciskiem myszy i wybierz **Uruchom testy**, lub uruchom test z Eksploratora testów.  
  
     Podczas wykonywania kodowanego przebiegu testu interfejsu użytkownika aplikacja SimpleWPFApp jest widoczna. Wykonuje ona działania, których nie było w poprzedniej procedurze. Jednak gdy test próbuje zaznacz pole wyboru dla formantu pole wyboru, okno wyników testu pokazuje, że testowanie nie powiodło się. To jest, ponieważ test próbuje zaznacz pole wyboru, ale nie jest pamiętać, że kontrolka pola wyboru jest wyłączone, aż pasek postępu jest wykonane w 100%. Problem można rozwiązać i podobne problemy przy użyciu różnych `UITestControl.WaitForControlXXX()` metod, które są dostępne dla kodowanych testów UI. Następna procedura zostaną przedstawione za pomocą `WaitForControlEnabled()` metodę, aby rozwiązać ten problem, który spowodował niepowodzenie tego testu. Aby uzyskać więcej informacji, zobacz [tworzenie kodowanego interfejsu użytkownika testy oczekiwania dla określonych zdarzeń podczas odtwarzania](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).  
  
### <a name="edit-and-rerun-the-coded-ui-test"></a>Edytowanie i ponowne uruchamianie kodowanego testu interfejsu użytkownika  
  
1.  W oknie Eksploratora testów wybierz testu nie powiodło się i w **ślad stosu** wybierz pierwszy link do **UIMap.SimpleAppTest()**.  
  
2.  Plik UIMap.Designer.cs otwiera się z punktem błędu wyróżnionego w kodzie:  
  
    ```csharp  
  
    // Select 'CheckBox' check box  
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;  
    ```  
  
3.  Aby rozwiązać ten problem, należy wybrać kodowanego testu interfejsu użytkownika, poczekaj, aż formant wyboru włączenia przed kontynuowaniem się przy użyciu tego wiersza `WaitForControlEnabled()` metody.  
  
    > [!WARNING]
    >  Nie należy modyfikować pliku UIMap.Designer.cs. Wszelkie zmiany kodu wprowadzone w pliku UIMapDesigner.cs zostaną każdorazowo zastąpione przy generowaniu kodu za pomocą UIMap — Konstruktora kodowanego testu interfejsu użytkownika. Jeśli trzeba zmodyfikować nagraną metodę, należy skopiować ją do pliku UIMap.cs i zmienić jej nazwę. Plik UIMap.cs może służyć do zastępowania metod i właściwości w pliku UIMapDesigner.cs. Musisz usunąć odwołanie do oryginalnej metody w pliku Coded UITest.cs, a następnie zastąpić je zmienioną nazwą metody.  
  
4.  W Eksploratorze rozwiązań, Znajdź **UIMap.uitest** w projekcie kodowanego testu interfejsu użytkownika.  
  
5.  Otwórz menu skrótów **UIMap.uitest** i wybierz polecenie **Otwórz**.  
  
     Kodowany test interfejsu użytkownika jest wyświetlany w Edytorze kodowanego testu interfejsu użytkownika. Teraz można wyświetlać i edytować kodowany test interfejsu użytkownika.  
  
6.  W **akcji IU** okienku, wybierz metody testowej (SimpleAppTest), który chcesz przenieść plik UIMap.cs lub UIMap.vb ułatwiające funkcję kodu niestandardowego, która nie będzie zastąpione, gdy kod testu jest ponownie kompilowana.  
  
7.  Wybierz **Przenieś kod** przycisk na pasku narzędzi edytora testu interfejsu użytkownika na stałe.  
  
8.  Pojawi się okno dialogowe programu Microsoft Visual Studio. Zawiera ono ostrzeżenie, że metoda ta ma zostać przeniesiona z pliku UIMap.uitest do pliku UIMap.cs i nie będzie już można edytować metody za pomocą Edytora kodowanego testu interfejsu użytkownika. Wybierz **tak**.  
  
     Metoda testu jest usuwana z pliku UIMap.uitest i nie jest już wyświetlana w okienku Akcje interfejsu użytkownika. Aby edytować przeniesiony plik testowy, otwórz plik UIMap.cs w Eksploratorze rozwiązań.  
  
9. Na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wybierz **zapisać**.  
  
     Aktualizacje do metody testowej są zapisywane w pliku UIMap.Designer.  
  
    > [!CAUTION]
    >  Po przeniesieniu metody nie będzie można edytować jej za pomocą Edytora kodowanego testu interfejsu użytkownika. Należy dodać niestandardowy kod i obsługiwać go za pomocą Edytora kodu.  
  
10. Zmień nazwę metody z `SimpleAppTest()` do`ModifiedSimpleAppTest()`  
  
11. Dodaj następującą instrukcję using do pliku:  
  
    ```csharp  
  
    using Microsoft.VisualStudio.TestTools.UITesting.WpfControls;  
  
    ```  
  
12. Dodaj następujące `WaitForControlEnabled()` metody przed ataku wiersz kodu zidentyfikowane wcześniej:  
  
    ```csharp  
  
              uICheckBoxCheckBox.WaitForControlEnabled();  
  
    // Select 'CheckBox' check box  
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;  
  
    ```  
  
13. W pliku CodedUITest1.cs Znajdź **CodedUITestMethod** — metoda i albo komentarz lub zmień nazwę odwołania do oryginalnej metody SimpleAppTest() i zastąp go ModifiedSimpleAppTest() nowe:  
  
    ```csharp  
    [TestMethod]  
            public void CodedUITestMethod1()  
            {  
                // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
                // For more information on generated code, see http://go.microsoft.com/fwlink/?LinkId=179463  
                //this.UIMap.SimpleAppTest();  
                this.UIMap.ModifiedSimpleAppTest();  
            }  
  
    ```  
  
14. Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.  
  
15. Kliknij prawym przyciskiem myszy **CodedUITestMethod** metodę i wybierz **Uruchom testy**.  
  
16. Teraz kodowanego testu interfejsu użytkownika pomyślnym zakończeniu wszystkich kroków testu i **przekazanego** jest wyświetlany w oknie Eksploratora testów.  
  
### <a name="refactor-a-control-in-the-simplewpfapp"></a>Reorganizacja formantu w aplikacji SimpleWPFApp  
  
1.  W pliku MainWindow.xaml w Projektancie zaznacz formant przycisku.  
  
2.  W górnej części okna właściwości, należy zmienić **nazwa** wartość właściwości z button1 buttonA.  
  
3.  Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.  
  
4.  W Eksploratorze testów, uruchom **CodedUITestMethod1**.  
  
     Test zakończy się niepowodzeniem, ponieważ w UIMap jako button1 kodowany test interfejsu użytkownika nie można znaleźć formantu przycisku, który pierwotnie był mapowany. Refaktoryzacja może w ten sposób wpłynąć na kodowane testy interfejsu użytkownika.  
  
5.  W oknie Eksploratora testów w **ślad stosu** wybierz pierwszy link obok pozycji **(UIMpa.ModifiedSimpleAppTest)**.  
  
     Otwiera plik UIMap.cs. Punkt błędu jest wyróżniany w kodzie:  
  
    ```csharp  
  
    // Click 'Start' button  
    Mouse.Click(uIStartButton, new Point(27, 10));  
    ```  
  
     Należy zauważyć, że wiersz kodu we wcześniejszej części tej procedury jest przy użyciu `UiStartButton`, która jest nazwą UIMap przed jego został zrefaktoryzowany.  
  
     Aby rozwiązać ten problem, można dodać wycofany formant do UIMap za pomocą Konstruktora kodowanego testu interfejsu użytkownika. Należy zaktualizować kod testu do kodu, jak pokazano w następnej procedurze.  
  
### <a name="map-refactored-control-and-edit-and-rerun-the-coded-ui-test"></a>Mapowanie wycofanej kontroli i edycji oraz ponowne przeprowadzenie kodowanego testu interfejsu użytkownika  
  
1.  W pliku CodedUITest1.cs w **CodedUITestMethod1()** metoda, kliknij prawym przyciskiem myszy, wybierz opcję **Generuj kod dla kodowanego testu interfejsu użytkownika** , a następnie wybierz **konstruktora kodowanego testu interfejsu użytkownika używana**.  
  
     Pojawi się UIMap — Konstruktor kodowanego testu interfejsu użytkownika.  
  
2.  Za pomocą skrótu na pulpicie został utworzony wcześniej, uruchom aplikację SimpleWPFApp utworzony wcześniej.  
  
3.  Przeciągnij narzędzie krzyżyk, aby na UIMap — Konstruktor kodowanego testu interfejsu użytkownika, **Start** przycisk na SimpleWPFApp.  
  
     **Start** przycisku jest ujęta w polu niebieska i konstruktora kodowanego testu interfejsu użytkownika zajmuje kilka sekund do przetwarzania danych dla wybranej kontrolki i wyświetla właściwości kontrolki. Zwróć uwagę, że **AutomationUId** nosi nazwę **buttonA**.  
  
4.  We właściwościach formantu wybierz strzałkę w lewym górnym rogu, aby rozwinąć Mapę formantów UI. Zwróć uwagę, że **UIStartButton1** jest zaznaczone.  
  
5.  Na pasku narzędzi wybierz **Dodaj formant do mapy formantów interfejsu użytkownika**.  
  
     Stan w dolnej części okna sprawdza akcji, wyświetlając **zaznaczony formant został dodany do mapy formantów interfejsu użytkownika**.  
  
6.  Na UIMap — Konstruktor kodowanego testu interfejsu użytkownika, wybierz **Generuj kod**.  
  
     Kodowany konstruktora testu interfejsu użytkownika — generowanie kodu występuje z notatki z informacją, że żadna nowa metoda jest wymagana i że kod zostanie wygenerowany tylko zmiany mapy formantów interfejsu użytkownika.  
  
7.  Wybierz **Generowanie**.  
  
8.  Zamknij aplikację SimpleWPFApp.exe.  
  
9. Zamknij UIMap — Konstruktor kodowanego interfejsu użytkownika testu.  
  
     UIMap — Konstruktor kodowanego testu interfejsu użytkownika zajmuje kilka sekund procesu formantu interfejsu użytkownika mapowania zmiany.  
  
10. W Eksploratorze rozwiązań otwórz plik UIMap.Designer.cs.  
  
11. W pliku UIMap.Designer.cs zlokalizować właściwości UIStartButton1. Powiadomienie `SearchProperties` ma ustawioną wartość `"buttonA"`:  
  
    ```csharp  
  
    public WpfButton UIStartButton1  
            {  
                get  
                {  
                    if ((this.mUIStartButton1 == null))  
                    {  
                        this.mUIStartButton1 = new WpfButton(this);  
                        #region Search Criteria  
                        this.mUIStartButton1.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";  
                        this.mUIStartButton1.WindowTitles.Add("MainWindow");  
                        #endregion  
                    }  
                    return this.mUIStartButton1;  
                }  
            }  
  
    ```  
  
     Teraz można zmodyfikować kodowany test interfejsu użytkownika do korzystania z ostatnio mapowanego formantu. Jak wskazano w poprzedniej procedurze, aby zastąpić jakąkolwiek metodę lub właściwości w kodowanym teście interfejsu użytkownika, należy to zrobić w pliku UIMap.cs.  
  
12. W pliku UIMap.cs, dodaj konstruktor, a następnie określ `SearchProperties` właściwość `UIStartButton` właściwości do użycia `AutomationID` właściwość z wartością`"buttonA":`  
  
    ```csharp  
  
    public UIMap()  
            {  
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";  
            }  
  
    ```  
  
13. Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.  
  
14. W Eksploratorze testów Uruchom CodedUITestMethod1.  
  
     Tym razem kodowany test interfejsu użytkownika pomyślnie zakończy wszystkie etapy testu.  W oknie wyników testu, pojawi się stan **przekazanego**.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
### <a name="videos"></a>Wideo  
 ![łącze do wideo](../data-tools/media/playvideo.gif "PlayVideo") [kodowanego interfejsu użytkownika testów-DeepDive-Episode1-GettingStarted](http://go.microsoft.com/fwlink/?LinkID=230573)  
  
 ![łącze do wideo](../data-tools/media/playvideo.gif "PlayVideo") [kodowanego interfejsu użytkownika testów-DeepDive-Episode2-MaintainenceAndDebugging](http://go.microsoft.com/fwlink/?LinkID=230574)  
  
 ![łącze do wideo](../data-tools/media/playvideo.gif "PlayVideo") [kodowanego interfejsu użytkownika testów-DeepDive-Episode3-HandCoding](http://go.microsoft.com/fwlink/?LinkID=230575)  
  
### <a name="hands-on-lab"></a>Ćwiczenia praktyczne  
 [Wirtualne laboratorium MSDN: Wprowadzenie do tworzenia kodowanych testów interfejsu użytkownika z programu Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkID=22508)  
  
### <a name="faq"></a>Najczęściej zadawane pytania  
 [Kodowanych testów interfejsu użytkownika — często zadawane pytania - 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Kodowanych testów interfejsu użytkownika — często zadawane pytania -2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>Forum  
 [Visual Studio automatyzacji testów UI (w tym CodedUI)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
 [Wprowadzenie do projektanta WPF](http://msdn.microsoft.com/en-us/18e61d03-b96a-4058-a166-8ec6b3f6116b)   
 [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Edytowanie kodowanych testów interfejsu użytkownika za pomocą edytora kodowanych testów interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
