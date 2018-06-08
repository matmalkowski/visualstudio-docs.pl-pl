---
title: 'Porady: tworzenie adaptera danych diagnostycznych w programie Visual Studio'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, creating
ms.assetid: bd7ad36c-54cb-4d2a-9aea-9d10ad98d7ba
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 923296a6eaed79edc345b9071d5e1d4e2ececefe
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844745"
---
# <a name="how-to-create-a-diagnostic-data-adapter"></a>Porady: tworzenie adaptera danych diagnostycznych

Aby utworzyć *adaptera danych diagnostycznych*, Utwórz bibliotekę klasy przy użyciu programu Visual Studio, a następnie dodaj diagnostycznych danych karty interfejsów API dostarczonych przez Visual Studio Enterprise do biblioteki klas. Wyślij wszystkie informacje, które ma być strumienia lub pliku <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> podane przez platformę, gdy obsługi zdarzeń, które są wywoływane podczas uruchomienia testu. Strumienie lub plików wysłane do <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> są przechowywane jako załączniki wyników testu, po zakończeniu testu. Po utworzeniu usterki z tych testów wyniki lub jeśli używasz [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)], pliki są również powiązane usterki.

 Można utworzyć adaptera danych diagnostycznych, która wpływa na komputerze, gdy testy są uruchamiane lub na komputerze, który jest częścią środowiska, którego używasz do uruchamiania aplikacji w ramach testu. Na przykład zbieranie plików na komputerze testowym, gdy testy są uruchamiane lub zbieranie plików na komputerze pełnią rolę serwera sieci Web dla aplikacji.

 Przyjazna nazwa, która jest wyświetlana podczas tworzenia ustawień testu przy użyciu narzędzia Microsoft Test Manager lub programu Visual Studio można nadać Twojego adaptera danych diagnostycznych. Ustawienia testu umożliwiają zdefiniowanie, od roli komputera zostanie uruchomiony adapterów danych diagnostycznych określonej w danym środowisku, po uruchomieniu testów. Podczas tworzenia ustawienia testu, można także skonfigurować karty danych diagnostycznych. Na przykład może utworzyć adaptera danych diagnostycznych, który służy do zbierania dzienników niestandardowych z serwera sieci Web. Podczas tworzenia ustawienia testu, można wybrać do uruchomienia tego adaptera danych diagnostycznych na komputerze lub komputerów, na których działają w tej roli serwera sieci Web i można zmodyfikować konfigurację ustawień testu do zbierania tylko ostatnich trzech dzienników, które zostały utworzone. Aby uzyskać więcej informacji dotyczących ustawień testu, zobacz [zbieranie diagnostycznych informacji za pomocą testu ustawień](../test/collect-diagnostic-information-using-test-settings.md).

 Zdarzenia są generowane podczas uruchamiania testów, tak aby Twojego adaptera danych diagnostycznych można wykonać zadania w tym momencie w teście.

> [!IMPORTANT]
> Te zdarzenia może zostać zgłoszone w różnych wątkach, zwłaszcza w przypadku testów uruchomionych na wielu komputerach. W związku z tym należy należy pamiętać o możliwych problemach wątków i nie mogą przypadkowo spowodować uszkodzenie danych wewnętrznych niestandardowe karty. Upewnij się, że Twojego adaptera danych diagnostycznych jest bezpieczne dla wątków.

 Oto częściowej listy kluczy zdarzeń, które można używać podczas tworzenia Twojego adaptera danych diagnostycznych. Aby uzyskać pełną listę zdarzeń adaptera danych diagnostycznych, zobacz abstract <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents> klasy.

|Zdarzenie|Opis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionStart>|Uruchomienia testu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionEnd>|Koniec testu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseStart>|Początek każdego testu w uruchomieniu testu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseEnd>|Koniec każdego testu w uruchomieniu testu|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepStart>|Początek każdego kroku testu w teście|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepEnd>|Koniec każdego kroku testu w teście|

> [!NOTE]
> Po zakończeniu testu ręcznego danych kolekcji zdarzenia nie są wysyłane do adaptera danych diagnostycznych. Podczas ponownego uruchomienia testu ma nowy identyfikator przypadku testowego. Jeśli użytkownik resetuje testu podczas testu (które generuje <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseReset> zdarzeń), lub wynik kroku zmienia ustawienia testu, nie zdarzenia zbierania danych są wysyłane do adaptera danych diagnostycznych, ale identyfikator przypadku testowego jest taka sama. Aby ustalić, czy przypadkiem testowym został zresetowany, możesz śledzić identyfikator przypadku testowego w Twojego adaptera danych diagnostycznych.

 Poniższa procedura umożliwia utworzenie adaptera danych diagnostycznych, która gromadzi plik danych na podstawie informacji, które można skonfigurować podczas tworzenia ustawień testu.

 Dla projektu adaptera danych diagnostycznych pełny przykład, włączając edytora konfiguracji niestandardowej, zobacz [przykładowy projekt do tworzenia adaptera danych diagnostycznych](../test/sample-project-for-creating-a-diagnostic-data-adapter.md).

##  <a name="CreateAdapter"></a> Tworzenie i instalowanie adaptera danych diagnostycznych

#### <a name="to-create-and-install-a-diagnostic-data-adapter"></a>Aby utworzyć i zainstalować adapter danych diagnostycznych

1.  Tworzenie nowej biblioteki klas.

    1.  Na **pliku** menu, wybierz **nowy**, a następnie wskaż **nowy projekt**.

    2.  Z **typy projektów**, wybierz język do użycia.

    3.  Z **zainstalowane szablony Visual Studio**, wybierz pozycję **biblioteki klas**.

    4.  Wpisz nazwę dla Twojego adaptera danych diagnostycznych.

    5.  Wybierz **OK**.

2.  Dodaj zestaw **Microsoft.VisualStudio.QualityTools.ExecutionCommon**.

    1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **odwołania** i wybierz polecenie **Dodaj odwołanie** polecenia.

    2.  Wybierz **.NET** i Znajdź **Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**.

    3.  Wybierz **OK**.

3.  Dodaj zestaw **Microsoft.VisualStudio.QualityTools.Common**.

    1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **odwołania** i wybierz **Dodaj odwołanie** polecenia.

    2.  Choose **/.NET**, locate **Microsoft.VisualStudio.QualityTools.Common.dll**.

    3.  Wybierz **OK**.

4.  Dodaj następujące `using` instrukcje do pliku klasy:

    ```csharp
    using Microsoft.VisualStudio.TestTools.Common;
    using Microsoft.VisualStudio.TestTools.Execution;
    using System.Linq;
    using System.Text;
    using System.Xml;
    using System;
    ```

5.  Dodaj <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute> do klasy dla Twojego adaptera danych diagnostycznych zidentyfikować go jako adaptera danych diagnostycznych, zastępując **firmy**, **produktu**, i **wersji** z odpowiednie informacje dla Twojego adaptera danych diagnostycznych:

    ```csharp
    [DataCollectorTypeUri("datacollector://Company/Product/Version")]
    ```

6.  Dodaj <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute> atrybutu do klasy, zastępując parametry odpowiednich informacji dotyczących Twojego adaptera danych diagnostycznych:

    ```csharp
    [DataCollectorFriendlyName("Collect Log Files", false)]
    ```

     Przyjazna nazwa jest wyświetlana w działaniu ustawień testu.

    > [!NOTE]
    > Można również dodać <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> do określenia `Type` z edytora konfiguracji niestandardowej dla tej karty danych i opcjonalnie Określ plik pomocy dla edytora.
    >
    > Można także zastosować <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute> do określenia, że powinien zawsze być włączone.

7.  Musi dziedziczyć po klasie adaptera danych diagnostycznych <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector> klas w następujący sposób:

    ```csharp
    public class MyDiagnosticDataAdapter : DataCollector
    ```

8.  Dodaj zmiennych lokalnych w następujący sposób:

    ```csharp
    private DataCollectionEvents dataEvents;
    private DataCollectionLogger dataLogger;
    private DataCollectionSink dataSink;
    private XmlElement configurationSettings;
    ```

9. Dodaj <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector.Initialize*> — metoda i **Dispose** metody. W `Initialize` metody zainicjować ujścia danych, wszelkie dane konfiguracji z ustawień testu i zarejestruj obsługę zdarzeń, aby użyć w następujący sposób:

    ```csharp
    public override void Initialize(
        XmlElement configurationElement,
        DataCollectionEvents events,
        DataCollectionSink sink,
        DataCollectionLogger logger,
        DataCollectionEnvironmentContext environmentContext)
    {
           dataEvents = events;  // The test events
           dataLogger = logger;  // The error and warning log
           dataSink = sink;      // Saves collected data
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
    }

    public override void Dispose(bool disposing)
    {
        if (disposing)
        {
            // Unregister the registered events
            dataEvents.SessionStart -=
                new EventHandler<SessionStartEventArgs>(OnSessionStart);
            dataEvents.SessionEnd -=
                new EventHandler<SessionEndEventArgs>(OnSessionEnd);
            dataEvents.TestCaseStart -=
                new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
            dataEvents.TestCaseEnd -=
                new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
        }
    }
    ```

10. Za pomocą następujący kod obsługi zdarzenia i Metoda prywatna zbierać pliki dziennika wygenerowanych podczas testu:

    ```csharp
    public void OnTestCaseEnd(sender, TestCaseEndEventArgs e)
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

    // A private method that returns the file names
    private List<string> getFilesToCollect()
    {
        // Get a namespace manager with our namespace
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
    ```

     Te pliki są dołączone do wyników testu. Po utworzeniu usterki z tych testów wyniki lub jeśli używasz [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)], pliki są również dołączone do usterki.

     Jeśli chcesz użyć własnych edytora do zbierania danych użycia w ustawieniach testu, zobacz [porady: tworzenie edytora niestandardowego dla danych dla adaptera danych diagnostycznych Your](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md).

11. Aby zbierać pliku dziennika, gdy test zakończy oparte na użytkownika skonfigurowanego w ustawieniach testu, należy utworzyć `App.config` plik i dodać go do rozwiązania. Ten plik ma następujący format i musi zawierać identyfikator URI dla Twojego adaptera danych diagnostycznych zidentyfikować go. Zastąp wartość rzeczywista "firmy/ProductName/Version".

    > [!NOTE]
    > Jeśli nie trzeba konfigurować żadnych informacji dla Twojego adaptera danych diagnostycznych, następnie zbędna, nie można utworzyć pliku konfiguracji.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
      <configSections>
        <section name="DataCollectorConfiguration" type="Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationSection, Microsoft.VisualStudio.QualityTools.ExecutionCommon, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a "/>
      </configSections>
      <DataCollectorConfiguration xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/2010">
        <DataCollector typeUri="datacollector://MyCompany/MyProduct/1.0">
          <DefaultConfiguration>
            <!-- Your default config settings -->
            <Binaries>
              <Binary FullPath="C:\Example\Example.dll"/>
              <Binary FullPath="\\Server2\Example2.dll"/>
            </Binaries>
            <Symbols>
              <Symbol FullPath="\\ExampleServer\ExampleSymbol.pdb"/>
            </Symbols>
          </DefaultConfiguration>
        </DataCollector>
      </DataCollectorConfiguration>
    </configuration>
    ```

    > [!NOTE]
    > Domyślny element konfiguracji może zawierać żadnych danych, która jest wymagana. Jeśli użytkownik nie konfiguruje adaptera danych diagnostycznych w ustawieniach testu, a następnie domyślnych danych zostanie przekazany do Twojego adaptera danych diagnostycznych podczas jej wykonywania. Ponieważ XML, należy dodać do `<DefaultConfigurations>` sekcji nie mogą być zadeklarowane schematu, możesz zignorować wszelkie generuje błędy XML.
    >
    > Istnieją inne przykłady pliki konfiguracji w następującej ścieżki katalogu instalacji w oparciu: **10.0\Common7\IDE\PrivateAssemblies\DataCollectors Program Files\Microsoft Visual Studio**.

     Aby uzyskać więcej informacji o sposobie konfigurowania ustawień testu do korzystania ze środowiska, po uruchomieniu testów, zobacz [zbierania danych diagnostycznych podczas wykonywania testów ręcznych (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests).

     Aby uzyskać więcej informacji o instalowaniu pliku konfiguracji, zobacz [porady: Instalowanie niestandardowego adaptera danych diagnostycznych](../test/how-to-install-a-custom-diagnostic-data-adapter.md)

12. Skompiluj rozwiązanie, aby utworzyć użytkownika zestaw adaptera danych diagnostycznych.

13. Informacje o instalowaniu edytora niestandardowych, zobacz [porady: Instalowanie niestandardowego adaptera danych diagnostycznych](../test/how-to-install-a-custom-diagnostic-data-adapter.md).

14. Aby uzyskać więcej informacji o sposobie konfigurowania ustawień testu do korzystania ze środowiska, po uruchomieniu testów, zobacz [zbierania danych diagnostycznych podczas wykonywania testów ręcznych (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests).

15. Aby wybrać Twojego adaptera danych diagnostycznych, musi najpierw wybierz istniejące ustawienia testu lub Utwórz nową z Microsoft Test Manager lub programu Visual Studio. Karta jest wyświetlana na **danych i informacji diagnostycznych** kartę Ustawienia testu z przyjazna nazwa przypisana do klasy.

16. Ustaw ustawienia na aktywny testu. Aby uzyskać więcej informacji dotyczących ustawień testu, zobacz [zbieranie diagnostycznych informacji za pomocą testu ustawień](../test/collect-diagnostic-information-using-test-settings.md).

17. Uruchom testy przy użyciu ustawień testów z Twojego adaptera danych diagnostycznych wybrane.

   Określony plik danych jest dołączony do wyników testu.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute>
- [Zbierz informacje diagnostyczne przy użyciu ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)
- [Zbieranie danych diagnostycznych podczas wykonywania testów ręcznych (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests)
- [Zbierane dane diagnostyczne podczas testowania (VSTS)](/vsts/manual-test/collect-diagnostic-data)
- [Porady: tworzenie edytora niestandardowego dla danych dla Twojego adaptera danych diagnostycznych](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)