---
title: Projektant przepływu pracy — wywoływania debugera programu Visual Studio dla programu Windows Workflow Foundation (starsze)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- stepping
- Step Over command
- stepping, commands
- debugging, using workflow debugger
- workflows, debugger
- workflow debugger, starting
- Step In command
- debugger, workflow
- Step Out command
- debugging workflows, starting the debugger
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a326f8b6dc482c2adfc2caba797c38094a99f8c5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976422"
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Wywoływanie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsze)

W tym temacie opisano sposób debugowanie aplikacji Windows Workflow Foundation (WF) w starszej wersji projektanta przepływów pracy systemu Windows przy użyciu debuger programu Visual Studio. Starsze projektanta przepływów pracy należy używać wtedy, gdy konieczne objęcie .NET Framework w wersji 3.5 lub WinFX.

Ogólnie rzecz biorąc można debugowania starszych przepływów pracy, tak samo, jak debugować programów napisanych w innych językach programowania Visual Studio. Można uruchomić programu Visual Studio Debugger dla systemu Windows Workflow Foundation w następujący sposób:

-   Wybierz **dołączyć do procesu** na **debugowania** menu, aby wybrać działającego wystąpienia przepływu pracy z dostępnych procesów.

-   Naciśnij klawisz **F5** uruchomione wystąpienie przepływu pracy lub kontynuować działanie po został trafiony punkt przerwania.

## <a name="stepping-through-code"></a>Krokowe wykonywanie kodu

Debuger obsługuje jedną z najbardziej typowych procedur debugowania, wykonywanie krok po kroku, który jest wykonywany jednego wiersza kodu w czasie. Istnieją trzy polecenia krokowe wykonywanie kodu:

-   **Krok w**: można przejść do działania przy użyciu **F11**. Kroki debugera do dowolnego obsługi, który jest zdefiniowany. Jeśli obsługa nie jest zdefiniowana, Przekrocz nad działania lub z działań złożonych, które zawierają inne działania, Wkrocz pierwszy wykonywanego działania. Wykonywanie krok po kroku do programów obsługi kodu w projektancie nie jest obsługiwane dla następujących działań: **IfElseActivity**, **Działanie WhileActivity**, **grupy ConditionedActivityGroup**, lub **Działanie ReplicatorActivity**. Aby debugować obsługi skojarzone z tych działań, możesz umieścić jawne punkty przerwania w kodzie.

-   **Step Out**: można wychodzenia z działania przy użyciu **Shift F11**. Wykonywanie krok po kroku, poza działanie uruchamia bieżące działanie i jego element równorzędny działania do zakończenia. Debuger następnie dzieli na nadrzędnego bieżącego działania. Przy przechodzeniu z obsługi kodu, debuger dzieli się na działania, z którym jest skojarzony program obsługi.

-   **Step Over**: można Przekrocz nad działania przy użyciu **F10**. Przy przechodzeniu przez działania złożonego. Debuger dzieli na pierwszy element podrzędny wykonywalnego działania złożonego. Przy przechodzeniu przez z systemem innym niż złożone, takich jak **z typu CodeActivity** działania, debuger wykonuje działanie i jego skojarzony programów obsługi i podziału na następne działanie. Działania, która jest wykonywana w przypadku ostatniego działania podrzędne działania złożonego, następnie po wykonaniu debuger dzieli na działania nadrzędnego.

## <a name="attaching-to-a-process"></a>Dołączanie do procesu
 Aby debugować przepływ pracy przez dołączenie do procesu, wybierz proces dostępne z **dostępne procesy** pole listy w **dołączyć do procesu** okno dialogowe. Jeśli **automatycznego: kod przepływu pracy** nie jest wyświetlana w **dołączyć do** tekstu, a następnie kliknij przycisk **wybierz**. W **wybór typu kodu** okno dialogowe, kliknij przycisk **Debuguj te typy kodu** i wybierz **przepływu pracy**. Następnie kliknij przycisk **OK** i kliknij przycisk **Attach**.

## <a name="debugging-with-f5"></a>Debugowanie za pomocą F5
 Jeśli aplikacja hosta przepływu pracy i przepływ pracy DLL znajdują się w różnych projektów programu Visual Studio, na przykład, korzystając z biblioteki działań przepływów pracy, musisz ustawić projektu biblioteki DLL przepływu pracy jako projekt startowy rozwiązania Visual Studio, aby debugować przepływ pracy przy użyciu **F5**. Należy także ustawić ścieżkę do aplikacji hosta w projekcie DLL przepływu pracy **uruchomienia programu zewnętrznego** właściwości.

 Aby skonfigurować projekt startowy w Eksploratorze rozwiązań, kliknij prawym przyciskiem myszy nazwę projektu i wybierz **Ustaw jako projekt startowy**. Aby ustawić ścieżkę do hosta w **uruchomienia programu zewnętrznego** właściwości, kliknij dwukrotnie plik projektu przepływu pracy **właściwości** węzła w Eksploratorze rozwiązań i wybierz **debugowania** Karta. W obszarze **Akcja uruchamiania**, wybierz pozycję **uruchomienia programu zewnętrznego** i wprowadź ścieżkę do pliku .exe, który jest hostem chcesz debugować przepływ pracy.

 Jeśli aplikacja hosta jest ustawiony jako projekt startowy, tylko debuger programu Visual Studio jest wywoływany do debugowania. Nie można wywołać programu Visual Studio Debugger dla systemu Windows Workflow Foundation Jeśli używany jest debuger programu Visual Studio, tylko języka C# lub punktów przerwania kodu języka Visual Basic są osiągane; nie są osiągane punktów przerwania ustawionych w Projektancie przepływów pracy. Na przykład punkt przerwania ustawiony na <xref:System.Workflow.Activities.ParallelActivity> działania w Projektancie zostaje trafiony użycie programu Visual Studio Debugger dla systemu Windows Workflow Foundation, ale nie w przypadku, gdy używasz debuger programu Visual Studio.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Ustawianie punktów przerwania w przepływach pracy (starsza wersja)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)
- [Debugowanie starszych wersji przepływów pracy](../workflow-designer/debugging-legacy-workflows.md)