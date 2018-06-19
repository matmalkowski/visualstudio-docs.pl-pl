---
title: 'Projektant przepływu pracy — porady: Ustawianie punktów przerwania w przepływach pracy (starsze)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
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
ms.openlocfilehash: c0c70b630404830fa8c733a7310e4700da8f08b3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975198"
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Porady: Ustawianie punktów przerwania w przepływach pracy (starsze)

W tym temacie opisano, jak można ustawić punktów przerwania w systemie Windows Workflow Foundation (WF) kompilacji aplikacji za pomocą projektanta przepływów pracy programu starszej wersji systemu Windows. Gdy aplikacja Windows Workflow Foundation wymaga objęcie .NET Framework w wersji 3.5 lub WinFX za pomocą starszej wersji projektanta przepływu pracy.

 Jeśli używasz starszej wersji projektanta przepływów pracy w Visual Studio 2010 do tworzenia aplikacji systemu Windows Workflow Foundation, tak jak w programie Visual Studio można ustawić punktów przerwania w C# i Visual Basic code. Zgodnie z oczekiwaniami, w każdym punkcie przerwania ustawionych powoduje zatrzymanie wykonywania przepływu pracy.

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