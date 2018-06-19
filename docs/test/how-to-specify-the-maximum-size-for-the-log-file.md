---
title: Rozmiar pliku dziennika dla testów obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging
ms.assetid: 417059bf-37ae-4e7a-b9b0-29bd71f1414f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 7faf5402f495eefe64000c67048bcb85c9197388
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31965089"
---
# <a name="how-to-specify-the-maximum-size-for-the-log-file-for-load-tests"></a>Porady: określanie maksymalnego rozmiaru pliku dziennika dla testów obciążenia

Domyślnie maksymalny rozmiar pliku dziennika, który jest używany do testów obciążenia wynosi 20 MB. Tę wartość można zmienić, edytując plik konfiguracyjny skojarzony z usługą kontrolera.

## <a name="specify-the-maximum-log-file-size-for-load-test"></a>Określ maksymalny rozmiar pliku dziennika dla testu obciążenia

1.  Otwórz *QTCcontroller.exe.config* znajduje się w % ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config pliku konfiguracji XML.

2.  Zlokalizuj `<add key="LogSizeLimitInMegs" value="20"/>` wpis w `<appSettings>` tagu.

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

3.  Modyfikowanie `value ="20"` do maksymalny dozwolony rozmiar chcesz określić, czy w pliku dziennika.

    > [!NOTE]
    > Wprowadzenie wartości "0" Określa, czy plik dziennika jest ograniczona tylko rozmiar przez dostępnego miejsca na dysku.

## <a name="see-also"></a>Zobacz także

- [Modyfikowanie ustawień logowania dla testu obciążenia](../test/modify-load-test-logging-settings.md)
- [Konfigurowanie portów dla kontrolerów testów i agentów testowych](../test/configure-ports-for-test-controllers-and-test-agents.md)