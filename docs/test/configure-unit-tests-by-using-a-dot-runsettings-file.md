---
title: Konfigurowanie testów jednostkowych przy użyciu pliku runsettings
ms.date: 02/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: f0cb4989877445a0679a5682aaa17e4b7f759a33
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815980"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Konfigurowanie testów jednostkowych przy użyciu *runsettings* pliku

Testy jednostkowe w programie Visual Studio można skonfigurować przy użyciu *runsettings* pliku. Na przykład można zmienić wersji .NET Framework, na którym są uruchamiane testy, katalog wyników testu lub dane zebrane podczas uruchomienia testu.

Pliki ustawień uruchamiania są opcjonalne. Jeśli nie wymaga żadnej specjalnej konfiguracji, nie ma potrzeby *runsettings* pliku. Najczęściej używane *runsettings* ma dostosować plik [analiza pokrycia kodu](../test/customizing-code-coverage-analysis.md).

## <a name="specify-a-run-settings-file"></a>Określ plik parametrów uruchomieniowych

Ustawienia plików może służyć do konfigurowania testy, które są uruchamiane z wiersza polecenia, w IDE lub uruchomienia [kompilacji przepływu pracy](/vsts/pipelines/test/getting-started-with-continuous-testing?view=vsts) przy użyciu programu Visual Studio Team Services (VSTS) lub Team Foundation Server (TFS).

### <a name="specify-a-run-settings-file-in-the-ide"></a>Określ plik parametrów uruchomieniowych w środowisku IDE

Wybierz **testu** > **ustawień testu** > **wybierz plik ustawień testu** , a następnie wybierz *runsettings*pliku. Ten plik będzie występował na **ustawień testu** menu, a wybierz lub Anuluj wybór. Gdy zaznaczony plik parametrów uruchomieniowych odnosi się po wybraniu **Analizuj pokrycie kodu**.

![Wybierz menu Plik ustawień testu w programie Visual Studio](media/select-test-settings-file.png)

### <a name="specify-a-run-settings-file-at-the-command-line"></a>Określ plik parametrów uruchomieniowych w wierszu polecenia

Aby uruchomić testy z wiersza polecenia, użyj *vstest.console.exe* i określ plik ustawień za pomocą **/Settings** parametru.

1. Uruchom wiersz polecenia programisty dla programu Visual Studio:

   W systemie Windows **Start** menu, wybierz **programu Visual Studio 2017** > **wiersz polecenia dla programu VS 2017 deweloperów**.

2. Wprowadź polecenie podobne do:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

## <a name="customize-tests"></a>Dostosowywanie testów

Aby dostosować testy przy użyciu *runsettings* , wykonaj następujące kroki:

1. Dodawanie pliku XML do rozwiązania Visual Studio i zapisz go jako *test.runsettings*.

   > [!TIP]
   > Nazwa pliku nie ma znaczenia, tak długo, jak użyć rozszerzenia *runsettings*.

1. Zamień zawartość pliku XML w następującym przykładzie oraz dostosować zgodnie z potrzebami.

1. Na **testu** menu, wybierz **ustawień testu** > **wybierz plik ustawień testu**. Przejdź do *runsettings* utworzonego pliku, a następnie wybierz **OK**.

   > [!TIP]
   > Możesz utworzyć więcej niż jedną *runsettings* pliku rozwiązania i wybierz jedną jako plik ustawienia aktywnego testu, zgodnie z potrzebami.

## <a name="example-runsettings-file"></a>Przykład *runsettings* pliku

Następujący kod XML zawiera zawartość typowe *runsettings* pliku. Każdy element pliku jest opcjonalna, ponieważ ma ona wartości domyślnej.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to solution directory -->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64 -->
    <!-- You can also change it from menu Test > Test Settings > Default Processor Architecture -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>

    <!-- TestSessionTimeout is only available with Visual Studio 2017 version 15.5 and higher -->
    <!-- Specify timeout in milliseconds. A valid value should be greater than 0 -->
    <TestSessionTimeout>10000</TestSessionTimeout>
  </RunConfiguration>

  <!-- Configurations for data collectors -->
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
            <ModulePaths>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>

      <!--Video data collector is only available with Visual Studio 2017 version 15.5 and higher -->
      <DataCollector uri="datacollector://microsoft/VideoRecorder/1.0" assemblyQualifiedName="Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder.VideoRecorderDataCollector, Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" friendlyName="Screen and Voice Recorder">
      </DataCollector>

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at runtime -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

  <!-- Adapter Specific sections -->

  <!-- MSTest adapter -->
  <MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
  </MSTest>

</RunSettings>
```

## <a name="elements-of-a-runsettings-file"></a>Elementy *runsettings* pliku

W kolejnych sekcjach opisano elementy *runsettings* pliku.

### <a name="run-configuration"></a>Uruchom konfigurację

```xml
<RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <ResultsDirectory>.\TestResults</ResultsDirectory>
    <TargetPlatform>x86</TargetPlatform>
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
    <TestSessionTimeout>10000</TestSessionTimeout>
</RunConfiguration>
```

**RunConfiguration** może zawierać następujące elementy:

|Węzeł|Domyślny|Wartości|
|----------|-------------|------------|
|**ResultsDirectory**||Katalog rozmieszczenia wyników testu.|
|**targetFrameworkVersion**|Framework40|Framework35, Framework40, Framework45<br /><br />To ustawienie określa, która wersja platformy testów jednostkowych służy do odnajdywania i wykonać testów. Może ona być inna niż wersja platformy .NET określonej we właściwościach kompilacji projektu badania jednostki.|
|**TargetPlatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|false|fałsz, prawda|
|**TestAdaptersPaths**||Jeden lub wiele ścieżek do katalogu, w którym znajdują się TestAdapters|
|**MaxCpuCount**|1|Ten kontroluje stopień wykonywanie równoległe testu podczas testów jednostkowych uruchomione, przy użyciu dostępne rdzenie komputera. Aparat wykonywania testu uruchamiania jako proces unikatowe na każdym dostępne rdzenie i zapewnia kontener core każdego z testów do uruchomienia. Kontener może być zestawu, biblioteki DLL lub odpowiednie artefaktu. Kontener testu jest jednostka planowania. W każdym kontenerze testy są uruchamiane zgodnie ze struktury testowej. Jeśli istnieje wiele kontenerów, następnie przetwarza zakończenia wykonywania testów w kontenerze, one są podane następnego kontenera dostępności.<br /><br />MaxCpuCount można:<br /><br />n, gdzie 1 < = n < = liczba rdzeni: maksymalnie n procesy uruchamiania<br /><br />n, gdzie n = dowolna inna wartość: liczba procesów uruchomić wynosi liczba rdzeni dostępne|
|**TestSessionTimeout**||Umożliwia użytkownikom zakończyć sesję testową, gdy przekracza ona podanego limitu czasu. Test sesji i ustawienia, którego przekroczenie limitu czasu gwarantuje, że zasoby są również używane są ograniczone do określonym czasie. Ustawienie jest dostępne w **programu Visual Studio 2017 wersji 15,5 cala** i nowszych.|

### <a name="diagnostic-data-adapters-data-collectors"></a>Adaptery danych diagnostycznych (moduły zbierające dane)

**DataCollectors** element określa ustawienia adapterów danych diagnostycznych. Adaptery danych diagnostycznych zbierać dodatkowe informacje na temat środowiska i testowanej aplikacji. Każda karta zawiera ustawienia domyślne, a następnie trzeba podać ustawienia, jeśli nie chcesz użyć wartości domyślnych.

#### <a name="code-coverage-adapter"></a>Adapter pokrycia kodu

```xml
<CodeCoverage>
    <ModulePaths>
        <Exclude>
            <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
        </Exclude>
    </ModulePaths>

    <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
    <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
    <CollectFromChildProcesses>True</CollectFromChildProcesses>
    <CollectAspDotNet>False</CollectAspDotNet>
</CodeCoverage>
```

Moduł zbierający dane pokrycia kodu tworzy dziennik z zapisami, które części kodu aplikacji zostały wykonane w teście. Aby uzyskać więcej informacji dotyczących dostosowywania ustawień pokrycia kodu, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

#### <a name="video-data-collector"></a>Moduł zbierający dane wideo

Moduł zbierający dane wideo przechwytuje rejestrowania ekranu, gdy testy są uruchamiane. Rejestracji jest przydatne podczas rozwiązywania problemów testów interfejsu użytkownika. Moduł zbierający dane wideo jest dostępna w **programu Visual Studio 2017 wersji 15,5 cala** i nowszych.

Aby dostosować innego typu adapterów danych diagnostycznych, użyj [plik ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
</TestRunParameters>
```

Parametry testu umożliwiają definiowanie zmiennych i wartości, które są dostępne dla testów w czasie wykonywania. Dostęp przy użyciu parametrów <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType> właściwości:

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
```

Aby użyć parametrów uruchomienia testu, Dodaj prywatnej <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> pola i publiczny <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> właściwości do własnej klasy testu.

### <a name="mstest-run-settings"></a>Ustawienia uruchomienia MSTest

```xml
<MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
</MSTest
```

Te ustawienia są specyficzne dla adaptera testu, który uruchamia metody testowe, które mają <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybutu.

|Konfiguracja|Domyślny|Wartości|
|-------------------|-------------|------------|
|**ForcedLegacyMode**|false|W programie Visual Studio 2012 MSTest adapter została zoptymalizowana pod kątem ułatwiają i skalowalność. Niektóre zachowania, na przykład kolejność, w jakiej są uruchamiane testy, mogą nie być dokładnie takie same, jak w poprzednich wersjach programu Visual Studio. Ta wartość **true** używać starszej karty testu.<br /><br />Na przykład możesz użyć tego ustawienia, jeśli masz *app.config* plik określony dla testu jednostkowego.<br /><br />Zaleca się, aby rozważyć refaktoryzację testów pozwalającą na użycie nowszego adaptera.|
|**IgnoreTestImpact**|false|Funkcja wpływu na testy określa priorytety testów, których dotyczą ostatnie zmiany, po uruchomieniu w programie MSTest lub Microsoft Test Manager. To ustawienie powoduje wyłączenie funkcji. Aby uzyskać więcej informacji, zobacz [testy, które powinny być uruchamiane od czasu poprzedniej kompilacji](https://msdn.microsoft.com/library/dd286589).|
|**Plik_ustawień**||Można określić plik ustawień testu do użycia w adaptera MSTest. Można również określić plik ustawień testu wybierając **Test** > **testowanie ustawień** > **wybierz plik ustawień testu**.<br /><br />Jeśli ta wartość jest określona, należy także ustawić **ForcedlegacyMode** do **true**.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|false|Po zakończeniu przebiegu testu MSTest jest zamykany. Proces, który jest uruchamiany jako część testu jest również skasowane. Jeśli chcesz podtrzymywania modułu wykonania testu, ustaw wartość na **true**. To ustawienie można na przykład użyć, aby zachować przeglądarki uruchomionych między kodowane testy interfejsu użytkownika.|
|**DeploymentEnabled**|true|Jeśli wartość jest ustawiona **false**, elementów wdrożenia, które zostały określone w metodę testu nie są kopiowane do katalogu wdrożenia.|
|**CaptureTraceOutput**|true|Możesz zapisywać do śledzenia debugowania używana metoda testu <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType>.|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Aby zachować katalogu wdrożenia po uruchomieniu testu, ustaw tę wartość na **false**.|
|**MapInconclusiveToFailed**|false|Po zakończeniu testu o stanie niejednoznaczny, jest zamapowany na stan pominięto w **Eksploratora testów**. Jeśli chcesz niejednoznaczny testy, które ma być wyświetlany jako zakończony niepowodzeniem, ustaw wartość na **true**.|
|**InProcMode**|false|Jeśli chcesz testów do uruchomienia tego samego procesu jako adaptera MSTest, ta wartość **true**. To ustawienie zapewnia mniejszy przyrost wydajności. Jednak jeśli test kończy działanie z powodu wyjątku, pozostałe testy nie działają.|
|**AssemblyResolution**|false|Można określić ścieżki do następującej liczby dodatkowych zestawów podczas wyszukiwania i przeprowadzanie testów jednostkowych. Na przykład użyć tych ścieżek dla zestawów zależności, które nie znajdują się w tym samym katalogu co zestaw testowy. Aby określić ścieżkę, należy użyć **ścieżki katalogu** elementu. Ścieżki może zawierać zmienne środowiskowe.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md)
- [Visual Studio Test zadań (VSTS)](/vsts/pipelines/tasks/test/vstest?view=vsts)