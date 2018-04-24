---
title: Konfigurowanie usługi zdalnej R w systemie Linux
description: Jak skonfigurować usługi zdalnej R Ubuntu i podsystemu systemu Windows dla systemu Linux.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: ec988b9739dfbec60fe19b41145ae0de1b3d3f77
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="remote-r-service-for-linux"></a>Usługa zdalnego R dla systemu Linux

Usługa zdalnego R dla systemu Linux jest obecnie dostarczana w rtvs demon. Demon jest obsługiwana i przetestowany Ubuntu 16.04, 16.10 pulpitu LTS, serwera i podsystem Windows systemem Ubuntu Linux. Zbiorczego ten artykuł zawiera instrukcje dotyczące konfigurowania usługi zdalnej R w tych systemach różnych.

Po skonfigurowaniu komputera zdalnego następujące kroki połączenie narzędzi R do tej usługi dla programu Visual Studio (RTVS):

1. Wybierz **narzędzia R > Windows > obszary robocze** otworzyć **obszarów roboczych** okna.
1. Wybierz **Dodaj połączenie**.
1. Nadaj nazwę Połącz i podaj adres URL, taki jak `https://localhost:5444` (podsystem Windows dla systemu Linux) lub `https://public-ip:5444` (kontenera platformy Azure). Wybierz **zapisać** po zakończeniu.
1. Wybierz ikonę połączenia lub kliknij dwukrotnie element połączenia.
1. Podaj poświadczenia logowania. Nazwa użytkownika musi być poprzedzona znakiem `<<unix>>\` jako w `<<unix>>\ruser1` (co jest wymagane dla wszystkich połączeń z komputerami zdalnymi z systemem Linux).
1. Jeśli używasz certyfikatu z podpisem własnym, mogą pojawić się ostrzeżenie. Komunikat zawiera instrukcje dotyczące Popraw ostrzeżenia.

## <a name="setting-up-remote-r-service"></a>Konfigurowanie usługi zdalnej R

W tej sekcji opisano następujące opcje:

- [Komputer fizyczny Ubuntu](#physical-ubuntu-computer)
- [Ubuntu Server maszyny Wirtualnej lub nauki danych maszyny Wirtualnej na platformie Azure](#ubuntu-server-vm-or-data-science-vm-on-azure)
- [Kontener Docker lokalnym lub zdalnym (kompilacja czysta)](#local-or-remote-docker-container-clean-build)
- [Kontener systemem wystąpień kontenera platformy Azure](#container-running-on-azure-container-instances)

W każdym przypadku komputer zdalny musi mieć jedną z następujących tłumaczy R zainstalowane:

- [Otwórz program Microsoft R](https://mran.microsoft.com/open/)
- [Sieci CRAN R dla systemu Windows](https://cran.r-project.org/bin/linux/ubuntu/)

### <a name="physical-ubuntu-computer"></a>Komputer fizyczny Ubuntu

1. Po zalogowaniu się do komputera, należy pobrać tarball demon rtvs:

    ```bash
    wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current
    tar -xvzf rtvs-daemon.tar.gz
    ```

1. Uruchom skrypt instalacji:

    ```bash
    sudo ./rtvs-install
    ```

    Automatyzacja dyskretną, można użyć `sudo ./rtvs-install -s`.

1. Włącz i uruchom usługę:

    ```bash
    sudo systemctl enable rtvsd
    sudo systemctl start rtvsd
    ```

1. Konfigurowanie certyfikatu protokołu SSL (wymagane dla trybu produkcyjnego). Domyślnie używa demon rtvs `ssl-cert-snakeoil.pem` i `ssl-cert-snakeoil.pem` generowane przez `ssl-cert` pakietu. Podczas instalacji są łączone w `ssl-cert-snakeoil.pfx`. Do celów produkcyjnych należy użyć certyfikatu SSL, udostępnionych przez administratora. Certyfikat SSL można skonfigurować zapewniając `.pfx` plików i hasło opcjonalny import w: `/etc/rtvs/rtvsd.config.json`.

1. (Opcjonalnie) Sprawdź, czy usługa jest uruchomiona:

    ```bash
    ps -A -f | grep rtvsd
    ```

    Jeśli nie widzisz procesu uruchomionego przy użyciu nazwy użytkownika `rtvssvc`. Aby uruchomić przy użyciu następującego polecenia:

    ```bash
    sudo systemctl start rtvsd
    ```

1. Aby skonfigurować dalsze demona rtvs, zobacz `man rtvsd`.

### <a name="ubuntu-server-vm-or-data-science-vm-on-azure"></a>Ubuntu Server maszyny Wirtualnej lub nauki danych maszyny Wirtualnej na platformie Azure

#### <a name="create-a-vm"></a>Tworzenie maszyny Wirtualnej

1. Zaloguj się do [portalu Azure](https://portal.azure.com).
1. Przejdź do maszyny wirtualnej, a następnie wybierz **Dodaj**.
1. Na liście dostępnych obrazów maszyn wirtualnych Wyszukaj i wybierz jedną z następujących czynności:
    - Ubuntu Server: `Ubuntu Server 16.04 LTS`
    - Połączenie analiz danych maszyny Wirtualnej: `Linux Data Science` (zobacz [danych maszyny wirtualnej nauki](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) szczegółowe informacje)
1. Wartość modelu wdrażania `Resource manager` i wybierz **Utwórz**.
1. Wybierz nazwę dla maszyny Wirtualnej, podaj nazwę użytkownika i hasło (wymagane jest hasło, jako SSH publicznego klucza logowania nie jest obsługiwane).
1. Wprowadź żądane zmiany w konfiguracji maszyny Wirtualnej.
1. Wybierz rozmiar maszyny Wirtualnej, sprawdź konfigurację i wybierz **Utwórz**. Po utworzeniu maszyny Wirtualnej, przejdź do następnej sekcji.

#### <a name="configure-the-vm"></a>Konfigurowanie maszyny Wirtualnej

1. Na maszynie wirtualnej **sieci** Dodaj 5444 jako dozwolone portu wejściowego. Aby użyć innego portu, zmień ustawienie w pliku konfiguracyjnym demona RTVS (`/etc/rtvs/rtvsd.config.json`).
1. (Opcjonalnie) Ustaw nazwę DNS; można również użyć adresu IP.
1. Połączenie z maszyną Wirtualną przy użyciu klienta SSH, takiego jak PuTTY dla systemu WIndows.
1. Postępuj zgodnie z instrukcjami dotyczącymi [komputera fizycznego Ubuntu](#physical-ubuntu-computer) powyżej.

### <a name="windows-subsystem-for-linux-wsl"></a>Podsystem systemu Windows dla systemu Linux (WSL)

1. Postępuj zgodnie z instrukcjami instalacji WSL jednego [systemu Windows 10](https://msdn.microsoft.com/commandline/wsl/install-win10) lub [systemu Windows Server](https://msdn.microsoft.com/en-us/commandline/wsl/install-on-server).
1. Uruchom bash w systemie Windows, a następnie postępuj zgodnie z instrukcjami wcześniejszych [komputera fizycznego Ubuntu](#physical-ubuntu-computer) z jednym wyjątkiem. W kroku 3, należy uruchomić usługę za pomocą polecenia `rtvsd`zamiast ponieważ WSL aktualnie nie obsługuje interfejsów systemd/systemctl.

### <a name="local-or-remote-docker-container-clean-build"></a>Kontener Docker lokalnym lub zdalnym (kompilacja czysta)

1. Utwórz plik Docker z zawartością poniżej, które instaluje demon usługi zdalnego R i najnowszej wersji R. **Uwaga**: ten skrypt tworzy użytkownika o nazwie "ruser1" hasło "foobar", które można dostosować zgodnie z potrzebami w dwa końcowego `RUN` instrukcje.

    ```docker
    FROM ubuntu:16.04

    ARG DEBIAN_FRONTEND=noninteractive

    RUN apt-get update \
     && apt-get install -y software-properties-common python-software-properties \
     && apt-get install -y apt-transport-https \
     && rm -rf /var/lib/apt/lists/*

    RUN sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list' \
     && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 417A0893 \
     && sh -c 'echo "deb https://cran.revolutionanalytics.com/bin/linux/ubuntu xenial/" > /etc/apt/sources.list.d/cran-r.list' \
     && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9 \
     && rm -rf /var/lib/apt/lists/* \
     && apt-get clean

    RUN apt-get update --fix-missing && apt-get update \
     && apt-get install -y dotnet-dev-1.0.4 libexplain51 libzip4 libc6 git lshw ssl-cert wget \
     && rm -rf /var/lib/apt/lists/*

    # install R
    RUN apt-get update && apt-get install -y r-base-dev
    RUN apt upgrade -y

    # install rtvs-daemon
    RUN wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current && tar -xvzf rtvs-daemon.tar.gz && ./rtvs-install -s

    RUN useradd --create-home ruser1
    RUN echo "ruser1:foobar" | chpasswd

    EXPOSE 5444
    ```

1. Tworzenie i uruchamianie pliku docker:

    ```bash
    docker build -t myrimage .
    docker run -p 5444:5444 myrimage rtvsd
    ```

1. Aby nawiązać połączenie zawiera z RTVS, użyj `https://localhost:5444` jako ścieżka, nazwa użytkownika `<<unix>>\ruser1`i hasło `foobar`. Jeśli kontener jest uruchomiona na komputerze zdalnym, należy użyć `https://remote-host-name:5444` jako ścieżkę zamiast tego. Numer portu można zmienić, aktualizując `/etc/rtvs/rtvsd.config.json`.

### <a name="container-running-on-azure-container-instances"></a>Kontener systemem wystąpień kontenera platformy Azure

1. Postępuj zgodnie z instrukcjami [kontenera Docker lokalnego lub zdalnego (kompilacja czystą)](#local-or-remote-docker-container-clean-build) do utworzenia obrazu.
1. Wypchnij kontenera do Centrum Docker lub repozytorium kontenera platformy Azure.
1. Uruchom z wiersza polecenia platformy Azure i zaloguj się przy użyciu `az login` polecenia.
1. Użyj `az container create` polecenie, aby utworzyć kontener, za pomocą `--command-line "rtvsd"` , jeśli nie zdefiniowano kontener uruchamianie `rtvsd` jako `systemd` usługi. W poniższym poleceniu obraz powinien znajdować się w Centrum Docker. Umożliwia także repozytorium kontenera Azure przez dodanie repozytorium kontenera poświadczeń argumentów do wiersza polecenia.

    ```bash
    az container create --image myimage:latest --name myaz-container --resource-group myaz-container-res --ip-address public --port 5444 --cpu 2 --memory 4 --command-line "rtvsd"
    ```
1. Użyj `az container list` polecenie, aby sprawdzić stan. Wyszukaj `provisioningState`: `Succeeded`.
1. Jeśli Udostępnianie zakończyło się pomyślnie, teraz można podłączyć do kontenera. Wyszukaj publicznego adresu IP w `ipAddress` pola, które umożliwia przy użyciu poświadczeń w pliku docker nawiązywanie połączenia z RTVS do kontenera.

