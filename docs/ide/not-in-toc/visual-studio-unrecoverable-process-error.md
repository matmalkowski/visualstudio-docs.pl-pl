---
title: Błąd nieodwracalny proces programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/23/2017
ms.topic: conceptual
helpviewer_keywords:
- editor
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 37cb88b9a07728c2e8c263551e9f0aa2e750ec12
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# Błąd nieodwracalny proces programu Visual Studio

Visual Studio 2017 używa wielu procesów poza procesem do wykonania zadania w tle wymagane, takie jak testy jednostkowe na żywo, code analizatory i inne. Te procesy są uruchamiane poza procesem umożliwiają zalety wydajności programu Visual Studio, np. włączenie szybszym reagowaniu podczas wykonywania zadań intensywnie, długotrwałą programu Visual Studio. Ponieważ program Visual Studio jest proces 32-bitowy, uruchamianie poza procesem procesów daje również pracy intensywnie wykorzystujących pamięć większą przestrzeń pamięci działania.

Jeśli jakiegoś powodu któregoś z powyższych wymaga zakończenia procesów, pasek informacji wyskakujące pojawia się następujący komunikat o błędzie:

"Niestety, proces używany przez Visual Studio napotkał nieodwracalny błąd. Zalecamy zapisywanie Twojej pracy, a następnie zamknięcie i ponowne uruchomienie programu Visual Studio."

Ten komunikat zostanie wyświetlony, należy natychmiast Zapisz swoją pracę, a następnie zamknij i ponownie program Visual Studio. Jeśli nie zrobisz, Visual Studio może ulec awarii w dowolnej chwili.

## Lista procesów

Poniżej przedstawiono listę procesów poza procesem, używany przez Visual Studio, który musi być uruchomiony dla programu Visual Studio do poprawnego działania.

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
