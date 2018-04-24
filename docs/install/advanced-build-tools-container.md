---
title: Przykład zaawansowane kontenerów
description: ''
ms.custom: ''
ms.date: 04/18/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c941928495dc39dc6b6ecbe9600f39dad969fec2
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="advanced-example-for-containers"></a>Przykład zaawansowane kontenerów

Przykładowy plik Dockerfile w [Instalowanie narzędzi kompilacji do kontenera](build-tools-container.md) zawsze używa [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) obrazu na podstawie najnowszych obrazu microsoft/windowsservercore i najnowszych Visual Instalator 2017 narzędzia kompilacji Studio. W przypadku publikowania tego obrazu, aby [rejestru Docker](https://azure.microsoft.com/services/container-registry) innym osobom do ściągnięcia, ten obraz może być edytowane przez wiele scenariuszy. Jednak w praktyce jest najczęściej na konkretnym jakie base obrazu, należy użyć, jakie pliki binarne, możesz pobrać i które narzędzie instalacji wersji.

W poniższym przykładzie plik Dockerfile użyto tag obrazu microsoft dotnet ramowych określonej wersji. Przy użyciu określonego tagu na podstawowy obraz jest powszechne i umożliwia łatwą do zapamiętania ten budynek lub ponownie skompilować obrazy zawsze ma tej samej podstawie.

> [!NOTE]
> Nie można zainstalować programu Visual Studio do microsoft/windowsservercore:10.0.14393.1593 lub żadnego obrazu na jego podstawie ma znane problemy uruchamiania Instalatora w kontenerze. Aby uzyskać więcej informacji, zobacz [znane problemy](build-tools-container-issues.md).

W poniższym przykładzie pliki do pobrania najnowszej wersji 2017 narzędzia kompilacji. Jeśli chcesz użyć starszej wersji narzędzi Build Tools można zainstalować w kontenerze później, należy najpierw [utworzyć](create-an-offline-installation-of-visual-studio.md) i [Obsługa](update-a-network-installation-of-visual-studio.md) układ.

## <a name="install-script"></a>Skrypt instalacji

Aby zbierać dzienniki po wystąpieniu błędu instalacji, w katalogu roboczym utworzyć skrypt wsadowy o nazwie "Install.cmd" o następującej treści:

```shell
@if not defined _echo echo off
setlocal enabledelayedexpansion

call %*
if "%ERRORLEVEL%"=="3010" (
    exit /b 0
) else (
    if not "%ERRORLEVEL%"=="0" (
        set ERR=%ERRORLEVEL%
        call C:\TEMP\collect.exe -zip:C:\vslogs.zip

        exit /b !ERR!
    )
)
```

## <a name="dockerfile"></a>Plik Dockerfile

W katalogu roboczym należy utworzyć plik "Dockerfile" o następującej treści:

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:1a66e2b5f3a5b8b98ac703a8bfd4902ae60d307ed9842978df40dbc04ac86b1b
ARG FROM_IMAGE=microsoft/dotnet-framework:4.7.1-20180410-windowsservercore-1709
FROM ${FROM_IMAGE}

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/15/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Download and install Build Tools excluding workloads and components with known issues.
ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --all `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

# Default to PowerShell if no other command specified.
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

Uruchom następujące polecenie, aby utworzyć obraz w bieżącym katalogu roboczym:

```shell
docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
```

Przekazać opcjonalnie jednego lub obu tych `FROM_IMAGE` lub `CHANNEL_URL` przy użyciu argumentów `--build-arg` przełącznik wiersza polecenia, aby określić inny obraz podstawowy lub lokalizacja układu wewnętrzny, aby zachować stały obraz.

## <a name="diagnosing-install-failures"></a>Diagnozowanie błędów instalacji

W tym przykładzie pliki do pobrania określonego narzędzia i weryfikuje, czy skróty są zgodne. On również pobiera najnowsze Visual Studio i narzędzie kolekcji dziennika .NET tak, że jeśli wystąpi błąd instalacji, możesz skopiować dzienniki do komputera-hosta do analizowania awarii.

```shell
> docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
Sending build context to Docker daemon
...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

Po zakończeniu wykonywania ostatniego wiersza otworzyć na komputerze "% TEMP%\vslogs.zip", lub Prześlij problemu na [społeczność deweloperów](https://developercommunity.visualstudio.com) witryny sieci web.

## <a name="get-support"></a>Uzyskaj pomoc techniczną

Czasami może wystąpienia problemów. Jeśli niepowodzenie instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony. Jeśli żaden z kroki rozwiązywania problemów, można skontaktować się nam przez rozmów na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [strony pomocy technicznej programu Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:

* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu i odpowiedzi w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/).
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio). (Ta opcja wymaga [GitHub](https://github.com/) konta.)

## <a name="see-also"></a>Zobacz także

* [Instalowanie narzędzi do kompilacji w kontenerze](build-tools-container.md)
* [Znane problemy z kontenerami](build-tools-container-issues.md)
* [Visual Studio kompilacji narzędzia 2017 obciążenia i składnik identyfikatorów](workload-component-id-vs-build-tools.md)
