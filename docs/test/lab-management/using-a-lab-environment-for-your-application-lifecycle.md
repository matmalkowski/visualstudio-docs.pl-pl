---
title: "Użyj środowiska laboratoryjnego dla Twojego devops | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: lab environment, test lab
ms.assetid: b435eb39-dc7c-46fa-a91b-6e6dd614f01c
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: 88068cf7da401388ac7d8e72e665e91ef1b958b1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="use-a-lab-environment-for-your-devops"></a>Użyj środowiska laboratoryjnego dla Twojego opracowywania oprogramowania

Środowisko laboratoryjne jest kolekcją maszyn wirtualnych i fizycznych, które służy do tworzenia i testowania aplikacji. Środowisko laboratoryjne może zawierać wiele ról, potrzebne do testowania aplikacji wielowarstwowych, takie jak stacje robocze, serwery sieci web i serwery baz danych. Ponadto można przepływu pracy kompilacja wdrażanie testy środowisko laboratorium zautomatyzować proces tworzenia, wdrażania i uruchamiania testów automatycznych w swojej aplikacji.

* **Użyj planu testów do uruchomienia testów automatycznych** — możesz uruchomić zbiór testów automatycznych, nazywany *planu testu*i wyświetlić informację o postępie.  
  
* **Używanie przepływu pracy kompilacja wdrażanie testy** -przepływu pracy kompilacja wdrażanie testy służy do testowania aplikacji wielowarstwowych automatycznie. Typowym przykładem jest przepływ pracy, który rozpoczyna się kompilacja, wdraża plików kompilacji na odpowiednich komputerach w środowisku laboratoryjnym, a następnie wykonuje testów automatycznych. Ponadto można zaplanować przepływu pracy do uruchomienia w określonych odstępach czasu.  
  
* **Zbierania danych diagnostycznych z wszystkich maszyn, nawet podczas testowania ręcznego** — może zbierać dane diagnostyczne z wiele maszyn jednocześnie. Można na przykład podczas jednego uruchomienia testu, zbieranie danych funkcji IntelliTrace, testowanie wpływu i inne rodzaje danych z serwera sieci web, serwera bazy danych i klienta.  
  
Oto przykłady typowych środowisk laboratoryjnych:  
  
| Topologia | Opis |  
|---|---|  
|![Tylko topologii serwerów](../media/topology_backend.png)| To środowisko laboratorium ma *topologii serwerów*, często używany do uruchamiania testów ręcznych na potrzeby aplikacji serwera, a co pozwala testerów sprawdzić błędy w środowisku przy użyciu ich własnych komputerów klienckich. W topologii wewnętrznej bazy danych w środowisku laboratoryjnym zawiera tylko serwery. Korzystając z tego typu topologii, należy zwykle łączą się z serwerów w środowisku laboratoryjnym nie przy użyciu komputera klienta, który jest częścią środowiska.|  
|![Środowisko laboratorium chmury](../media/topology_cloud.png)| Środowiska laboratoryjnego zawiera podobne możliwości i funkcji jako _topologii serwerów_, ale eliminuje konieczność fizycznej lub w środowisku lokalnym; maszyn wirtualnych, które można skrócić czas instalacji, uprościć Konserwacja i ograniczania kosztów. Skonfigurowanie wielu witryn internetowych i maszyn wirtualnych wraz z niestandardowych sieci jest szybkie i łatwe w środowisku chmury, takich jak Microsoft Azure. [Więcej szczegółów](#usebandrm).|  
|![Środowisko laboratoryjne klient serwer](../media/topology_clientserver.png)| To środowisko laboratorium ma *topologii klient serwer*, który często służy do testowania aplikacji, która zawiera składniki klienta i serwera. W topologii klient/serwer wszystkich komputerów klienckich i serwerów używane do testowania aplikacji znajdują się w środowisku laboratoryjnym. Korzystając z tej topologii, może zbierać dane testowe z każdym komputerze, który ma wpływ na testy.|  
  
Zobacz [wideo: Zarządzanie środowiskami laboratoryjnymi na potrzeby testowania](http://go.microsoft.com/fwlink/?LinkID=252614).  
  
Typowe techniki przygotowywania środowiska laboratorium są: 
  
* **[Chmury za pomocą usługi Team Services lub kompilacji programu Team Foundation Server &amp; zlecenia](#usebandrm)**

* **[Korzystanie z funkcji programu Visual Studio Lab Management programu Microsoft Test Manager](#usemtmlm)**

<a name="usebandrm"></a>
## <a name="use-the-cloud-with-team-services-or-team-foundation-server-build-amp-release"></a>Chmury za pomocą usługi Team Services lub kompilacji programu Team Foundation Server &amp; zlecenia

Można wykonać testów automatycznych i automatyzacji kompilacja wdrażanie testy przy użyciu [kompilacji &amp; wersji](https://www.visualstudio.com/team-services/continuous-integration/) funkcji w programie Team Foundation Server (TFS) i Visual Studio Team Services. Oto niektóre zalety są:

* Nie trzeba kontroler kompilacji lub kontrolera testów.
* Agent testowy jest zainstalowany za pomocą zadania jako część kompilacji lub wersji.
* To proste dostosować procedury wdrażania. Nie jesteś już ograniczona do za pomocą jednego skryptu. Można również korzystać z wielu zadań, które są dostępne w ramach produktu, a także jak Visual Studio Marketplace.
* Nie masz Obsługa pakietów testowych. Można bezpośrednio uruchomić testy z plików binarnych.
* Możesz uzyskać wbudowanego bardziej zaawansowane funkcje raportowania środowisko dla testów, które został uruchomiony w ramach każdego kompilacji lub wersji.
* Trwałe, które można śledzić (zlecenia, tworzenie elementów roboczych, zatwierdzeń) są obecnie wdrożone i przetestowane w każdym środowisku.
* Można dostosować i rozszerzenie automatyzacji, aby łatwo wdrożyć wiele środowisk testowych, a nawet produkcji.
* Można zaplanować automatyzacji nastąpić zawsze, gdy istnieje ewidencjonowania lub zatwierdzania lub każdego dnia o określonej godzinie.

[Więcej informacji](use-build-or-rm-instead-of-lab-management.md).

<a name="usemtmlm"></a>
## <a name="use-the-visual-studio-lab-management-features-of-microsoft-test-manager"></a>Korzystanie z funkcji programu Visual Studio Lab Management programu Microsoft Test Manager

Można utworzyć i zarządzać nimi środowisk laboratoryjnych z funkcjami programu Visual Studio Lab Management programu Microsoft Test Manager, korzystając z programu Visual Studio Enterprise lub Visual Studio Test Professional.

Lab Management automatycznie instaluje agentów testowych na każdym komputerze w danym środowisku.  
  
Jeśli używasz Lab Management w połączeniu z System Center Virtual Machine Manager (SCVMM), można także uzyskać tych korzyści używania środowisk laboratoryjnych:  
  
* **Szybko odtworzyć konfiguracje maszyny** — można przechowywać kolekcji maszyn wirtualnych, które są skonfigurowane do odtworzenia środowisk produkcji. Następnie można przeprowadzić każdy test na nową kopię przechowywanych środowiska.  
  
* **Odtwórz dokładne warunki usterki** — w przypadku niepowodzenia uruchomienia testu, można przechowywać kopię stanu w środowisku laboratoryjnym i do niego dostęp z wyników kompilacji lub elementu roboczego.  
  
* **Uruchamianie wielu kopii środowiska laboratoryjnego w tym samym czasie** — w tym samym czasie bez konfliktów nazw można uruchomić wiele kopii w środowisku laboratoryjnym.  
  
### <a name="standard-environments-and-scvmm-environments"></a>Standardowych środowisk i środowisk programu SCVMM

Istnieją dwa typy środowisk laboratoryjnych, które można tworzyć z programu Visual Studio Lab Management: **standardowych środowisk** i **środowisk programu SCVMM**.
Jednak możliwości poszczególnych typów środowiska są różne.  
  
> **Uwaga**: Lab Management **nie** obsługi w programie SCVMM 2016. Informacje w programie SCVMM, zobacz [programu Virtual Machine Manager](http://go.microsoft.com/fwlink/?LinkId=226332). 
  
**Standardowych środowisk:** może zawierać zarówno maszyny wirtualne i fizyczne. Maszyny wirtualne można również dodać do standardowego środowiska, które są zarządzane przez platformy wirtualizacji innej firmy. Ponadto standardowych środowisk nie wymaga dodatkowego serwera zasobów, takich jak serwer SCVMM.  
  
**Środowisk programu SCVMM:** może zawierać tylko maszyn wirtualnych, które są zarządzane przez program SCVMM (System Center Virtual Machine Manager), więc maszyn wirtualnych w środowisku SCVMM można uruchomić tylko w ramach wirtualizacji funkcji Hyper-V. Jednak środowisk programu SCVMM zapewniają następujące funkcje zarządzania i automatyzacji, które nie są dostępne w standardowych środowisk:  
  
- **Migawki środowiska:** migawki środowiska zawiera stan środowisko laboratoryjne, więc można szybko przywrócić czystego środowiska lub zapisać stanu środowiska, które zostały zmodyfikowane. Przepływ pracy kompilacja wdrażanie testy umożliwia również zautomatyzować proces zapisywanie i przywracanie migawki środowiska.  
  
- **Przechowywane środowisk:** przechowują kopię środowiska SCVMM, a następnie wdrożenie wielu kopii tego środowiska.  
  
- **Izolacja sieci:** izolacji sieci służy do jednoczesnego uruchamiania wielu kopii identycznych środowiska SCVMM bez konfliktów nazw komputerów.  
  
- **Szablony maszyn wirtualnych:** szablon maszyny wirtualnej jest maszyny wirtualnej, który miał jego nazwa i usunąć innych identyfikatorów. Szablon maszyny Wirtualnej jest wdrażana w środowisku SCVMM, program Microsoft Test Manager generuje nowych identyfikatorów. Dzięki temu możesz wdrażać kopie maszyny wirtualnej w tym samym środowisku lub wiele środowisk, a następnie uruchom maszyn wirtualnych jednocześnie.  
  
- **Przechowywane maszyny wirtualne:** maszyny wirtualnej, która jest przechowywana w bibliotece projektu zespołowego i zawiera unikatowe identyfikatory.  
  
Aby uzyskać więcej informacji o tych funkcjach, zobacz [wskazówki dotyczące tworzenia i zarządzania środowisk programu SCVMM](https://msdn.microsoft.com/en-gb/library/ee830480.aspx).  
  
Standardowych środowisk i środowisk programu SCVMM obsługują wiele te same funkcje. Istnieje jednak kilka istotnych różnic wziąć pod uwagę. W poniższej tabeli porównano funkcje, które są dostępne dla standardowych środowisk i środowisk programu SCVMM.  
  
|Możliwość|Środowiska SCVMM|Standardowych środowisk|  
|----------------|------------------------|---------------------------|  
|**Testowanie**|||  
|Uruchom testy ręczne|Obsługiwane|Obsługiwane|  
|Uruchamianie kodowanego interfejsu użytkownika i inne testy automatyczne|Obsługiwane|Obsługiwane|  
|Usterki sformatowanego plików za pomocą adapterów diagnostycznych|Obsługiwane|Obsługiwane|  
|**Wdrożenie kompilacji**|||  
|Automatyczne przepływy pracy kompilacja wdrażanie testy|Obsługiwane|Obsługiwane|  
|**Tworzenie środowiska i zarządzanie nimi**|||  
|Użyj maszyn fizycznych oprócz maszyny wirtualne|Nieobsługiwane|Obsługiwane|  
|Użyj maszyn wirtualnych innych firm|Nieobsługiwane|Obsługiwane|  
|Automatycznie Zainstaluj agentów testowych na komputerach w środowisku laboratoryjnym|Obsługiwane|Obsługiwane|  
|Zapisz i wdróż stan środowiska laboratoryjnego korzystanie z environment snapshots|Obsługiwane|Nieobsługiwane|  
|Tworzenie środowisk laboratoryjnych z szablonów maszyny Wirtualnej|Obsługiwane|Nieobsługiwane|  
|Start/stop/migawki środowiska|Obsługiwane|Nieobsługiwane|  
|Połącz ze środowiskiem za pomocą podglądu środowiska|Obsługiwane|Obsługiwane|  
|Uruchamianie wielu kopii środowiska w tym samym czasie przy użyciu izolacji sieci|Obsługiwane|Nieobsługiwane|  
  
### <a name="lab-management-concepts"></a>Pojęcia dotyczące zarządzania laboratorium

Poniżej przedstawiono niektóre dodatkowe pojęcia, które należy poznać przed kontynuowaniem:  
  
|Termin|Opis|  
|----------|-----------------|  
|Centrum laboratoryjnego|Obszar programu Microsoft Test Manager gdzie tworzenie i zarządzanie nimi środowisk laboratoryjnych.|  
|Laboratorium projektu zespołowego|Kolekcja środowisk laboratoryjnych, które zostały tak skonfigurowany, można podłączyć do nich i uruchamiania ich maszyn wirtualnych.|  
|Bibliotecznego projektu zespołowego|Archiwum przechowywanych maszyn wirtualnych, szablonów i środowisk laboratoryjnych przechowywane, które zostały zaimportowane do grupy hostów projektu zespołowego. Można używać elementów w bibliotece z SCVMM environments; jednak nie można ich dodać bezpośrednio do standardowego środowiska. Nie można uruchomić elementy w bibliotece; zamiast niej używać ich do wdrożenia nowego środowiska.|  
|Wdrożony środowiska|Środowisko laboratoryjne, która została wdrożona do środowiska laboratoryjnego projektu zespołowego, aby mogli nawiązać z nim i uruchomienia jej maszyn.|  

#### <a name="related-topics"></a>Tematy pokrewne

* [Planowanie laboratorium](https://msdn.microsoft.com/library/ff756575%28v=vs.140%29.aspx) 
* [Administrowanie laboratorium](https://msdn.microsoft.com/library/dd936084%28v=vs.140%29.aspx) 
* [Konfigurowanie dla środowiska SCVMM](https://msdn.microsoft.com/library/dd380687%28v=vs.140%29.aspx) 
* [Uaktualnienie programu SCVMM 2008 R2 do wersji SCVMM 2012](upgrade-scvmm-2008-r2-scvmm-2012.md) 
* [Zarządzaj uprawnieniami](https://msdn.microsoft.com/library/dd380760%28v=vs.140%29.aspx) 
* [Zmień ustawienia](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx) 
* [Rozwiązywanie problemów](https://msdn.microsoft.com/library/ee853230%28v=vs.140%29.aspx)
  
### <a name="set-up-environments"></a>Konfigurowanie środowisk

* [Tworzenie &amp; środowisk chmury zlecenia](use-build-or-rm-instead-of-lab-management.md)
* [Standardowe środowiska laboratoryjne](https://msdn.microsoft.com/en-gb/library/ee390842.aspx)
* [Środowiska (wirtualne) SCVMM](https://msdn.microsoft.com/en-gb/library/ee943322.aspx)
* [Tworzenie i używanie środowisku sieci izolowanej](https://msdn.microsoft.com/en-gb/library/ee518924.aspx)
  
## <a name="see-also"></a>Zobacz także
  
* [Instalowanie i konfigurowanie agentów testowych](install-configure-test-agents.md)
* [Przewodnik po zarządzania laboratorium programu Visual Studio](http://go.microsoft.com/fwlink/?LinkID=230951)  
* [Zarządzanie środowiskami laboratoryjnymi na potrzeby testowania](http://go.microsoft.com/fwlink/?LinkID=252614)  
* [Visual Studio devops + Blog programu Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=254496)  
