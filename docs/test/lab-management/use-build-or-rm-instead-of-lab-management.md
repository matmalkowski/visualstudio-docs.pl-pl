---
title: "Użyj kompilacji lub zarządzania zleceniami dla automatycznego testowania w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 03/02/2018
ms.technology: vs-devops-test
ms.topic: article
helpviewer_keywords:
- automated testing, lab management, test lab
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: b12bffb6f2e5df0209fd3dfe3ea5fd005897d58d
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2018
---
# <a name="use-build-and-release-management-instead-of-lab-management-for-automated-testing"></a>Użyj kompilacji i zarządzania zleceniami zamiast Lab Management dla testowanie automatyczne

Jeśli używasz programu Microsoft Test Manager (MTM) i Lab Management do testów automatycznych lub automatyzacji kompilacja wdrażanie testy w tym temacie wyjaśniono, jak można osiągnąć te same cele przy użyciu [kompilacji i wydania](/vsts/build-release/) funkcji w programie Team Foundation Server (TFS) i Visual Studio Team Services (VSTS).

## <a name="build-deploy-test-automation"></a>Automatyzacja kompilacja wdrażanie testy

MTM i Lab Management korzystają z definicji kompilacji XAML do automatyzowania kompilacji, wdrażania i testowania aplikacji. Kompilacji XAML polega na różne konstrukcje utworzone w programie MTM, takich jak środowisko laboratoryjne, zestawów testów i ustawień testowania i na różnych składników infrastruktury, takich jak kontroler kompilacji, agentów kompilacji kontrolera testów i agentów testowych na osiągnięcie tego celu. Można to wykonać za pomocą mniejszej liczby kroków kompilacji lub zarządzania zleceniami w programie TFS i usługi Team Services.

| Kroki | Z kompilacji XAML | Z kompilacji lub zarządzania zleceniami |
|-------|----------------------|-----------------|
| Zidentyfikuj maszyny do kompilacji do wdrażania i uruchamiania testów. | Utwórz środowisko laboratoryjne standardowe w programie MTM z tych maszyn. | n/d |
| Określ testy do uruchomienia. | Tworzenie zestawu testów w programie MTM, tworzenie przypadków testowych i kojarzenie automatyzacji z każdego przypadku testowego. Tworzenie ustawień testów w programie MTM identyfikowanie roli maszyn w środowisku laboratoryjnym, w którym należy uruchomić testy. | Utwórz w programie MTM zestawu testów automatycznych w taki sam sposób jak Jeśli planowane jest zarządzanie testowania przy użyciu planów testów. Alternatywnie można pominąć, to jeśli chcesz uruchomić testy bezpośrednio z utworzonego przez kompilacji plików binarnych testów. Nie istnieje potrzeba do tworzenie ustawień testów w każdym przypadku. |
| Automatyzowania wdrażania i testowania. | Tworzenie definicji kompilacji XAML przy użyciu LabDefaultTemplate.*.xaml. Określ kompilację, zestawów testów i środowiska laboratoryjnego w definicji kompilacji. | Utwórz [kompilacji lub wersji definicji](/vsts/build-release/) z jednym środowiskiem. Uruchom sam skrypt wdrażania (od definicji kompilacji XAML) za pomocą zadania wiersza polecenia i Uruchamianie testów automatycznych przy użyciu zadania wdrażania agenta testowego i uruchom testy funkcjonalne. Określ listę maszyn i poświadczeń jako dane wejściowe, aby te zadania. |

Niektóre korzyści wynikające ze stosowania kompilacji lub zarządzania zleceniami w tym scenariuszu są:

* Nie trzeba kontroler kompilacji lub kontrolera testów.
* Agent testowy jest zainstalowany za pomocą zadania jako część kompilacji lub wersji.
* To proste dostosować procedury wdrażania. Nie jesteś już ograniczona do za pomocą jednego skryptu. Można również korzystać z wielu zadań, które są dostępne w ramach produktu, a także jak Visual Studio Marketplace.
* Nie masz Obsługa pakietów testowych. Można bezpośrednio uruchomić testy z plików binarnych.
* Możesz uzyskać wbudowanego bardziej zaawansowane funkcje raportowania środowisko dla testów, które został uruchomiony w ramach każdego kompilacji lub wersji.
* Trwałe, które można śledzić (zlecenia, tworzenie elementów roboczych, zatwierdzeń) są obecnie wdrożone i przetestowane w każdym środowisku.
* Można dostosować i rozszerzenie automatyzacji, aby łatwo wdrożyć wiele środowisk testowych, a nawet produkcji.
* Można zaplanować automatyzacji nastąpić zawsze, gdy istnieje ewidencjonowania lub zatwierdzania lub każdego dnia o określonej godzinie.

## <a name="self-service-management-of-scvmm-environments"></a>Samoobsługowe zarządzanie środowiska SCVMM

[Centrum laboratoryjnego programu Microsoft Test Manager](https://msdn.microsoft.com/library/dd997438.aspx) obsługuje zarządzanie biblioteki szablonów środowiska, a także udostępnić środowisk na żądanie przy użyciu [serwer SCVMM](/system-center/vmm/overview?view=sc-vmm-1801).

Samoobsługowe funkcje inicjowania obsługi administracyjnej Centrum laboratoryjnego ma dwa różne cele:

* Podaj prostszy sposób zarządzania infrastrukturą. Zarządzanie szablonami maszyny Wirtualnej i środowiska i automatyczne tworzenie sieci prywatne, aby odizolować klony środowisk od siebie były przykłady infrastruktury zarządzania.

* Podaj prostszy sposób dla zespołów użycie maszyn wirtualnych w ich testowania, wdrażania i działania. Tworzenie laboratorium używanego środowiska dostępne przez ten sam model zabezpieczeń projektu zespołowego i zintegrowane z tych maszyn wirtualnych w scenariuszach testów zostały przykłady łatwość użycia.

Jednak takie jak podane rozwoju bardziej rozbudowane chmur publicznych i prywatnych systemów zarządzania [Microsoft Azure](https://azure.microsoft.com/) i [Microsoft Azure stosu](https://azure.microsoft.com/overview/azure-stack/), nie istnieje żadne zmiany infrastruktury funkcji zarządzania w TFS 2017 i nowszych. Zamiast tego jest nadal fokus na łatwość użycia zasobów zarządzanych za pomocą takich infrastruktury chmury.

W poniższej tabeli przedstawiono typowych działań, wykonywanych w Centrum laboratoryjnego i jak można wykonać je za pomocą programu SCVMM albo Azure (jeśli są działania związane z zarządzaniem infrastruktury) lub za pomocą TFS i usługi Team Services (jeśli są one działań testów lub wdrożenia):

| Kroki | Z Centrum laboratoryjnym | Z kompilacji lub zarządzania zleceniami |
|-------|----------------------|-----------------|
| Zarządzanie biblioteki szablonów środowiska. | Utworzyć środowisko laboratoryjne. Zainstaluj oprogramowanie na maszynach wirtualnych. Narzędzie Sysprep i magazynu środowiska jako szablon w bibliotece. | Używana jest Konsola administracyjna programu SCVMM bezpośrednio do tworzenia i zarządzania nimi, szablony maszyn wirtualnych lub szablonów usług. Podczas korzystania z usługi Azure, wybierz jedną z [szablonów Szybki Start Azure](/resources/templates/). |
| Utworzyć środowisko laboratoryjne. | Wybierz szablon środowiska w bibliotece, a następnie wdrożyć go. Podaj parametry niezbędne do dostosowania konfiguracji maszyn wirtualnych. | Bezpośrednio za pomocą konsoli administracyjnej programu SCVMM za pomocą szablonów można tworzyć maszyn wirtualnych i wystąpień usługi. Bezpośrednio za pomocą portalu Azure utworzenie zasobów. Lub Utwórz definicję wersji ze środowiskiem. Użyj platformy Azure, zadania lub zadania związane z [rozszerzenia integracji programu SCVMM](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) do utworzenia nowej maszyny wirtualnej. Tworzenie nowej wersji tej definicji jest odpowiednikiem tworzenia nowego środowiska w Centrum laboratoryjnego. |
| Połączyć się z komputerami. | Otwórz środowisko laboratoryjne w przeglądarce środowiska. | Bezpośrednio za pomocą konsoli administracyjnej programu SCVMM połączenia z maszynami wirtualnymi. Aby otworzyć sesji pulpitu zdalnego można również użyć adresu IP lub nazwy DNS maszyn wirtualnych. |
| Utwórz punkt kontrolny środowiska, lub przywrócić środowiska do czystą punktu kontrolnego. | Otwórz środowisko laboratoryjne w przeglądarce środowiska. Wybierz opcję Utwórz punkt kontrolny lub przywracania do poprzedniego punktu kontrolnego. | Bezpośrednio za pomocą konsoli administracyjnej programu SCVMM wykonywać te operacje na maszynach wirtualnych. Lub, aby wykonać te czynności w ramach większych automatyzacji, obejmują zadań punkt kontrolny z [rozszerzenia integracji programu SCVMM](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) jako część środowiska w definicji wersji. |

## <a name="creation-of-network-isolated-environments"></a>Tworzenie środowisk sieci izolowanych

Środowisko laboratorium izolowane sieci jest grupą SCVMM maszyn wirtualnych, które można bezpiecznie sklonować bez powodowania konfliktach sieciowych. Zostało to zrobić w programie MTM przy użyciu szeregu instrukcji, które umożliwiają skonfigurowanie maszyn wirtualnych w sieci publicznej zestaw kart interfejsu sieciowego można skonfigurować maszyn wirtualnych w sieci prywatnej, a innego zestawu kart interfejsu sieciowego.

Jednak VSTS i TFS w połączeniu z programu SCVMM kompilacji i zadanie wdrażania, można użyć do zarządzania środowisk programu SCVMM, udostępniania izolowanych sieci wirtualnych i zaimplementować scenariusze kompilacja wdrażanie testy. Na przykład można użyć zadania:

* Tworzenie, przywracania i Usuń punkty kontrolne
* Tworzenie nowych maszyn wirtualnych przy użyciu szablonu
* Uruchamianie i zatrzymywanie maszyn wirtualnych
* Uruchamianie niestandardowych skryptów programu PowerShell dla programu SCVMM

Aby uzyskać więcej informacji, zobacz [Utwórz środowisko wirtualne sieci izolowanej dla scenariuszy kompilacja wdrażanie testy](/vsts/build-release/actions/virtual-networks/create-virtual-network).
