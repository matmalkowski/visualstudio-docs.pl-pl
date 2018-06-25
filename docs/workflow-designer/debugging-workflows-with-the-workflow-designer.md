---
title: Debugowanie przepływów pracy za pomocą Projektanta przepływu pracy
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- Visual Studio Workflow Designer [WFD], debugging workflows
- Workflow Designer [WFD], debugging workflows
ms.assetid: d71308cf-d464-4536-8711-0d0a8eadb255
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 482e13a91513151d7c4595e0a622f223751ae553
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755317"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>Debugowania przepływów pracy za pomocą projektanta przepływów pracy

**Projektanta przepływów pracy** umożliwia debugowanie przepływów pracy i działań niestandardowych. Proces i zachowanie są podobne do elementu domyślny debuger programu Visual Studio.

## <a name="invoke-the-workflow-debugger"></a>Wywoływanie debugger przepływu pracy

Ogólnie rzecz biorąc można debugowania przepływów pracy, tak samo, jak debugować programów napisanych w innych językach programowania Visual Studio. Debuger przepływu pracy można uruchomić w następujący sposób:

- Wybierz **dołączyć do procesu** na **debugowania** menu, aby wybrać uruchomionego procesu hosta dla swojego wystąpienia przepływu pracy. Ta procedura jest taka sama jak dołączanie do procesu hosta w kodzie zarządzanym.

- Naciśnij klawisz **F5** uruchomione wystąpienie przepływu pracy lub kontynuować działanie po został trafiony punkt przerwania.

- Użyj zdalnego debugowania. Informacje na temat używania zdalnego debugowania, zobacz [porady: Włączanie debugowania zdalnego](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100)).

   > [!NOTE]
   > Jeśli aplikacja przepływu pracy jest przeznaczony dla x86 architektury jest obsługiwany na maszynie z systemem 64-bitowym systemie operacyjnym, a następnie zdalne debugowanie nie będzie działać, chyba że Visual Studio jest zainstalowany na zdalnym komputerze lub element docelowy dla aplikacji przepływu pracy jest zmieniana na  **Wszelkie Procesora**.

## <a name="step-through-code"></a>Krokowo kodu

- **Krok w**: Wkrocz do działania przez naciśnięcie przycisku **F11**. Kroki debugera do dowolnego obsługi, który jest zdefiniowany. Jeśli obsługa nie jest zdefiniowana, Przekrocz nad działania lub z działań złożonych, które zawierają inne działania, Wkrocz pierwszy wykonywanego działania.

- **Limit krok:** wychodzenia z działania, naciskając klawisz **Shift**+**F11**. Wykonywanie krok po kroku, poza działanie uruchamia bieżące działanie i jego element równorzędny działania do zakończenia. Debuger następnie dzieli na nadrzędnego bieżącego działania. Przy przechodzeniu z obsługi kodu, debuger dzieli się na działania, z którym jest skojarzony program obsługi.

- **Step Over**: Przekrocz działania przez naciśnięcie przycisku **F10**. Przy przechodzeniu przez działanie złożone, debuger dzieli na pierwszy element podrzędny wykonywalnego działania złożonego. Przy przechodzeniu przez z systemem innym niż złożone, takich jak <xref:System.Activities.Statements.Assign> działania, debuger wykonuje działanie i jego skojarzony programów obsługi i podziału na następne działanie. Działania, która jest wykonywana w przypadku ostatniego działania podrzędne działania złożonego, następnie, po wykonaniu debuger dzieli na działania nadrzędnego.

## <a name="debug-with-f5"></a>Debugowanie przy użyciu F5

Jeśli tworzysz aplikację konsoli przepływu pracy, wystarczy nacisnąć klawisz **F5** aby rozpocząć debugowanie do aplikacji i przepływ pracy. Jeśli tworzysz Biblioteka działań samodzielnie, należy określić aplikacji hosta wykonywalny jako projekt startowy. Aby ustawić projekt startowy w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu hosta i wybierz **Ustaw jako projekt startowy**.