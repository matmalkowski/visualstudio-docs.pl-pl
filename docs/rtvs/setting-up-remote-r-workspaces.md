---
title: "Zdalnych obszarów roboczych z R Tools for Visual Studio | Dokumentacja firmy Microsoft"
description: "Jak skonfigurować zdalnych obszarów roboczych R i nawiązać z nią w programie Visual Studio."
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: db6fa380b7ecff1338afe3d755a27111a72e0f0a
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="setting-up-remote-workspaces"></a>Konfigurowanie zdalnego obszary robocze

W tym artykule opisano sposób konfigurowania serwera zdalnego z protokołu SSL i odpowiednią usługę R. Dzięki temu R narzędzi dla programu Visual Studio (RTVS) do nawiązania połączenia zdalnego obszaru roboczego na tym serwerze.

- [Wymagania dotyczące komputera zdalnego](#remote-computer-requirements)
- [Zainstaluj certyfikat SSL](#install-an-ssl-certificate)
- [Zainstaluj certyfikat SSL w systemie Windows](#install-an-ssl-certificate-on-windows)
- [Zainstaluj certyfikat SSL na Ubuntu](#install-an-ssl-certificate-on-ubuntu)
- [Zainstaluj usługi R w systemie Windows](#install-r-services-on-windows)
- [Zainstaluj usługi R w systemie Linux](#install-r-services-on-Linux)
- [Konfigurowanie usług R](#configure-r-services)
- [Rozwiązywanie problemów](#troubleshooting)

## <a name="remote-computer-requirements"></a>Wymagania dotyczące komputera zdalnego

- Windows 10, Windows Server 2016 lub Windows Server 2012 R2. Wymaga również RTVS
- [.NET framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) lub nowszej

## <a name="install-an-ssl-certificate"></a>Zainstaluj certyfikat SSL

RTVS wymaga, aby cała komunikacja z serwerem zdalnym się stanie, za pośrednictwem protokołu HTTP, która wymaga certyfikatu SSL na serwerze. Można użyć certyfikatu podpisanego przez zaufany urząd certyfikacji (zalecane) lub certyfikatu z podpisem własnym. (Certyfikatu z podpisem własnym powoduje, że RTVS ostrzeżenia problem podczas połączenia). Z jednej następnie należy go zainstalować na komputerze i zezwolić na dostęp do jego klucz prywatny.

### <a name="obtaining-a-trusted-certificate"></a>Uzyskiwanie zaufanego certyfikatu

Zaufany certyfikat jest wystawiony przez urząd certyfikacji (zobacz [certyfikatów urzędów w witrynie Wikipedia](https://en.wikipedia.org/wiki/Certificate_authority) w tle). Podobnie jak uzyskiwanie karty identyfikacyjne dla instytucji rządowych, wystawiania certyfikatów zaufanych obejmuje więcej procesów oraz ewentualne opłaty, ale sprawdza autentyczności żądania oraz obiekt żądający.

Pole klucza, który musi być w certyfikacie jest w pełni kwalifikowaną nazwą domeny komputera serwera R. Urząd certyfikacji wymaga potwierdzenia, że masz uprawnienia do utworzenia nowego serwera do domeny, do której należy serwer.

W tle więcej, zobacz [certyfikatów kluczy publicznych](https://en.wikipedia.org/wiki/Public_key_certificate) w witrynie Wikipedia.

## <a name="install-an-ssl-certificate-on-windows"></a>Zainstaluj certyfikat SSL w systemie Windows

Certyfikat SSL musi zostać zainstalowany ręcznie w systemie windows. Postępuj zgodnie z instrukcjami poniżej, aby zainstalować certyfikat protokołu SSL.

### <a name="obtaining-a-self-signed-certificate-windows"></a>Uzyskiwanie certyfikatu z podpisem własnym (system Windows)

Jeśli masz zaufanego certyfikatu, należy pominąć tę sekcję. W porównaniu z certyfikatu z zaufanego urzędu certyfikatu z podpisem własnym przypomina tworzenia karty identyfikacyjne dla siebie. Ten proces jest oczywiście znacznie łatwiejsze niż w przypadku pracy z zaufanego urzędu, ale również nie ma silnego uwierzytelniania, co oznacza, że atakujący można zastąpić certyfikatu dla certyfikatu bez znaku i przechwytywać cały ruch między klientem i serwer. W związku z tym *certyfikatu z podpisem własnym należy używać tylko do testowania scenariuszy, w zaufanej sieci, a nie w środowisku produkcyjnym.*

Z tego powodu RTVS zawsze wystawia następujące ostrzeżenie podczas nawiązywania połączenia z serwerem z certyfikatu z podpisem własnym:

![Okno dialogowe z ostrzeżeniem certyfikatu z podpisem własnym](media/workspaces-remote-self-signed-certificate-warning.png)

Do wystawiania certyfikatu z podpisem własnym:

1. Zaloguj się na komputerze serwera R przy użyciu konta administratora.
1. Otwórz wiersz polecenia programu PowerShell nowego administratora i wydać następujące polecenie, zastępując `"remote-machine-name"` z w pełni kwalifikowaną nazwę komputera serwera.

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. Jeśli nigdy nie uruchomiono programu Powershell przed na komputerze serwera R, uruchom następujące polecenie, aby umożliwić wykonywanie poleceń jawnie:

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

W tle, zobacz [certyfikaty z podpisem własnym](https://en.wikipedia.org/wiki/Self-signed_certificate) w witrynie Wikipedia.

### <a name="installing-the-certificate"></a>Instalowanie certyfikatu

Aby zainstalować certyfikat na komputerze zdalnym, uruchom `certlm.msc` (Menedżer certyfikatów) w wierszu polecenia. Kliknij prawym przyciskiem myszy **osobistych** i wybierz polecenie **wszystkie zadania > Import** polecenie:

![Polecenie Import certyfikatu](media/workspaces-remote-certificate-import.png)

### <a name="granting-permissions-to-read-the-ssl-certificates-private-key"></a>Udzielanie uprawnień do odczytu klucza prywatnego certyfikatu SSL

Po zaimportowaniu certyfikatu udzielić `NETWORK SERVICE` uprawnienia do odczytu klucza prywatnego, zgodnie z opisem w poniższych instrukcjach konta. `NETWORK_SERVICE`to konto służy do uruchamiania brokera usług R to usługa, która kończy przychodzących połączeń SSL na serwerze.

1. Uruchom `certlm.msc` (Menedżer certyfikatów) z wiersza polecenia z uprawnieniami administratora.
1. Rozwiń węzeł **osobiste > Certyfikaty**, kliknij prawym przyciskiem myszy certyfikat, a wybierz **wszystkie zadania > Zarządzaj kluczami prywatnymi**.
1. Kliknij prawym przyciskiem myszy certyfikat, a następnie wybierz polecenie Zarządzaj kluczami prywatnymi, w obszarze wszystkich zadań
1. W wyświetlonym oknie dialogowym wybierz **Dodaj** , a następnie wprowadź `NETWORK SERVICE` jako nazwa konta:

    ![Okno dialogowe kluczy prywatnych, Dodawanie usługi NETWORK_SERVICE Zarządzanie](media/workspaces-remote-manage-private-key-dialog.png)

1. Wybierz **OK** dwa razy, aby zamknąć okna dialogowe i zatwierdzić zmiany.

## <a name="install-an-ssl-certificate-on-ubuntu"></a>Zainstaluj certyfikat SSL na Ubuntu

`rtvs-daemon` Pakietu zostanie zainstalowany certyfikat z podpisem własnym domyślnie jako część instalacji.

### <a name="obtaining-a-self-signed-certificate-ubuntu"></a>Uzyskiwanie certyfikatu z podpisem własnym (Ubuntu)

Zalety i wady używania certyfikatu z podpisem własnym dla opis systemu windows. `rtvs-daemon` Pakietu generuje i konfiguruje certyfikatu z podpisem własnym podczas instalacji. Należy to zrobić tylko, jeśli chcesz zastąpić automatycznie wygenerowany certyfikat z podpisem własnym.

Aby wystawić samodzielnie certyfikat z podpisem samodzielnie:

1. SSH lub zaloguj się do komputera z systemem linux.
1. Zainstaluj `ssl-cert` pakietu:
    ```sh
    sudo apt-get install ssl-cert
    ```
1. Uruchom `make-ssl-cert` można wygenerować certyfikatu SSL z podpisem własnym domyślne:
    ```sh
    sudo make-ssl-cert generate-default-snakeoil --force-overwrite
    ```
1. Przekonwertować wygenerowany klucz i pliki PEM PFX. Wygenerowany plik PFX musi należeć do folderu macierzystego:
    ```sh
    openssl pkcs12 -export -out ~/ssl-cert-snakeoil.pfx -inkey /etc/ssl/private/ssl-cert-snakeoil.key -in /etc/ssl/certs/ssl-cert-snakeoil.pem -password pass:SnakeOil
    ```

### <a name="configuring-rtvs-daemon"></a>Konfigurowanie demon RTVS

Ścieżka pliku certyfikatu SSL (ścieżka do pliku PFX) musi być ustawiona w `/etc/rtvs/rtvsd.config.json`. Aktualizacja `X509CertificateFile` i `X509CertificatePassword` przy użyciu ścieżki pliku i hasła odpowiednio.

```json
{
  "logging": { "logFolder": "/tmp" },
  "security": {
    "allowedGroup": "",
    "X509CertificateFile": "/etc/rtvs/ssl-cert-snakeoil.pfx",
    "X509CertificatePassword": "SnakeOil"
  },
  "startup": { "name": "rtvsd" },
  "urls": "https://0.0.0.0:5444"
}
```

Zapisz plik i ponownie uruchomić tego demona `sudo systemctl restart rtvsd`.

## <a name="install-r-services-on-windows"></a>Zainstaluj usługi R w systemie Windows

Aby uruchomić kod języka R, komputer zdalny musi mieć interpreter języka R zainstalować w następujący sposób:

1. Pobierz i zainstaluj jedną z następujących czynności:

    - [Microsoft R Open](https://mran.microsoft.com/open/)
    - [Sieci CRAN R dla systemu Windows](https://cran.r-project.org/bin/windows/base/)

    Mają identyczną funkcjonalność, ale Microsoft R Otwórz korzyści z dodatkowy sprzęt przyspieszony bibliotek algebraiczną liniowy dzięki uprzejmości [biblioteki jądra matematyczne Intel](https://software.intel.com/intel-mkl).

1. Uruchom [Instalatora usług R](https://aka.ms/rtvs-services) i ponowny rozruch po wyświetleniu monitu. Instalator wykonuje następujące czynności:

    - Utwórz folder w `%PROGRAMFILES%\R Tools for Visual Studio\1.0\` i skopiuj wszystkie wymagane pliki binarne.
    - Zainstaluj `RHostBrokerService` i `RUserProfileService` i skonfigurować do automatycznego uruchamiania.
    - Skonfiguruj `seclogon` na uruchamianie automatyczne.
    - Dodaj `Microsoft.R.Host.exe` i `Microsoft.R.Host.Broker.exe` do zapory reguły dla ruchu przychodzącego na domyślnym porcie 5444.

R usług jest uruchamiana automatycznie przy ponownym uruchomieniu komputera:

- **Usługa Broker hosta R** obsługuje cały ruch HTTPS między Visual Studio i procesów, którym kod języka R jest uruchomiona na komputerze.
- **Usługi profilu użytkownika R** jest składnikiem uprzywilejowane, który obsługuje tworzenie profilu użytkownika systemu Windows. Usługa jest wywoływana, gdy nowy użytkownik najpierw loguje się do komputera serwera R.

Widzisz tych usług w konsoli zarządzania usługami (`compmgmt.msc`).

## <a name="install-r-services-on-linux"></a>Zainstaluj usługi R w systemie Linux

Aby uruchomić kod języka R, komputer zdalny musi mieć interpreter języka R zainstalować w następujący sposób:

1. Pobierz i zainstaluj jedną z następujących czynności:

    - [Microsoft R Open](https://mran.microsoft.com/open/)
    - [Sieci CRAN R dla systemu Windows](https://cran.r-project.org/bin/linux/ubuntu/)

    Mają identyczną funkcjonalność, ale Microsoft R Otwórz korzyści z dodatkowy sprzęt przyspieszony bibliotek algebraiczną liniowy dzięki uprzejmości [biblioteki jądra matematyczne Intel](https://software.intel.com/intel-mkl).

1. Postępuj zgodnie z instrukcjami [zdalny R dla systemu Linux](setting-up-remote-r-service-on-linux.md), która obejmuje komputery fizyczne Ubuntu Ubuntu maszynach, podsystemu systemu Windows dla systemu Linux (WSL) i Docker kontenerów, łącznie z uruchomionymi w repozytorium Azure kontenera.

## <a name="configure-r-services"></a>Konfigurowanie usług R

Z usługami R uruchomiony na komputerze zdalnym można również muszą tworzyć konta użytkowników, ustawić reguły zapory, skonfigurować sieć platformy Azure i skonfigurować certyfikat SSL.

1. Konta użytkowników: tworzenie kont dla każdego użytkownika uzyskującego dostęp do komputera zdalnego. Można tworzyć albo konta lokalnego użytkownika standardowego (nieuprzywilejowany) lub przyłącz komputer serwera R do swojej domeny i Dodaj grupy zabezpieczeń odpowiednich do `Users` grupy zabezpieczeń.

1. Reguły zapory: Domyślnie `R Host Broker` nasłuchuje na porcie TCP 5444. W związku z tym, upewnij się, że są włączone dla ruchu przychodzącego i wychodzącego reguł zapory systemu Windows (wychodzącego jest potrzebne do instalowania pakietów i podobne scenariusze).  Instalator usług R ustawia te zasady automatycznie wbudowane zapory systemu Windows. Jeśli korzystasz z zapory innej firmy, otwórz port 5444 `R Host Broker` ręcznie.

1. Konfiguracja programu Azure: Jeśli komputer zdalny jest maszynę wirtualną na platformie Azure, otwórz port 5444 ruch przychodzący w sieci Azure jako dobrze, która jest niezależna od zapory systemu Windows. Aby uzyskać więcej informacji, zobacz [filtrowania ruchu sieciowego z sieciową grupą zabezpieczeń](https://docs.microsoft.com/azure/virtual-network/virtual-networks-nsg) w dokumentacji platformy Azure.

1. Poinformuj brokera hosta R certyfikatu SSL, które można załadować: Jeśli użytkownik instaluje certyfikat na serwerze sieci Intranet, jest prawdopodobnie w pełni kwalifikowaną nazwą domeny serwera jest taka sama jak jego nazwa NETBIOS. W takim przypadku nie ma nic, które należy wykonać, ponieważ jest to domyślny certyfikat, który jest ładowany.

    Jednak jeśli certyfikat jest instalowany na serwerze połączonych z Internetem (na przykład w przypadku maszyny Wirtualnej platformy Azure), użyć pełni kwalifikowaną nazwą domeny (FQDN) serwera, ponieważ nazwa FQDN serwera internetowy nigdy nie jest taka sama jak jego nazwa NETBIOS.

    Użyj nazwy FQDN, przejdź do zainstalowanym usług R (`%PROGRAM FILES%\R Remote Service for Visual Studio\1.0` domyślnie), otwórz `Microsoft.R.Host.Broker.Config.json` plik w edytorze tekstów i zastąp jego zawartość CN następujących, przypisywanie do niezależnie od serwera do nazwy FQDN, takich jak `foo.westus.cloudapp.azure.com`:

    ```json
    {
      "server.urls": "https://0.0.0.0:5444",
      "security": {
        "X509CertificateName": "CN=your-server-fully-qualified-domain-name"
      }
    }
    ```

    Zapisz plik i ponownie uruchom komputer, aby zastosować zmiany.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

**Komputer serwera R nie odpowiada, co należy zrobić?**

Spróbuj wykonać polecenie ping do komputera zdalnego z wiersza polecenia: `ping remote-machine-name`. Jeśli polecenie ping nie powiedzie się, upewnij się, że na komputerze jest zainstalowany.

**Q. Okno interaktywne R mówi znajduje się na komputerze zdalnym, ale Dlaczego usługa nie jest uruchomiona?**

Istnieją trzy możliwe przyczyny:

- [.NET framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) lub nie jest zainstalowany na komputerze.
- Zasady zapory `Microsoft.R.Host.Broker` i `Microsoft.R.Host` nie są włączone dla przychodzących i wychodzących połączeń na porcie 5444.
- Certyfikat SSL z `CN=<remote-machine-name>` nie został zainstalowany.

Ponowne uruchomienie komputera po wprowadzeniu zmiany powyżej. Następnie upewnij się, że `RHostBrokerService` i `RUserProfileService` są uruchomione przy użyciu albo Menedżera zadań (karta usług) lub `services.msc`.

**Q. Dlaczego okno interaktywne R powiedzieć "401 Odmowa dostępu" podczas nawiązywania połączenia z serwerem R?**

Istnieją dwie możliwe przyczyny:

- Istnieje duże prawdopodobieństwo, że `NETWORK SERVICE` konto nie ma dostępu do klucza prywatnego certyfikatu protokołu SSL. Postępuj zgodnie z instrukcjami wcześniejszych udzielenia `NETWORK SERVICE` dostępu do klucza prywatnego.
- Upewnij się, że `seclogon` usługa jest uruchomiona. Użyj `services.msc` skonfigurować `seclogon` do automatycznego uruchamiania.

**Q. Dlaczego okno interaktywne R powiedzieć "nie znaleziono 404" podczas nawiązywania połączenia z serwerem R?**

Ten błąd prawdopodobnie z powodu braku biblioteki pakietu redystrybucyjnego Visual C++. Sprawdź okno interaktywne R, czy jest komunikatem dotyczącym library(DLL) Brak. Następnie sprawdź, czy VS 2015 redistributable jest zainstalowany, i czy masz R również zainstalowany.

**Q. Nie mam dostępu do Internetu/zasobu z okno interaktywne R, co należy zrobić?**

Upewnij się, że reguły zapory `Microsoft.R.Host.Broker` i `Microsoft.R.Host` zezwolić na dostęp wychodzący na porcie 5444. Ponowne uruchomienie komputera po wprowadzeniu zmian.

**Q. Podejmowano tych rozwiązań, a nadal nie działa. Co teraz?**

Szukaj w plikach dzienników w `C:\Windows\ServiceProfiles\NetworkService\AppData\Local\Temp`. Ten folder zawiera osobne pliki dziennika dla każdego wystąpienia usługi Broker R, która została uruchomiona. Nowy plik dziennika jest tworzony przy każdym ponownym uruchomieniu usługi. Sprawdź najnowszy plik dziennika dla wskazówek dotyczących co może być przejście niewłaściwy.
