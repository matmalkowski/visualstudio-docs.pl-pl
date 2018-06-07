---
title: 'Wskazówki: Tworzenie prostej aplikacji w języku C# lub Visual Basic'
ms.date: 10/03/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3efb5315b3adb02f74b41d193a6b9173f38ec992
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749560"
---
# <a name="walkthrough-create-a-simple-application-with-c-or-visual-basic"></a>Wskazówki: Tworzenie prostej aplikacji w języku C# lub Visual Basic

Wykonując tego przewodnika, użytkownik będzie zapoznanie się z wielu narzędzi, okna dialogowe i projektantów, których można używać podczas opracowywania aplikacji za pomocą programu Visual Studio. Będzie utworzyć prostą aplikację "Hello, World", projektowanie interfejsu użytkownika, Dodaj kod i debugowanie błędów w czasie Dowiedz się więcej o pracy w zintegrowane środowisko programistyczne (IDE).

## <a name="configure-the-ide"></a>Konfigurowanie IDE

Po uruchomieniu programu Visual Studio po raz pierwszy, zostanie wyświetlony monit do logowania. Ten krok jest opcjonalny w ramach tego przewodnika. Następnie możesz mogą zostać wyświetlone okno dialogowe z prośbą o wybierz motyw kolorów i ustawienia środowiska deweloperskiego. Zachowaj wartości domyślne, a następnie wybierz pozycję **Uruchom Visual Studio**.

![Wybierz ustawienia — okno dialogowe](../ide/media/exploreide-settings.png)

Po uruchomieniu programu Visual Studio, zobaczysz okna narzędzi, menu i pasków narzędzi oraz obszaru głównego okna. Narzędzia systemu windows są zadokowane po lewej i prawej stronie okna aplikacji **Szybkie uruchamianie**, paska menu i standardowym pasku narzędzi u góry. W Centrum w oknie aplikacji jest **— strona początkowa**. Podczas ładowania rozwiązania lub projektu, edytory i projektantom są wyświetlane w obszarze gdzie **— strona początkowa** jest. Podczas opracowywania aplikacji poświęcany większość czasu w tym obszarze centralnej.

![IDE z zastosowaniem ustawień ogólnych](../ide/media/exploreide-idewithgeneralsettings.png)

## <a name="create-the-project"></a>Utwórz projekt

Podczas tworzenia aplikacji w programie Visual Studio, należy najpierw utworzyć projekt i rozwiązanie. W tym przykładzie utworzysz projekt Windows Presentation Foundation (WPF).

1. Utwórz nowy projekt. Na pasku menu wybierz **pliku** > **nowy** > **projektu**.

     ![Na pasku menu wybierz plik, nowy projekt](../ide/media/exploreide-filenewproject.png)

1. W **nowy projekt** okno dialogowe, wybierz opcję **zainstalowana** > **Visual C#** (lub **Visual Basic**) >  **System Windows Desktop** kategorii, a następnie wybierz **WPF aplikacji (.NET Framework)** szablonu. Nazwij projekt **HelloWPFApp**.

     ![Szablon aplikacji WPF w oknie dialogowym Nowy projekt programu Visual Studio](../ide/media/exploreide-newprojectcsharp.png)

1. Wybierz **OK**.

Program Visual Studio tworzy HelloWPFApp projektu i rozwiązania, oraz **Eksploratora rozwiązań** zawiera różne pliki. **Projektanta WPF** Pokazuje widok projektu i widok XAML *MainWindow.xaml* w widoku podzielonego. Przesuń, podziału, aby wyświetlić więcej lub mniej albo widoku. Można wyświetlić visual widoku lub widoku XAML. (Aby uzyskać więcej informacji, zobacz [deweloperzy WPF Projektant dla formularzy systemu Windows](http://msdn.microsoft.com/47ad0909-e89b-4996-b4ac-874d929f94ca).) Następujące elementy są wyświetlane w **Eksploratora rozwiązań**:

![Eksplorator rozwiązań z plikami HelloWPFApp załadowany](../ide/media/exploreide-hellowpfappfiles.png)

Po utworzeniu projektu, można go dostosować. Za pomocą **właściwości** okna (znalezione na **widoku** menu), można wyświetlać i zmieniać opcje dla elementów projektu, formantów i innych elementów w aplikacji.

### <a name="change-the-name-of-mainwindowxaml"></a>Zmień nazwę MainWindow.xaml

Załóżmy nazwę właściwości MainWindow bardziej szczegółowych.

1. W **Eksploratora rozwiązań**, wybierz pozycję *MainWindow.xaml*. Powinny pojawić się **właściwości** okna, ale jeśli nie wybierz **widoku** menu, a następnie **okna właściwości** elementu.

1. Zmień **nazwę pliku** właściwości `Greetings.xaml`.

     ![Okno właściwości z wyróżnionym nazwy pliku](../ide/media/exploreide-filenameinpropertieswindow.png)

     **Eksplorator rozwiązań** wskazuje, że nazwa pliku jest teraz *Greetings.xaml*, a teraz nazwę pliku zagnieżdżonego kodu *Greetings.xaml.vb* lub *Greetings.xaml.cs*. Ten plik kod jest zagnieżdżony w obszarze *.xaml* pliku węzeł są ściśle powiązane ze sobą.

## <a name="design-the-user-interface-ui"></a>Zaprojektuj interfejs użytkownika

Trzy typy formantów zostanie dodany do tej aplikacji: <xref:System.Windows.Controls.TextBlock> kontrolować dwa <xref:System.Windows.Controls.RadioButton> formantów, a <xref:System.Windows.Controls.Button> formantu.

### <a name="add-a-textblock-control"></a>Dodawanie formantu blok tekstu

1. Otwórz **przybornika** okna, wybierając **widoku** menu i **przybornika** elementu.

2. W **przybornika**, rozwiń węzeł **wspólnych formantów WPF** węzeł, aby formant jest blok tekstu.

     ![Przybornika z formantem blok tekstu wyróżnione](../ide/media/exploreide-textblocktoolbox.png)

3. Dodawanie formantu blok tekstu na powierzchnię projektu, wybierając **blok tekstu** element i przeciągając go do okna na powierzchni projektu. Centrum sterowania w górnej części okna.

Okno powinno wyglądać podobnie, jak na poniższej ilustracji:

![Blok tekstu formantu w formularzu pozdrowienia](../ide/media/exploreide-greetingswithtextblockonly.png)

Znacznik XAML powinien wyglądać mniej więcej tak:

```xaml
<TextBlock HorizontalAlignment="Center" TextWrapping="Wrap" VerticalAlignment="Center" RenderTransformOrigin="4.08,2.312" Margin="237,57,221,238"><Run Text="TextBlock"/><InlineUIContainer><TextBlock TextWrapping="Wrap" Text="TextBlock"/>
```

### <a name="customize-the-text-in-the-text-block"></a>Dostosowywanie tekstu w bloku tekstu

1. W widoku XAML zlokalizować kod znaczników dla obiektu TextBlock i zmienić atrybut tekstu:

   ```xaml
   Text="Select a message option and then choose the Display button."
   ```

2. Ponownie Centrum blok tekstu, jeśli to konieczne i Zapisz zmiany, naciskając klawisz **Ctrl**+**S** lub przy użyciu **pliku** elementu menu.

Następnie dodasz dwa [RadioButton](/dotnet/framework/wpf/controls/radiobutton) formantów w formularzu.

### <a name="add-radio-buttons"></a>Dodawanie przycisków radiowych

1. W **przybornika**, Znajdź **RadioButton** formantu.

     ![Okno przybornika z zaznaczonym formancie RadioButton](../ide/media/exploreide-radiobuttontoolbox.png)

2. Dodawanie dwóch formantów RadioButton w projekcie, surface, wybierając **RadioButton** element i przeciągając go do okna na powierzchni projektu. Przenieś przycisków (zaznaczając je i za pomocą klawiszy strzałek), aby przyciski wyświetlane obok siebie pod kontrolą blok tekstu.

     Okno powinno wyglądać następująco:

     ![Formularz pozdrowienia z blokiem tekstu i dwa elementy RadioButton](../ide/media/exploreide-greetingswithradiobuttons.png)

3. W **właściwości** w oknie po lewej stronie formantu RadioButton, zmień **nazwa** właściwości (właściwość w górnej części **właściwości** okna) do `HelloButton`.

     ![Okno właściwości RadioButton](../ide/media/exploreide-buttonproperties.png)

4. W **właściwości** okna dla formantu RadioButton prawo, zmień **nazwa** właściwości `GoodbyeButton`, a następnie zapisz zmiany.

Możesz teraz dodawać wyświetlany tekst dla każdego formantu RadioButton. Następujące aktualizacje procedury **zawartości** właściwości formantu RadioButton.

### <a name="add-display-text-for-each-radio-button"></a>Dodaj tekst wyświetlany dla przycisku radiowego

1. Na powierzchni projektu otwórz menu skrótów dla HelloButton naciskając HelloButton prawym przyciskiem myszy, wybierz pozycję **Edycja tekstu**, a następnie wprowadź `Hello`.

2. Otwórz menu skrótów GoodbyeButton naciskając prawym przyciskiem myszy na GoodbyeButton, wybierz **Edycja tekstu**, a następnie wprowadź `Goodbye`.

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Ustaw przycisku radiowego, który ma być sprawdzany domyślnie

W tym kroku zaplanujemy HelloButton do zaznaczone domyślnie, dzięki czemu zawsze wybrano jeden z przycisków radiowych dwa.

W widoku XAML zlokalizować kod znaczników dla HelloButton i Dodaj **IsChecked** atrybutu:

```xaml
IsChecked="True"
```

Element interfejsu użytkownika końcowego należy dodać to [przycisk](/dotnet/framework/wpf/controls/button) formantu.

### <a name="add-the-button-control"></a>Dodawanie formantu przycisku

1. W **przybornika**, Znajdź **przycisk** kontroli, a następnie dodaj ją na powierzchnię projektu w obszarze formantów RadioButton, przeciągając go do formularza w widoku Projekt.

2. W widoku XAML, zmień wartość **zawartości** dla formantu przycisku z `Content="Button"` do `Content="Display"`, a następnie zapisz zmiany.

     Kod znaczników powinien wyglądać następująco:   `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

     Okno powinno wyglądać podobnie, jak na poniższej ilustracji.

     ![Formularz pozdrowienia z etykiety formantu](../ide/media/exploreide-greetingswithconrollabels.png)

### <a name="add-code-to-the-display-button"></a>Dodawanie kodu do wyświetlania przycisku

Po uruchomieniu tej aplikacji, pojawi się komunikat po użytkownik wybierze przycisk radiowy, a następnie wybiera **wyświetlania** przycisku. Jedno okno komunikatu pojawi się, żeby wyświetlić „Hello”, a inne pojawi się, aby wyświetlić „Goodbye”. Aby utworzyć ten problem, można dodać kod `Button_Click` zdarzenia w *Greetings.xaml.vb* lub *Greetings.xaml.cs*.

1. Na powierzchni projektu, kliknij dwukrotnie **wyświetlania** przycisku.

     *Greetings.XAML.VB* lub *Greetings.xaml.cs* otwiera kursor znajduje się w `Button_Click` zdarzeń.

    ```vb
    Private Sub Button_Click_1(sender As Object, e As RoutedEventArgs)

    End Sub
    ```

    ```csharp
    private void Button_Click_1(object sender, RoutedEventArgs e)
    {

    }
    ```

2. Wprowadź następujący kod:

    ```vb
    If HelloButton.IsChecked = True Then
        MessageBox.Show("Hello.")
    ElseIf GoodbyeButton.IsChecked = True Then
        MessageBox.Show("Goodbye.")
    End If
    ```

    ```csharp
    if (HelloButton.IsChecked == true)
    {
         MessageBox.Show("Hello.");
    }
    else if (GoodbyeButton.IsChecked == true)
    {
        MessageBox.Show("Goodbye.");
    }
    ```

3. Zapisz aplikację.

## <a name="debug-and-test-the-application"></a>Debugowanie i testowanie aplikacji

Następnie będzie debugowania aplikacji, aby wyszukać błędy i testowanie, czy oba pola wiadomości są wyświetlane poprawnie. Poniższe instrukcje informujące, jak skompilować i uruchomić debugera, ale później mogą odczytać [kompilacji aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) i [debugowanie WPF](../debugger/debugging-wpf.md) Aby uzyskać więcej informacji.

### <a name="find-and-fix-errors"></a>Znajdowanie i naprawianie błędów

W tym kroku można znaleźć błąd, który spowodował możemy wcześniej, zmieniając nazwę *MainWindow.xaml* pliku.

#### <a name="start-debugging-and-find-the-error"></a>Rozpocznij debugowanie i Znajdź błąd

1. Uruchom debuger, wybierając **debugowania**, następnie **Rozpocznij debugowanie**.

     ![Rozpocznij debugowanie polecenia menu debugowania](../ide/media/exploreide-startdebugging.png)

     A **Podziel tryb** zostanie wyświetlone okno i **dane wyjściowe** okno oznacza, że wystąpił wyjątek IOException: nie można zlokalizować zasobu "mainwindow.xaml".

2. Zatrzymywanie działania debugera, wybierając **debugowania** > **Zatrzymaj debugowanie**.

     ![Zatrzymaj debugowanie polecenia menu debugowania](../ide/media/exploreide-stopdebugging.png)

Możemy zmienić nazwy *MainWindow.xaml* do *Greetings.xaml* na początku tego przewodnika, ale kod nadal odwołuje się do *MainWindow.xaml* jako uruchamiania identyfikatora URI dla aplikacji , więc nie można uruchomić projektu.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Określ Greetings.xaml jako uruchamiania identyfikatora URI

1. W **Eksploratora rozwiązań**, otwórz *App.xaml* pliku (w projektu C#) lub *Application.xaml* pliku (w projektach Visual Basic).

2. Zmień `StartupUri="MainWindow.xaml"` do `StartupUri="Greetings.xaml"`, a następnie zapisz zmiany.

Uruchom ponownie debuger (naciśnij klawisz **F5**). Powinny pojawić się **pozdrowienia** okna aplikacji. Teraz można zamknąć okna aplikacji, aby zatrzymać debugowanie.

### <a name="debug-with-breakpoints"></a>Debugowanie przy użyciu punktów przerwania

Można przetestować kodu podczas debugowania przez dodanie niektórych punktów przerwania. Można dodać punkty przerwania, wybierając **debugowania** > **Przełącz punkt przerwania**, klikając w miejscu podziału występuje lewego marginesu edytora obok wiersza kodu lub naciskając klawisz  **F9**.

#### <a name="add-breakpoints"></a>Dodać punkty przerwania

1. Otwórz *Greetings.xaml.vb* lub *Greetings.xaml.cs*i wybierz następujący wiersz: `MessageBox.Show("Hello.")`

2. Dodaj punkt przerwania z menu, wybierając **debugowania**, następnie **Przełącz punkt przerwania**.

     ![Przełącz punkt przerwania — polecenie menu debugowania](../ide/media/exploreide-togglebreakpoint.png)

     Obok wiersza kodu na marginesie po lewej stronie okna edytora jest wyświetlane czerwone koło.

3. Wybierz następujący wiersz: `MessageBox.Show("Goodbye.")`.

4. Naciśnij klawisz **F9** klawisz, aby dodać punkt przerwania, a następnie naciśnij klawisz **F5** można rozpocząć debugowania.

5. W **pozdrowienia** okna, wybierz **Hello** przycisk radiowy, a następnie wybierz pozycję **wyświetlania** przycisku.

     Wiersz `MessageBox.Show("Hello.")` jest wyróżnione kolorem żółtym. W dolnej części IDE, automatycznych, zmienne lokalne i obejrzyj systemu windows zostanie zadokowanych po lewej stronie, a stos wywołań, punkty przerwania, polecenia, natychmiastowe i dane wyjściowe systemu windows są ze sobą zadokowane po prawej stronie.

6. Na pasku menu wybierz **debugowania** > **Wyjdź**.

     Aplikacji wznawia wykonywanie i pojawi się okno komunikatu od słowa "Hello".

7. Wybierz **OK** przycisk w oknie komunikatu, aby je zamknąć.

8. W **pozdrowienia** okna, wybierz **Goodbye** przycisk radiowy, a następnie wybierz pozycję **wyświetlania** przycisku.

     Wiersz `MessageBox.Show("Goodbye.")` jest wyróżnione kolorem żółtym.

9. Wybierz **F5** klawisz, aby kontynuować debugowanie. Gdy pojawi się okno komunikatu, wybierz **OK** przycisk w oknie komunikatu, aby je zamknąć.

10. Zamknij okno aplikacji, aby zatrzymać debugowanie.

11. Na pasku menu wybierz **debugowania** > **Wyłącz wszystkie punkty przerwania**.

### <a name="build-a-release-version-of-the-application"></a>Tworzenie dystrybucyjnej wersji tej aplikacji

Teraz, gdy upewnieniu się, że wszystko działa, można przygotować kompilację wersji aplikacji.

1. W menu głównym wybierz **kompilacji** > **czyszczenia rozwiązania** do usuwania plików pośrednich i pliki wyjściowe, które zostały utworzone w poprzednich wersjach. Nie jest to konieczne, ale jego czyści dane wyjściowe kompilacji debugowania.

     ![Polecenie Wyczyść rozwiązanie w menu kompilacji](../ide/media/exploreide-cleansolution.png)

2. Zmień konfigurację kompilacji dla HelloWPFApp z **debugowania** do **wersji** za pomocą kontrolki rozwijanej na pasku narzędzi (wyświetlany jest tekst "Debugowanie" obecnie).

     ![Standardowym pasku narzędzi w wersji wybrane](../ide/media/exploreide-releaseversion.png)

3. Skompiluj rozwiązanie, wybierając **kompilacji** > **Kompiluj rozwiązanie**.

     ![Kompiluj rozwiązanie, polecenie menu kompilacji](../ide/media/exploreide-buildsolution.png)

Gratulujemy zakończenia instruktażu! Można znaleźć *.exe* utworzony w katalogu rozwiązania i projektu (*...\HelloWPFApp\HelloWPFApp\bin\Release*).

## <a name="see-also"></a>Zobacz także

- [Co to jest nowa w programie Visual Studio 2017 r.](../ide/whats-new-in-visual-studio.md)
- [Wskazówki dotyczące produktywności](../ide/productivity-tips-for-visual-studio.md)