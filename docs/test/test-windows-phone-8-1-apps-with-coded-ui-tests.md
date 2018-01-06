---
title: "Test z kodowanych testów interfejsu użytkownika systemu Windows platformy uniwersalnej systemu Windows i aplikacji Phone 8.1 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b866776-f2d5-4823-8d15-919f889db26f
caps.latest.revision: "28"
ms.author: douge
manager: douge
ms.workload: uwp
ms.openlocfilehash: 8aa1bac1a98d8121dcba30dace22483e4a80e1d8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="test-windows-uwp-and-81-phone-apps-with-coded-ui-tests"></a>Test z kodowanych testów interfejsu użytkownika systemu Windows platformy uniwersalnej systemu Windows i aplikacji Phone 8.1

Użyj tego przewodnika tworzenia testów interfejsu użytkownika dla aplikacji platformy uniwersalnej systemu Windows, które można uruchamiać na urządzeniu przenośnym lub emulatorów i aplikacji opartych na języku XAML Phone 8.1.  

## <a name="create-a-simple-windows-phone-app"></a>Tworzenie prostej aplikacji Windows Phone  
  
1.  Utwórz nowy projekt dla pustej aplikacji Windows Phone przy użyciu szablonu Visual C# lub Visual Basic.  
  
     ![Utwórz nową aplikację Windows Phone](../test/media/cuit_phone_app_newproject.png "CUIT_Phone_App_NewProject")  
  
2.  W Eksploratorze rozwiązań Otwórz MainPage.xaml. Z przybornika przeciągnij formant przycisku i kontrolki pola tekstowego na powierzchnię projektu.  
  
     ![Dodaj contols do MainPage.xaml](../test/media/cuit_phone_app_addcontrols.png "CUIT_Phone_App_AddControls")  
  
3.  W oknie właściwości Nazwa formantu przycisku.  
  
     ![Nazwa formantu przycisku](../test/media/cuit_phone_namebutton.png "CUIT_Phone_NameButton")  
  
4.  Nazwa formantu textbox.  
  
     ![Nazwa formantu textbox](../test/media/cuit_phone_nametesxtbox.png "CUIT_Phone_NameTesxtBox")  
  
5.  Na powierzchni projektanta dwukrotnie przycisk i Dodaj następujący kod:  
  
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
  
6.  Naciśnij klawisz F5, aby uruchomić aplikację Windows Phone w emulatorze i sprawdź, czy działa.  
  
     ![Uruchom Windows Phone app](../test/media/cuit_phone_runapp.png "CUIt_Phone_RunApp")  
  
7.  Zamknij emulator.  
  
## <a name="deploy-the-windows-phone-app"></a>Windows Phone wdrażania aplikacji  
  
1.  Przed kodowanego testu interfejsu użytkownika można mapować kontroli aplikacji, należy wdrożyć aplikację.  
  
     ![Windows Phone wdrażanie aplikacji](../test/media/cuit_phone_deploy.png "CUIT_Phone_Deploy")  
  
     Zostanie uruchomiony emulator. Aplikacja jest teraz dostępna do testowania.  
  
     ![Aplikacji wdrożonych na emulatorze](../test/media/cuit_phone_deployed.png "CUIT_Phone_Deployed")  
  
     Zachowaj emulator uruchomiony podczas tworzenia kodowanego testu interfejsu użytkownika.  
  
## <a name="create-a-coded-ui-test-for-the-windows-phone-app"></a>Tworzenie kodowanego testu interfejsu użytkownika dla aplikacji Windows Phone  

[Jak utworzyć kodowane testy interfejsu użytkownika dla aplikacji uniwersalnych platformy systemu Windows (UWP)?](#uwpapps)
  
1.  Dodaj nowy projekt kodowanego testu interfejsu użytkownika do rozwiązania w aplikacji Windows Phone.  
  
     ![Utwórz nowy kodowanego testu interfejsu użytkownika dla Windows Phone](../test/media/cuit_phone_newproject.png "CUIT_Phone_NewProject")  
  
2.  Wybierz Edytuj mapę interfejsu użytkownika za pomocą narzędzia krzyżyk.  
  
     ![Generowanie kodowanego interfejsu użytkownika testu za pomocą innej &#45; narzędzie włosów. ] (../test/media/cuit_phone_howgencodedialog.png "CUIT_Phone_HowGenCodeDialog")  
  
3.  Użyj narzędzia krzyżyk, aby wybrać aplikację, a następnie skopiuj wartość aplikacji **AutomationId** właściwość, która będzie używana później, aby uruchomić aplikację w teście.  
  
     ![Kopiuj wartość AutomationId aplikacji](../test/media/cuit_phone_getautomationid.png "CUIT_Phone_GetAutomationId")  
  
4.  W emulatorze należy uruchomić aplikację i użyj narzędzia krzyżyk, aby wybrać formantu przycisku. Następnie można dodać formantu przycisku do mapy formantów interfejsu użytkownika.  
  
     ![Użyj krzyżyk &#45; narzędzie włosów do mapy formantów](../test/media/cuit_phone_mapbuttoncontrol.png "CUIT_Phone_MapButtonControl")  
  
5.  Aby dodać TextBox — formant do mapy formantów interfejsu użytkownika, powtórz poprzedni krok.  
  
     ![Użyj krzyżyk &#45; formantu textbox narzędzia, a następnie mapować włosów](../test/media/cuit_phone_maptextboxcontrol.png "CUIT_Phone_MapTextBoxControl")  
  
6.  Generuj kod w celu utworzenia kodu zmiany mapy formantów interfejsu użytkownika.  
  
     ![Generowanie kodu na podstawie konstruktora](../test/media/cuit_phone_generatecode.png "CUIT_Phone_GenerateCode")  
  
7.  Użyj narzędzia krzyżyk wybierz kontrolkę pola tekstowego, a następnie wybierz **tekst** właściwości.  
  
     ![Wybierz właściwość Text](../test/media/cuit_phone_textproperty.png "CUIT_Phone_TextProperty")  
  
8.  Dodawanie potwierdzenie. Będzie można użyć w testu Aby sprawdzić, czy wartość jest poprawna.  
  
     ![Dodaj potwierdzenie w teście](../test/media/cuit_phone_addassertion.png "CUIT_Phone_AddAssertion")  
  
9. Dodaj i generowanie kodu dla metody potwierdzenia.  
  
     ![Generuj kod potwierdzenia](../test/media/cuit_phone_generatecodeassertion.png "CUIT_Phone_GenerateCodeAssertion")  
  
10. **Visual C#**  
  
     W Eksploratorze rozwiązań Otwórz plik UIMap.Designer.cs, aby wyświetlić kod, który właśnie został dodany do metody assert i formanty.  
  
     **Visual Basic**  
  
     W Eksploratorze rozwiązań Otwórz plik CodedUITest1.vb. W CodedUITestMethod1() testowania kodu metody, kliknij prawym przyciskiem myszy wywołanie metody potwierdzenia, który został dodany automatycznie `Me.UIMap.AssertMethod1()` i wybierz polecenie **przejdź do definicji**. Spowoduje to otwarcie pliku UIMap.Designer.vb w edytorze kodu, aby wyświetlić kod, który dodaje metody assert i kontrolek.  
  
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
        Assert.AreEqual(this.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text);  
    }  
    ```  
  
    ```vb  
    Public Sub AssertMethod1()  
        Dim uITextBoxEdit As XamlEdit = Me.UIApp1Window.UITextBoxEdit  
  
        'Verify that the 'Text' property of 'textBox' text box equals 'button'  
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text)  
    End Sub  
    ```  
  
     **Kontrolki**  
  
    ```csharp  
    #region Properties  
    public virtual AssertMethod1ExpectedValues AssertMethod1ExpectedValues  
    {  
        get  
        {  
            if ((this.mAssertMethod1ExpectedValues == null))  
            {  
                this.mAssertMethod1ExpectedValues = new AssertMethod1ExpectedValues();  
            }  
            return this.mAssertMethod1ExpectedValues;  
        }  
    }  
  
    public UIApp1Window UIApp1Window  
    {  
        get  
        {  
            if ((this.mUIApp1Window == null))  
            {  
                this.mUIApp1Window = new UIApp1Window();  
            }  
            return this.mUIApp1Window;  
        }  
    }  
    #endregion  
  
    #region Fields  
    private AssertMethod1ExpectedValues mAssertMethod1ExpectedValues;  
  
    private UIApp1Window mUIApp1Window;  
    #endregion  
    ```  
  
    ```vb  
    #Region "Properties"  
    Public ReadOnly Property UIButtonButton() As XamlButton  
        Get  
            If (Me.mUIButtonButton Is Nothing) Then  
                Me.mUIButtonButton = New XamlButton(Me)  
                Me.mUIButtonButton.SearchProperties(XamlButton.PropertyNames.AutomationId) = "button"  
            End If  
            Return Me.mUIButtonButton  
        End Get  
    End Property  
  
    Public ReadOnly Property UITextBoxEdit() As XamlEdit  
        Get  
            If (Me.mUITextBoxEdit Is Nothing) Then  
                Me.mUITextBoxEdit = New XamlEdit(Me)  
                Me.mUITextBoxEdit.SearchProperties(XamlEdit.PropertyNames.AutomationId) = "textBox"  
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
  
11. W Eksploratorze rozwiązań Otwórz plik CodedUITest1.cs lub CodedUITest1.vb. Można teraz dodać kod do metody CodedUTTestMethod1 dla akcji niezbędnych do uruchomienia testu. Użyj formantów, które zostały dodane do UIMap w celu dodania kodu:  
  
    1.  Uruchamianie aplikacji Windows Phone przy użyciu właściwości ID automatyzacji wcześniej skopiowany do Schowka:  
  
        ```csharp  
        XamlWindow myAppWindow = XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");  
        ```  
  
        ```vb  
        XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");  
        ```  
  
    2.  Dodawanie gestów do formantu przycisku Wybierz:  
  
        ```csharp  
        Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);  
        ```  
  
        ```vb  
        Gesture.Tap(Me.UIMap.UIApp1Window.UIButtonButton)  
        ```  
  
    3.  Sprawdź, czy wywołanie metody assert, który został wygenerowany automatycznie pochodzą po uruchomieniu aplikacji i gestów na przycisku Wybierz:  
  
        ```csharp  
        this.UIMap.AssertMethod1();  
        ```  
  
        ```vb  
        Me.UIMap.AssertMethod1()  
        ```  
  
     Po dodaniu kod metody testowej CodedUITestMethod1 powinna wyglądać następująco:  
  
    ```csharp  
    [TestMethod]  
    public void CodedUITestMethod1()  
    {  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
  
        // Launch the app.  
        XamlWindow myAppWindow = XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");  
  
        // Tap the button.  
        Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);  
  
        this.UIMap.AssertMethod1();  
    }  
    ```  
  
    ```vb  
    <CodedUITest>  
    Public Class CodedUITest1  
  
        <TestMethod()>  
        Public Sub CodedUITestMethod1()  
            '              
            ' To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
            '  
            ' Launch the app.  
            XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App")  
  
            '// Tap the button.  
            Gesture.Tap(Me.UIMap.UIApp1Window.UIButtonButton)  
  
            Me.UIMap.AssertMethod1()  
        End Sub  
    ```  
  
## <a name="run-the-coded-ui-test"></a>Uruchamianie kodowanego testu interfejsu użytkownika  
  
1.  Tworzenie testu, a następnie uruchom test przy użyciu Eksploratora testów.  
  
     ![Tworzenie i Uruchamianie testów za pomocą Eksploratora testów](../test/media/cuit_phone_runtestexplorer.png "CUIT_Phone_RunTestExplorer")  
  
     Uruchamia aplikacji Windows Phone, naciśnij przycisk zakończeniu i tekst polu tekstowym właściwości jest wypełniane i weryfikowane przy użyciu metody potwierdzenia.  
  
     ![Uruchamianie testu systemu Windows Phone](../test/media/cuit_phone_runtestexplorerrunning.png "CUIT_Phone_RunTestExplorerRunning")  
  
     Po zakończeniu testu Eksploratora testów potwierdza, że przekazany testu.  
  
     ![Eksplorator wyniki testu](../test/media/cuit_phone_runtestexplorerresults.png "CUIT_Phone_RunTestExplorerResults")  
  
##  <a name="TestingPhoneAppsCodedUI_DataDriven"></a>Użyj opartych na danych kodowanych testów interfejsu użytkownika w aplikacji Windows Phone  
 Aby przetestować różnych warunkach, kodowanego testu interfejsu użytkownika można uruchomić wiele razy z różnych zestawów danych.  
  
 Oparte na danych kodowanych testów interfejsu użytkownika dla Windows Phone są definiowane dla metody testowej przy użyciu atrybutu element DataRow. Następujące przykładowe, x i y Użyj wartości 1 i 2 pierwszej iteracji i -1 -2 dla drugiego iteracji testu.  
  
```  
[DataRow(1, 2, DisplayName = "Add positive numbers")]  
[DataRow(-1, -2, DisplayName = "Add negative numbers")]  
[TestMethod]  
public void DataDrivingDemo_MyTestMethod(int x, int y)  
  
```  
  
## <a name="q--a"></a>Pytania i odpowiedzi  
  
### <a name="q-do-i-have-to-deploy-the-windows-phone-app-in-the-emulator-in-order-to-map-ui-controls"></a>Pytanie: należy ponownie wdrożyć aplikację Windows Phone w emulatorze do mapy formantów interfejsu użytkownika?  
 **A**: tak, kodowanego testu interfejsu użytkownika wymaga, aby być uruchomiony emulator, i można do niego wdrożyć aplikację. W przeciwnym razie zgłosi komunikat o błędzie informujący, nie stwierdzono bez uruchomionego emulatora.  
  
###  <a name="TestingPhoneAppsCodedUI_EmulatorDevice"></a>Pytanie: czy można wykonać testy na emulatorze tylko lub czy można również użyć urządzenia fizycznego?  
 **A**: jedną z tych opcji jest obsługiwana. Obiekt docelowy dla wykonywania testów jest wybierany przez zmianę typu emulatora lub wybranie urządzenia w pasku narzędzi urządzenia. Jeśli urządzenie nie zostanie wybrane, niebieski Phone urządzenie musi być połączony z jednym z portów USB na komputerze.  
  
 ![Wybierz wersję emulator lub urządzenie fizyczne](../test/media/cuit_phone_testtarget.png "CUIT_Phone_TestTarget")  
  
### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>Pytanie: Dlaczego nie widzi opcji Zapisz moje kodowanego testu interfejsu użytkownika w Generuj kod dla okna dialogowego kodowanego testu interfejsu użytkownika?  
 **A**: możliwość rejestrowania nie jest obsługiwana dla aplikacji Windows Phone.  
  
### <a name="q-can-i-create-a-coded-ui-test-for-my-windows-phone-apps-based-on-winjs-silverlight-or-html5"></a>Pytanie: czy można utworzyć kodowanego testu interfejsu użytkownika dla Moje aplikacje Windows Phone, na podstawie WinJS, Silverlight lub HTML5?  
 **A**: nie są obsługiwane tylko XAML na podstawie aplikacji.  
  
### <a name="q-can-i-create-coded-ui-tests-for-my-windows-phone-apps-on-a-system-that-is-not-running-windows-81-or-windows-10"></a>Pytanie: czy można utworzyć kodowane testy interfejsu użytkownika dla Moje aplikacje Windows Phone w systemie, czy nie jest uruchomiona, Windows 8.1 lub Windows 10?  
 **A**: nie, szablonów projektu testu w kodowanego interfejsu użytkownika są dostępne tylko na Windows 8.1 i Windows 10. Aby utworzyć automatyzacji dla aplikacji uniwersalnych platformy systemu Windows (UWP), będziesz potrzebować systemu Windows 10.  

<a name="uwpapps"></a>  
### <a name="q-how-do-i-create-coded-ui-tests-for-universal-windows-platform-uwp-apps"></a>Pytanie: jak tworzyć kodowane testy interfejsu użytkownika dla aplikacji uniwersalnych platformy systemu Windows (UWP)?  
 **A**: w zależności od platformy, na którym w przypadku testowania aplikacji platformy uniwersalnej systemu Windows, tworzenie projektu testu w usłudze kodowanego interfejsu użytkownika w jeden z następujących sposobów:  
  
-   Aplikacji platformy uniwersalnej systemu Windows uruchomionej na komputerze lokalnym zostanie uruchomiony jako aplikację platformy uniwersalnej systemu Windows. Aby to sprawdzić, należy użyć **kodowanego interfejsu użytkownika Testowanie projektu (system Windows)** szablonu. Aby znaleźć ten szablon, podczas tworzenia nowego projektu, przejdź do **Windows**, **uniwersalnych** węzła. Lub przejdź do **Windows**, **systemu Windows 8**, **Windows** węzła.  
  
-   Aplikacji platformy uniwersalnej systemu Windows uruchomionej na urządzeniu przenośnym lub emulator działa jako aplikację telefonów. Aby to sprawdzić, należy użyć **kodowanego interfejsu użytkownika Testowanie projektu (Windows Phone)** szablonu. Aby znaleźć ten szablon, podczas tworzenia nowego projektu, przejdź do **Windows**, **uniwersalnych** węzła. Lub przejdź do **Windows**, **systemu Windows 8**, **Windows Phone** węzła.  
  
 Po utworzeniu projektu tworzenia testu pozostaje taki sam jak przed.  
  
### <a name="q-can-i-select-controls-that-are-outside-the-emulator"></a>Pytanie: czy można zaznaczyć formantów znajdujących się poza emulator?  
 **A**: nie, Konstruktor nie wykrywa je.  
  
### <a name="q-can-i-use-the-coded-ui-test-builder-to-map-controls-using-a-physical-phone-device"></a>Pytanie: czy można użyć konstruktora kodowanego testu interfejsu użytkownika do mapy formantów za pomocą urządzenia fizycznego telefonu?  
 **A**: nie, konstruktora można tylko zamapować elementy interfejsu użytkownika, jeśli aplikacja została wdrożona do emulatora.  
  
### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>Pytanie: Dlaczego nie można zmodyfikować kod w pliku UIMap.Designer?  
 **A**: kod wprowadzonych zmian w pliku UIMapDesigner.cs zostaną zastąpione zawsze Generuj kod przy użyciu UIMap — Konstruktor kodowanego testu interfejsu użytkownika. Jeśli trzeba zmodyfikować nagraną metodę, należy skopiować ją do pliku UIMap.cs i zmienić jej nazwę. Plik UIMap.cs może służyć do zastępowania metod i właściwości w pliku UIMapDesigner.cs. Musisz usunąć odwołanie do oryginalnej metody w pliku Coded UITest.cs, a następnie zastąpić je zmienioną nazwą metody.  
  
### <a name="q-can-i-run-a-coded-ui-test-on-my-windows-phone-app-from-the-command-line"></a>Pytanie: czy mogę uruchomić kodowanego testu interfejsu użytkownika na mojej aplikacji Windows Phone z wiersza polecenia  
 **A**: tak, przy użyciu pliku runsettings można określić urządzenie docelowe dla wykonywania testów. Na przykład:  
  
 **/settings:devicetarget.runsettings "pathToYourCodedUITestDll" vstest.Console.exe**  
  
 Przykładowy plik runsettings:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<RunSettings>  
<MSPhoneTest>  
<!--to specify test execution on device, use a TargetDevice option as follows-->  
<TargetDevice>Device</TargetDevice>  
<!--to specify an emulator instead, use a TargetDevice option like below-->  
<!--<TargetDevice>Emulator 8.1 WVGA 4 inch 512MB</TargetDevice>-->  
</MSPhoneTest>  
</RunSettings>  
```  
  
### <a name="q-what-are-the-differences-between-coded-ui-tests-for-xaml-based-uwp-apps-and-windows-phone-apps"></a>Pytanie: jakie są różnice między kodowane testy interfejsu użytkownika dla aplikacji opartych na języku XAML platformy uniwersalnej systemu Windows i Windows Phone aplikacje?  
 **A**: są to niektóre podstawowe różnice:  
  
|Funkcja|Aplikacji platformy uniwersalnej systemu Windows|Aplikacje Windows Phone|  
|-------------|------------------------|------------------------|  
|Element docelowy dla uruchamiania testów|Komputer lokalny lub zdalny. Może zostać określona komputerów zdalnych, gdy automatyczny przypadek testowy jest używane do uruchamiania testów. Zobacz [Automatyzacja przypadków testowych w programie Microsoft Test Manager](/devops-test-docs/test/automate-a-test-case-in-microsoft-test-manager).|Emulator lub urządzenie. Zobacz, [pytanie: czy można wykonać testy na emulatorze tylko lub czy można również użyć urządzenia fizycznego?](#TestingPhoneAppsCodedUI_EmulatorDevice) w tym temacie.|  
|Wykonywanie z poziomu wiersza polecenia|Plik ustawień nie są wymagane do określenia docelowej.|Wymagany do określenia docelowego pliku Runsettings.|  
|Specjalne klasy formantów powłoki|<xref:Microsoft.VisualStudio.TestTools.UITesting.DirectUIControls.DirectUIControl>|<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl>|  
|Kontrolki WebView w aplikacji XAML|Obsługiwane, jeśli używasz Html * specjalizowany klasy do interakcji z elementów HTML. Zobacz <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>.|Nieobsługiwane.|  
|Wykonywanie testów automatycznych z MTM|Obsługiwane.|Nieobsługiwane.|  
|Testów opartych na danych|Zobacz [testów opartych na danych](../test/creating-a-data-driven-coded-ui-test.md) informacji o użyciu zewnętrznych źródeł danych i źródła danych atrybutu dla metody testowej.|Dane są określony w tekście, przy użyciu atrybutu element DataRow dla metody testowej. Zobacz [opartych na danych użyj kodowanych testów interfejsu użytkownika w aplikacji Windows Phone](#TestingPhoneAppsCodedUI_DataDriven) w tym temacie.|  
  
 Informacji o kodowane testy interfejsu użytkownika dla aplikacji platformy uniwersalnej systemu Windows, temacie [testu Windows aplikacji platformy uniwersalnej systemu Windows za pomocą kodowanych testów interfejsu użytkownika](../test/test-windows-store-8-1-apps-with-coded-ui-tests.md).  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Microsoft Visual Studio Application Lifecycle Management blogu: [przy użyciu kodowanego interfejsu użytkownika do testowania aplikacji Windows Phone opartych na języku XAML](http://blogs.msdn.com/b/visualstudioalm/archive/2014/04/05/using-coded-ui-to-test-xaml-based-windows-phone-apps.aspx?PageIndex=2#comments)  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
