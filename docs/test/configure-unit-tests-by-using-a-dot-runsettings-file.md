---
title: Konfigurowanie testów jednostkowych programu Visual Studio przy użyciu pliku runsettings | Dokumentacja firmy Microsoft
ms.date: 02/28/2018
ms.technology: vs-ide-test
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 813a2c003923159b6805280ab3a7f5c3c0559f13
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Konfigurowanie testów jednostkowych przy użyciu *runsettings* pliku

Testy jednostkowe w programie Visual Studio można skonfigurować przy użyciu *runsettings* pliku. Na przykład można zmienić wersji .NET Framework, na którym są uruchamiane testy, katalog wyników testu lub dane zebrane podczas uruchomienia testu.

> [!NOTE]
> Nazwa pliku nie ma znaczenia, tak długo, jak użyć rozszerzenia "runsettings".

Jeśli nie wymaga żadnej specjalnej konfiguracji, nie ma potrzeby *runsettings* pliku. Najczęściej używane *runsettings* ma dostosować plik [analiza pokrycia kodu](../test/customizing-code-coverage-analysis.md).

## <a name="customize-tests"></a>Dostosowywanie testów

1. Dodawanie pliku XML do rozwiązania Visual Studio i zmienić jego nazwę na *test.runsettings*.

1. Zamień zawartość pliku XML w następującym przykładzie oraz dostosować zgodnie z potrzebami.

1. Na **testu** menu, wybierz **ustawień testu** > **wybierz plik ustawień testu**.

Możesz utworzyć więcej niż jedną *runsettings* pliku w rozwiązaniu i włączyć lub wyłączyć je w różnych momentach za pomocą **ustawień testu** menu.

![Włączenie pliku ustawień uruchamiania](../test/media/runsettings-1.png)

## <a name="example-runsettings-file"></a>Przykład *runsettings* pliku

Poniżej przedstawiono typowe *runsettings* pliku. Każdy element pliku jest opcjonalny, ponieważ każda wartość ma domyślne parametry.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to solution directory -->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64
      - You can also change it from menu Test, Test Settings, Default Processor Architecture -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>

     <!--TestSessionTimeout is only available with Visual Studio 2017 version 15.5 and higher -->
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

*Runsettings* pliku jest również używany do konfigurowania [analiza pokrycia kodu](../test/customizing-code-coverage-analysis.md).

W dalszej części tego artykułu opisano zawartości pliku.

## <a name="edit-your-runsettings-file"></a>Edytowanie użytkownika *runsettings* pliku

W kolejnych sekcjach opisano elementy *runsettings* pliku.

### <a name="test-run-configuration"></a>Konfiguracja przebiegu testowego

|Węzeł|Domyślny|Wartości|
|----------|-------------|------------|
|`ResultsDirectory`||Katalog rozmieszczenia wyników testu.|
|`TargetFrameworkVersion`|Framework40|Framework35, Framework40, Framework45<br /><br /> To ustawienie określa, która wersja platformy testów jednostkowych służy do odnajdywania i wykonać testów. Może ona być inna niż wersja platformy .NET określonej we właściwościach kompilacji projektu badania jednostki.|
|`TargetPlatform`|x86|x86, x64|
|`TreatTestAdapterErrorsAsWarnings`|false|fałsz, prawda|
|`TestAdaptersPaths`||Jeden lub wiele ścieżek do katalogu, w którym znajdują się TestAdapters|
|`MaxCpuCount`|1|Ten kontroluje stopień wykonywanie równoległe testu podczas testów jednostkowych uruchomione, przy użyciu dostępne rdzenie komputera. Aparat wykonywania testu uruchamiania jako proces unikatowe na każdym dostępne rdzenie i zapewnia kontener core każdego z testów do uruchomienia. Kontener może być zestawu, biblioteki DLL lub odpowiednie artefaktu. Kontener testu jest jednostka planowania. W każdym kontenerze testy są uruchamiane zgodnie ze struktury testowej. Jeśli istnieje wiele kontenerów, następnie jako przetwarza zakończenia wykonywania testów w kontenerze, otrzymują one następnego kontenera dostępności.<br /><br /> MaxCpuCount można:<br /><br /> n, gdzie 1 < = n < = liczba rdzeni: maksymalnie n procesów zostanie uruchomiony<br /><br /> n, gdzie n = dowolna inna wartość: liczba procesów uruchamiana będzie maksymalnie maksymalnie dostępne rdzenie komputera|
|`TestSessionTimeout`||Umożliwia użytkownikom zakończyć sesję testową, gdy przekracza ona podanego limitu czasu. Test sesji i ustawienia, którego przekroczenie limitu czasu gwarantuje, że zasoby są również używane są ograniczone do określonym czasie. Ustawienie jest dostępne w **programu Visual Studio 2017 wersji 15,5 cala** i nowszych.

### <a name="diagnostic-data-adapters-data-collectors"></a>Adaptery danych diagnostycznych (kolektory danych)

`DataCollectors` Element określa ustawienia adapterów danych diagnostycznych. Adaptery danych diagnostycznych zbierać dodatkowe informacje na temat środowiska i testowanej aplikacji. Każda karta zawiera ustawienia domyślne, a następnie trzeba podać ustawienia, jeśli nie chcesz użyć wartości domyślnych.

#### <a name="code-coverage-adapter"></a>Adapter pokrycia kodu

Moduł zbierający dane pokrycia kodu tworzy dziennik z zapisami, które części kodu aplikacji zostały wykonane w teście. Aby uzyskać więcej informacji dotyczących dostosowywania ustawień pokrycia kodu, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

#### <a name="video-data-collector"></a>Moduł zbierający dane wideo

Moduł zbierający dane wideo przechwytuje rejestrowania ekranu, gdy testy są uruchamiane. Rejestracji jest przydatne podczas rozwiązywania problemów testów interfejsu użytkownika. Moduł zbierający dane wideo jest dostępna w **programu Visual Studio 2017 wersji 15,5 cala** i nowszych.

Aby dostosować innego typu adaptera danych diagnostycznych, należy użyć [plik ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="testrunparameters"></a>TestRunParameters

TestRunParameters udostępnia sposób definiowania zmiennych i wartości, które są dostępne dla testów w czasie wykonywania. Te zmienne jest możliwy za pomocą [TestContext](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testcontext(v=vs.140).aspx) obiektu.

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
```

Aby używać TestContext, Dodaj prywatnej [TestContext](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testcontext(v=vs.140).aspx) pola i publiczny `TestContext` właściwości do własnej klasy testu.

### <a name="mstest-run-settings"></a>Ustawienia wykonywania MSTest

Te ustawienia są specyficzne dla adaptera testu, który uruchamia metody testowe, które mają `[TestMethod]` atrybutu.

|Konfiguracja|Domyślny|Wartości|
|-------------------|-------------|------------|
|ForcedLegacyMode|false|W programie Visual Studio 2012 MSTest adapter została zoptymalizowana pod kątem ułatwiają i skalowalność. Niektóre zachowania, na przykład kolejność, w jakiej są uruchamiane testy, mogą nie być dokładnie takie same, jak w poprzednich wersjach programu Visual Studio. Ustaw tę wartość `true` używać starszej karty testu.<br /><br /> Na przykład możesz użyć tego ustawienia, jeśli masz *app.config* plik określony dla testu jednostkowego.<br /><br /> Zaleca się, aby rozważyć refaktoryzację testów pozwalającą na użycie nowszego adaptera.|
|IgnoreTestImpact|false|Funkcja wpływu na testy określa priorytety testów, których dotyczą ostatnie zmiany, po uruchomieniu w programie MSTest lub Microsoft Test Manager. To ustawienie powoduje wyłączenie funkcji. Aby uzyskać więcej informacji, zobacz [porady: zbieranie danych do sprawdzenia, które testy będą można uruchomić po zmiany kodu](http://msdn.microsoft.com/Library/2f921ea1-9bb0-4870-a30f-0521fc22cb47).|
|SettingsFile||Można tu określić plik ustawień testowych do użycia z adapterem MS Test. Można również określić plik ustawień testu za pomocą menu **Test**, **testowanie ustawień**, **wybierz plik ustawień testu**.<br /><br /> Jeśli ta wartość jest określona, należy także ustawić **ForcedlegacyMode** do **true**.<br /><br /> `<RunSettings>   <MSTest>     <SettingsFile>my.testsettings</SettingsFile>      <ForcedLegacyMode>true</ForcedLegacyMode>    </MSTest> </RunSettings>`|
|KeepExecutorAliveAfterLegacyRun|false|Po zakończeniu przebiegu testu MSTest jest zamykany. Proces, który jest uruchamiany jako część testu jest również skasowane. Jeśli program wykonujący test ma być nadal aktywny, ustaw dla tej konfiguracji wartość true.<br /><br /> To ustawienie można na przykład użyć, aby zachować przeglądarki uruchomionych między kodowane testy interfejsu użytkownika.|
|DeploymentEnabled|true|Jeśli wartość jest ustawiona na wartość false, elementów wdrożenia, które określono w metodę testu nie będą kopiowane do katalogu wdrażania.|
|CaptureTraceOutput|true|Można zapisywać do śledzenia debugowania ze swojej metody testowej przy użyciu Trace.WriteLine. Za pomocą tej konfiguracji można wyłączyć ślady debugowania.|
|DeleteDeploymentDirectoryAfterTestRunIsComplete|true|Można zachować Deployment Directory po przebiegu testu z ustawieniem tej wartości jako fałszywej.|
|MapInconclusiveToFailed|false|Jeśli test jest zwracany ze stanem Niejednoznaczny, zwykle będzie mapowany do stanu Pominięty w Eksploratorze testów. Niejednoznaczny testy mają być wyświetlane jako niepowodzenie firmy, należy użyć tej konfiguracji.|
|InProcMode|false|Jeśli testy mają być wykonywane w tym samym procesie co adapter MS Test, dla wartości tej należy wybrać ustawienie true. To ustawienie zapewnia mniejszy przyrost wydajności. Jeśli jednak test kończy się wyjątkiem, inne testy nie będą kontynuowane.|
|AssemblyResolution|false|Można określić ścieżki do następującej liczby dodatkowych zestawów podczas wyszukiwania i przeprowadzanie testów jednostkowych. Na przykład użyć tych ścieżek dla zestawów zależności, które nie znajdują się w tym samym katalogu co zestaw testowy. Aby określić ścieżkę, należy użyć elementu "Ścieżka katalogu". Ścieżki może zawierać zmienne środowiskowe.<br /><br /> `<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md)