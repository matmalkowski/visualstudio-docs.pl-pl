---
title: Powiąż kontrolera testów lub agenta testowego z kartą sieciową w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- controllers, netwrok adapter
- agents, configuring
- agents, network adapter
- controllers, configuring
ms.assetid: 7eb9290a-f9f6-4e41-9caa-796fcfaf0610
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 79aef9a4ad15f364df00dfd4ee6c7f1d7925c281
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter"></a>Porady: powiązanie kontrolera lub testowym agenta testowego z kartą sieciową

Jeśli na komputerze kontrolera testów lub zainstalowane oprogramowanie agenta testowego jest wiele kart sieciowych, należy określić adres IP zamiast nazwy komputera, aby zidentyfikować, że kontroler lub test agent testowy.

> [!WARNING]
> Podczas konfigurowania agenta testowego, zostanie zgłoszony następujący błąd:
>
> **Błąd 8110. Nie można połączyć się z komputerem określony kontroler lub uzyskać dostępu do obiektu kontrolera**
>
> Ten błąd może być spowodowany przez zainstalowanie na komputerze, który ma więcej niż jedną kartę sieciową z kontrolerem testów. Istnieje również możliwość pomyślnie zainstalować agentów, a nie widzieć ten problem, dopóki nie zostanie podjęta próba uruchomienia testu.

## <a name="binding-a-test-controller-to-a-specific-network-adapter"></a>Powiązanie kontrolera testu z określoną kartą sieciową

### <a name="to-obtain-the-ip-addresses-of-the-network-adapters"></a>Do uzyskiwania adresów IP kart sieciowych

1.  W systemie Microsoft Windows, wybrać **Start**, wybierz w **Rozpocznij wyszukiwanie** wpisz **cmd**, a następnie wybierz pozycję **Enter**.

2.  Typ **ipconfig/all**.

     Adresy IP dla karty sieciowe są wyświetlane. Zapisz adres IP karty sieciowej, które chcesz powiązać z kontrolera do.

### <a name="to-bind-a-network-adapter-to-a-test-controller"></a>Aby powiązać kartą sieciową z kontrolerem testu

1.  W systemie Microsoft Windows, wybrać **Start**, wybierz w **Rozpocznij wyszukiwanie** wpisz **services.msc**, a następnie wybierz pozycję **Enter**.

     **Usług** zostanie wyświetlone okno dialogowe.

2.  W okienku wyników w obszarze **nazwa** kolumny, kliknij prawym przyciskiem myszy **Visual Studio Test Controller** usługi, a następnie wybierz pozycję **zatrzymać**.

     —lub—

     Otwórz wiersz polecenia z podwyższonym poziomem uprawnień i uruchom następujące polecenie na polecenie:

     `net stop vsttcontroller`

3.  Otwórz *QTCcontroller.exe.config* znajduje się w pliku konfiguracji XML *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\\<edition>\Common7\IDE*.

4.  Zlokalizuj `<appSettings>` tagu.

    ```xml
    <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentConnectionTimeoutInSeconds" value="120"/>
      <add key="AgentSyncTimeoutInSeconds" value="300"/>
      <add key="ControllerServicePort" value="6901"/>
      <add key="ControllerUsersGroup" value="TeamTestControllerUsers"/>
      <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins"/>
      <add key="CreateTraceListener" value="no"/>
    </appSettings>
    ```

5.  Dodaj `BindTo` klawisz, aby określić, które kartę sieciową do użycia w `<appSettings>` sekcji.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6.  Uruchom usługę kontrolera testu. Aby to zrobić, uruchom następujące polecenie w wierszu polecenia:

    `net start vsttcontroller`

    > [!WARNING]
    > Należy uruchomić instalację agenta testowego ponownie, aby połączyć agenta testowego z kontrolerem. Teraz, podaj adres IP dla kontrolera zamiast nazwy kontrolera.

     Dotyczy to kontroler, Usługa agenta, a proces agenta. `BindTo` Musi być ustawiona właściwość dla każdego procesu, który jest uruchomiony na komputerze, który ma więcej niż jedną kartę sieciową. Procedury, aby ustawić `BindTo` właściwość jest taka sama dla wszystkich trzech procesów, określony wcześniej w tym temacie dla kontrolera testów.

### <a name="to-bind-a-network-interface-card-to-a-test-agent"></a>Aby powiązać agenta testowego do karty interfejsu sieciowego

1.  W systemie Microsoft Windows, wybrać **Start**, wybierz w **Rozpocznij wyszukiwanie** wpisz **services.msc**, a następnie wybierz pozycję **Enter**.

    **Usług** zostanie wyświetlone okno dialogowe.

2.  W okienku wyników w obszarze **nazwa** kolumny, kliknij prawym przyciskiem myszy **Visual Studio Test Agent** usługi, a następnie wybierz pozycję **zatrzymać**.

     —lub—

     Otwórz wiersz polecenia z podwyższonym poziomem uprawnień i uruchom następujące polecenie na polecenie:

     **polecenie net stop vsttagent**

3.  Otwórz *QTAgentService.exe.config* znajduje się w pliku konfiguracji XML *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\\<edition>\Common7\IDE*.

4.  Zlokalizuj `<appSettings>` tagu.

    ```xml
    <appSettings>
      <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentServicePort" value="6910"/>
      <add key="ControllerConnectionPeriodInSeconds" value="30"/>
      <add key="StopTestRunCallTimeoutInSeconds" value="120"/>
      <add key="CreateTraceListener" value="no"/>
      <add key="GetCollectorDataTimeout" value="300"/>
    </appSettings>  </appSettings>
    ```

5.  Dodaj `BindTo` klawisz, aby określić, które kartę sieciową do użycia w `<appSettings>` sekcji.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6.  Uruchom usługę agenta testowego. Aby to zrobić, uruchom następujące polecenie w wierszu polecenia:

    `net start vsttagent`

## <a name="see-also"></a>Zobacz także

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
- [Modyfikowanie ustawień logowania dla testu obciążenia](../test/modify-load-test-logging-settings.md)
- [Konfigurowanie portów dla kontrolerów testów i agentów testowych](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Porady: określanie maksymalnego rozmiaru pliku dziennika](../test/how-to-specify-the-maximum-size-for-the-log-file.md)
- [Porady: Określanie limitów czasu dla kontrolerów testów i agentów testowych](../test/how-to-specify-timeout-periods-for-test-controllers-and-test-agents.md)