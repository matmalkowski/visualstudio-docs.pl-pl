---
title: "Błąd nieodwracalny proces programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/23/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords: editor
ms.assetid: 2263956f-3ae0-4bdc-9d3a-4991dfaf4ddb
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.openlocfilehash: 8750d16a485de062e66041e66e28fa591e957efd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe
- WaAppAgent.exe
