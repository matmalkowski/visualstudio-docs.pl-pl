---
title: "Udoskonalanie jakości kodu z zasadami ewidencjonowania projektu zespołowego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 36e0ab96c1c0c3deeced62ff9808737c903e682b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Udoskonalanie jakości kodu z zasadami ewidencjowania projektu zespołowego

Korzystając z kontroli wersji typu Team Foundation (TFVC), można utworzyć zasady ewidencjonowania dla projektów zespołowych. Aby wymusić rozwiązań wywołujące lepsze kodu i bardziej wydajne programowanie grupy. Zasady ewidencjonowania są reguły, które są ustawione na poziomie projektu zespołowego i wymuszane na komputerach deweloperów, zanim będzie mógł zostać zaewidencjonowane kodu.

Można określić te zasadami projektu zespołowego Zaewidencjonuj:

- **Tworzy**: wymaga się, że podziały kompilacji, które zostały utworzone podczas kompilacji muszą zostać usunięte przed zaewidencjonowaniem nowe.

- **Komentarze zmian**: wymaga od użytkowników podania komentarz podczas ewidencjonowania zmian.

- **Analiza kodu**: wymaga uruchamiania analizy kodu przed zaewidencjonowaniem.

- **Elementy robocze**: wymaga skojarzone z wyboru — w co najmniej jednego elementu roboczego.

> [!IMPORTANT]
> Aby użyć zasad ewidencjonowania, musisz mieć połączenie do [!INCLUDE[vststfsLong](../code-quality/includes/vststfslong_md.md)].

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Zawartość pomocnicza|
|----------|------------------------|
|**Tworzenie i używanie zasad ewidencjonowania analizy kodu:** możesz wybrać spośród standardowego zestawu reguł analizy kodu, lub można utworzyć niestandardowy zestaw.|[Tworzenie zasad zaewidencjonowania analizy kodu i korzystanie z nich](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|

## <a name="related-tasks"></a>Tematy pokrewne

|Zadanie|Zawartość pomocnicza|
|----------|------------------------|
|**Użycie analizy kodu w procesie tworzenia:** członków zespołu przeprowadzanie analizy kodu na swoich komputerach programowanie. W programie Visual Studio, deweloperzy skonfigurować, uruchomić uruchomień analizy kodu dla kodu poszczególnych projektów, wyświetlać i analizować problemy znalezione przez uruchamia i tworzenie elementów roboczych dla ostrzeżenia.|[Analizowanie jakości aplikacji](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|
|**Tworzenie i Uruchamianie testów jednostkowych:** testów jednostkowych zapewniają deweloperów i testerów szybko wyszukać błędy logikę w metod klas w projektów C#, Visual Basic .NET i C++. Testu jednostkowego można utworzyć jeden raz i uruchamiać za każdym razem, że kod źródłowy jest zmieniana na upewnij się, że zostały wprowadzone nie błędy.|[Testowanie jednostek kodu](../test/unit-test-your-code.md)|
|**Śledzenie elementów pracy i wad:** elementów roboczych można użyć do śledzenia i zarządzanie służbowy i informacje o projekcie zespołowym. Element roboczy jest bazą danych rekord [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] używa do śledzenia przypisania i stan prac. Można użyć różnych typów elementów roboczych do śledzenia różne typy pracy, takich jak wymagania dotyczące klienta, usterki produktu i zadań związanych z projektowaniem.|[Elementy robocze (VSTS)](/vsts/work/work-items/index)|

## <a name="external-resources"></a>Zasoby zewnętrzne

[Testowanie pod kątem ciągłego dostarczania w programie Visual Studio 2012 — rozdział 2: testy jednostkowe: testowanie wewnątrz](http://go.microsoft.com/fwlink/?LinkID=255188)