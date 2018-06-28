---
title: Instalowanie agentów testowych i kontrolery testów dla programu Visual Studio
ms.date: 03/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- configure test agents, test lab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09d48461d46153731d66844080cb35aa1135d17c
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056981"
---
# <a name="install-test-agents-and-test-controllers"></a>Instalowanie agentów testowych i kontrolerów testów

Scenariusze testowania, korzystających z programu Visual Studio i Visual Studio Team Services (VSTS) lub Team Foundation Server (TFS) nie trzeba kontrolera testów. Agents for Visual Studio obsługują aranżacji komunikując się z programu VSTS lub TFS. Scenariusz można uruchomić ciągłego testów dla kompilacji, a następnie zwolnij przepływów pracy programu VSTS lub TFS.

Można także rozważyć czy lepiej używać jest [kompilacji lub zarządzania zleceniami](use-build-or-rm-instead-of-lab-management.md) zamiast zarządzania laboratorium.

## <a name="system-requirements"></a>Wymagania systemowe

| Element | Wymagania |
| ---- | ------------ |
| **Agent** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 z dodatkiem Service Pack 1<br />Dodatek Service Pack 3 dla systemu Windows XP<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 Release 2 z dodatkiem Service Pack 1 |
| **Kontrolera** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 z dodatkiem Service Pack 1<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 Release 2 z dodatkiem Service Pack 1 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="install-the-test-controller-and-test-agents"></a>Zainstaluj test controller i agenci testowi

Możesz pobrać agentów dla programu Visual Studio 2017 z [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?q=agents). Przewiń do dołu strony i poszukaj *Agents for Visual Studio 2017*. Wybierz opcję *agenta* lub *kontrolera*, a następnie wybierz pozycję *Pobierz*. Uruchom pobrany plik wykonywalny, aby zainstalować agenta testowego lub kontrolera.

Możesz pobrać agentów dla programu Visual Studio 2015 i Visual Studio 2013 z [starsze pliki do pobrania](https://visualstudio.microsoft.com/vs/older-downloads/) strony.

Te pliki instalacyjne są dostępne w postaci plików ISO prosta instalacja na maszynach wirtualnych.

## <a name="compatible-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>Niezgodne wersje TFS, program Microsoft Test Manager, kontrolera testów i agent testowy

Różne wersje programu TFS, Microsoft Test Manager (MTM) kontroler testów i agent testowy może mieszać zgodnie z poniższą tabelą:

| TFS | MTM z Centrum laboratoryjnym | Kontrolera | Agent |
| --- | -------------------------------------- | ---------- | ----- |
| 2017: instalacji lub uaktualniania z 2015 | 2017 | 2017 | 2017 |
| 2017: instalacji lub uaktualniania z 2015 | 2017 | 2013 Update 5 | 2013 Update 5 |
| 2017: instalacji lub uaktualniania z 2015 | 2015 | 2013 Update 5 | 2013 Update 5 |
| 2015: uaktualnianie z 2013 | 2013 | 2013 |2013 |
| 2015: instalacja nowego | 2013 | 2013 | 2013 |
| 2015: instalacji lub uaktualniania z 2013 | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

## <a name="upgrade-from-visual-studio-2013-test-agents"></a>Uaktualnienie agentów testowych programu Visual Studio 2013

Zalecane jest użycie agentów dla programu Visual Studio w ramach wszystkich nowych scenariuszy testowania automatycznych. Można użyć *wdrażania agentów Test* zadania w definicji kompilacji, aby pobrać i zainstalować agentów testowych na tym komputerze.

W poniższej tabeli przedstawiono scenariusze obsługiwane przez agentów dla programu Visual Studio 2013 i alternatywy dla Team Foundation Server (TFS) 2015 i VSTS:

| Scenariusze obsługiwane przez agentów dla programu Visual Studio 2013 | Zamiast w programie TFS i programu VSTS |
| --- | --- |
| Przepływ pracy kompilacja-wdrażanie-testy w programie Visual Studio | Użytkownicy mogą używać [definicji kompilacji](/vsts/build-release/) (nie kompilacji XAML) dla kompilacji, wdrożyć i przetestować scenariusze w programie TFS. |
| Obciążenia testowania (testowanie wydajności) przy użyciu lokalnych komputerach zdalnych | Użyj kontrolera testów i Test agentów 2013 aktualizacji 5 obciążenia testy lokalnie. |
| Zdalne wykonywanie testów automatycznych z Microsoft Test Manager za pomocą środowiska laboratoryjnego | Obecnie nie istnieje alternatywa dla tego scenariusza. Firma Microsoft zaleca zadanie Uruchom testy funkcjonalne służy w kompilacji i wydania definicje (nie w kompilacji XAML) można zdalnie wykonać testy. |
| Deweloperzy zdalnego testy są wykonywane w programie Visual Studio | Nie jest już obsługiwana. |
