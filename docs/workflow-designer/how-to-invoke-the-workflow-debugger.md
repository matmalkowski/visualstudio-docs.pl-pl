---
title: "Porady: wywoływanie Debugger przepływu pracy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: "9"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8d7fbdb1851669d704cb8a44f8144291c04ae0ce
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Porady: wywoływanie Debugger przepływu pracy
Ogólnie rzecz biorąc można debugowania przepływów pracy, tak samo, jak debugować programów napisanych w innych językach programowania Visual Studio. Debuger przepływu pracy można uruchomić w następujący sposób:  
  
-   Wybierz **dołączyć do procesu** na **debugowania** menu, aby wybrać uruchomionego procesu hosta dla swojego wystąpienia przepływu pracy. Ta procedura jest taka sama jak dołączanie do procesu hosta w kodzie zarządzanym.  
  
-   Naciśnij klawisz **F5** uruchomione wystąpienie przepływu pracy lub kontynuować działanie po został trafiony punkt przerwania.  
  
-   Użyj zdalnego debugowania. Informacje na temat używania zdalnego debugowania, zobacz [porady: Włączanie debugowania zdalnego](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
    > [!NOTE]
    >  Jeśli aplikacja przepływu pracy jest przeznaczony dla x86 architektury i znajduje się na maszynie z systemem 64-bitowym systemie operacyjnym, a następnie zdalne debugowanie nie będzie działać, chyba że [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] jest zainstalowany na komputerze zdalnym lub element docelowy dla aplikacji przepływu pracy został zmieniony na **Dowolnego Procesora**.  
  
### <a name="stepping-through-code"></a>Krokowe wykonywanie kodu  
  
-   **Krok w**: można przejść do działania przy użyciu **F11**. Kroki debugera do dowolnego obsługi, który jest zdefiniowany. Jeśli obsługa nie jest zdefiniowana, Przekrocz nad działania lub z działań złożonych, które zawierają inne działania, Wkrocz pierwszy wykonywanego działania.  
  
-   **Limit krok:** można wychodzenia z działania przy użyciu **Shift F11**. Wykonywanie krok po kroku, poza działanie uruchamia bieżące działanie i jego element równorzędny działania do zakończenia. Debuger następnie dzieli na nadrzędnego bieżącego działania. Przy przechodzeniu z obsługi kodu, debuger dzieli się na działania, z którym jest skojarzony program obsługi.  
  
-   **Step Over**: można Przekrocz nad działania przy użyciu **F10**. Przy przechodzeniu przez działanie złożone, debuger dzieli na pierwszy element podrzędny wykonywalnego działania złożonego. Przy przechodzeniu przez z systemem innym niż złożone, takich jak <xref:System.Activities.Statements.Assign> działania, debuger wykonuje działanie i jego skojarzony programów obsługi i podziału na następne działanie. Działania, która jest wykonywana w przypadku ostatniego działania podrzędne działania złożonego, następnie, po wykonaniu debuger dzieli na działania nadrzędnego.  
  
### <a name="debugging-with-f5"></a>Debugowanie za pomocą F5  
  
-   Jeśli tworzysz projekt aplikacji Konsolowej przepływu pracy, wystarczy nacisnąć klawisz **F5** aby rozpocząć debugowanie do aplikacji i przepływ pracy. Jeśli tworzysz Biblioteka działań samodzielnie, musi mieć aplikację hosta wykonywalny jako projekt startowy. Aby ustawić projekt startowy w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu hosta i wybierz **Ustaw jako projekt startowy**.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Ustawianie punktów przerwania w przepływach pracy](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [Debugowanie przepływów pracy za pomocą projektanta przepływów pracy](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)