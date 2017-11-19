---
title: "Testowanie aplikacji uniwersalnej systemu Windows z kodowanych testów interfejsu użytkownika | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8d9c15e-ce3c-401a-86ec-c5c124a239d8
caps.latest.revision: "23"
ms.author: douge
manager: douge
ms.openlocfilehash: 9680f9886e4aeaefe8c476b7e9fff46fb3e24182
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2017
---
# <a name="test-windows-uwp-apps-with-coded-ui-tests"></a>Testowanie aplikacji uniwersalnej systemu Windows z kodowanych testów interfejsu użytkownika

Użyj tego przewodnika tworzenia testów interfejsu użytkownika dla aplikacji platformy uniwersalnej systemu Windows i opartych na języku XAML 8.1 aplikacji. 
  
## <a name="create-a-simple-uwp-app"></a>Tworzenie prostej aplikacji platformy uniwersalnej systemu Windows  
  
1.  Jeśli chcesz uruchomić kodowane testy interfejsu użytkownika dla aplikacji platformy uniwersalnej systemu Windows opartych na języku XAML, należy najpierw [Ustawianie unikatowej właściwości automatyzacji identyfikujący każdego formantu](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md).  
  
     Na **narzędzia** menu wskaż **opcje** , a następnie wybierz **Edytor tekstu**, następnie **XAML**, a na końcu **różne** .  
  
     Zaznacz pole wyboru, aby automatycznie nazwa elementy interakcyjne przy tworzeniu.  
  
     ![XAML różne opcje](../test/media/cuit_windowsstoreapp_b.png "CUIT_WindowsStoreApp_B")  
  
2.  Utwórz nowy projekt dla aplikacji platformy uniwersalnej systemu Windows przy użyciu szablonu Visual C# lub Visual Basic na podstawie pustego XAML.  
  
     ![Tworzenie aplikacji sieci &#40; XAML &#41; ] (../test/media/cuit_windowsstoreapp_newproject_blankstoreapp.png "CUIT_WindowsStoreApp_NewProject_BlankStoreApp")  
  
3.  W Eksploratorze rozwiązań Otwórz MainPage.xaml. Z przybornika przeciągnij formant przycisku i kontrolki pola tekstowego na powierzchnię projektu.  
  
     ![Projekt aplikacji platformy uniwersalnej systemu Windows](../test/media/cuit_windowsstoreapp_design.png "CUIT_WindowsStoreApp_Design")  
  
4.  Kliknij dwukrotnie formantu przycisku i Dodaj następujący kod:  
  
    ```csharp  
    private void button_Click_1(object sender, RoutedEventArgs e)  
    {  
        this.textBox.Text = this.button.Name;  
    }  
  
    ```  
  
    ```vb  
    Public NotInheritable Class MainPage  
        Inherits Page  
  
        Private Sub button_Click(sender As Object, e As RoutedEventArgs) Handles Button.Click  
            Me.textBox.Text = Me.button.Name  
        End Sub  
    End Class  
    ```  
  
5.  Naciśnij klawisz F5, aby uruchomić aplikację platformy uniwersalnej systemu Windows.  
  
## <a name="create-and-run-a-coded-ui-test-for-the-uwp-app"></a>Tworzenie i uruchamianie kodowanego testu interfejsu użytkownika dla aplikacji platformy uniwersalnej systemu Windows  

[Jak utworzyć kodowane testy interfejsu użytkownika dla aplikacji uniwersalnych platformy systemu Windows (UWP)?](#uwpapps)
  
1.  Tworzenie nowego kodowanego interfejsu użytkownika projektu testu dla aplikacji platformy uniwersalnej systemu Windows.  
  
     ![Nowy projekt kodowanego interfejsu użytkownika tet &#40; &#41; w aplikacji platformy uniwersalnej systemu Windows ] (../test/media/cuit_windowsstore_newproject.png "CUIT_WindowsStore_NewProject")  
  
2.  Wybierz Edytuj mapę interfejsu użytkownika za pomocą narzędzia krzyżyk.  
  
     ![Wybierz pozycję Edytuj mapę interfejsu użytkownika lub Dodaj asercje](../test/media/cuit_windowsstoreapp_createproject_gencodedialog.png "CUIT_WindowsStoreApp_CreateProject_GenCodeDialog")  
  
3.  Użyj narzędzia krzyżyk w Konstruktorze kodowanego testu interfejsu użytkownika, aby wybierz Kafelek aplikacji, kliknij prawym przyciskiem myszy **AutomationId** i wybierz polecenie **wartość kopiowania do Schowka**. Wartość w Schowku posłuży później dla działania zapisywania można uruchomić aplikacji do testowania.  
  
     ![Kopiuj do Schowka AutomationId](../test/media/cuit_windows_store_tileautomationid.png "CUIT_Windows_Store_TileAutomationID")  
  
4.  W uruchomionej aplikacji platformy uniwersalnej systemu Windows należy użyć narzędzia krzyżyk wybranie formantu przycisku i formantu textbox. Po dodaniu każdego formantu, wybierz **Dodaj formant do mapy formantów interfejsu użytkownika** przycisku w pasku narzędzi Konstruktora kodowanego testu interfejsu użytkownika.  
  
     ![Dodaj formant do mapy interfejsu użytkownika](../test/media/cuit_windowsstoreapp_uimap.png "CUIT_WindowsStoreApp_UIMap")  
  
5.  Wybierz **Generuj kod** przycisku w pasku narzędzi Konstruktora kodowanego testu interfejsu użytkownika, a następnie wybierz pozycję **Generuj** tworzyć kod, aby zmiany mapy formantów interfejsu użytkownika.  
  
     ![Generuj kod dla mapy interfejsu użytkownika](../test/media/cuit_windowsstoreapp_generate.png "CUIT_WindowsStoreApp_Generate")  
  
6.  Wybierz przycisk, aby ustawić wartość w polu tekstowym.  
  
     ![Kliknij przycisk formantu można ustawić wartości tekstowe](../test/media/cuit_windowsstoreapp_clickbutton.png "CUIT_WindowsStoreApp_ClickButton")  
  
7.  Użyj narzędzia krzyżyk wybierz kontrolkę pola tekstowego, a następnie wybierz **tekst** właściwości.  
  
     ![Wybierz właściwość Text](../test/media/cuit_windowsstoreapp_selecttextproperty.png "CUIT_WindowsStoreApp_SelectTextProperty")  
  
8.  Dodawanie potwierdzenie. Będzie można użyć w testu Aby sprawdzić, czy wartość jest poprawna.  
  
     ![Wybierz testbox z między &#45; włosów i dodać potwierdzenia](../test/media/cuit_windowsstoreapp_textbox_addassertion.png "CUIT_WindowsStoreApp_Textbox_AddAssertion")  
  
9. Dodaj i generowanie kodu do potwierdzenia.  
  
     ![Generowanie kodu dla pola tekstowego potwierdzenia](../test/media/cuit_windowsstoreapp_textbox_generate_assertion.png "CUIT_WindowsStoreApp_Textbox_Generate_Assertion")  
  
10. **Visual C#**  
  
     W Eksploratorze rozwiązań Otwórz plik UIMap.Designer.cs, aby wyświetlić dodany kod dla metody assert i kontrolek.  
  
     **Visual Basic**  
  
     W Eksploratorze rozwiązań Otwórz plik CodedUITest1.vb i następnie w kodzie metody CodedUITestMethod1() testu, kliknij prawym przyciskiem myszy wywołanie metody potwierdzenia, który został dodany automatycznie `Me.UIMap.AssertMethod1()` i wybierz polecenie **przejdź do definicji**. Spowoduje to otwarcie pliku UIMap.Designer.vb w edytorze kodu, więc można wyświetlić widoku dodany kod dla metody assert i kontrolek.  
  
    > [!WARNING]
    >  Nie należy modyfikować pliku UIMap.designer.cs lub UIMap.Designer.vb bezpośrednio. Jeśli to zrobisz, zmiany w pliku zostaną zastąpione zawsze, gdy test jest generowany.  
  
     **Assert — metoda**  
  
    ```csharp  
    public void AssertMethod1()  
    {  
        #region Variable Declarations  
        XamlEdit uITextBoxEdit = this.UIApp1Window.UITextBoxEdit;  
        #endregion  
  
        // Verify that the 'Text' property of 'textBox' text box equals 'button'  
        Assert.AreEqual(this.AssertMethod3ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text);  
    }  
    ```  
  
    ```vb  
    Public Sub AssertMethod1()  
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit  
  
        'Verify that the 'Text' property of 'textBox' text box equals 'button'  
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text)  
    End Sub  
    ```  
  
     **Formanty**  
  
    ```csharp  
    #region Properties  
    public XamlButton UIButtonButton  
    {  
        get  
        {  
            if ((this.mUIButtonButton == null))  
            {  
                this.mUIButtonButton = new XamlButton(this);  
                #region Search Criteria  
                this.mUIButtonButton.SearchProperties[XamlButton.PropertyNames.AutomationId] = "button";  
                this.mUIButtonButton.WindowTitles.Add("App1");  
                #endregion  
            }  
            return this.mUIButtonButton;  
        }  
    }  
  
    public XamlEdit UITextBoxEdit  
    {  
        get  
        {  
            if ((this.mUITextBoxEdit == null))  
            {  
                this.mUITextBoxEdit = new XamlEdit(this);  
                #region Search Criteria  
                this.mUITextBoxEdit.SearchProperties[XamlEdit.PropertyNames.AutomationId] = "textBox";  
                this.mUITextBoxEdit.WindowTitles.Add("App1");  
                #endregion  
            }  
            return this.mUITextBoxEdit;  
        }  
    }  
    #endregion  
  
    #region Fields  
    private XamlButton mUIButtonButton;  
  
    private XamlEdit mUITextBoxEdit;  
    #endregion  
    ```  
  
    ```vb  
    #Region "Properties"  
    Public ReadOnly Property UIButtonButton() As XamlButton  
        Get  
            If (Me.mUIButtonButton Is Nothing) Then  
                Me.mUIButtonButton = New XamlButton(Me)  
                Me.mUIButtonButton.SearchProperties(XamlButton.PropertyNames.AutomationId) = "button"  
                Me.mUIButtonButton.WindowTitles.Add("App2")  
            End If  
            Return Me.mUIButtonButton  
        End Get  
    End Property  
  
    Public ReadOnly Property UITextBoxEdit() As XamlEdit  
        Get  
            If (Me.mUITextBoxEdit Is Nothing) Then  
                Me.mUITextBoxEdit = New XamlEdit(Me)  
                Me.mUITextBoxEdit.SearchProperties(XamlEdit.PropertyNames.AutomationId) = "textBox"  
                Me.mUITextBoxEdit.WindowTitles.Add("App2")  
            End If  
            Return Me.mUITextBoxEdit  
        End Get  
    End Property  
    #End Region  
  
    #Region "Fields"  
    Private mUIButtonButton As XamlButton  
  
    Private mUITextBoxEdit As XamlEdit  
    #End Region  
    ```  
  
11. W Eksploratorze rozwiązań Otwórz plik CodedUITest1.cs lub CodedUITest1.vb. Można teraz dodać kod do metody CodedUTTestMethod1 akcje trzeba uruchomić test przy użyciu to formanty dodawane do UIMap:  
  
    1.  Uruchamianie aplikacji platformy uniwersalnej systemu Windows przy użyciu właściwości ID automatyzacji wcześniej skopiowany do Schowka:  
  
        ```csharp  
        XamlWindow.Launch("8ebca7c4-effe-4c86-9998-068daccee452_cyrqexqw8cc7c!App")  
        ```  
  
        ```vb  
        XamlWindow myAppWindow = XamlWindow.Launch("7254db3e-20a7-424e-8e05-7c4dabf4f28d_cyrqexqw8cc7c!App");  
        ```  
  
    2.  Dodawanie gestów do formantu przycisku Wybierz:  
  
        ```csharp  
        Gesture.Tap(this.UIMap.UIApp1Window. UIButtonButton);  
        ```  
  
        ```vb  
        Gesture.Tap(Me.UIMap.UIApp2Window. UIButtonButton)  
        ```  
  
    3.  Sprawdź, czy wywołanie metody assert, który został wygenerowany automatycznie pochodzą po uruchomieniu aplikacji i gestów na przycisku Wybierz:  
  
        ```csharp  
        this.UIMap.AssertMethod1();  
        ```  
  
        ```vb  
        Me.UIMap.AssertMethod1()  
        ```  
  
     Po dodaniu kod, metody testowej CodedUITestMethod1 powinna wyglądać następująco:  
  
    ```csharp  
    [TestMethod]  
    public void CodedUITestMethod1()  
    {  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
  
        // Launch the app.  
        XamlWindow myAppWindow = XamlWindow.Launch("7254db3e-20a7-424e-8e05-7c4dabf4f28d_cyrqexqw8cc7c!App");  
  
        // Tap the button.  
        Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);  
  
        this.UIMap.AssertMethod1();  
    }  
    ```  
  
    ```vb  
    <CodedUITest(CodedUITestType.WindowsStore)>  
    Public Class CodedUITest1  
  
        <TestMethod()>  
        Public Sub CodedUITestMethod1()  
            '              
            ' To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
            '  
  
            ' Launch the app.  
            XamlWindow.Launch("8ebca7c4-effe-4c86-9998-068daccee452_cyrqexqw8cc7c!App")  
  
            '// Tap the button.  
            Gesture.Tap(Me.UIMap.UIApp2Window.UIButtonButton)  
  
            Me.UIMap.AssertMethod1()  
        End Sub  
    ```  
  
12. Tworzenie testu, a następnie uruchom test przy użyciu Eksploratora testów.  
  
     ![Uruchamianie kodowanego testu interfejsu użytkownika z poziomu Eksploratora testów](../test/media/cuit_windowsstoreapp_runtest.png "CUIT_WindowsStoreApp_RunTest")  
  
     Uruchomieniu aplikacji platformy uniwersalnej systemu Windows, naciśnij przycisk zakończeniu i tekst polu tekstowym właściwości jest wypełniane i weryfikowane przy użyciu metody potwierdzenia.  
  
     ![Uruchamianie kodowanego testu interfejsu użytkownika](../test/media/cuit_windowsstoreapp_running.png "CUIT_WindowsStoreApp_Running")  
  
     Po zakończeniu testu, Eksploratora testów Wyświetla, że przekazany testu.  
  
     ![Przekazany Wyświetla testu w Eksploratorze testów](../test/media/cuit_windowsstorapp_passedtest.png "CUIT_WindowsStorApp_PassedTest")  
  
## <a name="q--a"></a>Pytania i odpowiedzi  
  
#### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>Pytanie: Dlaczego nie widzi opcji Zapisz moje kodowanego testu interfejsu użytkownika w Generuj kod dla kodowanego testu interfejsu użytkownika okna dialogowego? **  
  
**A**: możliwość rejestrowania nie jest obsługiwana dla aplikacji platformy uniwersalnej systemu Windows.  
  
#### <a name="q-can-i-create-a-coded-ui-test-for-my-uwp-apps-based-on-winjs"></a>Pytanie: czy mogę tworzyć kodowanego testu interfejsu użytkownika dla mojej aplikacji platformy uniwersalnej systemu Windows oparte na WinJS? **  

**A**: nie są obsługiwane tylko XAML na podstawie aplikacji.  
  
#### <a name="q-can-i-create-coded-ui-tests-for-my-uwp-apps-on-a-system-that-is-not-running-windows-81-or-windows-10"></a>Pytanie: czy mogę tworzyć kodowane testy interfejsu użytkownika dla mojej aplikacji platformy uniwersalnej systemu Windows w systemie, czy nie jest uruchomiona, Windows 8.1 lub Windows 10? **  
  
**A**: nie, szablonów projektu testu w kodowanego interfejsu użytkownika są dostępne tylko na Windows 8.1 i Windows 10. Aby utworzyć automatyzacji dla aplikacji uniwersalnych platformy systemu Windows (UWP), będziesz potrzebować systemu Windows 10.  

<a name="uwpapps"></a>  
#### <a name="q-how-do-i-create-coded-ui-tests-for-universal-windows-platform-uwp-apps"></a>Pytanie: jak tworzyć kodowane testy interfejsu użytkownika dla aplikacji systemu Windows platformy Uniwersalnej? **  
  
**A**: w zależności od platformy, na którym w przypadku testowania aplikacji platformy uniwersalnej systemu Windows, tworzenie projektu testu w usłudze kodowanego interfejsu użytkownika w jeden z następujących sposobów:  
  
- Aplikacji platformy uniwersalnej systemu Windows uruchomionej na komputerze lokalnym zostanie uruchomiony jako aplikację platformy uniwersalnej systemu Windows. Aby to sprawdzić, należy użyć **kodowanego interfejsu użytkownika Testowanie projektu (system Windows)** szablonu. Aby znaleźć ten szablon, podczas tworzenia nowego projektu, przejdź do **Windows**, **uniwersalnych** węzła. Lub przejdź do **Windows**, **systemu Windows 8**, **Windows** węzła.  
  
- Aplikacji platformy uniwersalnej systemu Windows uruchomionej na urządzeniu przenośnym lub emulator działa jako aplikację telefonów. Aby to sprawdzić, należy użyć **kodowanego interfejsu użytkownika Testowanie projektu (Windows Phone)** szablonu. Aby znaleźć ten szablon, podczas tworzenia nowego projektu, przejdź do **Windows**, **uniwersalnych** węzła. Lub przejdź do **Windows**, **systemu Windows 8**, **Windows Phone** węzła.  
  
Po utworzeniu projektu tworzenia testu pozostaje taki sam jak przed.  
  
#### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>Pytanie: Dlaczego nie można zmodyfikować kod w pliku UIMap.Designer? **  
  
**A**: kod wprowadzonych zmian w pliku UIMapDesigner.cs zostaną zastąpione zawsze Generuj kod przy użyciu UIMap — Konstruktor kodowanego testu interfejsu użytkownika. Jeśli trzeba zmodyfikować nagraną metodę, należy skopiować ją do pliku UIMap.cs i zmienić jej nazwę. Plik UIMap.cs może służyć do zastępowania metod i właściwości w pliku UIMapDesigner.cs. Musisz usunąć odwołanie do oryginalnej metody w pliku Coded UITest.cs, a następnie zastąpić je zmienioną nazwą metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
 [Ustawianie unikatowej właściwości automatyzacji dla formantów platformy uniwersalnej systemu Windows do testowania](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)
