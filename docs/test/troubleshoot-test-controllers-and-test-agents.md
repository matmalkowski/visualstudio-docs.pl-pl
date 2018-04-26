---
title: Rozwiązywanie problemów z kontrolerów testów i agentów testowych w Visual Studio
ms.date: 10/20/2016
ms.topic: troubleshooting
helpviewer_keywords:
- load tests, test controllers
- load tests, troubleshooting
- load tests, test agents
- troubleshooting, test controllers and agents in load tests
ms.assetid: 77329348-3a5d-43de-b6cb-90f93296a081
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: f218d571d8b747b5dfcfbe8c807d3a2779a99345
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="strategies-for-troubleshooting-test-controllers-and-test-agents-in-load-tests"></a>Strategie rozwiązywania problemów związanych z kontrolerami testów i agentami testowymi w testach obciążenia

W tym artykule omówiono niektóre typowe problemy, które mogą wystąpić podczas pracy z kontrolerów testów i agentów testowych w Visual Studio.

##  <a name="unable-to-collect-performance-counters-on-test-agent-computer"></a>Nie można zebrać liczników wydajności na komputerze agenta testowego

 Po uruchomieniu testu obciążenia może pojawić się błędy podczas próby połączenia z komputerem agenta testowego i zbierania liczników wydajności. Usługa Rejestr zdalny jest usługa odpowiedzialna za przekazywanie danych licznika wydajności z komputerem zdalnym. W niektórych systemach operacyjnych usługa Rejestr zdalny nie zostanie uruchomiona automatycznie. Aby rozwiązać ten problem, należy ręcznie uruchomić usługę Rejestr zdalny.

> [!NOTE]
> Można uzyskać dostępu do usługi Rejestr zdalny w **Panelu sterowania.** Wybierz **narzędzia administracyjne** , a następnie wybierz **usług**.


 Inną przyczyną tego problemu jest, że nie masz wystarczających uprawnień do odczytu liczników wydajności. Dla uruchomień testów lokalnego konto użytkownika, który jest uruchomiony test musi być członkiem grupy Użytkownicy zaawansowani lub wyższy lub być członkiem grupy Użytkownicy monitora wydajności. Zdalne testu jest uruchomiony, konto kontrolera jest skonfigurowany do uruchamiania jako musi być członkiem grupy Użytkownicy zaawansowani lub nowszej, lub być członkiem grupy Użytkownicy monitora wydajności.

## <a name="setting-the-logging-level-on-a-test-controller-computer"></a>Ustawienie poziomu rejestrowania na komputerze kontrolera testów
 Można kontrolować poziom rejestrowania na komputerze kontrolera testów. Jest to przydatne, gdy użytkownik próbuje zdiagnozować problem, po uruchomieniu testu obciążenia w środowisku.

### <a name="to-set-the-logging-level-on-a-test-controller-computer"></a>Aby ustawić poziom rejestrowania na komputerze kontrolera testów

1.  Zatrzymaj usługi kontrolera testu. W wierszu polecenia wpisz `net stop vsttcontroller`.

2.  Otwórz plik QTController.exe.config. Ten plik znajduje się w katalogu instalacyjnym kontrolera.

3.  Edytuj wpis dla `EqtTraceLevel` przełącznika w sekcji Diagnostyka systemu pliku. Kod powinien wyglądać następująco:

    ```
    <system.diagnostics>
        <trace autoflush="true" indentsize="4">
            <listeners>
                <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="d:\VSTestHost.log" />
            </listeners>
        </trace>
        <switches>
            <!-- You must use integral values for "value":
                    0 = off,
                    1 = error,
                    2 = warn,
                    3 = info,
                    4 = verbose. -->
            <add name="EqtTraceLevel" value="4" />
        </switches>
    </system.diagnostics>
    ```

4.  Zapisz plik.

5.  Uruchom usługę kontrolera. W wierszu polecenia wpisz `net start vsttcontroller`.

 Dotyczy to kontrolera testów, Usługa agenta testowego i procesu agenta testowego. Diagnozowanie problemów, jest przydatne włączyć rejestrowanie dla wszystkich trzech procesów. Procedury, aby ustawić poziom rejestrowania jest taka sama dla wszystkich trzech procesów, jak określone wcześniej dla kontrolera testów. Aby ustawić poziomy rejestrowania agenta testowego, usługi i procesu agenta, należy użyć następujących plików konfiguracji:

-   **QTController.exe.config** Conttoller usługi

-   **QTAgentService.exe.config** Usługa agenta

-   **.Exe.config QTDCAgent (32)** procesu karty danych agenta dla architektury 32-bitowych.

-   **.Exe.config QTDCAgent (64)** procesu karty danych agenta dla architektury 64-bitowym.

-   **.Exe.config QTAgent (32)** procesu agenta testowego dla architektury 32-bitowych.

-   **.Exe.config QTAgent (64)** procesu agenta testowego dla architektury 64-bitowym.

## <a name="binding-a-test-controller-to-a-network-adapter"></a>Wiązanie kontrolera testów z kartą sieciową
 Podczas konfigurowania agenta testowego, zostanie zgłoszony następujący błąd:

 **Błąd 8110. Nie można połączyć się z komputerem określony kontroler lub uzyskać dostępu do obiektu kontrolera.**

 Ten błąd może być spowodowany przez zainstalowanie na komputerze, który ma więcej niż jedną kartę sieciową z kontrolerem testów.

> [!NOTE]
> Istnieje również możliwość pomyślnego zainstalowania agentów testowych i nie zobaczyć ten problem, dopóki nie zostanie podjęta próba uruchomienia testu.


 Aby naprawić ten błąd, możesz powiązać kontrolera testu do jednej z kart sieciowych. Należy ustawić `BindTo` właściwość kontrolera testów, a następnie zmień agenta testowego do odwoływania się do kontrolera testów przez IP adresów zamiast według nazwy. Kroki są zawarte w poniższych procedur.

### <a name="to-obtain-the-ip-address-of-the-network-adapter"></a>Aby uzyskać adres IP karty sieciowej

1.  Wybierz **Start**, a następnie wybierz pozycję **Uruchom**.

     **Uruchom** zostanie wyświetlone okno dialogowe.

2.  Typ `cmd` , a następnie wybierz **OK**.

     Zostanie otwarty wiersz polecenia.

3.  Typ `ipconfig /all`.

     Adresy IP dla karty sieciowe są wyświetlane. Zapisz adres IP karty sieciowej, które chcesz powiązać z kontrolera do.

### <a name="to-bind-a-test-controller-to-a-network-adapter"></a>Aby powiązać kontrolera testów z kartą sieciową

1.  Zatrzymaj usługi kontrolera testu. W wierszu polecenia wpisz `net stop vsttcontroller`.

2.  Otwórz plik QTController.exe.config. Ten plik znajduje się w % ProgramFiles(x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE.

3.  Dodaj wpis dla `BindTo` właściwości do ustawień aplikacji. Określ adres IP karty sieciowej, które chcesz powiązać z kontrolerem na. Kod powinien wyglądać następująco:

    ```xml
    <appSettings>
        <add key="LogSizeLimitInMegs" value="20" />
        <add key="AgentSyncTimeoutInSeconds" value="120" />
        <add key="ControllerServicePort" value="6901" />
        <add key="ControllerUsersGroup" value="TeamTestControllerUsers" />
        <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins" />
        <add key="CreateTraceListener" value="no" />
        <add key="BindTo" value="<YOUR IP ADDRESS>" />
    </appSettings>
    ```

4.  Zapisz plik.

5.  Uruchom usługę kontrolera testu. W wierszu polecenia wpisz `net start vsttcontroller`.

### <a name="to-connect-a-test-agent-to-a-bound-controller"></a>Aby połączyć agenta testowego z kontrolerem powiązane

-   Uruchom ponownie instalację agenta testowego. Teraz, podaj adres IP dla kontrolera testów, zamiast nazwy kontrolera testu.

 Dotyczy to kontrolera testów, Usługa agenta testowego i procesu agenta testowego. `BindTo` Musi być ustawiona właściwość dla każdego procesu, który jest uruchomiony na komputerze, który ma więcej niż jedną kartę sieciową. Procedury, aby ustawić `BindTo` właściwość jest taka sama dla wszystkich trzech procesów, jak określone wcześniej dla kontrolera testów. Aby ustawić poziomy rejestrowania dla usługi agenta testowego i procesu agenta testowego, użyj pliki konfiguracyjne, które są wymienione w [ustawienie poziomu rejestrowania na komputerze kontrolera testów](#Logging).

## <a name="see-also"></a>Zobacz także

- [Kontrolerzy testów i agenci testowi](../test/configure-test-agents-and-controllers-for-load-tests.md)