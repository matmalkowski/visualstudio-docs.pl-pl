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
ms.openlocfilehash: 29329cb1403745b80d68670f5316ce570582d72c
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39379400"
---
# <a name="how-to-specify-the-maximum-size-for-the-log-file-for-load-tests"></a>Porady: określanie maksymalnego rozmiaru pliku dziennika dla testów obciążenia

Domyślnie maksymalny rozmiar pliku dziennika, który jest używany do testów obciążenia jest równa 20 megabajtów. Tę wartość można zmienić, edytując plik konfiguracyjny skojarzony z usługą kontrolera.

## <a name="specify-the-maximum-log-file-size-for-load-test"></a>Określ maksymalny rozmiar pliku dziennika dla testu obciążenia

1.  Otwórz *QTCcontroller.exe.config* plik konfiguracyjny XML znajdujący się w *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config*.

2.  Znajdź `<add key="LogSizeLimitInMegs" value="20"/>` wpis w `<appSettings>` tagu.

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

3.  Modyfikowanie `value ="20"` rozmiar maksymalny dopuszczalny rozmiar, aby określić plik dziennika.

    > [!NOTE]
    > Wprowadzenie wartości "0" Określa, że plik dziennika jest ograniczony tylko w rozmiarze przez dostępne miejsce na dysku.

## <a name="see-also"></a>Zobacz także

- [Modyfikowanie ustawień rejestrowania testu obciążeniowego](../test/modify-load-test-logging-settings.md)
- [Konfigurowanie portów dla kontrolerów testów i agentów testowych](../test/configure-ports-for-test-controllers-and-test-agents.md)