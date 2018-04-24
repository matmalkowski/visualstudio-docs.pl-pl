---
title: Profilowanie na HPC (przetwarzanie o wysokiej wydajności) klastrów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.hpc.wizard.exeoptions
- vs.performance.hpc.wizard.summary
- vs.performance.hpc.wizard.startoptions
- vs.performance.hpc.wizard.intro
- vs.performance.hpc.property.basic
- vs.performance.hpc.wizard.application
- vs.performance.hpc.wizard.clusteroptions
- vs.performance.hpc.property.advanced
helpviewer_keywords:
- profililng tools,HPC
- HPC profiling
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e4542289e0d9dceeeadf972db714148d4e1bec4d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="profiling-on-hpc-high-performance-computing-clusters"></a>Profilowanie na klastrach HPC (przetwarzanie o wysokiej wydajności)

Można profilu w węzłach obliczeniowych klastrów HPC systemu Windows firmy Microsoft, za pomocą metody pobierania próbek Visual Studio Profiling Tools. Aby uzyskać więcej informacji na temat HPC zobacz [Windows HPC](http://go.microsoft.com/fwlink/?LinkId=165393) w witrynie sieci Web firmy Microsoft.

## <a name="prerequisites"></a>Wymagania wstępne

Do profilowania w węźle obliczeń HPC, wykonaj następujące czynności:

- Zainstaluj program Microsoft HPC Pack 2008 na tym samym komputerze co program Visual Studio. Komputer nie musi być częścią klastra HPC. Można zainstalować pakietu HPC w [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=177414).

- Zainstaluj [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)] i autonomiczna wersja narzędzi profilowania na HPC węzła obliczeniowego. Zainstaluj programy dla obu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] i autonomiczny profiler są dostępne na nośniku instalacyjnym programu Visual Studio. **Uwaga** po zainstalowaniu należy ponownie uruchomić mocy obliczeniowej [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] oraz przed zainstalowaniem narzędzi profilowania.

 Aby zainstalować [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)] i autonomicznych narzędzi profilowania na active HPC obliczeniowe węzeł i Włącz profilowanie na komputerze klastra, wykonaj następujące kroki:

1. Otwórz okno wiersza polecenia, z zainstalowanym pakietem HPC.

2. Wpisz następujące polecenia w osobnych wierszy polecenia:

    1. `clusrun /all /scheduler:` *%HeadNode% %FxPath%* `/q /norestart`

    2. `clusrun /all /scheduler:` *% HeadNode %* `shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`

    3. `clusrun /all /scheduler:` *%HeadNode% %ProfilerPath%* `/q /norestart`

|||
|-|-|
|*%HeadNode%*|Nazwa węzła głównego klastra.|
|*%FxPath%*|Ścieżka do [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)] Instalatora. Na nośniku instalacyjnym programu Visual Studio jest ścieżka: WCU\dotNetFramework\dotNetFx40_Full_x86_x64.exe|
|*%ProfilerPath%*|Ścieżka do autonomiczna wersja Instalatora narzędzi profilowania. Na nośniku instalacyjnym programu Visual Studio ścieżka to: autonomiczny Profiler\x64\vs_profiler.exe|

## <a name="profiling-on-an-hpc-compute-node"></a>Profilowanie na węźle obliczeń HPC

Sesja profilowania konfigurowania za pomocą Kreatora osiągów HPC pozwala określić informacje o klastrze i obiekt docelowy HPC. Dodatkowe opcje można ustawić na stronach właściwości sesji wydajności. Narzędzia profilowania automatycznie Wdróż docelowy niezbędne pliki binarne i uruchomienia profilera i aplikacji HPC.

1. Na **Analizuj** menu, kliknij przycisk **Uruchom Kreatora osiągów HPC**. Jeśli polecenie nie jest dostępne, upewnij się, że powyższe wymagania wstępne.

2. Kliknij przycisk **dalej** na pierwszej stronie kreatora.

3. Na drugiej stronie kreatora wybierz aplikację, którą chcesz profilu.

    - Profilowanie projektu, który jest obecnie otwarty w [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], wybierz pozycję **co najmniej jeden z dostępnych projektów** opcji, a następnie wybierz nazwę projektu z listy.

    - Do pliku binarnego, który nie znajduje się w profilu wybierz Otwórz projekt **plik wykonywalny (. Plik EXE)** opcji.

4. Kliknij przycisk **Dalej**.

5. Na trzeciej stronie kreatora:

    - Jeśli plik wykonywalny, który nie ma otwartego projektu są profilowania, określ ścieżkę do pliku binarnego w **co to jest pełna ścieżka do pliku wykonywalnego**.

    - Jeśli plik wykonywalny, który nie ma otwartego projektu są profilowania, można określić żadnych argumentów wiersza polecenia do przekazania do procesu w **argumenty wiersza polecenia**.

    - W **zdalny katalog roboczy**, określ ścieżkę do folderu, który jest używany przez wystąpień procesu na poszczególne węzły obliczeniowe.

    - W **lokalizacja wdrożenia**, określ ścieżkę do katalogu, którego programu HPC server używa do etapu obrazów do wdrożenia.

6. Kliknij przycisk **Dalej**.

7. Na czwartej stronie kreatora:

    - W **Head, węzła** kliknij komputer, który działa jako węzła głównego klastra HPC w przebiegu profilowania. Węzeł Head może być "localhost", co umożliwia profilu na komputerze lokalnym, bez konieczności dla klastra.

    - W **liczba procesów** kliknij liczbę wystąpień do uruchomienia aplikacji.

    - Z **profilowania opcje** wybierz element docelowy profilowania.

         Profilowanie określonego procesu w klastrze, wybierz **profilu na rangę** opcji, a następnie wybierz pozycję procesu z listy rozwijanej.

         Profilowanie proces lub procesy, które są uruchamiane w określonym węźle w klastrze HPC, wybierz **profilu w węźle** opcji, a następnie wybierz węzeł z listy rozwijanej.

8. Kliknij przycisk **Dalej**.

9. Na stronie piątej kreatora można od razu rozpocząć profilera i profilowania procesu lub do uruchomienia profilowania później za pomocą Eksploratora wydajności.

    - Wybierz **Uruchom profilowanie po zakończeniu pracy kreatora** Uruchom profilowanie natychmiast, lub wyczyść pole wyboru do uruchomienia profilowania ręcznie.

10. Kliknij przycisk **Zakończ**.

## <a name="setting-hpc-profiling-properties-by-using-performance-session-property-pages"></a>Ustawianie właściwości profilowanie HPC za pomocą stron właściwości sesji wydajności

Można zmienić właściwości sesji wydajności, które można ustawić w Kreatorze profilowanie HPC na stronie właściwości uruchamianie HPC na stronie właściwości sesji wydajności. Można ustawić dodatkowe opcje na stronie właściwości zaawansowane HPC.

### <a name="to-open-the-performance-session-property-pages"></a>Otwieranie stron właściwości sesji wydajności

1. Jeśli to konieczne, otwórz plik sesji (.psess) wydajności w Eksploratorze wydajności. Na **pliku** menu, kliknij przycisk **Otwórz** i zlokalizuj plik.

2. W Eksploratorze wydajności, kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij przycisk **właściwości**.

3. W oknie dialogowym strony właściwości użyj jednej z następujących metod:

    - Kliknij przycisk **ogólne** , a następnie wybierz **zbierać w klastrze HPC** Włącz profilowanie na HPC, lub wyczyść pole wyboru, aby wyłączyć profilowanie HPC.

    - Kliknij przycisk **HPC uruchamianie właściwości** można zmienić właściwości, które uruchomienia aplikacji HPC.

    - Kliknij przycisk **właściwości zaawansowane HPC** można ustawić dodatkowe opcje

### <a name="hpc-launch-properties"></a>Właściwości uruchamiania HPC

|Właściwość|Opis|
|--------------|-----------------|
|**Nagłówek węzła**|Określa komputer, który działa jako węzła głównego klastra HPC w przebiegu profilowania.|
|**Liczba procesów**|Określa liczbę wystąpień aplikacji do uruchamiania w profilowanych aplikacji.|
|**Profile na pozycję**|Profilowanie określonego procesu w klastrze, wybierz **profilu na rangę** opcji, a następnie wybierz pozycję procesu z listy rozwijanej.|
|**Profil w węźle**|Profilowanie proces lub procesy, które są uruchamiane w określonym węźle w klastrze HPC, wybierz **profilu w węźle** opcji, a następnie wybierz węzeł z listy rozwijanej.|
|**Zdalny katalog roboczy**|Określa ścieżkę do folderu, który jest używany przez wystąpień procesu na poszczególne węzły obliczeniowe.|
|**Lokalizacja wdrożenia**|Określa ścieżkę do katalogu programu HPC server używa do etapu obrazów do wdrożenia.|

### <a name="advanced-properties"></a>Właściwości zaawansowane

|Właściwość|Opis|
|--------------|-----------------|
|**Nazwa projektu**|Nazwa bieżącego [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] projekt lub rozwiązanie.|
|**Czyszczenie po zatrzymaniu profilera**|W przypadku wartości true spowoduje usunięcie plików binarnych, które zostały wdrożone w katalogu wykonywania. Pliki i katalogi utworzone przez program użytkownika nie zostaną usunięte w tym kroku. Jeśli wykonanie katalog i katalog wdrożenia zostały utworzone przez środowisko IDE, IDE próbuje usunąć je, ale nie jest to jeśli dysponują pliki nie są wdrażane IDE.|
|**Dodatkowe pliki do wdrożenia**|Określa listę rozdzielonych średnikami wszelkie dodatkowe pliki do wdrożenia w węźle obliczeń. Możesz kliknąć przycisk wielokropka (**...** ) aby zaznaczyć wiele plików przy użyciu okna dialogowego.|
|**Polecenie Mpiexec**|Określa aplikację, która uruchamia aplikację MPI. Wartość domyślna to **mpiexec.exe**|
|**Argumenty Mpiexec**|Określa argumenty do przekazania do polecenia mpiexec.exe.|
|**Żądana węzłów w klastrze**|Określa liczbę węzłów w klastrze, na którym należy uruchomić aplikację.|
|**Wdrażanie plików CRT**|Gdy ma wartość true, wdraża C/C++, w czasie wykonywania w klastrze.|
|**Wstępnie profilu skryptu**|Określa ścieżkę i nazwę skryptu do uruchomienia na komputerze lokalnym programowanie, przed rozpoczęciem sesji profilowania.|
|**Argumenty skryptu przed profilu**|Określa argumenty do przekazania do skryptu przed profilu.|
|**Skrypt po profilu**|Określa ścieżkę i nazwę skryptu do uruchomienia na komputerze lokalnym programowanie po zakończeniu sesji profilowania.|
|**Argumenty skryptu po profilu**|Określa argumenty do przekazania do skryptu po profilu.|