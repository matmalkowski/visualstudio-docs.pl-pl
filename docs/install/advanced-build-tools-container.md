---
title: "Zaawansowane przykład kontenerów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: heaths
ms.author: heaths
manager: ghogen
ms.openlocfilehash: c1eb932eb079bca61eb5cea0959c56f00379114c
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="advanced-example-for-containers"></a>Przykład zaawansowane kontenerów

Przykładowy plik Dockerfile w [Instalowanie narzędzi kompilacji do kontenera](build-tools-container.md) zawsze używa najnowszych obrazu microsoft/windowsservercore i najnowszą wersję Instalatora 2017 z narzędzia kompilacji programu Visual Studio. W przypadku publikowania tego obrazu, aby [rejestru Docker](https://azure.microsoft.com/services/container-registry) innym osobom do ściągnięcia, ten obraz może być edytowane przez wiele scenariuszy. W praktyce, jednak jest najczęściej na konkretnym jakie base obrazu, należy użyć, jakie pliki binarne, możesz pobrać i które narzędzie instalacji wersji.

W poniższym przykładzie plik Dockerfile użyto tag obrazu microsoft/windowsservercore określonej wersji. Przy użyciu określonego tagu na podstawowy obraz jest powszechne i umożliwia łatwą do zapamiętania ten budynek lub ponownie skompilować obrazy zawsze ma tej samej podstawie.

> [!NOTE]
> Nie można zainstalować programu Visual Studio do microsoft/windowsservercore:10.0.14393.1593, który ma znane problemy uruchamiania Instalatora w kontenerze. Aby uzyskać więcej informacji, zobacz [znane problemy](build-tools-container-issues.md).

Funkcja programu inicjującego 2017 narzędzia kompilacji instalujący określonej wersji utworzony w tym samym czasie co program inicjujący. Produkt nadal mogły zostać zaktualizowane za pośrednictwem kanału wersji, ale nie jest praktyczne scenariusz dla kontenerów, które będą zazwyczaj odbudować. Jeśli chcesz pobrać adresy URL dla określonego kanału można pobrać kanału https://aka.ms/vs/15/release/channel, otwórz plik JSON i zbadać adresów URL programu inicjującego. Aby uzyskać więcej informacji, zobacz [instalacji sieciowej programu Visual Studio Utwórz](create-a-network-installation-of-visual-studio.md).

```dockerfile
# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:d841bd78721c74f9b88e2700f5f3c2d66b54cb855b8acb4ab2c627a76a46301d
FROM microsoft/windowsservercore:10.0.14393.1770

# Use PowerShell commands to download, validate hashes, etc.
SHELL ["powershell.exe", "-ExecutionPolicy", "Bypass", "-Command", "$ErrorActionPreference='Stop'; $ProgressPreference='SilentlyContinue'; $VerbosePreference = 'Continue';"]

# Download Build Tools 15.4.27004.2005 and other useful tools.
ENV VS_BUILDTOOLS_URI=https://aka.ms/vs/15/release/6e8971476/vs_buildtools.exe \
    VS_BUILDTOOLS_SHA256=D482171C7F2872B6B9D29B116257C6102DBE6ABA481FAE4983659E7BF67C0F88 \
    NUGET_URI=https://dist.nuget.org/win-x86-commandline/v4.1.0/nuget.exe \
    NUGET_SHA256=4C1DE9B026E0C4AB087302FF75240885742C0FAA62BD2554F913BBE1F6CB63A0

# Download tools to C:\Bin and install Build Tools excluding workloads and components with known issues.
RUN New-Item -Path C:\Bin, C:\TEMP -Type Directory | Out-Null; \
    [System.Environment]::SetEnvironmentVariable('PATH', "\"${env:PATH};C:\Bin\"", 'Machine'); \
    function Fetch ([string] $Uri, [string] $Path, [string] $Hash) { \
      Invoke-RestMethod -Uri $Uri -OutFile $Path; \
      if ($Hash -and ((Get-FileHash -Path $Path -Algorithm SHA256).Hash -ne $Hash)) { \
        throw "\"Download hash for '$Path' incorrect\""; \
      } \
    }; \
    Fetch -Uri $env:NUGET_URI -Path C:\Bin\nuget.exe -Hash $env:NUGET_SHA256; \
    Fetch -Uri $env:VS_BUILDTOOLS_URI -Path C:\TEMP\vs_buildtools.exe -Hash $env:VS_BUILDTOOLS_SHA256; \
    Fetch -Uri 'https://aka.ms/vscollect.exe' -Path C:\TEMP\collect.exe; \
    $p = Start-Process -Wait -PassThru -FilePath C:\TEMP\vs_buildtools.exe -ArgumentList '--quiet --wait --norestart --nocache --installPath C:\BuildTools --all --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 --remove Microsoft.VisualStudio.Component.Windows81SDK'; \
    if (($ret = $p.ExitCode) -and ($ret -ne 3010)) { C:\TEMP\collect.exe; throw ('Install failed with exit code 0x{0:x}' -f $ret) }

# Restore default shell for Windows containers.
SHELL ["cmd.exe", "/s", "/c"]

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

# Default to PowerShell if no other command specified.
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

W tym przykładzie pliki do pobrania określonego narzędzia i weryfikuje, czy skróty są zgodne. On również pobiera najnowsze Visual Studio i narzędzie kolekcji dziennika .NET tak, że jeśli wystąpi błąd instalacji, możesz skopiować dzienniki do komputera-hosta do analizowania awarii.

```shell
> docker build -t buildtools:15.4.27004.2005 -t buildtools:latest -m 2GB .
Sending build context to Docker daemon
...
Step 4/7 : RUN New-Item -Path C:\Bin, C:\TEMP -Type Directory | Out-Null; ...
 ---> Running in 4b62b4ce3a3c
Install failed with exit code 0x643
At line:1 char:1
+ throw ('Install failed with exit code 0x{0:x}' -f 1603)
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (Install failed with exit code 0x643:String) [], RuntimeException
    + FullyQualifiedErrorId : Install failed with exit code 0x643

> docker cp 4b62b4ce3a3c:C:\Users\ContainerAdministrator\AppData\Local\TEMP\vslogs.zip "%TEMP%\vslogs.zip"
```

Po zakończeniu wykonywania ostatniego wiersza otworzyć "% TEMP%\vslogs.zip" na komputerze lub Prześlij problemu na [społeczność deweloperów](https://developercommunity.visualstudio.com) witryny sieci web.

## <a name="get-support"></a>Uzyskaj pomoc techniczną
Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) stronę porady dotyczące rozwiązywania problemów. Jak również zgłosić problemy produktu z nami za pośrednictwem [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia w programie Visual Studio IDE lub udział sugestia z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579). Można śledzić problemy z produktu w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), zadawać pytania i odpowiedzi. Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą naszych [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio) (wymaga [GitHub](https://github.com/) konta).

## <a name="see-also"></a>Zobacz także
* [Zainstaluj narzędzia kompilacji do kontenera](build-tools-container.md)
* [Znane problemy dotyczące kontenerów](build-tools-container-issues.md)
