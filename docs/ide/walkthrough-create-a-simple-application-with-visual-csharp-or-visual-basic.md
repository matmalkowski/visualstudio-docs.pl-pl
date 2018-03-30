---
title: 'Wskazówki: Tworzenie prostej aplikacji w języku C# lub Visual Basic | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 10/03/2017
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
caps.latest.revision: 19
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 36f0bf93b85b3bc9582b7b0c656b0d105b61cecb
ms.sourcegitcommit: 064f8678f4a918e1dce60285090a9803d37dc34b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2018
---
# <a name="walkthrough-create-a-simple-application-with-c-or-visual-basic"></a>Wskazówki: Tworzenie prostej aplikacji w języku C# lub Visual Basic
Wykonując tego przewodnika, użytkownik będzie zapoznanie się z wielu narzędzi, okna dialogowe i projektantów, których można używać podczas opracowywania aplikacji za pomocą programu Visual Studio. Będzie utworzyć prostą aplikację "Hello, World", projektowanie interfejsu użytkownika, Dodaj kod i debugowanie błędów w czasie Dowiedz się więcej o pracy w zintegrowane środowisko programistyczne (IDE).

##  <a name="BKMK_ConfigureIDE"></a> Konfigurowanie środowiska IDE  
Po uruchomieniu programu Visual Studio po raz pierwszy, zostanie wyświetlony monit do logowania. Ten krok jest opcjonalny w ramach tego przewodnika. Następnie możesz mogą zostać wyświetlone okno dialogowe z prośbą o wybierz motyw kolorów i ustawienia środowiska deweloperskiego. Zachowaj wartości domyślne, a następnie wybierz pozycję **Uruchom Visual Studio**.  

![Wybierz okno dialogowe Ustawienia](../ide/media/exploreide-settings.png "exploreide — ustawienia")

Po uruchomieniu programu Visual Studio, zobaczysz okna narzędzi, menu i pasków narzędzi oraz obszaru głównego okna. Narzędzia systemu windows są zadokowane po lewej i prawej stronie okna aplikacji **Szybkie uruchamianie**, paska menu i standardowym pasku narzędzi u góry. W Centrum w oknie aplikacji jest **— strona początkowa**. Podczas ładowania rozwiązania lub projektu, edytory i projektantom są wyświetlane w obszarze gdzie **— strona początkowa** jest. Podczas opracowywania aplikacji poświęcany większość czasu w tym obszarze centralnej.  

![IDE z zastosowaniem ustawień ogólnych](../ide/media/exploreide-idewithgeneralsettings.png "ExploreIDE IDEwithgeneralsettings")  

##  <a name="BKMK_CreateApp"></a> Utworzyć prostą aplikację  

### <a name="create-the-project"></a>Utwórz projekt  
Podczas tworzenia aplikacji w programie Visual Studio, należy najpierw utworzyć projekt i rozwiązanie. W tym przykładzie utworzysz projekt Windows Presentation Foundation (WPF).  

#### <a name="to-create-the-wpf-project"></a>Aby utworzyć projekt WPF  

1.  Utwórz nowy projekt. Na pasku menu wybierz **pliku**, **nowy**, **projektu...** .  

     ![Na pasku menu, wybierz plik, nowy, projektu](../ide/media/exploreide-filenewproject.png "ExploreIDE FileNewProject")  

2.  Wybierz pozycję Visual Basic lub Visual C# WPF aplikacji szablonu, wybierając w okienku po lewej stronie **zainstalowana**, **Visual C#**, **Windows Desktop klasycznego**, na przykład, a następnie wybierając **WPF aplikacji (.NET Framework)** w środkowym okienku.  Nazwa projektu HelloWPFApp w dolnej części okna dialogowego Nowy projekt.  

     ![Tworzenie projektu C# WPF, HelloWPFApp](../ide/media/exploreide-newprojectcsharp.png "ExploreIDE NewProjectcsharp")  

Program Visual Studio tworzy HelloWPFApp projektu i rozwiązania, oraz **Eksploratora rozwiązań** zawiera różne pliki. Projektant WPF pokazuje widok projektu i widok XAML pliku MainWindow.xaml w widoku podzielonym. Przesuń, podziału, aby wyświetlić więcej lub mniej albo widoku.  Można wyświetlić visual widoku lub widoku XAML. (Aby uzyskać więcej informacji, zobacz [WPF projektanta dla deweloperów systemu Windows Forms](http://msdn.microsoft.com/47ad0909-e89b-4996-b4ac-874d929f94ca).) Następujące elementy są wyświetlane w **Eksploratora rozwiązań**:  

![Załadowany w Eksploratorze rozwiązań z plikami HelloWPFApp](../ide/media/exploreide-hellowpfappfiles.png "ExploreIDE HelloWPFAppFiles")  

Po utworzeniu projektu, można go dostosować. Za pomocą **właściwości** okna (znalezione na **widoku** menu), można wyświetlać i zmieniać opcje dla elementów projektu, formantów i innych elementów w aplikacji.  

#### <a name="to-change-the-name-of-mainwindowxaml"></a>Aby zmienić nazwę MainWindow.xaml  
Załóżmy nazwę właściwości MainWindow bardziej szczegółowych.  

1. W **Eksploratora rozwiązań**, wybierz MainWindow.xaml. Powinny pojawić się **właściwości** okna, ale jeśli nie wybierz **widoku** menu, a następnie **okna właściwości** elementu.  
2. Zmień **nazwę pliku** właściwości `Greetings.xaml`.  

     ![Okno właściwości o nazwie pliku wyróżnione](../ide/media/exploreide-filenameinpropertieswindow.png "ExploreIDE FilenameinPropertiesWindow")  

     **Eksplorator rozwiązań** pokazuje, że nazwa pliku jest teraz Greetings.xaml i Greetings.xaml.vb lub Greetings.xaml.cs ma teraz nazwę pliku zagnieżdżonego kodu. Ten plik kodu jest zagnieżdżony w węźle plik .xaml do pokazania są ściśle powiązane ze sobą.  

### <a name="design-the-user-interface-ui"></a>Zaprojektuj interfejs użytkownika  
Dodamy w tej aplikacji trzy typy kontrolek: kontrolkę TextBlock (blok tekstu), dwie kontrolki RadioButton (przycisk radiowy) i kontrolkę Button (przycisk).  

#### <a name="to-add-a-textblock-control"></a>Aby dodać kontrolkę TextBlock  

1.  Otwórz **przybornika** okna, wybierając **widoku** menu i **przybornika** elementu.  

2.  W **przybornika**, rozwiń węzeł **wspólnych formantów WPF** węzeł, aby formant jest blok tekstu.  

     ![Przybornika z formantem blok tekstu wyróżnione](../ide/media/exploreide-textblocktoolbox.png "ExploreIDE TextBlockToolbox")  

3.  Dodawanie formantu blok tekstu na powierzchnię projektu, wybierając **blok tekstu** element i przeciągając go do okna na powierzchni projektu. Centrum sterowania w górnej części okna.  

Okno powinno wyglądać podobnie, jak na poniższej ilustracji:  

![Blok tekstu formantu w formularzu pozdrowienia](../ide/media/exploreide-greetingswithtextblockonly.png "ExploreIDE GreetingswithTextblockonly")  

Znacznik XAML powinien wyglądać mniej więcej tak:  

```xaml  
<TextBlock HorizontalAlignment="Center" TextWrapping="Wrap" VerticalAlignment="Center" RenderTransformOrigin="4.08,2.312" Margin="237,57,221,238"><Run Text="TextBlock"/><InlineUIContainer><TextBlock TextWrapping="Wrap" Text="TextBlock"/>  
```  

#### <a name="to-customize-the-text-in-the-text-block"></a>Aby dostosować tekst w bloku tekstowym  

1.  W widoku XAML zlokalizować kod znaczników dla obiektu TextBlock i zmienić atrybut tekstu:  

   ```xaml
   Text="Select a message option and then choose the Display button."
   ```  

2.  Ponownie Centrum blok tekstu, jeśli to konieczne i Zapisz zmiany, naciskając klawisz **Ctrl-s** lub przy użyciu **pliku** elementu menu.  

Następnie dodasz dwa [RadioButton](/dotnet/framework/wpf/controls/radiobutton) formantów w formularzu.  

#### <a name="to-add-radio-buttons"></a>Aby dodać przyciski radiowe  

1.  W **przybornika**, Znajdź **RadioButton** formantu.  

     ![Okno przybornika z formantu RadioButton wybrane](../ide/media/exploreide-radiobuttontoolbox.png "ExploreIDE RadioButtonToolbox")  

2.  Dodawanie dwóch formantów RadioButton w projekcie, surface, wybierając **RadioButton** element i przeciągając go do okna na powierzchni projektu. Przenieś przycisków (zaznaczając je i za pomocą klawiszy strzałek), aby przyciski wyświetlane obok siebie pod kontrolą blok tekstu.  

     Okno powinno wyglądać następująco:  

     ![Pozdrowienia formularza z blokiem tekstu i dwa elementy RadioButton](../ide/media/exploreide-greetingswithradiobuttons.png "ExploreIDE Greetingswithradiobuttons")  

3.  W **właściwości** w oknie po lewej stronie formantu RadioButton, zmień **nazwa** właściwości (właściwość w górnej części **właściwości** okna) do  **HelloButton**.  

     ![Okno właściwości RadioButton](../ide/media/exploreide-buttonproperties.png "exploreide buttonproperties")  

4.  W **właściwości** okna dla formantu RadioButton prawo, zmień **nazwa** właściwości **GoodbyeButton**, a następnie zapisz zmiany.  

Możesz teraz dodawać wyświetlany tekst dla każdego formantu RadioButton. Następujące aktualizacje procedury **zawartości** właściwości formantu RadioButton.  

#### <a name="to-add-display-text-for-each-radio-button"></a>Aby dodać wyświetlany tekst dla każdego przycisku radiowego  

1.  Na powierzchni projektu otwórz menu skrótów dla HelloButton naciskając HelloButton prawym przyciskiem myszy, wybierz pozycję **Edycja tekstu**, a następnie wprowadź tekst "Hello".  

2.  Otwórz menu skrótów GoodbyeButton naciskając prawym przyciskiem myszy na GoodbyeButton, wybierz **Edycja tekstu**, a następnie wprowadź "Goodbye".  

### <a name="to-set-a-radio-button-to-be-checked-by-default"></a>Aby ustawić przycisku radiowego, który ma być sprawdzany domyślnie  
W tym kroku zaplanujemy HelloButton do zaznaczone domyślnie, dzięki czemu zawsze wybrano jeden z przycisków radiowych dwa.  

W widoku XAML zlokalizować kod znaczników dla HelloButton i Dodaj **IsChecked** atrybutu:

```xaml
IsChecked="True"
```  

Element interfejsu użytkownika końcowego należy dodać to [przycisk](/dotnet/framework/wpf/controls/button) formantu.  

#### <a name="to-add-the-button-control"></a>Aby dodać kontrolkę przycisku  

1.  W **przybornika**, Znajdź **przycisk** kontroli, a następnie dodaj ją na powierzchnię projektu w obszarze formantów RadioButton, przeciągając go do formularza w widoku Projekt.  

2.  W widoku XAML, zmień wartość **zawartości** dla formantu przycisku z `Content="Button"` do `Content="Display"`, a następnie zapisz zmiany.  

     Kod znaczników powinien wyglądać następująco:  
     `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`  

     Okno powinno wyglądać podobnie, jak na poniższej ilustracji.  

     ![Formularz pozdrowienia z etykiety formantu](../ide/media/exploreide-greetingswithconrollabels.png "ExploreIDE Greetingswithconrollabels")  

### <a name="add-code-to-the-display-button"></a>Dodaj kod do przycisku Display  
Po uruchomieniu tej aplikacji, pojawi się komunikat po użytkownik wybierze przycisk radiowy, a następnie wybiera **wyświetlania** przycisku. Jedno okno komunikatu pojawi się, żeby wyświetlić „Hello”, a inne pojawi się, aby wyświetlić „Goodbye”. Aby utworzyć to zachowanie, warto kodu zdarzenia Button_Click w Greetings.xaml.vb lub Greetings.xaml.cs.  

#### <a name="add-code-to-display-message-boxes"></a>Dodaj kod do wyświetlania okien komunikatów    
1.  Na powierzchni projektu, kliknij dwukrotnie **wyświetlania** przycisku.  

     Greetings.xaml.vb lub Greetings.xaml.cs otworzy się, kursor będzie się znajdował w zdarzeniu Button_Click.

    ```vb  
    Private Sub Button_Click_1(sender As Object, e As RoutedEventArgs)  

    End Sub  
    ```    
    ```csharp  
    private void Button_Click_1(object sender, RoutedEventArgs e)  
    {  

    }  
    ```  

2.  Wprowadź następujący kod:  

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

3.  Zapisz aplikację.  

##  <a name="BKMK_DebugTest"></a> Debugowanie i testowanie aplikacji  
Następnie będzie debugowania aplikacji, aby wyszukać błędy i testowanie, czy oba pola wiadomości są wyświetlane poprawnie. Poniższe instrukcje informujące, jak skompilować i uruchomić debugera, ale później mogą odczytać [kompilowania aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) i [debugowanie WPF](../debugger/debugging-wpf.md) Aby uzyskać więcej informacji.  

### <a name="find-and-fix-errors"></a>Znajdowanie i naprawianie błędów  
W tym kroku znajdziesz błąd, który spowodował możemy wcześniej, zmieniając nazwę pliku MainWindow.xaml.  

#### <a name="to-start-debugging-and-find-the-error"></a>Aby rozpocząć debugowanie i znaleźć błąd  

1.  Uruchom debuger, wybierając **debugowania**, następnie **Rozpocznij debugowanie**.  

     ![Rozpocznij debugowanie polecenia menu debugowania](../ide/media/exploreide-startdebugging.png "ExploreIDE StartDebugging")  

     A **Podziel tryb** zostanie wyświetlone okno i **dane wyjściowe** okno oznacza, że wystąpił wyjątek IOException: nie można zlokalizować zasobu "mainwindow.xaml".  

2.  Zatrzymywanie działania debugera, wybierając **debugowania**, **Zatrzymaj debugowanie**.  

     ![Zatrzymaj debugowanie polecenia menu debugowania](../ide/media/exploreide-stopdebugging.png "ExploreIDE StopDebugging")  

Możemy zmienić nazwy MainWindow.xaml Greetings.xaml na początku tego przewodnika, ale kod nadal odwołuje się do mainwindow.xaml jako uruchamiania identyfikatora URI dla aplikacji, więc nie można uruchomić projektu.  

#### <a name="to-specify-greetingsxaml-as-the-startup-uri"></a>Aby określić Greetings.xaml jako startowy identyfikator URI  

1.  W **Eksploratora rozwiązań**, otwórz plik App.xaml (w projektu C#) lub plik Application.xaml (w projektach Visual Basic).  

2.  Zmień `StartupUri="MainWindow.xaml"` do `StartupUri="Greetings.xaml"`, a następnie zapisz zmiany.  

Uruchom ponownie debuger (naciśnij klawisz **F5**). Powinieneś zobaczyć okno powitania aplikacji. Teraz można zamknąć okna aplikacji, aby zatrzymać debugowanie.  

### <a name="to-debug-with-breakpoints"></a>Aby debugować z punktami przerwania  
Można przetestować kodu podczas debugowania przez dodanie niektórych punktów przerwania. Można dodać punkty przerwania, wybierając **debugowania**, **Przełącz punkt przerwania**, klikając w miejscu podziału występuje lewego marginesu edytora obok wiersza kodu lub naciskając klawisz **F9**.  

#### <a name="to-add-breakpoints"></a>Aby dodać punkty przerwania  

1.  Otwórz Greetings.xaml.vb lub Greetings.xaml.cs, a następnie wybierz następujący wiersz: `MessageBox.Show("Hello.")`  

2.  Dodaj punkt przerwania z menu, wybierając **debugowania**, następnie **Przełącz punkt przerwania**.  

     ![Przełącz punkt przerwania — polecenie menu debugowania](../ide/media/exploreide-togglebreakpoint.png "togglebreakpoint — ExploreIDE")  

     Obok wiersza kodu na marginesie po lewej stronie okna edytora jest wyświetlane czerwone koło.  

3.  Wybierz następujący wiersz: `MessageBox.Show("Goodbye.")`.  

4.  Naciśnij klawisz **F9** klawisz, aby dodać punkt przerwania, a następnie naciśnij klawisz **F5** można rozpocząć debugowania.  

5.  W **pozdrowienia** okna, wybierz **Hello** przycisk radiowy, a następnie wybierz pozycję **wyświetlania** przycisku.  

     Wiersz `MessageBox.Show("Hello.")` jest wyróżnione kolorem żółtym. W dolnej części IDE, automatycznych, zmienne lokalne i obejrzyj systemu windows zostanie zadokowanych po lewej stronie, a stos wywołań, punkty przerwania, polecenia, natychmiastowe i dane wyjściowe systemu windows są ze sobą zadokowane po prawej stronie.  

6.  Na pasku menu wybierz **debugowania**, **Wyjdź**.  

     Aplikacji wznawia wykonywanie i pojawi się okno komunikatu od słowa "Hello".  

7.  Wybierz **OK** przycisk w oknie komunikatu, aby je zamknąć.  

8.  W **pozdrowienia** okna, wybierz **Goodbye** przycisk radiowy, a następnie wybierz pozycję **wyświetlania** przycisku.  

     Wiersz `MessageBox.Show("Goodbye.")` jest wyróżnione kolorem żółtym.  

9. Wybierz **F5** klawisz, aby kontynuować debugowanie. Gdy pojawi się okno komunikatu, wybierz **OK** przycisk w oknie komunikatu, aby je zamknąć.  

10. Zamknij okno aplikacji, aby zatrzymać debugowanie.  

11. Na pasku menu wybierz **debugowania**, **Wyłącz wszystkie punkty przerwania**.  

### <a name="build-a-release-version-of-the-application"></a>Tworzenie dystrybucyjnej wersji tej aplikacji  
 Teraz, gdy upewnieniu się, że wszystko działa, można przygotować kompilację wersji aplikacji.  

#### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Aby wyczyścić pliki rozwiązań i zbudować wersję przeznaczoną do publikacji  

1.  W menu głównym wybierz **kompilacji**, **czyszczenia rozwiązania** do usuwania plików pośrednich i pliki wyjściowe, które zostały utworzone w poprzednich wersjach. Nie jest to konieczne, ale jego czyści dane wyjściowe kompilacji debugowania.  

     ![Polecenie Wyczyść rozwiązanie w menu kompilacji](../ide/media/exploreide-cleansolution.png "ExploreIDE CleanSolution")  

2.  Zmień konfigurację kompilacji dla HelloWPFApp z **debugowania** do **wersji** za pomocą kontrolki rozwijanej na pasku narzędzi (wyświetlany jest tekst "Debugowanie" obecnie).  

     ![Standardowym pasku narzędzi w wersji wybrane](../ide/media/exploreide-releaseversion.png "ExploreIDE ReleaseVersion")  

3.  Skompiluj rozwiązanie, wybierając **kompilacji**, następnie **Kompiluj rozwiązanie**.  

     ![Kompiluj rozwiązanie, polecenie menu kompilacji](../ide/media/exploreide-buildsolution.png "ExploreIDE BuildSolution")  

Gratulujemy zakończenia instruktażu! Można znaleźć .exe utworzony w katalogu rozwiązania i projektu (...\HelloWPFApp\HelloWPFApp\bin\Release\\). Jeśli chcesz poznać więcej przykładów, zobacz [przykłady dotyczące programu Visual Studio](../ide/visual-studio-samples.md).  

## <a name="see-also"></a>Zobacz także
[Co to jest nowa w programie Visual Studio 2017 r.](../ide/whats-new-in-visual-studio.md)   
[Wprowadzenie do programowania z użyciem programu Visual Studio](../ide/get-started-developing-with-visual-studio.md)   
[Wskazówki dotyczące produktywności](../ide/productivity-tips-for-visual-studio.md)
