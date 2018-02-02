---
title: "Instalowanie i konfigurowanie agentów testowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configure test agents, test lab
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 5caa566e15f7f3c4c69f8d33a6c7dd0eead38785
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="install-and-configure-test-agents"></a>Instalowanie i konfigurowanie agentów testowych

Scenariusze testowania przy użyciu programu Visual Studio i Visual Studio Team Services lub Team Foundation Server (TFS) nie będzie potrzebna kontrolera testów, ponieważ agentów programu Microsoft Visual Studio obsługi aranżacji komunikując się z Team Services lub TFS. Na przykład uruchamiania ciągłego testów z kompilacji i wydania przepływów pracy w programie Team Services lub TFS.

Jeśli potrzebujesz agentem testowym lub kontrolera testu do pracy z programem TFS 2013, korzystania z agentów dla programu Microsoft Visual Studio 2013 Update 5 i konfigurowania kontrolera testu.

Należy również rozważyć Jeśli będzie można łatwiej [zamiast tego użyj kompilacji lub zarządzania zleceniami](use-build-or-rm-instead-of-lab-management.md).

## <a name="what-do-i-need"></a>Co jest potrzebne?

**Gdzie uzyskać kontrolera testów i agenci testowi**

* Jeśli są uruchomione testy za pomocą zadań vNext kompilacji i chcesz zainstalować agentów z katalogiem lokalnym- 

  * [Pobierz agentów dla programu Microsoft Visual Studio 2015 RTM oraz Update 1](http://go.microsoft.com/fwlink/p/?LinkId=619266). 

  * [Pobierz agentów dla programu Microsoft Visual Studio 2017 i Visual Studio 2015 Update 2](https://www.visualstudio.com/downloads/download-visual-studio-vs) — wybierz **Tools for Visual Studio 2015** , a następnie wybierz **Agents for Visual Studio 2015** z lewej strony pasek nawigacyjny.

* [Pobierz agentów dla programu Microsoft Visual Studio 2013 Update 5](http://go.microsoft.com/fwlink/p/?LinkId=619264), jeśli chcesz uruchomić:

  * Załaduj testy za pomocą lokalnych komputerów zdalnych.

  * Ciągłe testy zdalnie przy użyciu ustawień programu Microsoft Test Manager lub MSTest i testu dla testów laboratoryjnych środowiska.

  * Ciągłe testów za pomocą TFS 2013.

Te pliki instalacyjne są dostępne jako pliki ISO (wirtualny dysk CD) prosta instalacja na maszynach wirtualnych. 

[Czy można mieszać wersji TFS, program Microsoft Test Manager, kontrolera testów i agenta testowego?](#MixedVersions)

**Jakie wymagania systemowe należy zainstalować agentów kontrolera i testowania testu?**

| Element | Wymagania |
| ---- | ------------ |
| **Agent** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 z dodatkiem Service Pack 1<br />Dodatek Service Pack 3 dla systemu Windows XP<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 Release 2 z dodatkiem Service Pack 1 |
| **Kontrolera** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 z dodatkiem Service Pack 1<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 Release 2 z dodatkiem Service Pack 1 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="q--a"></a>Pytania i odpowiedzi

<!-- BEGINSECTION class="m-qanda" -->

<a name="MixedVersions"></a>

####<a name="q-can-i-mix-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>Pytanie: czy można mieszać wersji TFS, program Microsoft Test Manager, kontrolera testów i agenta testowego?

A: tak, w tym miejscu są zgodne i obsługiwane kombinacje:

| TFS | Program Microsoft Test Manager z Centrum laboratoryjnym | Kontrolera | Agent |
| --- | -------------------------------------- | ---------- | ----- |
| 2015: uaktualnianie z 2013 | 2013 | 2013 |2013 |
| 2015: instalacja nowego | 2013 | 2013 | 2013 |
| 2015: instalacji lub uaktualniania z 2013 | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

####<a name="q-will-the-test-agent-2015-support-all-the-scenarios-supported-by-test-controller-and-test-agent-of-visual-studio-2013"></a>Pytanie: Test Agent 2015 wspiera wszystkich scenariuszy obsługiwanych przez kontroler testów i Test Agent programu Visual Studio 2013?

Odpowiedź: Firma Microsoft zaleca się, że używasz agentów dla programu Visual Studio w wszystkie nowe automatycznego testowania scenariuszy. Zadanie wdrażania agentów testu definicji kompilacji umożliwia pobieranie i instalowanie agentów testowych na tym komputerze.
W poniższej tabeli przedstawiono scenariusze obsługiwane przez agentów programu Visual Studio 2013 i opis rozwiązań alternatywnych dla Team Foundation Server (TFS) 2015 i zespołu usług (TS).

| Scenariusze obsługiwane przez agentów dla programu Visual Studio 2013 | Zamiast w programie TFS i usług terminalowych |
| --- | --- |
| Przepływ pracy kompilacja-wdrażanie-testy w programie Visual Studio | Użytkownicy mogą używać [definicji kompilacji](https://www.visualstudio.com/team-services/continuous-integration/) (nie kompilacji XAML) dla kompilacji, wdrożyć i przetestować scenariusze w programie TFS. |
| Obciążenia testowania (testowanie wydajności) przy użyciu lokalnych komputerach zdalnych | Test Controller i testowanie agentów 2013 aktualizacji 5 umożliwia obciążenia testy lokalnie. [Więcej informacji](https://msdn.microsoft.com/library/ff400223.aspx). |
| Zdalne wykonywanie testów automatycznych z Microsoft Test Manager za pomocą środowiska laboratoryjnego | Obecnie nie istnieje alternatywa dla tego scenariusza. Firma Microsoft zaleca zadanie Uruchom testy funkcjonalne służy w kompilacji i wydania definicje (nie w kompilacji XAML) można zdalnie wykonać testy. |
| Deweloperzy zdalnego testy są wykonywane w programie Visual Studio | Nie jest już obsługiwana. |

<!-- ENDSECTION -->

## <a name="see-also"></a>Zobacz także

* [Konfigurowanie maszyn i zbierania informacji diagnostycznych przy użyciu ustawień testów](https://msdn.microsoft.com/library/dd286743%28v=vs.140%29.aspx)
