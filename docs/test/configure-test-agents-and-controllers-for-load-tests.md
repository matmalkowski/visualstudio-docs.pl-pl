---
title: "Konfigurowanie agentów testowych i testowanie kontrolerów testów obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, test agents and controllers
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 3ed020e6cef6dfb27901b6f72ba29c7c838cf8de
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="configure-test-agents-and-test-controllers-for-running-load-tests"></a>Konfigurowanie agentów testowych i kontrolery do uruchamiania testów obciążenia testów

Visual Studio może wygenerować symulowanym obciążeniem dla aplikacji za pomocą fizycznych lub maszynach wirtualnych. Te maszyny należy skonfigurować jako kontrolera pojedynczy test i jeden lub więcej agentów testowych. Test controller i agenci testowi służy do generowania obciążenia więcej niż jeden komputer może generować samodzielnie.

> [!NOTE]
> Umożliwia także testowania obciążenia opartego na chmurze do maszynom wirtualnym, które generują obciążenia w przypadku wielu użytkowników, dostęp do witryny sieci web, w tym samym czasie. Dowiedz się więcej o testowaniu obciążenia w chmurze w [Uruchamianie testów obciążenia przy użyciu programu VSTS](/vsts/load-test/get-started-simple-cloud-load-test).

## <a name="load-simulation-architecture"></a>Architektura symulacji obciążenia

Architektura symulacji obciążenia składa się z klienta programu Visual Studio, kontroler testów i agentów testowych.

-   Klient służy do opracowywania i wykonywania testów oraz do wyświetlania ich wyników.

-   Kontroler testów służy do administrowania agentami testowymi i gromadzenia wyników testów.

-   Agenci testowi służą do wykonywania testów oraz zbierania danych, w tym informacji systemowych i danych profilowania ze środowiska ASP.NET zdefiniowanych w ustawieniu testu.

Taka architektura ma szereg zalet:

-   Możliwość skalowania generowanego obciążenia przez dodawanie kolejnych agentów testowych do kontrolera testów.

-   Elastyczność instalowania oprogramowania klienta, kontrolera testów i agentów testowych na tym samym lub różnych komputerach. Na przykład:

     **Lokalnej konfiguracji:**

    -   Komputer 1: program Visual Studio, kontroler, agent.

     ![Komputerem lokalnym przy użyciu kontrolera i agenta](./media/load-test-configa.png)

     **Typowa konfiguracja zdalnego:**

    -   Komputery 1 i 2: program Visual Studio (wielu testerów może używać tego samego kontrolera).

    -   Komputer 3: kontroler (mogą być na nim również zainstalowani agenci).

    -   Agent Machine4 n: lub agentów skojarzoną z kontrolerem na KOMPUTER3.

     ![Komputerach zdalnych przy użyciu kontrolera i agentów](./media/load-test-configb.png)

Mimo że kontroler testów zarządza zwykle kilkoma agentami testowymi, każdy agent może być powiązany tylko z jednym kontrolerem. Każdego agenta testowego może używać cały zespół deweloperów. Taka architektura pozwala łatwo zwiększać liczbę agentów testowych, a efekcie generować większe obciążenia.

## <a name="test-agent-and-test-controller-interaction"></a>Interakcja między agentami testowymi a kontrolerem testów

Kontroler testów zarządza zbiorem agentów testowych faktycznie wykonujących testy. Kontroler testów komunikuje się z testy rozpoczęcia, Zatrzymaj testy Śledź stan agenta testowego i wyniki testów zbieranie agentów testowych.

### <a name="test-controller"></a>Kontroler testów

Kontroler testów zapewnia ogólną architekturę wykonywania testów oraz zawiera specjalne funkcje do prowadzenia testów obciążeniowych. Kontroler testów wysyła test obciążeniowy do wszystkich agentów testowych i czeka, aż agenci zainicjują test. Gdy wszyscy agenci testowi są gotowi, kontroler testów wysyła do nich komunikat nakazujący rozpoczęcie testu.

### <a name="test-agent"></a>Test Agent

Agent testowy działa jako usługa, która nasłuchuje od kontrolera testów żądań rozpoczęcia nowego testu. Kiedy agent testowy odbiera żądanie, Usługa agenta testowego uruchamia proces, na której uruchamiać testy. Każdy agent testowy wykonuje ten sam test obciążeniowy.

 Administrator przypisuje agentom testowym wagi, według których są następnie rozkładane obciążenia. Na przykład jeśli agent testowy 1 ma wagę 30, agent testowy 2 wagę 70, a obciążenie zostanie ustawione na 1000 użytkowników, agent testowy 1 będzie symulował 300, a agent testowy 2 — 700 wirtualnych użytkowników. Zobacz [Zarządzanie kontrolerami testów i agentami testowymi za pomocą programu Visual Studio](../test/manage-test-controllers-and-test-agents.md).

 Agent testowy ma zestaw testów i symulacji parametrów jako dane wejściowe. Kluczowe pojęcia są niezależne od komputera, na którym są uruchamiane testy.

## <a name="test-controller-and-test-agent-connection-points"></a>Punkty połączenia kontrolerów testów z agentami testowymi

Na poniższej ilustracji pokazano punkty połączenia między kontrolerem testów, agentem testowym i klientem. Opisano go, które porty są używane dla połączeń przychodzących i wychodzących, a także ograniczenia zabezpieczeń używane na tych portach.

 ![Testowanie sterownika i przetestuj agenta portów i zabezpieczeń](./media/test-controller-agent-firewall.png)

 Aby uzyskać więcej informacji, zobacz [Konfigurowanie portów dla kontrolerów testów i agentów testowych](../test/configure-ports-for-test-controllers-and-test-agents.md).

## <a name="test-controller-and-agent-installation-information"></a>Informacje na temat instalowania kontrolera testów i agentów

Ważne informacje o wymaganiach dotyczących sprzętu i oprogramowania dla kontrolerów testów i agentów testowych, zobacz procedury ich instalowania i konfigurowania środowiska, aby uzyskać optymalną wydajność, [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

## <a name="using-the-test-controller-and-test-agent-with-unit-tests"></a>Używanie kontrolera testów i agentów testowych do testów jednostkowych

Po zainstalowaniu kontrolera testów i jednego lub więcej agentów testowych można w ustawieniu testów obciążeniowych określić, czy kontroler testów ma wykonywać testy zdalnie. Ponadto można wskazać dane i adaptery diagnostyczne, które mają być używane do roli powiązanej z agentami w ustawieniu testu.

## <a name="see-also"></a>Zobacz także

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)