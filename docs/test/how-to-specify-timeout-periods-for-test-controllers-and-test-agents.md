---
title: Limitów czasu dla kontrolerów testów i agentów testowych w Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring
- agetns, timeouts
- controllers, configuring
- controllers, timeouts
ms.assetid: 777d0db5-0073-458a-a2a3-58b1c1f24c60
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 444c4e7214d55aad270a88325ee9e694e84987c6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31979051"
---
# <a name="how-to-specify-timeout-periods-for-test-controllers-and-test-agents"></a>Porady: określanie limitów czasu dla kontrolerów testów i agentów testowych

Zarówno kontrolera testów i agentem testowym ma kilka ustawienia limitu czasu, które określają, jak długo ma oczekiwać na odpowiedzi od siebie lub źródła danych przed niepowodzeniem z powodu błędu. W pewnych okolicznościach może być konieczne do edytowania wartości limitu czasu na potrzeby topologii lub inne problemy dotyczące środowiska. Aby edytować wartości limitu czasu, Edytuj plik konfiguracyjny XML, który jest skojarzony z kontrolerem testów lub agenta testowego, jak to opisano w następujących procedur.

 Aby edytować kontrolera testów lub różne ustawienia limitu czasu agenta testowego, zmodyfikuj następujące pliki konfiguracji przy użyciu nazwy klucza i wartości w tabeli:

-   Kontroler testów: QTController.exe.config

    |Nazwa klucza|Opis|Wartość|
    |--------------|-----------------|-----------|
    |AgentConnectionTimeoutInSeconds|Liczba sekund oczekiwania na żądanie ping agenta przed połączenie jest uznawane za utracone.|Liczba sekund "n".|
    |AgentSyncTimeoutInSeconds|Po rozpoczęciu synchronizacji uruchomienia testu, liczbę sekund oczekiwania na wszystkich agentów do synchronizacji przed przerwaniem uruchomienia.|Liczba sekund "n".|
    |AgentInitializeTimeout|Liczba sekund oczekiwania na wszystkich agentów i ich modułów zbierających dane, można zainicjować na początku testu uruchomić przed przerwaniem uruchomienia testu. Ta wartość powinna być rozsądnych dużych przy użyciu modułów zbierających dane.|Liczba sekund "n". Wartość domyślna: "120" (dwie minuty).|
    |AgentCleanupTimeout|Uruchom liczbę sekund oczekiwania na wszystkich agentów i ich modułów zbierających dane, aby wyczyścić przed ukończeniem testu. Ta wartość powinna być rozsądnych dużych przy użyciu modułów zbierających dane.|Liczba sekund "n". Wartość domyślna: "120" (dwie minuty).|

-   Test Agent: QTAgentService.exe.config

    |Nazwa klucza|Opis|Wartość|
    |--------------|-----------------|-----------|
    |ControllerConnectionPeriodInSeconds|Liczba sekund między próbuje połączyć się z kontrolerem.|Liczba sekund "n". Wartość domyślna: "30" (30 sekund).|
    |RemotingTimeoutSeconds|Maksymalny czas w sekundach trwają wywołaniem funkcji zdalnych.|Liczba sekund "n". Wartość domyślna: "600" (dziesięć minut).|
    |StopTestRunCallTimeoutInSeconds|Liczba sekund oczekiwania na połączenie się zatrzymanie uruchomienia testu.|Liczba sekund "n". Wartość domyślna: "120" (dwie minuty).|
    |GetCollectorDataTimeout|Liczba sekund oczekiwania modułów zbierających dane.|Liczba sekund "n". Wartość domyślna: "300" (pięć minut).|

## <a name="to-specify-agent-timeout-options-for-a-test-controller"></a>Aby określić opcje limitu czasu agenta dla kontrolera testów

1. Otwórz plik konfiguracji QTCcontroller.exe.config XML znajduje się w lokalizacji % ProgramFiles(x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE.

2. Zlokalizuj `<appSettings>` tagu.

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

3. Edytuj istniejącą wartość dla jednego z kluczy limitu czasu kontrolera testów. Na przykład można zmienić wartość domyślną dla klucza `AgentConnectionTimeoutInSeconds` z dwóch minut trzy minuty:

    ```xml
    <add key="AgentConnectionTimeoutInSeconds" value="180"/>
    ```

    —lub—

    Dodaj dodatkowe klucza i określ wartość limitu czasu. Na przykład można dodać `AgentInitializeTimeout` klucza w `<appSettings>` sekcji i określ wartość pięciu minut:

    ```xml
    <appSettings>
            <add key="AgentInitializeTimeout" value="300"/>
    </appSettings>
    ```

## <a name="to-specify-agent-timeout-options-for-a-test-agent"></a>Aby określić opcje limitu czasu agenta dla agenta testowego

1. Otwórz plik konfiguracji QTAgentService.exe.config XML znajduje się w lokalizacji % ProgramFiles(x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE.

2. Zlokalizuj `<appSettings>` tagu.

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

3. Edytuj istniejącą wartość dla jednego z kluczy limitu czasu agenta testowego. Na przykład można zmienić wartość domyślną dla klucza `ControllerConnectionPeriodInSeconds` od 30 sekund na jedną minutę:

    ```xml
    <add key="ControllerConnectionPeriodInSeconds" value="60"/>
    ```

    —lub—

    Dodaj dodatkowe klucza i określ wartość limitu czasu. Na przykład można dodać `RemotingTimeoutSeconds` klucza w `<appSettings>` sekcji i określ wartość 15 minut:

    ```xml
    <appSettings>
            <add key=" RemotingTimeoutSeconds " value="900"/>
    </appSettings>
    ```

## <a name="see-also"></a>Zobacz także

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
- [Modyfikowanie ustawień logowania dla testu obciążenia](../test/modify-load-test-logging-settings.md)
- [Konfigurowanie portów dla kontrolerów testów i agentów testowych](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Porady: określanie maksymalnego rozmiaru pliku dziennika](../test/how-to-specify-the-maximum-size-for-the-log-file.md)
- [Porady: powiązanie kontrolera testów lub agenta testowego z kartą sieciową](../test/how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter.md)