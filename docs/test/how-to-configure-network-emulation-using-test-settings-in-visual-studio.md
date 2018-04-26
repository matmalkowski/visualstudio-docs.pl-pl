---
title: Konfiguracja funkcji emulacji sieci przy użyciu ustawień testów w programie Visual Studio
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, network emulation
ms.assetid: ff275cfb-5df9-4710-9a91-9caabaaad34f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 66877397912fca0fbd3996c2dab146b040a047b3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-configure-network-emulation-using-test-settings-in-visual-studio"></a>Porady: konfiguracja funkcji emulacji sieci za pomocą opcji ustawień testów w Visual Studio

Można skonfigurować adapter danych diagnostycznych do testowania aplikacji w różnych środowiskach sieci w programie Visual Studio. Może być również skonfigurowane do testowania obciążenia sieciowego sztuczne lub "wąskie gardło", po uruchomieniu testów.

> [!WARNING]
> Po uruchomieniu testów w rzeczywistych sieci, który jest typem wolniej niż sieć, które są emulowanie testu będą nadal działać wolniej szybkością sieci. Emulacji można tylko spowolnić środowisko sieciowe, nie przyspieszenie działania.

 W poniższej procedurze opisano sposób konfigurowania emulacji sieci z edytora konfiguracji. Te kroki dotyczą edytora konfiguracji w programie Microsoft Test Manager i programu Visual Studio.

> [!NOTE]
> Adapter danych diagnostycznych emulacji sieci ma zastosowanie tylko do ustawień testów programu Visual Studio. Nie jest on używany dla ustawień testu w programie Microsoft Test Manager.

Należy użyć konta z uprawnieniami administratora dla emulacji sieci. Jeśli wybrano emulacji sieci dla roli lokalnej, który uruchamia testy ręczne, należy uruchomić program Microsoft Test Manager przy użyciu uprawnień administratora. Jeśli wybrano emulacji sieci dla żadnych innych ról, należy sprawdzić, czy agenta testowego na maszynie dla tej roli korzysta z konta użytkownika, który jest członkiem grupy Administratorzy. Aby uzyskać więcej informacji na temat sposobu konfigurowania konta dla agenta testowego, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

> [!NOTE]
> Konto Usługa sieciowa, która jest domyślne konto agenta testowego, nie jest członkiem grupy Administratorzy.

 **Emulacji sieci**

 Visual Studio będzie korzystać emulacji sieci opartych na oprogramowaniu dla wszystkich typów testu. W tym testów obciążenia. Emulacji sieci symuluje warunków sieciowych przez bezpośredniej pakietów sieciowych. Emulator sieci może emulować zachowanie przewodowej i bezprzewodowej sieci przy użyciu niezawodnych łącza fizycznego, takie jak Ethernet. Następujące atrybuty sieci są włączone do emulacji sieci:

-   Czasu Rundy sieci (opóźnienie)

-   Dostępna przepustowość

-   Zachowanie kolejkowania

-   Utraty pakietów

-   Ponowne porządkowanie pakietów

-   Błąd propagacji.

 Emulacji sieci, również zapewniają elastyczność filtrowanie pakietów sieciowych na podstawie adresów IP lub protokołów, takich jak TCP, UDP i protokołu ICMP.

 Można emulacji sieci opartych na sieci deweloperów i testerów emulować środowiska testowego żądaną, oceny wydajności, prognozowania wpływu zmiany lub podjąć decyzje dotyczące optymalizacji technologii. W porównaniu do łóżek testu sprzętu, emulacji sieci jest znacznie tańsze i bardziej elastyczne rozwiązania.

## <a name="configure-network-emulation-for-your-test-settings"></a>Konfiguracja funkcji emulacji sieci dla ustawień testu
 Przed wykonaniem kroków tej procedury należy otworzyć ustawień testu w programie Visual Studio, a następnie wybierz **danych i informacji diagnostycznych** strony.

### <a name="to-configure-network-emulation-for-your-test-settings"></a>Aby skonfigurować emulacji sieci dla ustawień testu

1.  Wybierz rolę, aby używać do emulowania określoną sieć.

    > [!NOTE]
    > Należy skonfigurować karty emulacja sieci tylko dla ról klienta lub roli serwera. Nie trzeba używać karty dla obu ról. Emuluje szum sieci, które ma wpływ na komunikację między obu ról, dzięki czemu nie trzeba używać jej na obu. Jeśli jest to konieczne, należy wybrać rolę klienta do karty emulacja sieci uniknąć dodatkowego obciążenia w roli serwera.

2.  Wybierz **emulacji sieci** , a następnie wybierz **Konfiguruj**.

     Zostanie wyświetlone okno dialogowe, aby skonfigurować emulacji sieci.

3.  Wybierz strzałkę obok pozycji **wybierz profil sieci**i wybierz typ sieci, który ma być emulować po uruchomieniu testu (na przykład **768Kps DSL kabel**).

    > [!WARNING]
    > Po uruchomieniu testów w rzeczywistych sieci, który jest typem wolniej niż sieci, w których są emulowanie testu będą nadal działać wolniej szybkością sieci. Emulacji można tylko spowolnić środowisko sieciowe, nie przyspieszenie działania.

4.  Jeśli zawierają adapter danych diagnostycznych emulacji sieci w ustawieniach testu i zamierzasz używać go na komputerze lokalnym, następnie użytkownik musi także powiązać sterownik emulacji sieci do jednej z kart sieciowych na komputerze. Sterownik emulacji sieci jest wymagana dla adaptera danych diagnostycznych emulacji sieci do funkcji. Sterownik emulacji sieci jest zainstalowany i powiązane z karty na dwa sposoby:

    -   **Sterownik emulacji sieci zainstalowane z Microsoft Visual Studio Test Agent:** Microsoft Visual Studio Test Agent może służyć na komputerze lokalnym i komputerach zdalnych. Po zainstalowaniu programu Visual Studio Test Agent proces instalacji obejmuje kroku konfiguracji, który wiąże sterownik emulacji sieci, do karty sieciowej. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

    -   **Sterownik emulacji sieci zainstalowane z Microsoft Visual Studio Test Professional:** użycie emulacji sieci po raz pierwszy, zostanie wyświetlony monit o sterownik emulacji sieci należy powiązać karty sieciowej.

    > [!TIP]
    > Można również zainstalować sterownik emulacji sieci z poziomu wiersza polecenia na komputerze lokalnym bez instalowania agenta testowego programu Visual Studio za pomocą następującego polecenia:   **/Install VSTestConfig NETWORKEMULATION**

## <a name="see-also"></a>Zobacz także

- [Zbierz informacje diagnostyczne przy użyciu ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)
- [Uruchom testy ręczne (VSTS)](/vsts/manual-test/getting-started/run-manual-tests)