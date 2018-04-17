---
title: 'Porady: Ustawianie punktów przerwania w przepływach pracy (starsze) | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 71d62395a4b719827cf33eacad46a650bd057c43
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Porady: Ustawianie punktów przerwania w przepływach pracy (starsze)
W tym temacie opisano, jak można ustawić punktów przerwania w [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] kompilacji aplikacji za pomocą projektanta przepływów pracy programu starszej wersji systemu Windows. Użyj starszego [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] gdy Twoje [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] aplikacja musi docelowy: [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] lub [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Jeśli używasz starszego [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] w [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] do tworzenia [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] aplikacji, można ustawić punktów przerwania w kodzie C# i Visual Basic, jak w programie Visual Studio. Zgodnie z oczekiwaniami, w każdym punkcie przerwania ustawionych powoduje zatrzymanie wykonywania przepływu pracy.

 Punkt przerwania ma trzy stany: *oczekujące*, *powiązany*, i *błąd*. Po ustawieniu punkt przerwania jest oczekujące i jest reprezentowany przez pusty czerwona ikona. Po załadowaniu typu przepływu pracy środowiska uruchomieniowego związane i jest reprezentowany przez stałe czerwona ikona. Jeśli określisz niepoprawny format dla punktu przerwania, podobnie jak w przypadku nazwy działania, która nie jest prawidłowy, pojawi się okno błędu. Punkt przerwania nadal został dodany do okna punkt przerwania, ale jest on oznaczony małą "x".

 Punkty przerwania w działaniu na powierzchni projektu przepływu pracy można ustawić w następujący sposób:

-   Kliknij działanie prawym przyciskiem myszy i wybierz **punktu przerwania \ wstawić punktu przerwania**.

-   Wybierz działanie, a następnie naciśnij klawisz F9.

-   Wybierz **nowego punktu przerwania** z **debugowania** menu.

     Można także użyć tej opcji, aby ustawić nowego punktu przerwania podczas debugowania, po zatrzymaniu debugera w punkcie przerwania.

    > [!NOTE]
    > Ustawianie punktów przerwania w przepływach pracy wywoływanego nie jest obsługiwane.

### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>Aby ustawić punkt przerwania przy użyciu nowego punktu przerwania w menu debugowania

1.  Na **debugowania** menu, wybierz opcję **nowego punktu przerwania**.

2.  Kliknij przycisk **dzielone w funkcji**.

     **Nowego punktu przerwania** zostanie otwarte okno dialogowe.

3.  Określ nazwę działania w **funkcja** pola tekstowego przy użyciu następującej składni: `QualifiedActivityId[:[FullClassName][:InstanceId]]`.

    > [!NOTE]
    > Opcjonalnie, zamiast nazwy działania w **funkcja** pole tekstowe, można ustawić punktu przerwania, określając ścieżkę bezwzględną działania przepływu pracy. Na przykład załóżmy, że masz rozwiązania przepływu pracy o nazwie **WorkflowConsoleApplication1** i przepływ pracy w rozwiązaniu o nazwie **Workflow1** używającą działanie o nazwie **Delay1**. Można użyć nazwy działania **Delay1** lub określ ścieżkę jako **Delay1:WorkflowConsoleApplication1.Workflow1** lub **Delay1:WorkflowConsoleApplication1.Workflow1: { 6614886A-608E-412B-BF98-99FF1559DDDF}**.

4.  Wybierz **Użyj IntelliSense** pole wyboru, aby sprawdzić nazwę funkcji.

     Jeśli to pole wyboru nie jest zaznaczone, jest wykonywane nie Weryfikacja nazwy punktu przerwania.

5.  Wybierz **przepływu pracy** z **języka** listy.

6.  Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także

- [Debugowanie starszych wersji przepływów pracy](../workflow-designer/debugging-legacy-workflows.md)
- [Wywoływanie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsza wersja)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)