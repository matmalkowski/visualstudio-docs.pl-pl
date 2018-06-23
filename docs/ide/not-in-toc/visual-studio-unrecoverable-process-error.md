---
title: Proces napotkał nieodwracalny błąd
ms.date: 06/22/2018
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ebd530b9db139cb232f735f7d6401199cab2f6fd
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325705"
---
# Błąd nieodwracalny proces programu Visual Studio

Visual Studio 2017 używa wielu procesów poza procesem do wykonania zadania w tle wymagane, takie jak testy jednostkowe na żywo, code analizatory i inne. Te procesy są uruchamiane poza procesem umożliwiają zalety wydajności programu Visual Studio, np. włączenie szybszym reagowaniu podczas długo, uruchamiania zadań intensywnie zasobów programu Visual Studio. Ponieważ program Visual Studio jest proces 32-bitowy, uruchamianie poza procesem procesów daje również pracy intensywnie wykorzystujących pamięć większą przestrzeń pamięci działania.

Jeśli *ServiceHub.RoslynCodeAnalysisService.exe* lub *ServiceHub.RoslynCodeAnalysisService32.exe* procesu jakiegoś powodu paska informacji wyskakujące pojawia się następujący komunikat o błędzie:

**"Niestety, proces używany przez Visual Studio napotkał nieodwracalny błąd. Zalecamy zapisywanie Twojej pracy, a następnie zamknięcie i ponowne uruchomienie programu Visual Studio."**

Ten komunikat zostanie wyświetlony, należy zapisać pracę i następnie zamknij i uruchom ponownie program Visual Studio.

## Lista procesów

Poniżej przedstawiono listę procesów poza procesem, używany przez Visual Studio. Ta lista jest tym procesy, które są uruchamiane w określonym przepływy pracy lub scenariuszy, a więc w większości przypadków te nie są wszystkie uruchomione w tym samym czasie.

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- PerfWatson2.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.VSDetouredHost.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- ServiceHub.RoslynCodeAnalysisService.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe
- WaAppAgent.exe

Jeśli dowolne z tych procesów zakończy się nieoczekiwanie, niektóre funkcje w programie Visual Studio przestanie działać. Dla niektórych procesów może być nieważny utratę funkcji. Dla innych osób dotyczy stabilności programu Visual Studio i jest wyświetlany komunikat o błędzie.