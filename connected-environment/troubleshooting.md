---
title: Rozwiązywanie problemów z | Dokumentacja firmy Microsoft
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: article
ms.technology: vsce-kubernetes
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: ghogen
ms.openlocfilehash: 0f35e31e3f3a109e65565592b56b6dc4177dd7c0
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="troubleshooting-guide"></a>Przewodnik rozwiązywania problemów

## <a name="error-upstream-connect-error-or-disconnectreset-before-headers"></a>Błąd "powyżej błąd połączenia lub odłączyć/reset przed nagłówki"
Ten błąd może zostać wyświetlony podczas próby uzyskania dostępu do usługi. Na przykład po przejściu do adresu URL usługi w przeglądarce. 

**Przyczyna:** port kontenera nie jest dostępna. Są to najbardziej typowe przyczyny: 
* Kontener nadal trwa są wbudowane i wdrożony. Może to mieć miejsce, jeśli uruchomisz `vsce up` lub uruchomienia debugera, a następnie spróbuj dostęp kontenera, zanim została pomyślnie wdrożona.
* Konfiguracja portów nie jest spójna z plik Dockerfile, wykres Helm i każdy kod serwera, który zostaje otwarty port.

**Wypróbuj:**
1. Jeśli kontener jest w trakcie wbudowane/wdrażany, możesz poczekaj 2-3 sekundy i spróbuj ponownie uzyskać dostęp do usługi. 
1. Sprawdź konfigurację portu. Numery portów określonej powinna być **identyczne** w poniższych zasobów:
    * **Plik Dockerfile:** określony przez `EXPOSE` instrukcji.
    * **[Wykres Helm](https://docs.helm.sh):** określony przez `externalPort` i `internalPort` wartości dla usługi (często znajduje się w `values.yml` pliku),
    * Wszystkie porty są otwarte w kodzie aplikacji, na przykład w środowisku Node.js: `var server = app.listen(80, function () {...}`


## <a name="config-file-not-found"></a>Nie znaleziono pliku konfiguracji
Uruchomienie `vsce up` i występuje następujący błąd: `Config file not found: .../vsce.yaml`

**Przyczyna:** `vsce up` wymaga do uruchomienia z katalogu głównego kodu chcesz uruchomić i folder kodu musi zainicjowano uruchamianie środowiska połączony.

**Wypróbuj:**
1. Zmień bieżący katalog na folder główny zawierający kodu usługi. 
1. Jeśli nie ma pliku vsce.yaml w folderze kodu, uruchom `vsce init` do generowania Docker, Kubernetes i VSCE zasoby.

## <a name="error-the-pipe-program-vsce-exited-unexpectedly-with-code-126"></a>Błąd: "potoku program został nieoczekiwanie zakończony z kodem 126" vsce"."
Uruchamianie debugera kodzie VS czasami może spowodować błąd. Jest to błąd.

**Wypróbuj:**
1. Zamknij i otwórz ponownie kodzie VS.
2. Ponownie naciśnij klawisz F5.


## <a name="debugging-error-configured-debug-type-coreclr-is-not-supported"></a>Debugowanie błędów "skonfigurowana debugowania"środowisko coreclr"nie obsługuje typu"
Uruchomienie debugera kodzie VS zgłasza błąd: `Configured debug type 'coreclr' is not supported.`

**Przyczyna:** nie ma rozszerzenia kodzie VS dla połączenia środowisko jest zainstalowane na komputerze deweloperskim.

**Spróbuj:** zainstalować [kodzie VS rozszerzenia dla środowiska połączone](get-started-netcore-01.md#get-kubernetes-debugging-for-vs-code).


## <a name="the-azure-portal-doesnt-show-connected-environment-instances"></a>Azure portal nie wyświetla wystąpienia środowiska połączone

**Przyczyna:** środowisko portalu Azure dla środowiska połączone nie jest jeszcze gotowy do podglądu.


## <a name="the-type-or-namespace-name-mylibrary-could-not-be-found"></a>Nie można odnaleźć nazwy typu lub przestrzeni nazw "MojaBiblioteka"

**Przyczyna:** kontekst kompilacji jest domyślnie na poziomie projektu/usługi, w związku z tym projektu biblioteki używasz nie zostaną znalezione.

**Spróbuj:** co trzeba zrobić:
1. Zmodyfikuj vsce.yaml Ustaw kontekst kompilacji do poziomu rozwiązania.
2. Zmodyfikuj plik Dockerfile i Dockerfile.develop pliki do odwoływania się do plików csproj poprawnie, względem nowy kontekst kompilacji.
3. Umieść plik .dockerignore obok pliku sln i modyfikować w razie potrzeby.

Na przykład można znaleźć https://github.com/sgreenmsft/buildcontextsample

## <a name="microsoftconnectedenvironmentregisteraction-authorization-error-when-creating-an-environment"></a>Błąd autoryzacji "Microsoft.ConnectedEnvironment/register/action" podczas tworzenia środowiska
Może się pojawić następujący błąd podczas zarządzania środowiska i korzystania z subskrypcji platformy Azure, nie masz właścicielem lub współautorem dostępu.
`The client '<User email/Id>' with object id '<Guid>' does not have authorization to perform action 'Microsoft.ConnectedEnvironment/register/action' over scope '/subscriptions/<Subscription Id>'.`

**Przyczyna:** wybranych subskrypcji platformy Azure nie został zarejestrowany Microsoft.ConnectedEnvironment przestrzeni nazw.

**Spróbuj:** właścicielem lub współautorem dostęp do subskrypcji platformy Azure można uruchomić następujące polecenie wiersza polecenia platformy Azure, aby ręcznie zarejestrować Microsoft.ConnectedEnvironment przestrzeni nazw:

```cmd
az provider register --namespace Microsoft.ConnectedEnvironment
```

## <a name="vsce-doesnt-seem-to-use-my-existing-dockerfile-to-build-a-container"></a>VSCE nie powiodła się Mój istniejący plik Dockerfile umożliwia tworzenie kontenera 

**Przyczyna:** VSCE można skonfigurować w celu wskaż plik Dockerfile określonych w projekcie. Wygląda na to, czy VSCE nie jest używany plik Dockerfile spodziewasz się tworzenie kontenerów, może być konieczne jawnie Poinformuj VSCE, gdzie jest. 

**Spróbuj:** Otwórz `vsce.yaml` pliku, który został wygenerowany przez VSCE w projekcie. Użyj `configurations->develop->build->dockerfile` dyrektywy wskaż plik Dockerfile, którego chcesz użyć:

```
...
configurations:
  develop:
    build:
      dockerfile: Dockerfile.develop
```