---
title: Tworzenie niestandardowego edytora danych dla adaptera danych diagnostycznych w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, creating custom editor
ms.assetid: 24970227-d1ea-4f6d-9839-e911478848ba
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 6141defb2248cf79888b0ed94824a827bd36815f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter"></a>Porady: tworzenie edytora niestandardowego dla danych dla Twojego adaptera danych diagnostycznych

Podczas tworzenia adaptera danych diagnostycznych, można umożliwić użytkownikom końcowym Konfigurowanie określonych danych po wybraniu z niestandardowego adaptera danych diagnostycznych dla ustawień testu. Na przykład można wybrać dane konfiguracji, które określa, które klucze rejestru, aby wyodrębnić poziomu obciążenia sieci, aby symulować lub w katalogu, który można znaleźć plików tymczasowych lub pracy plików do dołączenia.

Przy użyciu pliku konfiguracji musi skonfigurować wartości początkowe dla Twojego adaptera danych diagnostycznych. Możesz podać niestandardowego edytora, aby umożliwić użytkownikom modyfikowanie danych konfiguracji.

Aby utworzyć własną edytora, spowoduje utworzenie kontrolki użytkownika, który implementuje <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor>.

Można użyć Twojego adaptera danych diagnostycznych <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> w celu określenia klasy edytora do użycia na potrzeby edytowania danych diagnostycznych ustawienia konfiguracji.

Należy także określić domyślnych danych konfiguracji, który ma być używany.  Zobacz [przykładowy projekt do tworzenia adaptera danych diagnostycznych](../test/sample-project-for-creating-a-diagnostic-data-adapter.md) dla Przykładowa konfiguracja domyślna.

Poniższa procedura umożliwia utworzenie niestandardowego edytora, aby zaktualizować dane z ustawień testu stosowania Twojego adaptera diagnostyki danych niestandardowych.

> [!NOTE]
> Aby utworzyć niestandardowy edytor, należy najpierw utworzyć Twojego adaptera danych diagnostycznych, które ma <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> stosowanym do klasy. Można użyć opcjonalnego <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute.HelpUri*> właściwości tego atrybutu, aby określić źródło zawartości pomocy dla edytora. Aby uzyskać więcej informacji na temat tworzenia Twojego adaptera danych diagnostycznych, zobacz [porady: tworzenie adaptera danych diagnostycznych](../test/how-to-create-a-diagnostic-data-adapter.md).

Dla projektu adaptera danych diagnostycznych pełny przykład, włączając edytora konfiguracji niestandardowej, zobacz [przykładowy projekt do tworzenia adaptera danych diagnostycznych](../test/sample-project-for-creating-a-diagnostic-data-adapter.md).

## <a name="to-create-a-custom-editor-for-your-diagnostic-data-adapter"></a>Do tworzenia edytora niestandardowego dla Twojego adaptera danych diagnostycznych

1.  Tworzenie formantu użytkownika do projektu dla Twojego adaptera danych diagnostycznych:

    1.  Kliknij prawym przyciskiem myszy projekt kodu, który zawiera klasy adaptera danych diagnostycznych, wskaż pozycję **Dodaj** , a następnie wskaż polecenie **kontrolki użytkownika**.

    2.  Na przykład Dodaj etykietę do formularza z następującym tekstem: **nazwa pliku danych:** i pole tekstowe o nazwie **FileTextBox** umożliwi użytkownik musi wprowadzić potrzebne dane.

    > [!NOTE]
    > Obecnie obsługiwane są tylko formanty użytkownika formularzy systemu Windows.

2.  Dodaj następujące wiersze do sekcji deklaracji:

    ```csharp
    using System.Xml;
    using Microsoft.VisualStudio.TestTools.Common;
    using Microsoft.VisualStudio.TestTools.Execution;
    ```

3.  Ten formant użytkownika należy przekształcić Edytor niestandardowy.

    1.  Kliknij prawym przyciskiem myszy kontrolki użytkownika w projekcie kodu, a następnie wskaż **wyświetlić kod**.

    2.  Ustaw klasy do zaimplementowania interfejsu edytora <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor> w następujący sposób:

    ```csharp
    public partial class MyDataConfigEditor :
         UserControl, IDataCollectorConfigurationEditor
    ```

    1.  Kliknij prawym przyciskiem myszy <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor> w kodzie i wybierz **implementuj interfejs** polecenia. Metody, które należy zaimplementować dla tego interfejsu są dodawane do klasy.

    2.  Dodaj <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> do formantu użytkownika dla edytora zidentyfikować go jako edytora adapter danych diagnostycznych, zastępując **firmy**, **produktu**, i **wersji** z odpowiednie informacje dla Twojego adaptera danych diagnostycznych:

        ```csharp
        [DataCollectorConfigurationEditorTypeUri(
            "configurationeditor://MyCompany/MyConfigEditor/1.0")]
        ```

4.  Dodaj dwie zmienne prywatnych w następujący sposób:

    ```csharp
    private DataCollectorSettings collectorSettings;
    private IServiceProvider ServiceProvider { get; set; }
    ```

5.  Dodaj kod, aby zainicjować edytora dla Twojego adaptera danych diagnostycznych. Wartości domyślne można dodać do pól formantu użytkownika przy użyciu danych, który znajduje się w zmiennej ustawień. To są dane, który znajduje się w `<DefaultConfiguration>` elementu w pliku XML konfiguracji karty.

    ```csharp
    public void Initialize(
        IServiceProvider svcProvider,
        DataCollectorSettings settings)
    {
        ServiceProvider = svcProvider;
        collectorSettings = settings;

        // Display the default file name as listed in the settings file.
        this.SuspendLayout();
        this.FileTextBox.Text = getText(collectorSettings.Configuration);
        this.ResumeLayout();
    }
    ```

6.  Dodaj kod, aby zapisać dane z formantów w edytorze do formatu XML wymagany przez adapter danych diagnostycznych interfejsu API w następujący sposób:

    ```csharp
    public DataCollectorSettings SaveData()
    {
        collectorSettings.Configuration.InnerXml =
            String.Format(
    @"<MyCollectorName
        xmlns=""http://MyCompany/schemas/MyDiagnosticDataCollector/1.0"">
      <File FullPath=""{0}"" />
    </MyCollectorName>",
        FileTextBox.Text);
        return collectorSettings;
    }
    ```

7.  Jeśli jest to istotne dla Ciebie, Dodaj kod, aby zweryfikować dane są poprawne w `VerifyData` metody lub użytkownik może mieć metody zwrócić `true`.

    ```csharp
    public bool VerifyData()
    {
        // Not currently verifying data
        return true;
    }
    ```

8.  (Opcjonalnie) Można dodać kod, aby przywrócić dane początkowe ustawienia, które znajdują się w pliku konfiguracji XML w `ResetToAgentDefaults()` metodę, która używa prywatnego `getText()` metody.

    ```csharp
    // Reset to default value from XML configuration
    // using a custom getText() method
    public void ResetToAgentDefaults()
    {
        this.FileTextBox.Text = getText(collectorSettings.DefaultConfiguration);
    }

    // Local method to read the configuration settings
    private string getText(XmlElement element)
    {
        // Setup namespace manager with our namespace
        XmlNamespaceManager nsmgr =
            new XmlNamespaceManager(
                element.OwnerDocument.NameTable);

        // Find all the "File" elements under our configuration
        XmlNodeList files = element.SelectNodes("//ns:MyCollectorName/ns:File", nsmgr);

        string result = String.Empty;
        if (files.Count > 0)
        {
            XmlAttribute pathAttribute = files[0].Attributes["FullPath"];
            if (pathAttribute != null &&
                !String.IsNullOrEmpty(pathAttribute.Value))
            {
                result = pathAttribute.Value;
            }
        }

        return result;
    }
    ```

9. Skompiluj rozwiązanie. Skopiuj zestaw adaptera diagnostyki danych i pliku konfiguracji XML (`<diagnostic data adapter name>.dll.config`) w następującej lokalizacji na podstawie w katalogu instalacji: *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\ PrivateAssemblies\DataCollectors*.

    > [!NOTE]
    > Mimo że edytor konfiguracji mogą być w projekcie i zestawu, który różni się od adaptera danych diagnostycznych, można je również w tym samym zestawie.

10. Aby użyć Twojego adaptera danych diagnostycznych podczas testowania, musi wybrać z listy istniejących ustawień testu lub Utwórz nową z Microsoft Test Manager lub programu Visual Studio a następnie wybierz Twojego adaptera danych diagnostycznych.

     Karta jest wyświetlana na **danych i informacji diagnostycznych** kartę Ustawienia testu z przyjazna nazwa przypisana do klasy.

11. Aby skonfigurować Twojego adaptera danych diagnostycznych dla ustawień testu, wybierz **Konfiguruj** obok nazwy karty.

     Edytor niestandardowy jest teraz wyświetlone.

12. Edytuj pola w edytora niestandardowego zgodnie z wymaganiami, a następnie wybierz **zapisać**.

13. Jeśli korzystasz z testów z Microsoft Test Manager, można przypisać te ustawienia do planu testu testu, przed uruchomieniem testów, lub użyj **Uruchom z opcjami** polecenie, aby przypisać ustawień testu i zastąpić ustawienia testu. Aby uzyskać więcej informacji dotyczących ustawień testu, zobacz [zbieranie diagnostycznych informacji za pomocą testu ustawień](../test/collect-diagnostic-information-using-test-settings.md).

14. Zanim użyjesz nowego edytora konfiguracji adaptera danych diagnostycznych, należy najpierw zastosować <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> do każdej klasy adaptera danych diagnostycznych, którego chcesz użyć edytora i ponownie skompilować i zainstaluj je ponownie na komputerze klienckim. Aby uzyskać więcej informacji o sposobie instalowania adapterów danych diagnostycznych i edytory konfiguracji, zobacz [porady: Instalowanie niestandardowego adaptera danych diagnostycznych](../test/how-to-install-a-custom-diagnostic-data-adapter.md).

15. Uruchom testy przy użyciu ustawień testów z Twojego adaptera danych diagnostycznych wybrane.

     Plik danych, który określono w edytorze jest dołączony do wyników testu.

 Aby uzyskać więcej informacji o sposobie konfigurowania ustawień testu do korzystania ze środowiska, po uruchomieniu testów, zobacz [zbierania danych diagnostycznych podczas testowania (VSTS)](/vsts/manual-test/collect-diagnostic-data) lub [zbierania danych diagnostycznych podczas wykonywania testów ręcznych (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- [Tworzenie adaptera danych diagnostycznych zbieranie danych niestandardowych lub mają wpływ na maszynę testową](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)
- [Zbierz informacje diagnostyczne przy użyciu ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)
- [Przykładowy projekt do tworzenia adaptera danych diagnostycznych](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)