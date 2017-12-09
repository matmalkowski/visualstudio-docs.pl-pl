---
title: R Tools for Visual Studio i kontenery Docker | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author:
- kraigb
- karthiknadig
ms.author:
- kraigb
- karthiknadig
manager: ghogen
ms.openlocfilehash: eb756874e6366b84a0b8f1145a41b52ac063dc02
ms.sourcegitcommit: ae9450e81c4167b3fbc9ee5d1992fc693628eafa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="using-docker-containers-with-r-tools-for-visual-studio"></a>Używanie kontenerów Docker R narzędzia dla programu Visual Studio

R narzędzi dla programu Visual Studio (RTVS) w wersji 1.3 +, obok instalacji z [Docker dla systemu Windows](https://www.docker.com/docker-windows), obsługuje Praca z kontenerami Docker.

- [Utworzenie kontenera](#creating-a-container)
- [Łączenie z kontenera](#connecting-to-a-container)
- [Przy użyciu niestandardowej obrazów](#using-custom-built-images)

## <a name="creating-a-container"></a>Utworzenie kontenera

1. Wybierz **kontenery...**  przycisk w prawym rogu **obszarów roboczych** okna (**narzędzia R > Windows > obszary robocze**). Okno wyświetla informację, czy masz Docker dla systemu Windows zainstalowana i zawiera łącze do pobrania. Instalacja Docker może wymagać ponownego uruchomienia komputera.

    ![Okno obszarów roboczych w R Tools for Visual Studio (VS2017) przy użyciu polecenia kontenerów](media/container-workspaces-window.png)

1. W **kontenery** wybierz **Utwórz**:

    ![Utwórz polecenie w oknie kontenerów](media/containers-window-create.png)

1. Zakończenie wymaganych informacji w oknie dialogowym i wybierz **Utwórz**. Wprowadzone poświadczenia są również używane do tworzenia konta w systemie Linux, z którymi możesz się zalogować później.

    ![Wprowadzanie nazwy kontenera i poświadczeń podczas tworzenia kontenera](media/containers-window-create-fill.png)

1. Może upłynąć trochę czasu, zanim RTVS do utworzenia obrazu. **Dane wyjściowe** okna w programie Visual Studio przedstawia postęp, ale może się nie realizacji znacznie podczas długich obrazu pobiera; należy przygotować cierpliwość. Po utworzeniu obrazu, RTVS uruchamia kontenera i wyświetlone w **kontenera** okna. Formanty prawo stop, usuń lub uruchom ponownie kontenera.

    ![Kontenery okna pokazującego ukończone kontenera](media/containers-window-created.png)

## <a name="connecting-to-a-container"></a>Łączenie z kontenera

1. **Lokalnym systemem kontenery** sekcji **obszarów roboczych** okno Wyświetla kontenery uruchomiony demon RTVS na porcie 5444. (Zobacz [zdalnego R Server dla systemu Linux](workspaces-remote-r-service-for-linux.md) szczegółowe informacje dotyczące sposobu skonfigurowania demona.)

    ![Dostępne kontenery przedstawiający okno obszary robocze](media/workspaces-window-running-containers.png)

1. Aby połączyć się z kontenerem, kliknij dwukrotnie nazwę kontenera lub kliknij przycisk strzałki do przodu po jego prawej stronie. Po podłączeniu, zobacz **R interakcyjne** okna (zobacz [Praca z okno interaktywne R](interactive-repl.md)):

    ![Obszary robocze okna i REPL otworzyć kontenera](media/workspaces-window-container-connected.png)

## <a name="using-custom-built-images"></a>Przy użyciu niestandardowej obrazów

RTVS wykrywa i umożliwia zarządzanie kontenery utworzone za pomocą niestandardowej obrazy, takie jak obraz microsoft/rtvs opisanego w poniższy plik docker. Podstawowy obraz używany w tym miejscu ma demon rtvs R 3.4.2 i typowych pakietów języka R z preinstalowanym. **Uwaga**: Zmień nazwę użytkownika i hasło podane tutaj zgodnie z potrzebami.

```docker
FROM microsoft/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

Użyj następującego polecenia, aby utworzyć obraz, zmiana nazwy kontenera ( `--name` argument) pożądane:

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

`-p 6056:5444` Argument mapy portu 6056 do wewnętrznego portu 5444, używanym do wykrywania demon rtvs RTVS. Wszelkie kontener, który udostępnia port kontenera 5444 ma na liście **obszarów roboczych** okna. Następnie można użyć **obszarów roboczych** okna, aby nawiązać połączenie przy użyciu kontenera `<<unix>>\ruser1` jako nazwy użytkownika i "foobar" jako hasło, chyba że określono inne poświadczenia w pliku docker.
