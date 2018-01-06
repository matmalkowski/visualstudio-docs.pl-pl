---
title: "Nieobsługiwane scenariusze w Projektancie przepływów pracy debugowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
caps.latest.revision: "4"
ms.author: sdanie
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 79dfcd15a49b40f1473966e815ddb904c1d7f8f1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Nieobsługiwane scenariusze debugowania w Projektancie przepływów pracy
Projektant przepływu pracy w [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] dodano wiele nowych funkcji, ale nadal istnieją sytuacje debugowania, które nie obsługują. Ten dokument zawiera szczegóły dotyczące debugowania scenariusze nieobsługiwane projektanta przepływów pracy.  
  
-   Wykonanie nie może być kontynuowane po kodu został zmodyfikowany.  
  
-   Wykonanie nie może być kontynuowane z dowolnego punktu w przepływie pracy (Ustaw dalej).  
  
-   Wykonanie nie może być kontynuowane aż do osiągnięcia kursora (Uruchom do kursora).  
  
-   Projektant przepływu pracy nie może służyć do debugowania przepływów pracy tworzonych w kodzie bez użycia projektanta.  
  
-   Przepływy pracy utworzone we wcześniejszych wersjach [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] nie można debugować w [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] projektanta.  
  
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