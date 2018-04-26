---
title: Nieobsługiwane scenariusze debugowania w Projektancie przepływów pracy
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 2b876df1b7d997f3999c119d02abd593a88e6d5e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Nieobsługiwane scenariusze debugowania w Projektancie przepływów pracy

Projektant przepływu pracy w programie .NET Framework 4 dodano wiele nowych funkcji, ale nadal istnieją sytuacje debugowania, które nie obsługują.

Nieobsługiwany projektanta przepływów pracy debugowania scenariusze są następujące:

-   Wykonanie nie może być kontynuowane po kodu został zmodyfikowany.

-   Wykonanie nie może być kontynuowane z dowolnego punktu w przepływie pracy (Ustaw dalej).

-   Wykonanie nie może być kontynuowane aż do osiągnięcia kursora (Uruchom do kursora).

-   Projektant przepływu pracy nie może służyć do debugowania przepływów pracy tworzonych w kodzie bez użycia projektanta.

-   Nie można debugować przepływy pracy utworzone we wcześniejszych wersjach programu Windows Workflow Foundation (WF) w projektancie .NET Framework 4.

-   Punkty przerwania nie może być zdefiniowana w łączach między działaniami lub <xref:System.Activities.Statements.Flowchart> węzłów.

-   Schowek jest niedostępne podczas debugowania.

-   Punkty przerwania nie są zachowywane podczas działania są kopiowania i wklejania.

-   Nie można ustawić punktów przerwania przepływu pracy w oknie stosu wywołań.

-   Podczas tworzenia punktów przerwania w Projektancie **wiersza** i **znak** ustawienia w **nowego punktu przerwania** okna dialogowego nie są używane.

-   Menu okna lub skrótów punkt przerwania nie obsługuje następujących kolumn lub opcji debugowanie przepływu pracy:

    -   Warunek

    -   Liczba trafień

    -   Po trafieniu

    -   Funkcja

    -   Dane

    -   Proces

    -   Przejdź do dezasemblacji