---
title: "Konfigurowanie testów jednostkowych przy użyciu pliku runsettings | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 1925152f830d9969c8650fe698be6ebc70e65cf2
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Konfigurowanie testów jednostkowych przy użyciu pliku runsettings

Testy jednostkowe w programie Visual Studio można skonfigurować przy użyciu \*pliku runsettings. (Nazwa pliku nie ma znaczenia, pod warunkiem używane rozszerzenie "runsettings".) Na przykład można zmienić wersji platformy .NET, na którym zostaną uruchomione testy, katalogu zawierającego wyniki testu są dostarczane, a dane zebrane podczas testu Uruchom.

Jeśli nie wymaga żadnej specjalnej konfiguracji, nie ma potrzeby \*pliku runsettings. Najczęściej używane \*pliku runsettings jest, aby dostosować [pokrycie kodu](../test/customizing-code-coverage-analysis.md).

## <a name="customizing-tests-with-a-runsettings-file"></a>Dostosowywanie testów przy użyciu pliku .runsettings

1. Dodawanie pliku XML do rozwiązania Visual Studio i zmień jego nazwę na test.runsettings. (Nazwa pliku nie ma znaczenia, ale runsettings musi mieć rozszerzenie).

1. Zamień zawartość pliku XML w następującym przykładzie oraz dostosować zgodnie z potrzebami.

1. Na **testu** menu, wybierz **ustawień testu** > **wybierz plik ustawień testu**.

Możesz utworzyć więcej niż jedną \*runsettings pliku w rozwiązaniu i włączyć lub wyłączyć je w różnych momentach za pomocą **ustawień testu** menu.

![Włączanie plik parametrów uruchomieniowych](../test/media/runsettings-1.png "RunSettings-1")

## <a name="example-runsettings-file"></a>Przykładowy plik runsettings

Poniżej przedstawiono typowe \*pliku runsettings. Każdy element pliku jest opcjonalny, ponieważ każda wartość ma domyślne parametry.

```xml
<?xml version="1.0" encoding="utf-8"?>  
<RunSettings>  
  <!-- Configurations that affect the Test Framework -->  
  <RunConfiguration>  
    <MaxCpuCount>1</MaxCpuCount>  
    <!-- Path relative to solution directory -->  
    <ResultsDirectory>.\TestResults</ResultsDirectory>  
  
    <!-- [x86] | x64    
      - You can also change it from menu Test, Test Settings, Default Processor Architecture -->  
    <TargetPlatform>x86</TargetPlatform>  
  
    <!-- Framework35 | [Framework40] | Framework45 -->  
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>  
  
    <!-- Path to Test Adapters -->  
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>  
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
  
Pliku runsettings jest również używany do konfigurowania [pokrycie kodu](../test/customizing-code-coverage-analysis.md).  
  
W pozostałej części tego tematu opisano zawartość pliku.  

## <a name="edit-your-runsettings-file"></a>Edytuj plik .runsettings

Plik .runsettings zawiera poniższe elementy.

### <a name="test-run-configuration"></a>Konfiguracja przebiegu testowego

|Węzeł|Domyślny|Wartości|  
|----------|-------------|------------|  
|`ResultsDirectory`||Katalog, w którym zostaną umieszczone wyniki testu.|  
|`TargetFrameworkVersion`|Framework40|Framework35, Framework40, Framework45<br /><br /> Określa, która wersja środowiska testów jednostkowych jest używana do odnajdowania i wykonywania testów. Może ona być inna niż wersja platformy .NET określonej we właściwościach kompilacji projektu badania jednostki.|  
|`TargetPlatform`|x86|x86, x64|  
|`TreatTestAdapterErrorsAsWarnings`|false|fałsz, prawda|  
|`TestAdaptersPaths`||Jeden lub wiele ścieżek do katalogu, w którym znajdują się TestAdapters|  
|`MaxCpuCount`|1|To określa stopień wykonywanie równoległe testu podczas uruchamiania jednostki testy przy użyciu dostępne rdzenie komputera.  Aparat wykonywania testu uruchamiania jako proces unikatowe na każdym dostępne rdzenie i zapewnia kontener core każdego z testów do uruchomienia, takich jak zestaw, biblioteki DLL lub odpowiednie artefaktu.  Kontener testu jest jednostka planowania.  W każdym kontenerze testy są uruchamiane zgodnie ze struktury testowej.  Jeśli istnieje wiele kontenerów, następnie jako przetwarza zakończenia wykonywania testów w kontenerze, otrzymują one następnego kontenera dostępności.<br /><br /> MaxCpuCount można:<br /><br /> n, gdzie 1 < = n < = liczba rdzeni: maksymalnie n procesów zostanie uruchomiony<br /><br /> n, gdzie n = dowolna inna wartość: liczba procesów uruchamiana będzie maksymalnie maksymalnie dostępne rdzenie komputera|  
  
### <a name="diagnostic-data-adapters-data-collectors"></a>Adaptery danych diagnostycznych (kolektory danych)

`DataCollectors` Element określa ustawienia adapterów danych diagnostycznych. Adaptery danych diagnostycznych są używane do zbierania dodatkowych informacji dotyczących środowiska i testowanej aplikacji. Każda karta zawiera ustawienia domyślne, a następnie trzeba podać ustawienia, jeśli nie chcesz użyć wartości domyślnych.

#### <a name="code-coverage-adapter"></a>Adapter pokrycia kodu

Moduł zbierający dane pokrycia kodu tworzy dziennik z zapisami, które części kodu aplikacji zostały wykonane w teście. Aby uzyskać więcej informacji dotyczących dostosowywania ustawień pokrycia kodu, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

### <a name="testrunparameters"></a>TestRunParameters

TestRunParameters udostępnia sposób definiowania zmiennych i wartości, które są dostępne dla testów w czasie wykonywania.  

### <a name="mstest-run-settings"></a>Ustawienia wykonywania MSTest

Te ustawienia są specyficzne dla adaptera testu, który uruchamia metody testowe, które mają `[TestMethod]` atrybutu.  

|Konfiguracja|Domyślny|Wartości|  
|-------------------|-------------|------------|  
|ForcedLegacyMode|false|W programie Visual Studio 2012 adapter karty MSTest został zoptymalizowany, aby był bardziej skalowalny i działał szybciej. Niektóre zachowania, na przykład kolejność, w jakiej są uruchamiane testy, mogą nie być dokładnie takie same, jak w poprzednich wersjach programu Visual Studio. Ustaw tę wartość `true` używać starszej karty testu.<br /><br /> Można jej użyć na przykład wtedy, gdy dysponujesz plikiem app.config określonym dla testu jednostkowego.<br /><br /> Zaleca się, aby rozważyć refaktoryzację testów pozwalającą na użycie nowszego adaptera.|  
|IgnoreTestImpact|false|Funkcja wpływu na testy określa priorytety testów, których dotyczą ostatnie zmiany, po uruchomieniu w programie MSTest lub Microsoft Test Manager. To ustawienie powoduje wyłączenie funkcji. Aby uzyskać więcej informacji, zobacz [porady: zbieranie danych do sprawdzenia, które testy będą można uruchomić po zmiany kodu](http://msdn.microsoft.com/Library/2f921ea1-9bb0-4870-a30f-0521fc22cb47).|  
|SettingsFile||Można tu określić plik ustawień testowych do użycia z adapterem MS Test. Można również określić plik ustawień testu za pomocą menu **Test**, **testowanie ustawień**, **wybierz plik ustawień testu**.<br /><br /> Jeśli ta wartość jest określona, należy także ustawić **ForcedlegacyMode** do **true**.<br /><br /> `<RunSettings>   <MSTest>     <SettingsFile>my.testsettings</SettingsFile>      <ForcedLegacyMode>true</ForcedLegacyMode>    </MSTest> </RunSettings>`|  
|KeepExecutorAliveAfterLegacyRun|false|Po zakończeniu przebiegu testu MSTest jest zamykany. Każdy proces, który jest uruchamiany jako część testu, również będzie w tej chwili zatrzymywany. Jeśli program wykonujący test ma być nadal aktywny, ustaw dla tej konfiguracji wartość true.<br /><br /> Można na przykład wykorzystać ją do zachowania działania przeglądarki między kodowanymi testami interfejsu użytkownika.|  
|DeploymentEnabled|true|Jeśli zostanie ustawiona wartość false, elementy wdrożenia, które określono w metodzie testowej, nie zostaną skopiowane do katalogu wdrożenia.|  
|CaptureTraceOutput|true|Można zapisywać do śledzenia debugowania ze swojej metody testowej przy użyciu Trace.WriteLine. Za pomocą tej konfiguracji można wyłączyć ślady debugowania.|  
|DeleteDeploymentDirectoryAfterTestRunIsComplete|true|Można zachować Deployment Directory po przebiegu testu z ustawieniem tej wartości jako fałszywej.|  
|MapInconclusiveToFailed|false|Jeśli test jest zwracany ze stanem Niejednoznaczny, zwykle będzie mapowany do stanu Pominięty w Eksploratorze testów. Jeśli chcesz, aby testy niejednoznaczne były wykazywane jako Zakończone niepowodzeniem, użyj tej konfiguracji.|  
|InProcMode|false|Jeśli testy mają być wykonywane w tym samym procesie co adapter MS Test, dla wartości tej należy wybrać ustawienie true. To ustawienie zapewnia mniejszy przyrost wydajności. Jeśli jednak test kończy się wyjątkiem, inne testy nie będą kontynuowane.|  
|AssemblyResolution|false|Można określić ścieżki do następującej liczby dodatkowych zestawów podczas wyszukiwania i przeprowadzanie testów jednostkowych.  Na przykład użyć tych ścieżek dla zestawów zależności, które nie znajdują się w tym samym katalogu co zestaw testowy.  Aby określić ścieżkę, należy użyć elementu "Ścieżka katalogu".  Ścieżki może zawierać zmienne środowiskowe.<br /><br /> `<AssemblyResolution>  <Directory Path>"D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|  

## <a name="see-also"></a>Zobacz także

[Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md)  
