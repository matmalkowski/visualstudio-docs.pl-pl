---
title: "Zainstaluj narzędzia kompilacji do kontenera | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: heaths
ms.author: heaths
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 95f9c69ebca7dbdc7e576279b4e1ad3f17d2be25
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="install-build-tools-into-a-container"></a>Zainstaluj narzędzia kompilacji do kontenera

Możesz zainstalować program Visual Studio Tools kompilacji do kontenera systemu Windows do obsługi ciągłej integracji i przepływy pracy ciągłego dostarczania (CI/CD). W tym artykule przedstawiono Docker zmiany konfiguracji są wymagane, a także co [obciążeń i składniki](workload-component-id-vs-build-tools.md) można zainstalować w kontenerze.

[Kontenery](https://www.docker.com/what-container) to doskonały sposób, aby pakiet system kompilację spójności można nie tylko w środowisku serwera CI/CD, ale również środowisk deweloperskich. Można na przykład zainstalować kod źródłowy w kontenerze mają zostać utworzone przez dostosowane środowisko, nadal używać programu Visual Studio lub innych narzędzi do pisania kodu. Jeśli CI/CD przepływ pracy używa tego samego obrazu kontenera, można umieścić pewni, że kod tworzy spójne. Kontenery służącego do środowiska wykonawczego także spójność, co jest typowe dla micro-services przy użyciu wielu kontenerów przy użyciu systemu aranżacji, ale wykracza poza zakres tego artykułu.

Jeśli program Visual Studio Tools kompilacji nie wymagają kompilacji kodu źródłowego, można te same kroki dla innych produktów Visual Studio. Należy jednak pamiętać, że kontenery systemu Windows nie obsługują interaktywnego interfejsu użytkownika, więc wszystkie polecenia musi zostać zautomatyzowane.

## <a name="overview"></a>Omówienie

Przy użyciu [Docker](https://www.docker.com/what-docker) tworzenia obrazu, z której można utworzyć kontenerów, które kompilacji kodu źródłowego. Przykład plik Dockerfile instaluje najnowsze Visual Studio kompilacji narzędzia 2017 i inne programy przydatne często używanych do kompilowania kodu źródłowego. Dodatkowo można modyfikować własnych plik Dockerfile, aby uwzględnić inne narzędzia i skrypty do uruchomienia testów, publikowanie danych wyjściowych kompilacji i inne.

Jeśli użytkownik zainstalował już Docker dla systemu Windows, można przejdź do kroku 3.

## <a name="step-1-enable-hyper-v"></a>Krok 1. Włączanie funkcji Hyper-V

Funkcja Hyper-V nie jest włączona domyślnie. Musi być włączony do uruchamiania Docker dla systemu Windows, ponieważ obecnie tylko izolacji funkcji Hyper-V jest obsługiwana dla systemu Windows 10.

* [Włączanie funkcji Hyper-V w systemie Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)
* [Włączanie funkcji Hyper-V w systemie Windows Server 2016](https://docs.microsoft.com/windows-server/virtualization/hyper-v/get-started/install-the-hyper-v-role-on-windows-server)

> [!NOTE]
> Wirtualizacja musi być włączona na tym komputerze. Zazwyczaj jest włączona domyślnie; Jednak jeśli niepowodzenie instalacji funkcji Hyper-V, zapoznaj się z dokumentacją systemu, jak włączyć wirtualizacji.

## <a name="step-2-install-docker-for-windows"></a>Krok 2. Zainstaluj Docker dla systemu Windows

Jeśli używasz systemu Windows 10, możesz pobrać i zainstalować [Docker Community Edition dla systemu Windows](https://www.docker.com/docker-windows). Korzystając z programu PowerShell do [zainstalować Docker Enterprise Edition dla systemu Windows Server 2016](https://docs.docker.com/engine/installation/windows/docker-ee) przy użyciu żądanego stanu konfiguracji (DSC), lub [dostawcy pakietu](https://docs.microsoft.com/virtualization/windowscontainers/deploy-containers/deploy-containers-on-server) to prostą instalację pojedynczego.

## <a name="step-3-switch-to-windows-containers"></a>Krok 3. Przełącz się do systemu Windows kontenerów

2017 narzędzia kompilacji można zainstalować tylko w systemie Windows, co wymaga [przełączyć się do systemu Windows kontenery](https://docs.docker.com/docker-for-windows/#getting-started-with-windows-containers). Kontenery systemu Windows w systemie Windows 10 obsługuje tylko [izolacji funkcji Hyper-V](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container), podczas gdy kontenery systemu Windows w systemie Windows Server 2016 obsługuje zarówno funkcji Hyper-V i OLE DB.

## <a name="step-4-expand-maximum-container-disk-size"></a>Krok 4. Rozwiń kontener maksymalny rozmiar dysku

Visual Studio kompilacji narzędzia — i w większym stopniu Visual Studio — wymaga dużej ilości miejsca na dysku dla wszystkich narzędzi, które są zainstalowane. Mimo że w naszym przykładzie plik Dockerfile wyłącza pamięć podręczną pakietów, można zwiększyć rozmiar dysku kontener obrazów, aby pomieścić wymagane miejsce. Obecnie w systemie Windows, możesz tylko zwiększyć rozmiar dysku przez zmianę konfiguracji Docker.

**W systemie Windows 10**:

1. [Rick — kliknij ikonę Docker dla systemu Windows](https://docs.docker.com/docker-for-windows/#docker-settings) na pasku zadań i kliknij przycisk **ustawień...** .
2. [Polecenie demona](https://docs.docker.com/docker-for-windows/#docker-daemon) sekcji.
3. [Przełącz **podstawowe** ](https://docs.docker.com/docker-for-windows/#edit-the-daemon-configuration-file) przycisk, aby **zaawansowane**.
4. Dodaj następujące właściwości tablicy JSON zwiększenie miejsca na dysku do 120GB (więcej niż wystarczającego dla narzędzia kompilacji możliwości rozbudowy).

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   Ta właściwość jest dodawany do wszystkich danych, które już istnieje. Na przykład z te zmiany zostaną zastosowane do domyślnego pliku konfiguracji demon, powinien zostać wyświetlony:

   ```json
   {
     "registry-mirrors": [],
     "insecure-registries": [],
     "debug": true,
     "experimental": true,
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

5. Kliknij przycisk **zastosować**.

**W systemie Windows Server 2016**:

1. Zatrzymaj usługę "docker":

   ```shell
   sc.exe stop docker
   ```

2. W wierszu polecenia z podwyższonym poziomem uprawnień, należy edytować "% ProgramData%\Docker\config\daemon.json" (lub niezależnie od określony do `dockerd --config-file`).
3. Dodaj następujące właściwości tablicy JSON zwiększenie miejsca na dysku do 120GB (więcej niż wystarczającego dla narzędzia kompilacji możliwości rozbudowy).

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   Ta właściwość jest dodawany do wszystkich danych, które już istnieje.
4. Zapisz i zamknij plik.
5. Uruchom usługę "docker":

   ```shell
   sc.exe start docker
   ```

## <a name="step-5-create-and-build-the-dockerfile"></a>Krok 5. Tworzenie i kompilacja plik Dockerfile

Poniższy przykład plik Dockerfile musi zapisać do nowego pliku na dysku. Jeśli nazwą jest po prostu plik Dockerfile"", który jest rozpoznawany przez domyślne.

> [!NOTE]
> W tym przykładzie plik Dockerfile wyklucza tylko starsze zestawy Windows SDK, której nie można zainstalować w kontenerach. Starsze wersje spowodować polecenie kompilacji, aby zakończyć się niepowodzeniem.

1. Otwórz wiersz polecenia.
2. Utwórz nowy katalog (zalecane):

   ```shell
   mkdir C:\BuildTools
   ```

3. Przejdź do nowego katalogu:

   ```shell
   cd C:\BuildTools
   ```

3. Zapisz C:\BuildTools\Dockerfile następującą zawartość.

   ```dockerfile
   # Use the latest Windows Server Core image.
   FROM microsoft/windowsservercore

   # Download useful tools to C:\Bin.
   ADD https://dist.nuget.org/win-x86-commandline/v4.1.0/nuget.exe C:\\Bin\\nuget.exe

   # Download the Build Tools bootstrapper outside of the PATH.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\\TEMP\\vs_buildtools.exe

   # Add C:\Bin to PATH and install Build Tools excluding workloads and components with known issues.
   RUN setx /m PATH "%PATH%;C:\Bin" \
    && C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache --installPath C:\BuildTools --all \
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 \
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 \
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 \
       --remove Microsoft.VisualStudio.Component.Windows81SDK \
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

4. Uruchom następujące polecenie, w tym katalogu.

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   To polecenie tworzy plik Dockerfile w bieżącym katalogu przy użyciu 2GB pamięci. Wartość domyślna 1GB nie są wystarczające po zainstalowaniu niektórych obciążeń; jednak można kompilować z tylko 1GB pamięci, w zależności od wymagań kompilacji.

   Finalnego obrazu jest oznakowany "buildtools2017:latest", więc można łatwo uruchomić w kontenerze jako "buildtools2017" od "najnowszej" tag jest domyślnie, jeśli jest określony żaden tag. Jeśli chcesz użyć określonej wersji programu Visual Studio kompilacji narzędzia 2017 w bardziej [zaawansowanym scenariuszu](advanced-build-tools-container.md), może być zamiast tego tagu kontener o określonej kompilacji programu Visual Studio numer, a także "najnowszej" dzięki kontenery można użyć określonego Wersja spójnie.

## <a name="step-6-using-the-built-image"></a>Krok 6. Przy użyciu wbudowanego obrazu

Teraz, po utworzeniu obrazu, można uruchomić w kontenerze celu kompilacji zarówno interakcyjne i automatyczne. W przykładzie użyto wiersza polecenia dewelopera, więc ścieżki i zmiennych środowiskowych są już skonfigurowane.

1. Otwórz wiersz polecenia.
2. Uruchom zestaw zmiennych środowiska kontenera zaczynać się wszystkich deweloperów środowiska PowerShell:

   ```shell
   docker run -it buildtools2017
   ```

Aby użyć tego obrazu elementu konfiguracji/CD przepływu pracy, można opublikować go do własnych [rejestru kontenera Azure](https://azure.microsoft.com/services/container-registry) lub innych wewnętrzny [rejestru Docker](https://docs.docker.com/registry/deploying) , serwery muszą tylko ten.

## <a name="get-support"></a>Uzyskaj pomoc techniczną
Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony. Jeśli żaden z kroki rozwiązywania problemów, można skontaktować się nam przez rozmów na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [strony pomocy technicznej programu Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:
* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), zadawać pytania i odpowiedzi.
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą naszych [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio).  (Ta opcja wymaga [GitHub](https://github.com/) konta.)

## <a name="see-also"></a>Zobacz także

* [Zaawansowany przykład dotyczący kontenerów](advanced-build-tools-container.md)
* [Znane problemy z kontenerami](build-tools-container-issues.md)
* [Visual Studio kompilacji narzędzia 2017 obciążenia i składnik identyfikatorów](workload-component-id-vs-build-tools.md)
