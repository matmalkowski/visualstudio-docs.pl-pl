---
title: Testowanie aplikacji platformy uniwersalnej systemu Windows z kodowanego testu interfejsu użytkownika
ms.date: 05/31/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- uwp
ms.openlocfilehash: 081c61cb0d5a2db28b04ebdd12fd53713b41363f
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34694122"
---
# <a name="create-a-coded-ui-test-to-test-a-uwp-app"></a>Tworzenie kodowanego interfejsu użytkownika teście aplikacji platformy uniwersalnej systemu Windows

W tym artykule opisano sposób tworzenia kodowanego testu interfejsu użytkownika dla aplikacji uniwersalnych platformy systemu Windows (UWP).

## <a name="create-a-uwp-app-to-test"></a>Tworzenie aplikacji platformy uniwersalnej systemu Windows do testowania

Pierwszym krokiem jest do tworzenia prostej aplikacji platformy uniwersalnej systemu Windows, aby uruchomić test przed.

1. W programie Visual Studio Utwórz nowy projekt za pomocą **pusta aplikacja (uniwersalna systemu Windows)** szablonu dla języka Visual C# lub Visual Basic.

     ![Pusta aplikacja uniwersalna systemu Windows szablonu](../test/media/blank-uwp-app-template.png)

1. W **nowego projektu platformy uniwersalnej systemu Windows** okno dialogowe, wybierz opcję **OK** zaakceptować domyślne wersje platformy.

1. Z **Eksploratora rozwiązań**, otwórz *MainPage.xaml*.

   Otwiera plik w **projektanta XAML**.

1. Przeciągnij formant przycisku i kontrolki pola tekstowego z **przybornika** na powierzchnię projektu.

     ![Projekt aplikacji platformy uniwersalnej systemu Windows](../test/media/toolbox-controls.png)

1. Nadaj nazwę do formantów. Wybierz kontrolkę pola tekstowego, a następnie w **właściwości** okna, wprowadź **pole tekstowe** w **nazwa** pola. Wybierz kontrolkę przycisku, a następnie w **właściwości** okna, wprowadź **przycisk** w **nazwa** pola.

1. Kliknij dwukrotnie formantu przycisku i Dodaj następujący kod do treści `Button_Click` metody. Ten kod po prostu ustawia tekst w polu tekstowym Nazwa formantu przycisku Tak, aby wysłać nam, element, aby sprawdzić z kodowanego testu interfejsu użytkownika, które później utworzymy.

   ```csharp
   this.textBox.Text = this.button.Name;
   ```

   ```vb
   Me.textBox.Text = Me.button.Name
   ```

1. Naciśnij klawisz **Ctrl**+**F5** do uruchomienia aplikacji. Powinny zostać wyświetlone informacje podobne do następujących:

   ![Aplikacji platformy uniwersalnej systemu Windows za pomocą przycisku i pole tekstowe](media/uwp-app.png)

## <a name="create-a-coded-ui-test"></a>Tworzenie kodowanego testu interfejsu użytkownika

1. Aby dodać projekt testowy do rozwiązania, kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj** > **nowy projekt**.

1. W **nowy projekt** zaznacz pozycję **kodowanego testu interfejsu użytkownika projektu (uniwersalna systemu Windows)** szablonu. Można znaleźć szablonu w obszarze **uniwersalnych systemu Windows** kategorię w obszarze **Visual C#** lub **Visual Basic**.

     ![Nowy projekt kodowanego testu interfejsu użytkownika](../test/media/coded-ui-test-project-uwp-template.png)

   > [!NOTE]
   > Jeśli nie widzisz **kodowanego interfejsu użytkownika Testowanie projektu (uniwersalna systemu Windows)** szablonu, musisz [zainstalować składnik kodowanego testu interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

1. W **Generuj kod dla kodowanego testu interfejsu użytkownika** okno dialogowe, wybierz opcję **ręcznie Edytuj test**.

     ![Generuj kod dla okno dialogowe kodowanego testu interfejsu użytkownika](../test/media/manually-edit-the-test.png)

1. Jeśli aplikacji platformy uniwersalnej systemu Windows nie jest już uruchomiona, uruchom ją, naciskając klawisz **Ctrl**+**F5**.

1. Otwórz **konstruktora kodowanego testu interfejsu użytkownika** okna dialogowego, umieszczając kursor w `CodedUITestMethod1` metody, a następnie wybierając **testu** > **Generuj kod dla kodowanego testu interfejsu użytkownika**  >  **Używany jest zapisana w kodowanego testu interfejsu użytkownika**.

1. Dodaj formanty do mapy formantów interfejsu użytkownika. Użyj **konstruktora kodowanego testu interfejsu użytkownika** narzędzia krzyżyk, aby wybrać formantu przycisku w aplikacji platformy uniwersalnej systemu Windows. W **dodawania potwierdzeń** okna dialogowego, rozwiń węzeł **mapy formantów interfejsu użytkownika** okienka, jeśli to konieczne, a następnie wybierz **Dodaj formant do mapy formantów interfejsu użytkownika**.

     ![Dodaj formant do mapy interfejsu użytkownika](../test/media/add-control-to-ui-control-map.png)

1. Powtórz poprzedni krok, aby dodać TextBox — formant do mapy formantów interfejsu użytkownika.

1. W **konstruktora kodowanego testu interfejsu użytkownika** okno dialogowe, wybierz opcję **Generuj kod** lub naciśnij klawisz **Ctrl**+**G**. Następnie wybierz **Generuj** tworzyć kod, aby zmiany mapy formantów interfejsu użytkownika.

     ![Generuj kod dla mapy interfejsu użytkownika](../test/media/generate-code-dialog.png)

1. Aby sprawdzić, czy tekst w polu tekstowym zmienia się na **przycisk** po kliknięciu przycisku, kliknij przycisk.

     ![Kliknij przycisk formantu można ustawić wartości tekstowe](../test/media/uwp-app-button-textbox.png)

1. Dodaj potwierdzenie, aby sprawdzić tekst w formancie textbox. Użyj narzędzia krzyżyk wybierz kontrolkę pola tekstowego, a następnie wybierz **tekst** właściwości w **dodawania potwierdzeń** okna dialogowego. Następnie wybierz opcję **Dodaj potwierdzenie** lub naciśnij klawisz **Alt**+**A**. W **komunikat o błędzie potwierdzenia** wprowadź **jest nieoczekiwana wartość pola tekstowego.** a następnie wybierz **OK**.

     ![Wybierz pole tekstowe z krzyżyk i dodać potwierdzenia](../test/media/add-assertion-for-text.png)

1. Generuj kod testu do potwierdzenia. W **konstruktora kodowanego testu interfejsu użytkownika** okno dialogowe, wybierz opcję **Generuj kod**. W **Generuj kod** okno dialogowe, wybierz opcję **Dodaj i Generuj**.

     ![Generuj kod potwierdzenia pole tekstowe](../test/media/add-and-generate-assert-method.png)

   W **Eksploratora rozwiązań**, otwórz *UIMap.Designer.cs* wyświetlić dodany kod metody assert i kontrolek.

   > [!TIP]
   > Jeśli używasz programu Visual Basic, otwórz *CodedUITest1.vb*. Następnie w `CodedUITestMethod1()` testowania kodu metody, kliknij prawym przyciskiem myszy w wywołaniu metody potwierdzenia `Me.UIMap.AssertMethod1()` i wybierz polecenie **przejdź do definicji**. *UIMap.Designer.vb* zostanie otwarty w edytorze kodu i wyświetlić dodany kod dla metody assert i kontrolek.

    > [!WARNING]
    > Nie należy modyfikować *UIMap.designer.cs* lub *UIMap.Designer.vb* pliki bezpośrednio. Jeśli to zrobisz, zmiany zostaną zastąpione podczas generowania testu.

    Metody assert wygląda następująco:

    ```csharp
    public void AssertMethod1()
    {
        #region Variable Declarations
        XamlEdit uITextBoxEdit = this.UIUWPAppWindow.UITextBoxEdit;
        #endregion

        // Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(this.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.");
    }
    ```

    ```vb
    Public Sub AssertMethod1()
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit

        'Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.")
    End Sub
    ```
1. Następnie należy uzyskać **AutomationId** z platformy UWP [aplikacji](#create-a-simple-universal-windows-app) interesujące do testowania. Otwórz program Windows **Start** menu, aby zobaczyć kafelka aplikacji. Przeciągnij narzędzia krzyżyk ![ikonę](media/target-icon.png) z **konstruktora kodowanego testu interfejsu użytkownika** okna dialogowego, aby kafelka aplikacji. Gdy pole blue otaczający kafelka, zwolnij myszy.

   ![Narzędzia krzyżyk](media/cross-hair-tool.png)

   **Dodawania potwierdzeń** otwiera okno dialogowe i wyświetla **AutomationId** dla aplikacji. Kliknij prawym przyciskiem myszy **AutomationId** i wybierz polecenie **wartość kopiowania do Schowka**.

   ![AutomationID w oknie dialogowym Dodaj potwierdzenie](../test/media/automation-id.png)

1. Dodaj kod do metody testowej do uruchomienia aplikacji platformy uniwersalnej systemu Windows. W **Eksploratora rozwiązań**, otwórz *CodedUITest1.cs* lub *CodedUITest1.vb*. Powyżej wywołanie `AssertMethod1`, Dodaj kod, aby uruchomić aplikację platformy uniwersalnej systemu Windows:

   ```csharp
   XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")
   ```

   ```vb
   XamlWindow myAppWindow = XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");
   ```

   Zastąp identyfikator automatyzacji w przykładowym kodzie wartości, który został skopiowany do Schowka w poprzednim kroku.

   > [!IMPORTANT]
   > TRIM początku identyfikator automatyzacji do usuwania znaków, takich jak **P ~**. Jeśli te znaki nie trim, zgłasza testu `Microsoft.VisualStudio.TestTools.UITest.Extension.PlaybackFailureException` podczas próby uruchomienia aplikacji.

1. Następnie dodaj kod do metody testowej kliknięcie przycisku. W wierszu po `XamlWindow.Launch`, Dodaj gestu naciśnięcie przycisku formantu przycisku:

   ```csharp
   Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);
   ```

   ```vb
   Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)
   ```

   Po dodaniu kod pełną `CodedUITestMethod1` metody testowej powinna wyglądać następująco:

   ```csharp
   [TestMethod]
   public void CodedUITestMethod1()
   {
       XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");

       Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);

       // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
       this.UIMap.AssertMethod1();
   }
   ```

   ```vb
   <CodedUITest(CodedUITestType.WindowsStore)>
   Public Class CodedUITest1

       <TestMethod()>
       Public Sub CodedUITestMethod1()

           ' Launch the app.
           XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")

           '// Tap the button.
           Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)

           Me.UIMap.AssertMethod1()
       End Sub
   ```

1. Tworzenie projektu testowego, a następnie otwórz **Eksploratora testów** wybierając **Test** > **systemu Windows** > **Eksploratora testów**.

1. Wybierz **Uruchom wszystkie** do uruchomienia testu.

   Wybrany zostanie otwarta aplikacja przycisk i pole tekstowe **tekst** właściwości jest wypełnione. Metody assert weryfikuje pole tekstowe **tekst** właściwości.

   Po zakończeniu testu, **Eksploratora testów** Wyświetla, które pomyślnie testu.

   ![Wyświetla przekazany testu w Eksploratorze testów](../test/media/test-explorer-coded-ui-test-passed.png)

## <a name="q--a"></a>Pytania i odpowiedzi

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>Pytanie: Dlaczego nie widzi opcji Zapisz moje kodowanego testu interfejsu użytkownika w Generuj kod dla okna dialogowego kodowanego testu interfejsu użytkownika?

**A**: możliwość rejestrowania nie jest obsługiwana dla aplikacji platformy uniwersalnej systemu Windows.

### <a name="q-can-i-create-a-coded-ui-test-for-my-uwp-apps-based-on-winjs"></a>Pytanie: czy można utworzyć kodowanego testu interfejsu użytkownika dla mojej aplikacji platformy uniwersalnej systemu Windows oparte na WinJS?

**A**: nie są obsługiwane tylko aplikacji opartych na języku XAML.

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>Pytanie: Dlaczego nie można zmodyfikować kod w pliku UIMap.Designer?

**A**: code wszelkie zmiany wprowadzone w *UIMapDesigner.cs* pliku zostaną zastąpione w każdym wygenerowaniu kodu za pomocą **konstruktora kodowanego testu interfejsu użytkownika**. Jeśli masz zmodyfikuj metodę zarejestrowane, skopiuj go do *UIMap.cs* pliku i jego nazwa zostanie zmieniona. *UIMap.cs* plików może służyć do przesłonięcia metod i właściwości w *UIMapDesigner.cs* pliku. Usuń odwołanie do oryginalnej metody w *CodedUITest.cs* pliku i zamień ją na nazwę zmieniono nazwę metody.

## <a name="see-also"></a>Zobacz także

- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Ustaw właściwości Unikatowy automatyzacji dla formantów platformy uniwersalnej systemu Windows](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)