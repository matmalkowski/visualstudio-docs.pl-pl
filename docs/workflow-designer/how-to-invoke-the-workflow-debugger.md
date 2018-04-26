---
title: 'Projektant przepływu pracy — porady: wywoływanie Debugger przepływu pracy'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3fb48ee50ebc7c1e211634082cfc51dcb170a3de
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Porady: wywoływanie Debugger przepływu pracy

Ogólnie rzecz biorąc można debugowania przepływów pracy, tak samo, jak debugować programów napisanych w innych językach programowania Visual Studio. Debuger przepływu pracy można uruchomić w następujący sposób:

-   Wybierz **dołączyć do procesu** na **debugowania** menu, aby wybrać uruchomionego procesu hosta dla swojego wystąpienia przepływu pracy. Ta procedura jest taka sama jak dołączanie do procesu hosta w kodzie zarządzanym.

-   Naciśnij klawisz **F5** uruchomione wystąpienie przepływu pracy lub kontynuować działanie po został trafiony punkt przerwania.

-   Użyj zdalnego debugowania. Informacje na temat używania zdalnego debugowania, zobacz [porady: Włączanie debugowania zdalnego](http://go.microsoft.com/fwlink/?LinkId=196257).

    > [!NOTE]
    > Jeśli aplikacja przepływu pracy jest przeznaczony dla x86 architektury i znajduje się na maszynie z systemem 64-bitowym systemie operacyjnym, a następnie zdalne debugowanie nie będzie działać, chyba że Visual Studio jest zainstalowany na zdalnym komputerze lub element docelowy przepływu pracy aplikacji została zmieniona na **Dowolnego Procesora**.

## <a name="stepping-through-code"></a>Krokowe wykonywanie kodu

-   **Krok w**: można przejść do działania przy użyciu **F11**. Kroki debugera do dowolnego obsługi, który jest zdefiniowany. Jeśli obsługa nie jest zdefiniowana, Przekrocz nad działania lub z działań złożonych, które zawierają inne działania, Wkrocz pierwszy wykonywanego działania.

-   **Limit krok:** można wychodzenia z działania przy użyciu **Shift F11**. Wykonywanie krok po kroku, poza działanie uruchamia bieżące działanie i jego element równorzędny działania do zakończenia. Debuger następnie dzieli na nadrzędnego bieżącego działania. Przy przechodzeniu z obsługi kodu, debuger dzieli się na działania, z którym jest skojarzony program obsługi.

-   **Step Over**: można Przekrocz nad działania przy użyciu **F10**. Przy przechodzeniu przez działanie złożone, debuger dzieli na pierwszy element podrzędny wykonywalnego działania złożonego. Przy przechodzeniu przez z systemem innym niż złożone, takich jak <xref:System.Activities.Statements.Assign> działania, debuger wykonuje działanie i jego skojarzony programów obsługi i podziału na następne działanie. Działania, która jest wykonywana w przypadku ostatniego działania podrzędne działania złożonego, następnie, po wykonaniu debuger dzieli na działania nadrzędnego.

## <a name="debugging-with-f5"></a>Debugowanie za pomocą F5

-   Jeśli tworzysz projekt aplikacji Konsolowej przepływu pracy, wystarczy nacisnąć klawisz **F5** aby rozpocząć debugowanie do aplikacji i przepływ pracy. Jeśli tworzysz Biblioteka działań samodzielnie, musi mieć aplikację hosta wykonywalny jako projekt startowy. Aby ustawić projekt startowy w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu hosta i wybierz **Ustaw jako projekt startowy**.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Ustawianie punktów przerwania w przepływach pracy](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Debugowanie przepływów pracy za pomocą Projektanta przepływu pracy](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)