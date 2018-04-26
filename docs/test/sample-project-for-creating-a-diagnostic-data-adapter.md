---
title: Przykładowy projekt do tworzenia adaptera danych diagnostycznych w programie Visual Studio
ms.date: 10/19/2016
ms.topic: sample
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- samples. Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter, sample
ms.assetid: 548bdc5e-338f-4be7-a555-e6a2efb1df6b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: b7d2cd30faa5cbc5b4f8626c17de77c68bdf8bae
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="sample-project-for-creating-a-diagnostic-data-adapter"></a>Przykładowy projekt do tworzenia adaptera danych diagnostycznych

"MyDiagnosticDataAdapter" jest adaptera danych diagnostycznych proste, który można dołączyć plik dziennika do wyników testu, po uruchomieniu testów.

 Konieczne będzie uprawnienia administratora na dowolnym komputerze gdzie zbierania danych diagnostycznych lub Konfiguracja edytora jest zainstalowany.

## <a name="example-data-adapter"></a>Przykład adaptera danych

W tym przykładzie przedstawiono sposób wykonywania następujących zadań:

-   Stosowanie atrybutów, aby stał się klasę wykrywalny Microsoft Test Manager jako adaptera danych diagnostycznych.

-   Stosowanie atrybutów, aby stał się klasy formantu użytkownika wykrywalny Microsoft Test Manager jako edytora do użycia w celu zmiany konfiguracji dla adaptera danych diagnostycznych.

-   Dostęp do danych konfiguracji domyślnej.

-   Rejestr dla określonych zdarzeń diagnostycznych zbieranie danych.

-   Dołącz plik dziennika przez wysłanie ich do <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>.

```csharp
// My Data Collector Class
using Microsoft.VisualStudio.TestTools.Common;
using Microsoft.VisualStudio.TestTools.Execution;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Xml;
using System;

namespace MyCompany.MyDiagnosticDataAdapters
{
    // Provide a URI and friendly name for your diagnostic data adapter
    [DataCollectorTypeUri("datacollector://MyCompany/MyDataCollector/1.0")]
    [DataCollectorFriendlyName("Collect Log Files sample", false)]
    // Designate your chosen configuration editor
    [DataCollectorConfigurationEditor(
        "configurationeditor://MyCompany/MyDataConfigEditor/1.0")]
    public class MyDataCollector : DataCollector
    {
        private DataCollectionEvents dataEvents;
        private DataCollectionLogger dataLogger;
        private DataCollectionSink dataSink;
        private XmlElement configurationSettings;

        // Required method called by the testing framework
        public override void Initialize(
            XmlElement configurationElement,
            DataCollectionEvents events,
            DataCollectionSink sink,
            DataCollectionLogger logger,
            DataCollectionEnvironmentContext environmentContext)
        {
            dataEvents = events; // The test events
            dataLogger = logger; // The error and warning log
            dataSink = sink;     // Saves collected data
            // Configuration from the test settings
            configurationSettings = configurationElement;

            // Register common events for the data collector
            // Not all of the events are used in this class
            dataEvents.SessionStart +=
                new EventHandler<SessionStartEventArgs>(OnSessionStart);
            dataEvents.SessionEnd +=
                new EventHandler<SessionEndEventArgs>(OnSessionEnd);
            dataEvents.TestCaseStart +=
                new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
            dataEvents.TestCaseEnd +=
                new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
            dataEvents.DataRequest +=
                new EventHandler<DataRequestEventArgs>(OnDataRequest);
        }

        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                dataEvents.SessionStart -=
                    new EventHandler<SessionStartEventArgs>(OnSessionStart);
                dataEvents.SessionEnd -=
                    new EventHandler<SessionEndEventArgs>(OnSessionEnd);
                dataEvents.TestCaseStart -=
                    new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
                dataEvents.TestCaseEnd -=
                    new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
                dataEvents.DataRequest -=
                    new EventHandler<DataRequestEventArgs>(OnDataRequest);
            }
        }

        #region Event Handlers
        public void OnSessionStart(object sender, SessionStartEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnSessionEnd(object sender, SessionEndEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnTestCaseStart(object sender, TestCaseEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnTestCaseEnd(object sender, TestCaseEndEventArgs e)
        {
            // Get any files to be collected that are
            // configured in your test settings
            List<string> files = getFilesToCollect();

            // For each of the files, send the file to the data sink
            // which will attach it to the test results or to a bug
            foreach (string file in files)
            {
                dataSink.SendFileAsync(e.Context, file, false);
            }
        }

        public void OnDataRequest(object sender, DataRequestEventArgs e)
        {
            // TODO: Provide implementation
            // Most likely this occurs because a bug is being filed
        }
        #endregion

        // A private method to collect the configured file names
        private List<string> getFilesToCollect()
        {
            // Seetup namespace manager with our namespace
            XmlNamespaceManager nsmgr =
                new XmlNamespaceManager(
                    configurationSettings.OwnerDocument.NameTable);
            nsmgr.AddNamespace("ns",
                "http://MyCompany/schemas/MyDataCollector/1.0");

            // Find all of the "File" elements under our configuration
            XmlNodeList files =
                configurationSettings.SelectNodes(
                    "//ns:MyDataCollector/ns:File");

            // Build the list of files to collect from the
            // "FullPath" attributes of the "File" nodes.
            List<string> result = new List<string>();
            foreach (XmlNode fileNode in files)
            {
                XmlAttribute pathAttribute =
                    fileNode.Attributes["FullPath"];
                if (pathAttribute != null &&
                    !String.IsNullOrEmpty(pathAttribute.Value))
                {
                    result.Add(pathAttribute.Value);
                }
            }

            return result;
        }
    }
}
```

## <a name="example-configuration-editor"></a>Przykład edytor konfiguracji

To jest przykładowy Edytor konfiguracji dla Twojego adaptera danych diagnostycznych. Dodaj kontrolkę użytkownika do projektu i utworzyć bardzo proste formularz, który ma etykiety ("Nazwa pliku dziennika:") i pole tekstowe o nazwie "FileTextBox".

```csharp
using Microsoft.VisualStudio.TestTools.Common;
using Microsoft.VisualStudio.TestTools.Execution;
using System.Collections.Generic;
using System.ComponentModel;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using System.Xml;
using System;

namespace MyCompany.DiagnosticDataAdapters.ConfigurationEditors
{
    [DataCollectorConfigurationEditorTypeUri(
        "configurationeditor://MyCompany/MyConfigEditor/1.0")]
    public partial class MyDataConfigEditor :
        UserControl, IDataCollectorConfigurationEditor
    {
        private DataCollectorSettings collectorSettings;

        // Create a private property for the service provider
        private IServiceProvider ServiceProvider { get; set; }

        // Constructor
        public MyConfigurationEditor()
        {
            InitializeComponent();
        }

        // Required method called by the testing framework
        public void Initialize(
            IServiceProvider svcProvider,
            DataCollectorSettings settings)
        {
            ServiceProvider = svcProvider;
            collectorSettings = settings;

            // Display the file name as listed in the settings file.
            // If the configuration has not been updated before, this
            // data will be provided by the default configuration
            // section from <nameofcollector>.dll.config:
            // <DefaultConfiguration>
            //   <MyCollectorName
            //       xmlns="http://MyCompany/schemas/ProductName/Version");
            //     <File FullPath="C:\temp\logfile1.txt" />
            //   </MyCollectorName>
            // </DefaultConfiguration>
            this.SuspendLayout();
            this.FileTextBox.Text = GetText(collectorSettings.Configuration);
            this.ResumeLayout();
        }

        // Can be used to verify data before saving it
        public bool VerifyData()
        {
            // Not currently verifying data
            return true;
        }

        // Reset to default value from XML configuration
        // using a custom method
        public void ResetToAgentDefaults()
        {
            this.FileTextBox.Text =
                getText(collectorSettings.DefaultConfiguration);
        }

        // Saves data changed in the editor to the test configuration
        // settings. Does not change the default value.
        public DataCollectorSettings SaveData()
        {
            collectorSettings.Configuration.InnerXml =
                String.Format(
                    @"<MyCollectorName
      xmlns=""http://MyCompany/schemas/MyDataCollector/1.0"">
  <File FullPath=""{0}"" />
</MyCollectorName>",
                    FileTextBox.Text);
            return collectorSettings;
        }

        // Reads the configuration settings
        private string getText(XmlElement element)
        {
            // Setup namespace manager with our namespace
            XmlNamespaceManager nsmgr =
                new XmlNamespaceManager(
                    element.OwnerDocument.NameTable);

            // Find all the "File" elements under our configuration
            XmlNodeList files = element.SelectNodes("//ns:MyDataCollector/ns:File", nsmgr);

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
    }
}
```

## <a name="example-configuration-file"></a>Przykładowy plik konfiguracji

Oto przykładowy plik konfiguracyjny dla Edytora konfiguracji modułów zbierających dane diagnostyczne.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <section
      name="DataCollectorConfiguration"
      type="Microsoft.VisualStudio.QualityTools.Execution.DataCollectorConfigurationSection,
        Microsoft.visualStudio.QualityTools.ExecutionCommon,
        Version=4.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f7f11d50a3a" />
  </configSections>
  <DataCollectorConfiguration
      xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/11">
    <DataCollector
        typeUri="datacollector://MyCompany/MyDataCollector/1.0">
      <DefaultConfiguration>
        <!-- Your default config settings-->
        <File FullPath="c:\temp\logfile1.txt" />
      </DefaultConfiguration>
    </DataCollector>
  </DataCollectorConfiguration>
</configuration>

```

## <a name="compiling-the-code"></a>Kompilowanie kodu

### <a name="to-create-the-code-project-for-this-diagnostic-adapter"></a>Aby utworzyć projekt kodu dla tej karty diagnostycznych

1.  Tworzenie nowego projektu biblioteki klasy o nazwie "MyDataCollector".

2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **właściwości**. Aby wybrać folder do dodania, wybierz **ścieżek odwołania** , a następnie wybierz wielokropek (**...** ).

     **Wybierz ścieżkę odwołania** zostanie wyświetlone okno dialogowe.

3.  Wybierz następującej ścieżki katalogu instalacji w oparciu: *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*. Wybierz **OK**.

4.  Aby dodać folder na ścieżce odwołania, wybierz **Dodaj Folder**.

     Wyświetlana jest zawartość folderu w liście ścieżek odwołania.

5.  Wybierz **Zapisz wszystko** ikonę, aby zapisać ścieżek odwołania.

6.  Dodaj zestaw **Microsoft.VisualStudio.QualityTools.ExecutionCommon**.

    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** , a następnie wybierz **Dodaj odwołanie**.

    2.  Wybierz **Przeglądaj** i Znajdź **Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**.

         Ten zestaw będzie znajdować się w *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*.

    3.  Wybierz **OK**.

7.  Dodaj zestaw **Microsoft.VisualStudio.QualityTools.Common**.

    1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **odwołania** i wybierz **Dodaj odwołanie**.

    2.  Wybierz **Przeglądaj** i Znajdź **Microsoft.VisualStudio.QualityTools.Common.dll**.

         Ten zestaw będzie znajdować się w *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*.

    3.  Wybierz **OK**.

8.  Klasa karty danych diagnostycznych, który został wymieniony we wcześniejszej części tego dokumentu, skopiuj do klasy biblioteki klas. Zapisz tę klasę.

9. Aby dodać kontrolkę użytkownika do projektu, kliknij prawym przyciskiem myszy projekt MyDataCollector w Eksploratorze rozwiązań, wskaż **Dodaj**, a następnie wybierz pozycję **kontrolki użytkownika**. Wybierz **dodać**.

10. Przy użyciu przybornika, Dodaj etykietę do kontrolki użytkownika i zmień właściwość Text do **nazwa pliku:**.

11. Przy użyciu przybornika, Dodaj pole tekstowe do kontrolki użytkownika i Zmień nazwę, aby **textBoxFileName**.

12. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy kontrolki użytkownika, a następnie wybierz pozycję **widoku kodu.** Ta klasa formantu użytkownika należy zastąpić klasy formantu użytkownika, który był wcześniej w tym dokumencie. Zapisz tę klasę.

    > [!NOTE]
    > Domyślnie przez kontrolki użytkownika jest nazywany UserControl1. Upewnij się, że kod klasy formantu użytkownika używa nazwy formantu użytkownika.

13. Można utworzyć pliku konfiguracji w **Eksploratora rozwiązań** kliknij rozwiązanie prawym przyciskiem myszy, wskaż pozycję **Dodaj**, a następnie wybierz pozycję **nowy element**. Wybierz wybrać **pliku konfiguracji aplikacji**, a następnie wybierz pozycję **Dodaj**. Spowoduje to dodanie pliku o nazwie **App.config** do rozwiązania.

14. Skopiuj plik XML z próbki wcześniej dostarczony do pliku XML. Zapisz plik.

15. Skompiluj rozwiązanie, a następnie skopiuj skompilowany zestaw i `App.config` pliku do *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors* katalogu.

16. Tworzenie ustawień testów, które korzystanie z tego adaptera diagnostyki danych niestandardowych. Skonfiguruj ustawienia testu do zbierania plików, który istnieje.

     Jeśli korzystasz z testów z Microsoft Test Manager, można przypisać te ustawienia testu ustawień testów do planu testu, aby uruchomić testy lub za pomocą opcji Uruchom polecenie Opcje przypisywania ustawień testu i zastępowania. Aby uzyskać więcej informacji dotyczących ustawień testu, zobacz [zbieranie diagnostycznych informacji za pomocą testu ustawień](../test/collect-diagnostic-information-using-test-settings.md).

17. Uruchom testy przy użyciu ustawień testu z Twojego adaptera danych diagnostycznych wybrane.

     Określony plik danych zostanie dołączona do wyników testu podczas wykonywania testu.

## <a name="see-also"></a>Zobacz także

- [Porady: tworzenie adaptera danych diagnostycznych](../test/how-to-create-a-diagnostic-data-adapter.md)
- [Porady: tworzenie edytora niestandardowego dla danych dla Twojego adaptera danych diagnostycznych](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)
- [Porady: Instalowanie niestandardowego adaptera danych diagnostycznych](../test/how-to-install-a-custom-diagnostic-data-adapter.md)
- [Tworzenie adaptera danych diagnostycznych zbieranie danych niestandardowych lub mają wpływ na maszynę testową](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)