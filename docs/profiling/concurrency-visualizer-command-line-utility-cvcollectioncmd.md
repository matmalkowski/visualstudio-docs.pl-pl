---
title: "Narzędzie wiersza polecenia CONCURRENCY Visualizer (CVCollectionCmd) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.performance.cvcollectioncmd
ms.assetid: 476601be-1608-4014-af15-5aba6ccbed1c
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 53dd29671e20f19c0ef83d5920581c7038f32c9f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="concurrency-visualizer-command-line-utility-cvcollectioncmd"></a>Narzędzie wiersza polecenia Concurrency Visualizer (CVCollectionCmd)
Narzędzie wiersza polecenia Concurrency Visualizer (CVCollectionCmd.exe) umożliwia zbierać dane śledzenia w wierszu polecenia, aby wyświetlić w Concurrency Visualizer dla programu Visual Studio. Narzędzia można używać na komputerach, które nie mają zainstalowanego programu Visual Studio.  
  
> [!NOTE]
>  Począwszy od programu Visual Studio 2013 narzędzia Concurrency Visualizer to opcjonalne rozszerzenie. (Wcześniej go była ona dostępna w programie Visual Studio.) Możesz pobrać [współbieżności wizualizatora Collection Tools for Visual Studio 2015](http://www.microsoft.com/en-in/download/details.aspx?id=49103) z Centrum pobierania.  
  
## <a name="download-the-concurrency-visualizer-command-line-utility"></a>Pobieranie narzędzia wiersza polecenia wizualizatora współbieżności  
 Aby pobrać i zainstalować narzędzia wiersza polecenia, przejdź do [współbieżności wizualizatora Collection Tools for Visual Studio 2015](http://www.microsoft.com/en-in/download/details.aspx?id=49103) i postępuj zgodnie z instrukcjami. Domyślnie CVCollectionCmd.exe jest zainstalowany w %ProgramFiles%\Microsoft Tools\ kolekcji wizualizatora współbieżności (% ProgramFiles (x86) %\Microsoft Tools\ kolekcji wizualizatora współbieżności na x64 komputerów).  
  
## <a name="collect-a-trace-with-cvcollectioncmd"></a>Zbierz ślad z CVCollectionCmd  
 Możliwość zbierania śladu poprzez uruchomienie aplikacji z CVCollectionCmd lub dołączając do niej. Zobacz polecenie poniżej opcji. Na przykład  
  
```  
<Path>CVCollectionCmd /launch c:\myapp\myapp.exe /outdir c:\myapp\data  
```  
  
## <a name="commands-and-parameters"></a>Poleceń i parametrów  
 Aby uzyskać pomoc dotyczącą poleceń i parametrów w narzędziu wiersza polecenia, wpisz to polecenie w wierszu polecenia:  
  
 **CvCollectionCmd /?**  
  
|Opcja|Opis|Parametry|Zwracane wartości|  
|------------|-----------------|----------------|-------------------|  
|Zapytanie|Zwraca czy zbieranie danych można uruchomić.|Brak|0, jeśli kolekcja jest gotowy do uruchomienia.<br /><br /> 1, jeśli kolekcja jest już w toku.<br /><br /> 2. w przypadku kolekcji nie jest w toku, ale co najmniej jeden z wymaganych [ETW](/dotnet/framework/wcf/samples/etw-tracing) sesji jest już włączony.|  
|Uruchom|Uruchamia określony proces w obszarze narzędzia Concurrency Visualizer.|Ścieżka pliku wykonywalnego.|0, jeśli uruchomienie zakończyło się pomyślnie.<br /><br /> 1, jeśli uruchomienie nie powiodło się, ponieważ nie można uruchomić aplikacji docelowej.<br /><br /> 13, jeśli uruchomienie nie powiodło się, ponieważ CVCollectionCmd nie ma wystarczających uprawnień do zapisu w katalogu określonym produktem wyjściowym.|  
|Dołącz|Rozpoczyna się zbierania danych śledzenia systemowe; w przeciwnym razie dołącza do procesu, jeśli został określony.|Brak.|0, jeśli załącznika zakończyło się pomyślnie.<br /><br /> 1, jeśli załącznika nie powiodło się, ponieważ określony proces jest nieprawidłowych lub niejednoznacznych.<br /><br /> 13, jeśli załącznik nie powiodła się, ponieważ CVCollectionCmd nie ma wystarczających uprawnień do zapisu w katalogu określonym produktem wyjściowym.|  
|Odłącz|Zatrzymuje kolekcji.|Brak.|0, jeśli oderwania zakończyło się pomyślnie.<br /><br /> 1, jeśli oderwania nie powiodło się, ponieważ kolekcja nie jest obecnie w toku.<br /><br /> 2. w przypadku oderwania nie powiodło się, ponieważ nie można zatrzymać kolekcji.|  
|Analiza|Analizuje określony śledzenia.|Pełna ścieżka pliku CVTrace.|0, jeśli analiza powiodła się.<br /><br /> 1, jeśli nie można rozpocząć analizy, ponieważ określony śledzenia został całego systemu, ale nie podano żaden proces docelowy.<br /><br /> 2. w przypadku analizy nie można uruchomić, ponieważ śledzenie nie całego systemu i proces został określony.<br /><br /> 3, jeśli analiza nie powiodła się, ponieważ określony proces jest nieprawidłowy.<br /><br /> 4, jeśli analiza nie powiodła się, ponieważ określony plik CVTrace jest nieprawidłowy.|  
|LaunchArgs|Określa argumenty pliku wykonywalnego docelowej. Ta opcja dotyczy tylko polecenie Uruchom.|Argumenty wiersza polecenia do aplikacji.|Brak.|  
|Outdir|Określa katalog, w którym można zapisać plików śledzenia. Ma zastosowanie do uruchamiania i Dołącz poleceń.|Ścieżka lub ścieżka względna.|Brak.|  
|Proces|Określa proces, aby dołączyć do po wykonaniu polecenia Attach lub proces w śledzenia do analizowania podczas wykonywania polecenia analizy. Zastosowanie polecenia Attach i Analizuj.|Identyfikator PID lub nazwę procesu.|Brak.|  
|Konfiguracja|Określa ścieżkę pliku konfiguracji, jeśli chcesz, aby ustawienia kolekcji innych niż domyślne.   Ma zastosowanie do polecenia Uruchom, Dołącz i Analizuj.|Ścieżka katalogu lub względna ścieżka pliku konfiguracji XML.|Brak.|  
  
## <a name="customizing-configuration-settings"></a>Dostosowywanie ustawień konfiguracji  
 Jeśli używasz CVCollectionCmd Aby zbierać dane śledzenia i chcesz dostosować ustawienia kolekcji, a następnie określ je przy użyciu pliku konfiguracji.  
  
> [!NOTE]
>  Korzystając z programu Visual Studio Aby zbierać dane śledzenia, nie należy bezpośrednio modyfikować pliku konfiguracji.  Zamiast tego należy użyć [Zaawansowane ustawienia](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) okno dialogowe, aby zmodyfikować ustawienia.  
  
 Aby zmodyfikować ustawienia kolekcji, należy utworzyć plik konfiguracji, na komputerze, w którym zostanie uruchomione narzędzie CVCollectionCmd. Należy utworzyć plik konfiguracji, od początku lub można skopiować pliku konfiguracji na komputerze, który ma zainstalowanego programu Visual Studio i zmodyfikować to. Plik ma nazwę `UserConfig.xml` i znajduje się w **lokalnego AppData** folderu. Po uruchomieniu narzędzia, należy użyć opcji konfiguracji w połączeniu z polecenia uruchamiania, Attach lub analizy.  W parametrze skojarzoną z opcji konfiguracji Określ ścieżkę pliku konfiguracji.  
  
### <a name="configuration-file-tags"></a>Tagi pliku konfiguracji  
 Plik konfiguracji jest oparte na języku XML. Poniżej przedstawiono prawidłowych tagów i wartości:  
  
|Tag|Opis|Wartości|  
|---------|-----------------|------------|  
|Konfiguracja|Rozgranicza ogólną pliku konfiguracji.|Musi zawierać następujące elementy:<br /><br /> -MinorVersion<br />-MajorVersion|  
|MajorVersion|Określa wersję główną programu w pliku config.|Musi mieć wartość 1 dla [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] projektów. Jeśli nie 1, narzędzie nie będzie działać.|  
|MinorVersion|Określa wersję pomocniczą pliku konfiguracji.|Musi mieć wartość 0 odpowiadającą [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] projektów. Jeśli nie 0, narzędzie nie będzie działać.|  
|IncludeEnvSymbolPath|Ustawia wartość, która określa, czy używane jest środowisko ścieżki symboli (_NT_SYMBOL_PATH).|— Wartość true<br />— Wartość false|  
|DeleteEtlsAfterAnalysis|Ustawia wartość określającą, czy pliki ETL zostaną usunięte po zakończeniu analizy.|— Wartość true<br />— Wartość false|  
|SymbolPath|Określa ścieżkę serwera symboli. Aby uzyskać więcej informacji, zobacz [serwera Microsoft Symbol Server umożliwia uzyskanie plików symboli debugowania](http://go.microsoft.com/fwlink/?LinkID=149389).|Nazwa katalogu lub adres URL.|  
|Znaczniki|Zawiera listę dostawców znacznika.|Może zawierać zero lub więcej elementów MarkerProvider.|  
|MarkerProvider|Określa dostawcę jednego znacznika.|Musi zawierać następujące elementy:<br /><br /> -Poziom<br />— IDENTYFIKATOR GUID<br />-Name<br /><br /> Może zawierać następujące elementy:<br /><br /> -Kategorii<br />-IsEnabled|  
|Poziom|Ustawia poziom ważności MarkerProvider.|-Niski<br />-Normalny<br />-Wysoka<br />-Krytyczne<br />— Wszystko|  
|Identyfikator GUID|Globalnie unikatowy identyfikator dostawcy ETW znacznika.|IDENTYFIKATOR GUID.|  
|Nazwa|Określa opis dostawcy znacznika.|Ciąg.|  
|Kategorie|Określa kategorie zbierane dla dostawcy znacznika.|Rozdzielany przecinkami ciąg liczb lub zakresy numerów.|  
|IsEnabled|Ustawia wartość określającą, czy dostawca znacznik jest włączony dla kolekcji.|— Wartość true<br />— Wartość false|  
|FilterConfig|Określa listę opcji konfiguracji zdarzeń funkcji ETW, które zostały przefiltrowane z kolekcji.|Może zawierać następujące elementy:<br /><br /> -CollectClrEvents<br />-ClrCollectionOptions<br />-CollectSampleEvents<br />-CollectGpuEvents<br />-CollectFileIO|  
|CollectClrEvents|Wartość, która określa, czy są zbierane zdarzenia CLR.|— Wartość true<br />— Wartość false|  
|ClrCollectionOptions|Określa, czy do gromadzenia zdarzeń CLR dla aplikacji natywnych i czy służąca do gromadzenia zdarzeń zamknięcia NGEN.|Może zawierać jedną, zarówno lub żadna z tych wartości:<br /><br /> -CollectForNative<br />-DisableNGenRundown|  
|CollectSampleEvents|Ustawia wartość określającą, czy są zbierane zdarzenia próbkowania.|— Wartość true<br />— Wartość false|  
|CollectGpuEvents|Ustawia wartość określającą, czy są zbierane zdarzenia generowane przez DX.|— Wartość true<br />— Wartość false|  
|CollectFileIO|Ustawia wartość określającą, czy są zbierane zdarzenia We/Wy pliku.|— Wartość true<br />— Wartość false|  
|UserBufferSettings|Określa listę parametrów ustawienia bufora użytkownika.|Musi zawierać następujące elementy:<br /><br /> -BufferFlushTimer<br />-BufferSize<br />-MinimumBuffers<br />-MaximumBuffers|  
|KernelBufferSettings|Określa listę parametrów ustawienia buforu jądra.|Musi zawierać następujące elementy:<br /><br /> -BufferFlushTimer<br />-BufferSize<br />-MinimumBuffers<br />-MaximumBuffers|  
|BufferFlushTimer|Określa Czasomierz opróżniania buforów ETW.|Dodatnia liczba całkowita.|  
|BufferSize|Ilość pamięci przydzielonej dla każdego buforu sesji śledzenia zdarzeń w kilobajtach.|Liczba z przedziału od 0 do 1024.|  
|MinimumBuffers|Minimalna liczba buforów, które są przydzielone do puli buforów sesji śledzenia zdarzeń.|Dodatnia liczba całkowita większa lub równa dwa razy liczba rdzeni logicznych.|  
|MaximumBuffers|Maksymalna liczba buforów, które są przydzielone do puli buforów sesji śledzenia zdarzeń.|Liczba większa niż lub równa MinimumBuffers.|  
|JustMyCode|Określa listę katalogów tylko mój kod.|Lista elementów MyCodeDirectory zero lub więcej.|  
|MyCodeDirectory|Określa katalog, który zawiera kod.|Ścieżka bezwzględna.|  
  
### <a name="example"></a>Przykład  
 Zamiast tworzenia pliku konfiguracji, od początku, możesz skopiować poniższy przykład, a następnie zmodyfikować go zgodnie z wymaganiami.  
  
```xml  
<?xml version="1.0"?>  
<LocalConfig xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" MajorVersion="1" MinorVersion="0">  
  
  <IncludeEnvSymbolPath>true</IncludeEnvSymbolPath>  
  
  <DeleteEtlsAfterAnalysis>true</DeleteEtlsAfterAnalysis>  
  
  <TraceLocation>C:\traces</TraceLocation>  
  
  <SymbolPath>http://symweb</SymbolPath>  
  
  <Markers>  
    <MarkerProvider Name="Default" Guid="8d4925ab-505a-483b-a7e0-6f824a07a6f0" Level="Low" />  
    <MarkerProvider Name="TPL" Guid="2e5dba47-a3d2-4d16-8ee0-6671ffdcd7b5" Level="Normal" />  
    <MarkerProvider Name="TPL Dataflow" Guid="16f53577-e41d-43d4-b47e-c17025bf4025" Level="Normal" />  
    <MarkerProvider Name="TPL Synchronization" Guid="ec631d38-466b-4290-9306-834971ba0217" Level="Normal" />  
    <MarkerProvider Name="PLINQ" Guid="159eeeec-4a14-4418-a8fe-faabcd987887" Level="Normal" />  
    <MarkerProvider Name="Concurrency Runtime" Guid="f7b697a3-4db5-4d3b-be71-c4d284e6592f" Level="Normal" />  
    <MarkerProvider Name="Scenario Markers" Guid="fb9244c9-f23a-4966-8a9c-97a51f8c355b" Level="Low" />  
  
    <!-- The IsEnabled and Categories elements are optional -->  
    <MarkerProvider Name="myMarker1" Guid="d0dbb3a3-895c-4ce6-96d9-28f69d664dc3" Level="Critical" IsEnabled="false" Categories="0,1,3-5,8" />  
    <MarkerProvider Name="myMarker2" Guid="03452127-a617-4302-9e30-c0d10442e4ee" Level="Low" IsEnabled="false" Categories="0,1,3-5,8-10,11-13" />  
  </Markers>  
  
  <FilterConfig>  
    <CollectClrEvents>true</CollectClrEvents>  
    <ClrCollectionOptions>CollectForNative DisableNGenRundown</ClrCollectionOptions>  
    <CollectSampleEvents>true</CollectSampleEvents>  
    <CollectGpuEvents>true</CollectGpuEvents>  
    <CollectFileIO>true</CollectFileIO>  
  </FilterConfig>  
  
  <UserBufferSettings>  
    <BufferFlushTimer>0</BufferFlushTimer>  
    <BufferSize>256</BufferSize>  
    <MinimumBuffers>512</MinimumBuffers>  
    <MaximumBuffers>1024</MaximumBuffers>  
  </UserBufferSettings>  
  
  <KernelBufferSettings>  
    <BufferFlushTimer>0</BufferFlushTimer>  
    <BufferSize>256</BufferSize>  
    <MinimumBuffers>512</MinimumBuffers>  
    <MaximumBuffers>1024</MaximumBuffers>  
  </KernelBufferSettings>  
  
  <!-- List of MyCodeDirectory directories -->  
  <JustMyCode>  
    <MyCodeDirectory>C:\myBinaries1</MyCodeDirectory>  
    <MyCodeDirectory>C:\myBinaries2</MyCodeDirectory>  
  </JustMyCode>  
</LocalConfig>  
  
```
