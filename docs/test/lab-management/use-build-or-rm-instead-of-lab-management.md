---
title: "Użyj kompilacji lub zarządzania zleceniami dla testowanie automatyczne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: automated testing, lab management, test lab
ms.assetid: F34B0D19-B430-4C01-B402-62A861007E71
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.openlocfilehash: 8d843800666ae53a686a18fcab28d02eb4c16743
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="use-build-and-release-management-instead-of-lab-management-for-automated-testing"></a>Użyj kompilacji i zarządzania zleceniami zamiast Lab Management dla testowanie automatyczne

Jeśli używasz programu Microsoft Test Manager (MTM) i Lab Management do testów automatycznych lub automatyzacji kompilacja wdrażanie testy w tym temacie wyjaśniono, jak można osiągnąć te same cele przy użyciu [kompilacji &amp; wersji](https://www.visualstudio.com/team-services/continuous-integration/) funkcji w programie Team Foundation Server (TFS) i Visual Studio Team Services:

* [Automatyzacja kompilacja wdrażanie testy](#bdtautomation)

* [Samoobsługowe zarządzanie środowiska SCVMM](#managescvmm)

Kompilowanie i zarządzania zleceniami nie obsługują samoobsługowego tworzenia środowisk SCVMM izolowane od sieci i nie ma żadnych planów, aby zapewnić tę obsługę w przyszłości. Istnieją jednak niektóre [sugerowane alternatyw](#isolatedenvir).

<a name="bdtautomation"></a>
## <a name="build-deploy-test-automation"></a>Automatyzacja kompilacja wdrażanie testy

MTM i Lab Management korzystają z definicji kompilacji XAML do automatyzowania kompilacji, wdrażania i testowania aplikacji.
Kompilacji XAML polega na różne konstrukcje utworzone w programie MTM, takich jak środowisko laboratoryjne, zestawów testów i ustawień testowania i na różnych składników infrastruktury, takich jak kontroler kompilacji, agentów kompilacji kontrolera testów i agentów testowych na osiągnięcie tego celu. Można to wykonać za pomocą mniejszej liczby kroków kompilacji lub zarządzania zleceniami w programie TFS i usługi Team Services.

| Kroki | Z kompilacji XAML | Z kompilacji lub zarządzania zleceniami |
|-------|----------------------|-----------------|
| Zidentyfikuj maszyny do kompilacji do wdrażania i uruchamiania testów. | Utwórz środowisko laboratoryjne standardowe w programie MTM z tych maszyn. | n/d |
| Określ testy do uruchomienia. | Tworzenie zestawu testów w programie MTM, tworzenie przypadków testowych i kojarzenie automatyzacji z każdego przypadku testowego. Tworzenie ustawień testów w programie MTM identyfikowanie roli maszyn w środowisku laboratoryjnym, w którym należy uruchomić testy. | Utwórz w programie MTM zestawu testów automatycznych w taki sam sposób jak Jeśli planowane jest zarządzanie testowania przy użyciu planów testów. Alternatywnie można pominąć, to jeśli chcesz uruchomić testy bezpośrednio z utworzonego przez kompilacji plików binarnych testów. Nie istnieje potrzeba do tworzenie ustawień testów w każdym przypadku. |
| Automatyzowania wdrażania i testowania. | Tworzenie definicji kompilacji XAML przy użyciu LabDefaultTemplate.*.xaml. Określ kompilację, zestawów testów i środowiska laboratoryjnego w definicji kompilacji. | Utwórz [kompilacji definicji lub definicji wersji](https://www.visualstudio.com/team-services/continuous-integration/) z jednym środowiskiem. Uruchom sam skrypt wdrażania (od definicji kompilacji XAML) za pomocą zadania wiersza polecenia i Uruchamianie testów automatycznych przy użyciu zadania wdrażania agenta testowego i uruchom testy funkcjonalne. Określ listę maszyn i poświadczeń jako dane wejściowe, aby te zadania. |

Niektóre korzyści wynikające ze stosowania kompilacji lub zarządzania zleceniami w tym scenariuszu są:

* Nie trzeba kontroler kompilacji lub kontrolera testów.
* Agent testowy jest zainstalowany za pomocą zadania jako część kompilacji lub wersji.
* To proste dostosować procedury wdrażania. Nie jesteś już ograniczona do za pomocą jednego skryptu. Można również korzystać z wielu zadań, które są dostępne w ramach produktu, a także jak Visual Studio Marketplace.
* Nie masz Obsługa pakietów testowych. Można bezpośrednio uruchomić testy z plików binarnych.
* Możesz uzyskać wbudowanego bardziej zaawansowane funkcje raportowania środowisko dla testów, które został uruchomiony w ramach każdego kompilacji lub wersji.
* Trwałe, które można śledzić (zlecenia, tworzenie elementów roboczych, zatwierdzeń) są obecnie wdrożone i przetestowane w każdym środowisku.
* Można dostosować i rozszerzenie automatyzacji, aby łatwo wdrożyć wiele środowisk testowych, a nawet produkcji.
* Można zaplanować automatyzacji nastąpić zawsze, gdy istnieje ewidencjonowania lub zatwierdzania lub każdego dnia o określonej godzinie.

<a name="managescvmm"></a>
## <a name="self-service-management-of-scvmm-environments"></a>Samoobsługowe zarządzanie środowiska SCVMM

[Centrum laboratoryjnego programu Microsoft Test Manager](https://msdn.microsoft.com/library/dd997438.aspx) obsługuje zarządzanie biblioteki szablonów środowiska, a także udostępnić środowisk na żądanie przy użyciu [serwer SCVMM](https://technet.microsoft.com/system-center-docs/vmm/vmm).

Samoobsługowe funkcje inicjowania obsługi administracyjnej Centrum laboratoryjnego ma dwa różne cele:

* Podaj prostszy sposób zarządzania infrastrukturą. Zarządzanie szablonami maszyny Wirtualnej i środowiska i automatyczne tworzenie sieci prywatne, aby odizolować klony środowisk od siebie były przykłady infrastruktury zarządzania.

* Podaj prostszy sposób dla zespołów użycie maszyn wirtualnych w ich testowania, wdrażania i działania. Tworzenie laboratorium używanego środowiska dostępne przez ten sam model zabezpieczeń projektu zespołowego i zintegrowane z tych maszyn wirtualnych w scenariuszach testów zostały przykłady łatwość użycia.

Jednak takie jak podane rozwoju bardziej rozbudowane chmur publicznych i prywatnych systemów zarządzania [Microsoft Azure](https://azure.microsoft.com/) i [Microsoft Azure stosu](https://azure.microsoft.com/overview/azure-stack/), nie istnieje żadne zmiany infrastruktury funkcji zarządzania w TFS 2017 i nowszych. Zamiast tego jest nadal fokus na łatwość użycia zasobów zarządzanych za pomocą takich infrastruktury chmury.

W poniższej tabeli przedstawiono typowe działania używanego do wykonywania w Centrum laboratoryjnego i jak można wykonać je za pomocą programu SCVMM albo Azure (jeśli są działania związane z zarządzaniem infrastruktury) lub za pomocą TFS i usługi Team Services (jeśli są one testu lub wdrożenia czynności):

| Kroki | Z Centrum laboratoryjnym | Z kompilacji lub zarządzania zleceniami |
|-------|----------------------|-----------------|
| Zarządzanie biblioteki szablonów środowiska. | Utworzyć środowisko laboratoryjne. Zainstaluj oprogramowanie na maszynach wirtualnych. Narzędzie Sysprep i magazynu środowiska jako szablon w bibliotece. | Używana jest Konsola administracyjna programu SCVMM bezpośrednio do tworzenia i zarządzania nimi, szablony maszyn wirtualnych lub szablonów usług. Podczas korzystania z usługi Azure, wybierz jeden z wstępnie zdefiniowanych [szablonów usługi Azure Resource Manager](https://azure.microsoft.com/documentation/templates/) z [portalu Azure Marketplace](https://azure.microsoft.com/marketplace/) lub [Azure szybki start szablony](https://azure.microsoft.com/documentation/templates/). |
| Utworzyć środowisko laboratoryjne. | Wybierz szablon środowiska w bibliotece, a następnie wdrożyć go. Podaj parametry niezbędne do dostosowania konfiguracji maszyn wirtualnych. | Bezpośrednio za pomocą konsoli administracyjnej programu SCVMM za pomocą szablonów można tworzyć maszyn wirtualnych i wystąpień usługi. Bezpośrednio za pomocą portalu Azure utworzenie zasobów. Lub Utwórz definicję wersji ze środowiskiem. Użyj platformy Azure, zadania lub zadania związane z [rozszerzenia integracji programu SCVMM](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) do utworzenia nowej maszyny wirtualnej. Tworzenie nowej wersji tej definicji jest odpowiednikiem tworzenia nowego środowiska w Centrum laboratoryjnego. |
| Połączyć się z komputerami. | Otwórz środowisko laboratoryjne w przeglądarce środowiska. | Bezpośrednio za pomocą konsoli administracyjnej programu SCVMM połączenia z maszynami wirtualnymi. Aby otworzyć sesji pulpitu zdalnego można również użyć adresu IP lub nazwy DNS maszyn wirtualnych. |
| Utwórz punkt kontrolny środowiska, lub przywrócić środowiska do czystą punktu kontrolnego. | Otwórz środowisko laboratoryjne w przeglądarce środowiska. Wybierz opcję Utwórz punkt kontrolny lub przywracania do poprzedniego punktu kontrolnego. | Bezpośrednio za pomocą konsoli administracyjnej programu SCVMM wykonywać te operacje na maszynach wirtualnych. Lub, aby wykonać te czynności w ramach większych automatyzacji, obejmują zadań punkt kontrolny z [rozszerzenia integracji programu SCVMM](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) jako część środowiska w definicji wersji. |

<a name="isolatedenvir"></a>
## <a name="self-service-creation-of-network-isolated-environments"></a>Samoobsługowe tworzenie środowisk sieci izolowanych

Środowisko laboratorium izolowane sieci jest grupą SCVMM maszyn wirtualnych, które można bezpiecznie sklonować bez powodowania konfliktach sieciowych. Zostało to zrobić w programie MTM przy użyciu szeregu instrukcji, które umożliwiają skonfigurowanie maszyn wirtualnych w sieci publicznej zestaw kart interfejsu sieciowego można skonfigurować maszyn wirtualnych w sieci prywatnej, a innego zestawu kart interfejsu sieciowego.

Wraz z rozwojem bardziej rozbudowane publicznej i prywatnej chmurze systemy zarządzania, takich jak [Microsoft Azure](https://azure.microsoft.com/) i [Microsoft Azure stosu](https://azure.microsoft.com/overview/azure-stack/), może wykorzystywać więcej w chmurze narzędzia do zarządzania bezpośrednio podobne możliwości. Nie istnieje sposób równoważne na realizację tego celu, w kompilacji i zarządzania zleceniami.

Zachęcamy do rozważenia następujących alternatyw, jeśli potrzebujesz izolacji sieci:

* Jeden motywacją do izolacji sieci została łatwość konfiguracji wielu klonach. Każdy klonowania jest dokładne repliki oryginału, nazwy komputera i ustawień konfiguracji zostaną zachowane, ponieważ jest, a to ułatwia konfigurowanie nowych środowisk. Jednak takie same korzyści powoduje, że mogą wystąpić później w cyklu życia (na przykład w środowisku produkcyjnym), ponieważ sposób koniec wdrożenia aplikacji nie jest w tym samym problemy. **Zamiast tego**, warto rozważyć skonfigurowanie nowych środowisk w taki sam sposób jak skonfigurować produkcyjnych i unikać izolacji sieci.

* Korzystania z infrastruktury chmury publicznej, takich jak [Microsoft Azure](https://azure.microsoft.com/) na potrzeby testów wymaga. Możesz z łatwością użyć [szablonów usługi Azure Resource Manager](https://azure.microsoft.com/documentation/templates/) z [portalu Azure Marketplace](https://azure.microsoft.com/marketplace/) lub [Azure szybki start szablony](https://azure.microsoft.com/documentation/templates/) skonfigurowania grup maszyn wirtualnych, które są połączone za pośrednictwem sieci prywatnej i są dostępne do publicznej sieci tylko przy użyciu serwera proxy lub jumpbox.
