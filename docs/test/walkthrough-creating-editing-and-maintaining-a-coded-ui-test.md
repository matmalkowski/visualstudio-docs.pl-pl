---
title: Tworzenie kodowanego testu interfejsu użytkownika w programie Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 8f811905fb6fed0e0cbc061128622c72bf09fc07
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692330"
---
# <a name="walkthrough-create-edit-and-maintain-a-coded-ui-test"></a>Wskazówki: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika

W tym przewodniku dowiesz się, jak tworzenie, edytowanie i obsługa kodowanego interfejsu użytkownika teście aplikacji Windows Presentation Framework (WPF). Przewodnik zawiera rozwiązania korygowanie testów, które zostały przerwane przez różne problemy dotyczące synchronizacji i refaktoryzacji kontrolek.

## <a name="create-a-wpf-app"></a>Tworzenie aplikacji WPF

1.  Na **pliku** menu wskaż **nowy**, a następnie wybierz **projektu**.

     **Nowy projekt** zostanie wyświetlone okno dialogowe.

2.  W **zainstalowana** okienku rozwiń **Visual C#**, a następnie wybierz **pulpitu systemu Windows**.

3.  Nad środkowym okienku, sprawdź, czy na liście rozwijanej framework docelowy jest ustawiony na **.NET Framework 4.5**.

4.  W środkowym okienku wybierz **aplikacji WPF** szablonu.

5.  W **nazwa** polu tekstowym **SimpleWPFApp**.

6.  Wybierz folder, w którym zapiszesz projekt. W **lokalizacji** tekstu wpisz nazwę folderu.

7.  Wybierz **OK**.

     Zostanie otwarty program The WPF Designer for Visual Studio i pojawi się główne okno projektu.

8.  Jeśli przybornik nie jest otwarty, otwórz go. Wybierz **widoku** menu, a następnie wybierz pozycję **przybornika**.

9. W obszarze **wszystkich kontrolek WPF** sekcji, przeciągnij **przycisk**, **wyboru** i **ProgressBar** formant na właściwości MainWindow w projekcie powierzchni.

10. Zaznacz formant przycisku. W oknie Właściwości zmień wartość atrybutu **nazwa** właściwość z \<bez nazwy > Aby button1. Następnie zmień wartość atrybutu **zawartości** właściwości z przycisk Start.

11. Zaznacz formant paska postępu. W oknie Właściwości zmień wartość atrybutu **nazwa** właściwość z \<bez nazwy > Aby progressBar1. Następnie zmień wartość atrybutu **maksymalna** właściwość z **100** do **10000**.

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

### <a name="run-the-wpf-app"></a>Uruchamianie aplikacji WPF

1.  Na **debugowania** menu, wybierz opcję **Rozpocznij debugowanie** lub naciśnij klawisz **F5**.

2.  Zwróć uwagę, że kontrolka pola wyboru jest wyłączona. Wybierz **Start**.

     W ciągu kilku sekund pasek postępu powinien być zapełniony w 100%.

3.  Możesz teraz wybrać kontrolkę pola wyboru.

4.  Zamknij aplikację SimpleWPFApp.

## <a name="create-a-shortcut-to-the-wpf-app"></a>Utwórz skrót do aplikacji WPF

1.  Zlokalizuj aplikacji SimpleWPFApp, który został utworzony wcześniej.

2.  Utwórz na pulpicie skrót do aplikacji SimpleWPFApp. Kliknij prawym przyciskiem myszy *SimpleWPFApp.exe* i wybierz polecenie **kopiowania**. Na pulpicie kliknij prawym przyciskiem myszy i wybierz polecenie **Wklej skrót**.

    > [!TIP]
    > Skrót do aplikacji ułatwia dodawanie lub modyfikowanie kodowane testy interfejsu użytkownika dla aplikacji, ponieważ pozwala szybko uruchomić aplikację.

## <a name="create-a-coded-ui-test-for-simplewpfapp"></a>Tworzenie kodowanego testu interfejsu użytkownika dla SimpleWPFApp

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie, wybierz **Dodaj** , a następnie wybierz **nowy projekt**.

     **Dodawanie nowego projektu** zostanie wyświetlone okno dialogowe.

1. W **zainstalowana** okienku rozwiń **Visual C#**, a następnie wybierz **testu**.

1. W środkowym okienku wybierz **kodowanego interfejsu użytkownika projektu testowego** szablonu.

   > [!NOTE]
   > Jeśli nie widzisz **projekt testowanie kodowanego interfejsu użytkownika** szablonu, musisz [zainstalować składnik kodowanego testu interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

1. Wybierz **OK**.

     Nowy projekt testu interfejsu użytkownika o nazwie kodowanych **CodedUITestProject1** zostanie dodany do rozwiązania.

     **Generuj kod dla kodowanego testu interfejsu użytkownika** zostanie wyświetlone okno dialogowe.

1. Wybierz **Rejestruj akcje, Edytuj mapę interfejsu użytkownika lub Dodaj asercje** opcję i wybierz polecenie **OK**.

     **UIMap — Konstruktor kodowanego testu interfejsu użytkownika** zostanie wyświetlone okno dialogowe, a okno programu Visual Studio jest zminimalizowany.

     Aby uzyskać więcej informacji na temat opcji w oknie dialogowym, zobacz [tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md).

1. Wybierz **Rozpocznij nagrywanie** na **UIMap — Konstruktor kodowanego testu interfejsu użytkownika** okna dialogowego.

     ![Rozpocznij rejestrowanie](../test/media/cuit_builder_record.png)

     Można wstrzymać rejestrowania, jeśli to konieczne, na przykład jeśli masz radzenia sobie z poczty przychodzącej.

     ![Wstrzymanie nagrywania](../test/media/cuit_.png)

    > [!WARNING]
    > Wszystkie akcje wykonywane na pulpicie będą rejestrowane. Wstrzymanie nagrywania, wykonywania działań, które mogą prowadzić do włączenia rejestrowania danych poufnych.

1. Uruchom SimpleWPFApp za pomocą skrótu na pulpicie.

     Jak wcześniej Zwróć uwagę, że kontrolkę pola wyboru jest wyłączona.

1. Na SimpleWPFApp, wybierz **Start**.

     W ciągu kilku sekund pasek postępu powinien być zapełniony w 100%.

1. Zaznacz kontrolkę pola wyboru, która jest teraz włączony.

1. Zamknij aplikację SimpleWPFApp.

1. Na **UIMap — Konstruktor kodowanego testu interfejsu użytkownika** okno dialogowe, wybierz **Generuj kod**.

1. W **nazwę metody** wpisz **SimpleAppTest** i wybierz polecenie **Dodaj i Generuj**. W ciągu kilku sekund kodowanego testu interfejsu użytkownika pojawia się i zostanie dodany do rozwiązania.

1. Zamknij **UIMap — jest zapisana w kodowanego testu interfejsu użytkownika**.

     *CodedUITest1.cs* plik zostanie wyświetlony w edytorze kodu.

1. Zapisz projekt.

### <a name="run-the-test"></a>Uruchomienie testu

1. Z **testu** menu, wybierz **Windows** , a następnie wybierz **Eksploratora testów**.

2. Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

3. W *CodedUITest1.cs* pliku, Znajdź **CodedUITestMethod** metody, kliknij prawym przyciskiem myszy i wybierz **Uruchom testy**, lub uruchom test z **Eksploratora testów**.

   Podczas wykonywania kodowanego przebiegu testu interfejsu użytkownika aplikacja SimpleWPFApp jest widoczna. Wykonuje ona działania, których nie było w poprzedniej procedurze. Jednak gdy test próbuje zaznacz pole wyboru dla formantu pole wyboru **wyników testu** okna pokazuje, że testowanie nie powiodło się. To jest, ponieważ test próbuje zaznacz pole wyboru, ale nie jest pamiętać, że kontrolka pola wyboru jest wyłączone, aż pasek postępu jest wykonane w 100%. Problem można rozwiązać i podobne problemy przy użyciu różnych `UITestControl.WaitForControlXXX()` metod, które są dostępne dla kodowanych testów UI. Następna procedura zostaną przedstawione za pomocą `WaitForControlEnabled()` metodę, aby rozwiązać ten problem, który spowodował niepowodzenie tego testu. Aby uzyskać więcej informacji, zobacz [tworzenie kodowanego interfejsu użytkownika testy oczekiwania dla określonych zdarzeń podczas odtwarzania](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

## <a name="edit-and-rerun-the-coded-ui-test"></a>Edytuj i ponownie uruchom kodowanego testu interfejsu użytkownika

1.  W **Eksploratora testów** okna, wybierz test nie powiodło się i w **ślad stosu** wybierz pierwszy link do **UIMap.SimpleAppTest()**.

2.  *UIMap.Designer.cs* otwiera plik z punktem wyróżnione kod błędu:

    ```csharp
    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3.  Aby rozwiązać ten problem, należy wybrać kodowanego testu interfejsu użytkownika, poczekaj, aż formant wyboru włączenia przed kontynuowaniem się przy użyciu tego wiersza `WaitForControlEnabled()` metody.

    > [!WARNING]
    > Nie należy modyfikować *UIMap.Designer.cs* pliku. Żadnego kodu zmiany zostanie zastąpiony za każdym razem, gdy generowania kodu za pomocą **UIMap — Konstruktor kodowanego testu interfejsu użytkownika**. Jeśli masz zmodyfikuj metodę zarejestrowane, skopiuj go do *UIMap.cs* pliku i jego nazwa zostanie zmieniona. *UIMap.cs* plików może służyć do przesłonięcia metod i właściwości w *UIMapDesigner.cs* pliku. Należy usunąć odwołanie do oryginalnej metody w *CodedUITest.cs* pliku i zamień ją na nazwę zmieniono nazwę metody.

4.  W **Eksploratora rozwiązań**, zlokalizuj *UIMap.uitest* w projekcie kodowanego testu interfejsu użytkownika.

5.  Otwórz menu skrótów *UIMap.uitest* i wybierz polecenie **Otwórz**.

     Kodowany test interfejsu użytkownika jest wyświetlany w Edytorze kodowanego testu interfejsu użytkownika. Teraz można wyświetlać i edytować kodowany test interfejsu użytkownika.

6.  W **akcji IU** okienku, wybierz metodę testu (SimpleAppTest), który chcesz przenieść do *UIMap.cs* lub *UIMap.vb* pliku. Przenoszenie metody do innego pliku umożliwia kodu niestandardowego do dodania, który nie jest zastępowana kod testu jest ponownie kompilowana.

7.  Wybierz **Przenieś kod** znajdującego się na **kodowanego interfejsu użytkownika edytora testów** paska narzędzi.

8.  Pojawi się okno dialogowe programu Microsoft Visual Studio. Go ostrzega, że metoda ma zostać przeniesiona z *UIMap.uitest* pliku *UIMap.cs* plików i że nie będzie możliwe edytowanie metody, za pomocą edytora kodowanego testu interfejsu użytkownika. Wybierz **tak**.

     Metoda testowa zostanie usunięty z *UIMap.uitest* pliku i nie jest już wyświetlany w okienku Akcje interfejsu użytkownika. Aby edytować plik przeniesionego test, otwórz *UIMap.cs* plik z **Eksploratora rozwiązań**.

9. Na pasku narzędzi programu Visual Studio wybierz **zapisać**.

     Aktualizacje do metody testu są zapisywane w *UIMap.Designer* pliku.

    > [!WARNING]
    > Po przeniesieniu metody nie będzie można edytować jej za pomocą Edytora kodowanego testu interfejsu użytkownika. Należy dodać niestandardowy kod i obsługiwać go za pomocą Edytora kodu.

10. Zmień nazwę metody z `SimpleAppTest()` do `ModifiedSimpleAppTest()`

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

13. W *CodedUITest1.cs* pliku, Znajdź **CodedUITestMethod** — metoda i albo komentarz lub zmień nazwę odwołania do oryginalnej metody SimpleAppTest() i zastąp go z nowym ModifiedSimpleAppTest():

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

16. Teraz kodowanego testu interfejsu użytkownika pomyślnym zakończeniu wszystkich kroków testu, a **przekazanego** jest wyświetlany w **Eksploratora testów** okna.

## <a name="refactor-a-control-in-simplewpfapp"></a>Refaktoryzuj formantu w SimpleWPFApp

1.  W *MainWindow.xaml* pliku w projektancie, wybierz formantu przycisku.

2.  W górnej części **właściwości** Zmień **nazwa** wartość właściwości z **button1** do **buttonA**.

3.  Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

4.  W **Eksploratora testów**Uruchom **CodedUITestMethod1**.

     Test zakończy się niepowodzeniem, ponieważ w UIMap jako button1 kodowany test interfejsu użytkownika nie można znaleźć formantu przycisku, który pierwotnie był mapowany. Refaktoryzacja może w ten sposób wpłynąć na kodowane testy interfejsu użytkownika.

5.  W **Eksploratora testów**w **ślad stosu** wybierz pierwszy link obok pozycji **(UIMpa.ModifiedSimpleAppTest)**.

     *UIMap.cs* pliku zostanie otwarta. Punkt błędu jest wyróżniany w kodzie:

    ```csharp
    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     Należy zauważyć, że wiersz kodu we wcześniejszej części tej procedury jest przy użyciu `UiStartButton`, która jest nazwą UIMap przed jego został zrefaktoryzowany.

     Aby rozwiązać ten problem, można dodać refactored kontrolki do UIMap za pomocą **konstruktora kodowanego testu interfejsu użytkownika**. Należy zaktualizować kod testu do kodu, jak pokazano w następnej procedurze.

## <a name="map-refactored-control-rerun-the-test"></a>Mapowanie refaktoryzowane kontroli ponowne przeprowadzenie testu

1.  W *CodedUITest1.cs* pliku w **CodedUITestMethod1()** metoda, kliknij prawym przyciskiem myszy, wybierz opcję **Generuj kod dla kodowanego testu interfejsu użytkownika** , a następnie wybierz **użycia Kodowanego testu interfejsu użytkownika**.

     **UIMap — Konstruktor kodowanego testu interfejsu użytkownika** pojawi się.

2.  Za pomocą skrótu na pulpicie został utworzony wcześniej, uruchom aplikację SimpleWPFApp utworzony wcześniej.

3.  Na **UIMap — Konstruktor kodowanego testu interfejsu użytkownika** okna dialogowego, przeciągnij narzędzie krzyżyk, aby **Start** przycisk na SimpleWPFApp.

     **Start** przycisku jest ujęta w polu niebieski. **Kodowanego testu interfejsu użytkownika** zajmuje kilka sekund do przetwarzania danych dla wybranej kontrolki i wyświetlić właściwości formantu. Zwróć uwagę, że wartość **AutomationUId** jest **buttonA**.

4.  We właściwościach formantu wybierz strzałkę w lewym górnym rogu, aby rozwinąć Mapę formantów UI. Zwróć uwagę, że **UIStartButton1** jest zaznaczone.

5.  Na pasku narzędzi wybierz **Dodaj formant do mapy formantów interfejsu użytkownika**.

     Stan w dolnej części okna sprawdza akcji, wyświetlając **zaznaczony formant został dodany do mapy formantów interfejsu użytkownika**.

6.  Na **UIMap — Konstruktor kodowanego testu interfejsu użytkownika** okno dialogowe, wybierz **Generuj kod**.

     **Konstruktora kodowanego interfejsu użytkownika testu - Generuj kod** zostanie wyświetlone okno dialogowe z notatki z informacją, że jest wymagana żadna nowa metoda i ten kod będzie generowany tylko zmiany mapy formantów interfejsu użytkownika.

7.  Wybierz **Generowanie**.

8.  Zamknij aplikację SimpleWPFApp.

9. Zamknij **UIMap — jest zapisana w kodowanego testu interfejsu użytkownika**.

10. W **Eksploratora rozwiązań**, otwórz *UIMap.Designer.cs* pliku.

11. W pliku UIMap.Designer.cs Znajdź **UIStartButton1** właściwości. Powiadomienie `SearchProperties` ma ustawioną wartość `"buttonA"`:

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

12. W *UIMap.cs* pliku, Dodaj Konstruktor i określ `SearchProperties` właściwość `UIStartButton` właściwości do użycia `AutomationID` właściwość z wartością `"buttonA":`

    ```csharp
    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }
    ```

13. Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

14. W **Eksploratora testów**Uruchom **CodedUITestMethod1**.

     Tym razem kodowany test interfejsu użytkownika pomyślnie zakończy wszystkie etapy testu. W **wyników testu** okna, zostanie wyświetlony stan **przekazanego**.

## <a name="videos"></a>Wideo

![łącze do wideo](../data-tools/media/playvideo.gif "PlayVideo") [wprowadzenie kodowanych testów interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=230573)

![łącze do wideo](../data-tools/media/playvideo.gif "PlayVideo") [konserwacji i debugowanie kodowanych testów interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=230574)

![łącze do wideo](../data-tools/media/playvideo.gif "PlayVideo") [kodowania ręcznie kodowanych testów interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=230575)

## <a name="faq"></a>Najczęściej zadawane pytania

[Kodowanych testów interfejsu użytkownika — często zadawane pytania](https://social.msdn.microsoft.com/Forums/en-US/3a74dd2c-cef8-4923-abbf-7a91f489e6c4/faqs?forum=vsautotest)

## <a name="see-also"></a>Zobacz także

- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i rejestrowania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Edytowanie kodowanych testów interfejsu użytkownika za pomocą edytora kodowanych testów interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
