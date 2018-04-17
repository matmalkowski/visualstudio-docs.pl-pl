---
title: Tworzenie niestandardowego edytora HTTP dla edytora testów wydajności sieci Web w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, custom HTTP body editor
ms.assetid: a0b2d8ff-3e2a-487e-9172-90047174f336
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: c53d4db3f413ad8cf4f0b615db18bd5fb6368128
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor"></a>Porady: tworzenie niestandardowego edytora HTTP dla edytora testów wydajności sieci Web

Można utworzyć niestandardowego edytora zawartości, która pozwala na edycję zawartości treści ciągu lub zawartości binarnej treści żądania usługi sieci Web, na przykład protokołu SOAP, REST asmx, wcf, RIA i innych typów żądań usługi sieci Web.

 Można zaimplementować te rodzaje edytory:

-   **Edytor zawartości ciągu** ten sposób jest implementowany przy użyciu <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> interfejsu.

-   **Edytor plików binarnych zawartości** ten sposób jest implementowany przy użyciu <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> interfejsu.

Te interfejsy są zawarte w <xref:Microsoft.VisualStudio.TestTools.WebTesting> przestrzeni nazw.

## <a name="create-a-windows-control-library-project"></a>Tworzenie projektu Biblioteka formantów systemu Windows

### <a name="create-a-user-control-by-using-a-windows-control-library-project"></a>Tworzenie formantu użytkownika przy użyciu projektu Biblioteka formantów systemu Windows

1.  W programie Visual Studio na **pliku** menu, wybierz **nowy** , a następnie wybierz **projektu**.

     **Nowy projekt** zostanie wyświetlone okno dialogowe.

2.  W obszarze **zainstalowane szablony**, wybierz opcję **Visual Basic** lub **Visual C#** w zależności od swoich preferencji programowania, a następnie wybierz **systemuWindows**.

    > [!NOTE]
    > W przykładzie użyto Visual C#.

3.  Na liście szablonów wybierz **Biblioteka formantów formularzy systemu Windows**.

4.  W polu tekstowym Nazwa wpisz nazwę, na przykład `MessageEditors`i wybierz polecenie **OK**.

    > [!NOTE]
    > W przykładzie użyto MessageEditors.

     Projekt zostanie dodany do nowego rozwiązania i <xref:System.Windows.Forms.UserControl> nazwane UserControl1.cs są prezentowane w projektancie.

5.  Z **przybornika**w obszarze **formanty standardowe** kategorii, przeciągnij <xref:System.Windows.Forms.RichTextBox> na powierzchnię UserControl1.

6.  Wybierz akcję symbolu tagu (![symbol tagu inteligentnego](../test/media/vs_winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.RichTextBox> kontroli, a następnie wybierz i **Zadokuj w kontenerze nadrzędnym**.

7.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projektu biblioteki formularzy systemu Windows i wybierz **właściwości**.

8.  W oknie właściwości wybierz **aplikacji** kartę.

9. W **platformy docelowej** listy rozwijanej wybierz **.NET Framework 4**.

10. Zostanie wyświetlone okno dialogowe docelowego Framework zmiany.

11. Wybierz **tak**.

12. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **odwołania** a następnie wybierz węzeł **Dodaj odwołanie**.

13. **Dodaj odwołanie** zostanie wyświetlone okno dialogowe.

14. Wybierz. **NET** , przewiń w dół i wybierz **Microsoft.VisualStudio.QualityTools.WebTestFramework** , a następnie wybierz **OK**.

15. Jeśli widok projektanta nie jest jeszcze otwarty, w Eksploratorze rozwiązań, kliknij prawym przyciskiem myszy **UserControl1.cs** , a następnie wybierz **Widok projektanta**.

16. Na powierzchni projektu, kliknij prawym przyciskiem myszy i wybierz **kod widoku**.

17. (Opcjonalnie) Zmień nazwę klasy i konstruktora z UserControl1 na opisową nazwę, na przykład MessageEditorControl:

    > [!NOTE]
    > W przykładzie użyto MessageEditorControl.

    ```csharp
    namespace MessageEditors
    {
        public partial class MessageEditorControl : UserControl
        {
            public MessageEditorControl()
            {
                InitializeComponent();
            }
        }
    }
    ```

18. Dodaj następujące właściwości, aby włączyć pobieranie i ustawianie tekstu w RichTextBox1. <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> Interfejsu użyje EditString i <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> użyje EditByteArray:

   ```csharp
   public String EditString
   {
       get
       {
           return this.richTextBox1.Text;
       }
       set
       {
           this.richTextBox1.Text = value;
       }
   }

   public byte[] EditByteArray
   {
       get
       {
           return System.Convert.FromBase64String(richTextBox1.Text);
       }
       set
       {
           richTextBox1.Text = System.Convert.ToBase64String(value, 0, value.Length);
       }
   }
   ```

## <a name="add-a-class-for-to-the-windows-control-library-project"></a>Dodaj klasę do projektu Biblioteka formantów systemu Windows

Dodaj klasę do projektu. Będzie można użyć do wdrożenia <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> i <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> interfejsów.

**Przegląd kodu w tej procedurze**

MessageEditorControl <xref:System.Windows.Forms.UserControl> utworzony w poprzedniej procedurze zostanie uruchomiony jako messageEditorControl:

```csharp
private MessageEditorControl messageEditorControl
```

 Wystąpienie messageEditorControl znajduje się w obrębie wtyczki okna dialogowego, która jest tworzona przy <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.CreateEditor*> metody. Ponadto messageEditorControl w <xref:System.Windows.Forms.RichTextBox> jest wypełniana zawartości <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>. Jednak tworzenie wtyczki nie może wystąpić, chyba że <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> zwraca `true`. W przypadku tego edytora <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> zwraca `true` Jeśli <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> w <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> zawiera "xml".

 Po zakończeniu edycji ciągów tekstowych i użytkownik klika polecenie **OK** w oknie dialogowym wtyczki <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.GetNewValue*> jest wywoływana w celu pobrania tekstu jako ciągiem, a aktualizacja **ciągów tekstowych** w żądaniu w sieci Web Test wydajności edytora.

### <a name="to-create-a-class-and-implement-the-istringhttpbodyeditorplugin-interface-code"></a>Aby utworzyć klasę i implementowania kodu interfejsu IStringHttpBodyEditorPlugin

1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt Biblioteka formantów formularzy systemu Windows i wybierz **Dodaj nowy element**.

2.  **Dodaj nowy element** zostanie wyświetlone okno dialogowe.

3.  Wybierz **klasy**.

4.  W **nazwa** tekstu wpisz nazwę opisową dla tej klasy, na przykład `MessageEditorPlugins`.

5.  Wybierz **dodać**.

     Class1 zostanie dodany do projektu i wyświetlone w edytorze kodu.

6.  W edytorze kodu, dodaj następującą instrukcję using:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    ```

7.  Pisanie lub skopiuj następujący kod, aby utworzyć wystąpienia klasy XmlMessageEditor z <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> interfejsu i wdrożenie wymaganych metod:

    ```csharp
    /// <summary>
    /// Editor for generic text based hierarchical messages such as XML and JSON.
    /// </summary>
    public class XmlMessageEditor : IStringHttpBodyEditorPlugin
    {
        public XmlMessageEditor()
        {
        }

        /// <summary>
        /// Determine if this plugin supports the content type.
        /// </summary>
        /// <param name="contentType">The content type to test.</param>
        /// <returns>Returns true if the plugin supports the specified content type.</returns>
        public bool SupportsContentType(string contentType)
        {
            return contentType.ToLower().Contains("xml");
        }

        /// <summary>
        /// Create a UserControl to edit the specified bytes.
        /// This control will be hosted in the
        /// plugin dialog which provides OK and Cancel buttons.
        /// </summary>
        /// <param name="contentType">The content type of the BinaryHttpBody.</param>
        /// <param name="initialValue">The bytes to edit.  The bytes are the payload of a BinaryHttpBody.</param>
        /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
        public object CreateEditor(string contentType, string initialValue)
        {
            messageEditorControl = new MessageEditorControl();
            messageEditorControl.EditString = initialValue;
            return this.messageEditorControl;
        }

        /// <summary>
        /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
        /// </summary>
        public string GetNewValue()
        {
            return messageEditorControl.EditString;
        }

        private MessageEditorControl messageEditorControl;
    }
    ```

## <a name="add-a-ibinaryhttpbodyeditorplugin-to-the-class"></a>Dodaj IBinaryHttpBodyEditorPlugin do klasy

Implementowanie <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> interfejsu.

**Przegląd kodu w tej procedurze**

Implementacja kodu dla <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> interfejsu jest podobny do <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> opisanych w poprzedniej procedurze. Jednak binarna wersja używa tablicę bajtów do obsługi danych binarnych zamiast ciągu.

MessageEditorControl <xref:System.Windows.Forms.UserControl> utworzony w pierwszym procedury tworzenia wystąpienia klasy jako messageEditorControl:

```csharp
private MessageEditorControl messageEditorControl
```

Wystąpienie messageEditorControl znajduje się w obrębie wtyczki okna dialogowego, która jest tworzona przy <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.CreateEditor*> metody. Ponadto messageEditorControl w <xref:System.Windows.Forms.RichTextBox> jest wypełniana zawartości <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>. Jednak tworzenie wtyczki nie może wystąpić, chyba że <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> zwraca `true`. W przypadku tego edytora <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> zwraca `true` Jeśli <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> w <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> zawiera "msbin1".

Po zakończeniu edycji ciągów tekstowych i użytkownik klika polecenie **OK** w oknie dialogowym wtyczki <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.GetNewValue*> jest wywoływana w celu pobrania tekstu jako ciągiem, a aktualizacja **BinaryHttpBody.Data** w żądaniu w sieci Web testów wydajności Edytor.

### <a name="to-add-the-ibinaryhttpbodyeditorplugin-to-the-class"></a>Aby dodać IBinaryHttpBodyEditorPlugin do klasy

-   Pisanie lub skopiuj następujący kod w klasie XmlMessageEditor dodane w poprzedniej procedurze do utworzenia wystąpienia klasy Msbin1MessageEditor z <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> interfejsu i wdrożenie wymaganych metod:

    ```csharp
    /// <summary>
        /// Editor for MSBin1 content type (WCF messages)
        /// </summary>
        public class Msbin1MessageEditor : IBinaryHttpBodyEditorPlugin
        {
            /// <summary>
            ///
            /// </summary>
            public Msbin1MessageEditor()
            {
            }

            /// <summary>
            /// Determine if this plugin supports a content type.
            /// </summary>
            /// <param name="contentType">The content type to test.</param>
            /// <returns>Returns true if the plugin supports the specified content type.</returns>
            public bool SupportsContentType(string contentType)
            {
                return contentType.ToLower().Contains("msbin1");
            }

            /// <summary>
            /// Create a UserControl to edit the specified bytes.  This control will be hosted in the
            /// plugin dialog which provides OK and Cancel buttons.
            /// </summary>
            /// <param name="contentType">The content type of the BinaryHttpBody.</param>
            /// <param name="initialValue">The bytes to edit.  The bytes are the payload of a BinaryHttpBody.</param>
            /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
            public object CreateEditor(string contentType, byte[] initialValue)
            {
                messageEditorControl = new MessageEditorControl();
                messageEditorControl.EditByteArray = initialValue;
                return messageEditorControl;
            }

            /// <summary>
            /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
            /// </summary>
            public byte[] GetNewValue()
            {
                return messageEditorControl.EditByteArray;
            }

            private MessageEditorControl messageEditorControl;
            private object originalMessage;
        }
    ```

## <a name="build-and-deploy-the-plug-ins"></a>Skompiluj i wdróż dodatki plug-in

### <a name="to-build-and-deploy-the-resulting-dll-for-the-istringhttpbodyeditorplugin-and-ibinaryhttpbodyeditorplugin"></a>Do tworzenia i wdrażania wynikowa Biblioteka dll dla IStringHttpBodyEditorPlugin i IBinaryHttpBodyEditorPlugin

1.  W menu kompilacji, wybierz **kompilacji \<Biblioteka formantów formularzy systemu Windows, nazwa projektu >**.

2.  Zamknij wszystkie wystąpienia programu Visual Studio.

    > [!NOTE]
    > Zamknięcie programu Visual Studio upewnij się, że *.dll* plik nie jest zablokowany przed podjęciem próby skopiuj go.

3.  Skopiuj wynikowy *.dll* plików z projektów *bin\debug* folder (na przykład *MessageEditors.dll*) do katalogu %ProgramFiles%\Microsoft Visual Studio\2017\\ <edition>\Common7\IDE\PrivateAssemblies\WebTestPlugins.

4.  Otwórz program Visual Studio.

     *.Dll* teraz jest zarejestrowana w programie Visual Studio.

## <a name="verify-the-plug-ins-using-a-web-performance-test"></a>Sprawdź wtyczki za pomocą testu wydajności sieci Web

### <a name="to-test-your-plug-ins"></a>Aby przetestować wtyczki

1.  Tworzenie projektu testu.

2.  Tworzenie testu wydajności sieci Web i wprowadź adres URL w przeglądarce z usługą sieci Web, na przykład http://dev.virtualearth.net/webservices/v1/metadata/searchservice/dev.virtualearth.net.webservices.v1.search.wsdl.

3.  Po zakończeniu rejestrowania w sieci Web edytorze testów wydajności, rozwiń żądania usługi sieci Web i wybierz opcję **ciągów tekstowych** lub **binarne treści**.

4.  W oknie właściwości wybierz ciągów tekstowych lub binarnych treści i wybierz wielokropek (...).

     **Edytowanie danych treści HTTP** zostanie wyświetlone okno dialogowe.

5.  Można teraz edytować dane i kliknij przycisk OK. Wywołuje to odpowiedniej metody GetNewValue, aby zaktualizować zawartość w <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>.

## <a name="compile-the-code"></a>Kompilowanie kodu

Sprawdź, czy framework docelowe projektu biblioteki kontrolki Windows .NET Framework 4.5. Domyślnie projekty systemu Windows Biblioteka kontrolek docelowe struktury klienta programu .NET Framework 4.5, która nie zezwala na uwzględnienie odwołania Microsoft.VisualStudio.QualityTools.WebTestFramework.

Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.RichTextBox>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Porady: tworzenie wtyczki na poziomie żądania](../test/how-to-create-a-request-level-plug-in.md)
- [Kodowanie niestandardowej reguły wyodrębniania dla testów wydajności sieci web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kodowanie niestandardowej reguły walidacji dla testów wydajności sieci web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Porady: tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md)
- [Generowanie i Uruchamianie testów wydajności sieci web kodowane](../test/generate-and-run-a-coded-web-performance-test.md)
- [Porady: Tworzenie dodatku Visual Studio dla przeglądarki wyników testu wydajności sieci Web](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)