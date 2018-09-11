---
title: Utworzenie niestandardowego edytora danych dla adaptera danych diagnostycznych w programie Visual Studio
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
ms.openlocfilehash: 372cc01f1d7a0a21832ff099472e444d43d7a699
ms.sourcegitcommit: 28909340cd0a0d7cb5e1fd29cbd37e726d832631
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44320543"
---
# <a name="how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter"></a>Porady: tworzenie edytora niestandardowego dla danych dla adaptera danych diagnostycznych

Podczas tworzenia adaptera danych diagnostycznych, możesz chcieć umożliwić użytkownikowi konfigurowanie określonych danych po wybraniu użytkownika niestandardowego adaptera danych diagnostycznych dla ich ustawień testowych. Na przykład można wybrać dane konfiguracji, który określa, które klucze rejestru wyodrębnić, jaki poziom obciążenia sieciowego zasymulować lub, w którym katalogu znaleźć pliki tymczasowe lub pliki robocze do dołączenia.

Do ustawiania wartości początkowych karty danych diagnostycznych, należy użyć pliku konfiguracji. Możesz zapewnić niestandardowy edytor, aby umożliwić użytkownikowi modyfikowanie danych konfiguracji.

Aby utworzyć własny edytor, utworzysz formant użytkownika, który implementuje <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor>.

Można użyć adaptera danych diagnostycznych <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> do określenia klasy edytora do edycji ustawień konfiguracji danych diagnostycznych.

Określasz również domyślne dane konfiguracji, który chcesz użyć.  Zobacz [przykładowy projekt dotyczący tworzenia adaptera danych diagnostycznych](../test/sample-project-for-creating-a-diagnostic-data-adapter.md) dla przykładowej konfiguracji domyślnej.

Poniższa procedura umożliwia utworzenie niestandardowego edytora do aktualizowania danych ustawień testu, gdy jest używany z niestandardowego adaptera danych diagnostycznych.

> [!NOTE]
> Aby utworzyć niestandardowy edytor, należy najpierw utworzyć adaptera danych diagnostycznych, który ma <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> stosowane do klasy. Możesz użyć opcjonalnego <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute.HelpUri*> właściwości w tym atrybucie, aby określić źródło zawartości pomocy dla edytora. Aby uzyskać więcej informacji na temat tworzenia adaptera danych diagnostycznych, zobacz [porady: tworzenie adaptera danych diagnostycznych](../test/how-to-create-a-diagnostic-data-adapter.md).

Aby uzyskać pełny przykład projektu adaptera danych diagnostycznych, w tym z edytorem konfiguracji niestandardowych, zobacz [przykładowy projekt dotyczący tworzenia adaptera danych diagnostycznych](../test/sample-project-for-creating-a-diagnostic-data-adapter.md).

## <a name="to-create-a-custom-editor-for-your-diagnostic-data-adapter"></a>Aby utworzyć niestandardowy edytor dla adaptera danych diagnostycznych

1.  Tworzenie kontrolki użytkownika w projekcie adaptera danych diagnostycznych:

    1.  Kliknij prawym przyciskiem myszy projekt kodu, który zawiera klasy adaptera danych diagnostycznych, wskaż opcję **Dodaj** i wskaż **kontrolki użytkownika**.

    2.  W tym przykładzie należy dodać etykietę do formularza z tym tekstem: **nazwa pliku danych:** i pole tekstowe o nazwie **FileTextBox** co umożliwi użytkownikowi wprowadzanie niezbędnych danych.

    > [!NOTE]
    > Obecnie obsługiwane są tylko formanty użytkownika Windows Forms.

2.  Dodaj następujące wiersze do sekcji deklaracji:

    ```csharp
    using System.Xml;
    using Microsoft.VisualStudio.TestTools.Common;
    using Microsoft.VisualStudio.TestTools.Execution;
    ```

3.  Przekształć ten formant użytkownika w niestandardowy Edytor.

    1.  Kliknij prawym przyciskiem myszy formant użytkownika w projekcie kodu, a następnie wskaż **wyświetlić kod**.

    2.  Ustaw klasę, aby zaimplementować interfejs edytora <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor> w następujący sposób:

    ```csharp
    public partial class MyDataConfigEditor :
         UserControl, IDataCollectorConfigurationEditor
    ```

    1.  Kliknij prawym przyciskiem myszy <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor> w kodzie i wybierz **implementuj interfejs** polecenia. Metody, które należy zaimplementować dla tego interfejsu są dodawane do klasy.

    2.  Dodaj <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> do kontrolowania użytkowników tego edytora, aby zidentyfikować to jako edytora adaptera danych diagnostycznych, zastępując **firmy**, **produktu**, i **wersji** z odpowiednimi informacjami dla adaptera danych diagnostycznych:

        ```csharp
        [DataCollectorConfigurationEditorTypeUri(
            "configurationeditor://MyCompany/MyConfigEditor/1.0")]
        ```

4.  Dodaj dwie zmienne prywatne w następujący sposób:

    ```csharp
    private DataCollectorSettings collectorSettings;
    private IServiceProvider ServiceProvider { get; set; }
    ```

5.  Dodaj kod, aby zainicjować edytora dla adaptera danych diagnostycznych. Można dodać wartości domyślne do pól w kontrolce użytkownika przy użyciu danych, który znajduje się w zmiennej ustawienia. Są to dane, który znajduje się w `<DefaultConfiguration>` elementu w pliku konfiguracyjnym XML dla karty.

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

6.  Dodaj kod, aby zapisać dane z formantów w edytorze powrót do formatu XML, wymaganej przez adapter danych diagnostycznych interfejsu API w następujący sposób:

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

7.  Jeśli jest dla Ciebie ważne, Dodaj kod, aby sprawdzić, dane są poprawne w `VerifyData` metody lub użytkownik może mieć metoda może zwracać `true`.

    ```csharp
    public bool VerifyData()
    {
        // Not currently verifying data
        return true;
    }
    ```

8.  (Opcjonalnie) Możesz dodać kod, aby przywrócić dane do ustawień początkowych, które znajdują się w pliku konfiguracyjnym XML w `ResetToAgentDefaults()` metody, która używa prywatnej `getText()` metody.

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

9. Skompiluj rozwiązanie. Kopiuj zestaw adaptera danych diagnostycznych i plik konfiguracyjny XML (`<diagnostic data adapter name>.dll.config`) w następującej lokalizacji, w oparciu o katalogu instalacji: *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\ PrivateAssemblies\DataCollectors*.

    > [!NOTE]
    > Chociaż Edytor konfiguracji może być w projekcie i zestawu, który różni się od adaptera danych diagnostycznych, mogą również być tego samego zestawu.

10. Aby użyć karty danych diagnostycznych podczas testowania, należy wybrać z listy istniejących ustawień testu lub Utwórz nową z Microsoft Test Manager lub programu Visual Studio a następnie wybierz adaptera danych diagnostycznych.

     Adapter jest wyświetlany na **dane i Diagnostyka** kartę ustawień testu z przyjazną nazwą, która została przypisana do tej klasy.

11. Aby skonfigurować adapter danych diagnostycznych dla ustawień testu, wybierz **Konfiguruj** obok nazwy karty.

     Niestandardowego edytora jest teraz wyświetlany.

12. Edytuj pola w edytorze niestandardowym zgodnie z wymaganiami, a następnie wybierz **Zapisz**.

13. Jeśli używasz testów z Microsoft Test Manager, można przypisać te ustawienia testów do planu testów przed uruchomieniem testów lub użyć **Uruchom z opcjami** polecenia w celu przypisywania ustawień testów i zastępowania ustawień testu. Aby uzyskać więcej informacji na temat ustawień testowych, zobacz [zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

14. Przed użyciem nowej konfiguracji edytora za pomocą adaptera danych diagnostycznych, należy najpierw zastosować <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> do każdej klasy adaptera danych diagnostycznych, który chcesz użyć edytora, ponownie skompilować i ponownie je zainstalować na komputerze klienckim. Aby uzyskać więcej informacji na temat sposobu instalowania adapterów danych diagnostycznych i edytorów konfiguracji, zobacz [porady: Instalowanie niestandardowego adaptera danych diagnostycznych](../test/how-to-install-a-custom-diagnostic-data-adapter.md).

15. Uruchom testy przy użyciu ustawień testowych z wybraną kartą danych diagnostycznych.

     Plik danych, który określiłeś w edytorze jest dołączany do wyników testu.

 Aby uzyskać więcej informacji o sposobie konfigurowania ustawień testów w celu używania środowiska podczas wykonywania testów, zobacz [zbieranie danych diagnostycznych podczas testowania (plany testów platformy Azure)](/azure/devops/test/collect-diagnostic-data?view=vsts) lub [zbieranie danych diagnostycznych w podręczniku testów () Planów testowych platformy Azure)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- [Tworzenie adaptera danych diagnostycznych do zbierania danych niestandardowych lub wpływać na komputer testowy](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)
- [Zbieranie informacji diagnostycznych za pomocą ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)
- [Przykładowy projekt dotyczący tworzenia adaptera danych diagnostycznych](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)