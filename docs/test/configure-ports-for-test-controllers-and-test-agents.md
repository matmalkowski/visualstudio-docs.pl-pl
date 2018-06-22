---
title: Konfigurowanie portów dla kontrolerów testów i agentów testowych w Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- firewalls, configuring for test agents
- firewalls, configuring for test controllers
- test agents, firewalls
- test controllers, firewalls
- agents, firewalls
- controllers, firewalls
ms.assetid: 211edbd7-9fe4-4251-ba85-8bec4363261b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 9f41e372f6c75e10ebf4d66fcd68eb4652b02f0f
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2018
ms.locfileid: "36296296"
---
# <a name="configure-ports-for-test-controllers-and-test-agents"></a>Konfigurowanie portów dla kontrolerów testów i agenci testowi

Można zmienić domyślne porty przychodzące używany przez kontrolera testu, agenta testowego i klienta. Może to być konieczne, jeśli chcesz korzystać z kontrolera testów, agenta testowego lub klienta razem niektóre inne oprogramowanie powodujące konflikt z ustawieniami portu. Kolejny powód, aby zmienić porty wynika z ograniczeń zapory między kontrolerem testów i klienta. W takim przypadku można ręcznie skonfigurować port umożliwiających włączenie zaporę, tak, aby kontroler testów może wysyłać wyniki do klienta.

 Na poniższej ilustracji przedstawiono punkty połączenia między kontrolerem testów, agenta testowego i klienta. Opisano go, które porty są używane dla połączeń przychodzących i wychodzących, a także ograniczenia zabezpieczeń używane na tych portach.

 ![Testowanie sterownika i przetestuj agenta portów i zabezpieczeń](../test/media/test-controller-agent-firewall.png)

## <a name="incoming-connections"></a>Połączenia przychodzące

Domyślny port używany przez kontrolera testu jest 6901 i agenta testowego domyślny port to 6910. Klient korzysta z portu losowe domyślnie, który jest używany do odbierania wyników testu z kontrolera testów. W przypadku wszystkich połączeń przychodzących kontrolera testów uwierzytelnia strony i sprawdza, czy należy do określonej grupy zabezpieczeń.

- **Kontroler testów** są połączenia przychodzące na porcie TCP 6901. Jeśli zachodzi potrzeba, można skonfigurować port przychodzący. Aby uzyskać więcej informacji, zobacz [skonfigurować porty przychodzące](#configure-the-incoming-ports).

    Kontroler testów musi mieć możliwość połączenia wychodzącego do agenci testowi i do klienta.

    > [!NOTE]
    > Kontroler testów musi przychodzące **plików i drukarek udostępnianie** otwarte połączenia.

- **Agent testowy** są połączenia przychodzące na porcie TCP 6910. Jeśli zachodzi potrzeba, można skonfigurować port przychodzący. Aby uzyskać więcej informacji, zobacz [skonfigurować porty przychodzące](#configure-the-incoming-ports).

   Agent testowy musi mieć możliwość połączenia wychodzące z kontrolerem testów.

- **Klient** domyślnie losowy port TCP jest używany dla połączeń przychodzących. Jeśli zachodzi potrzeba, można skonfigurować port przychodzący. Aby uzyskać więcej informacji, zobacz [skonfigurować porty przychodzące](#configure-the-incoming-ports).

   Kontroler testów próba nawiązania połączenia czas klienta pierwszy, mogą otrzymywać powiadomień zapory.

   W systemie Windows Server 2008, powiadomienia zapory są domyślnie wyłączone i należy ręcznie dodać wyjątki zapory dla programów klienckich (*devenv.exe*, *mstest.exe*, *mlm.exe*) tak, aby umożliwić akceptowanie połączeń przychodzących.

## <a name="outgoing-connections"></a>Połączenia wychodzące

Losowe porty TCP są używane dla wszystkich połączeń wychodzących.

- **Kontroler testów** kontrolera testu musi mieć możliwość połączenia wychodzące do agentów i do klienta.

- **Agent testowy** agenta testowego musi mieć możliwość połączenia wychodzące do kontrolera.

- **Klient** klient musi mieć możliwość połączenia wychodzące do kontrolera.

## <a name="configure-the-incoming-ports"></a>Konfigurowanie portów przychodzących

Wykonaj te kroki, aby skonfigurować porty dla kontrolera testów i agenci testowi.

- **Usługa kontrolera** zmodyfikować wartość portu, edytując *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config* pliku:

    ```xml
    <appSettings>
      <add key="ControllerServicePort" value="6901"/>
    </appSettings>
    ```

- **Usługa agenta** zmodyfikować, edytując port *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTAgentService.exe.config* pliku:

    ```xml
    <appSettings>
      <add key="AgentServicePort" value="6910"/>
    </appSettings>
    ```

- **Klient** Edytor rejestru i dodaj następującą w rejestrze (**DWORD**) wartości. Klient użyje jeden z portów z określonego zakresu przy odbieraniu danych z kontrolera testów:

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeStart**

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeEnd**

## <a name="see-also"></a>Zobacz także

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)