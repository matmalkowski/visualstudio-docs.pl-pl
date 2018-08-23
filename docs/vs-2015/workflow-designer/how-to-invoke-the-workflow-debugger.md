---
title: 'Porady: wywoływanie debugera przepływu pracy | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 6142e12da9a32ccb325c6a8a199f67599c7228c8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42628993"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Porady: wywoływanie debugera przepływu pracy
Ogólnie rzecz biorąc należy debugowania przepływów pracy, tak samo, jak można debugować programy napisane w różnych językach programowania Visual Studio. Można uruchomić debugera przepływu pracy, w następujący sposób:  
  
-   Wybierz **dołączyć do procesu** na **debugowania** menu, aby wybrać uruchomionego procesu hosta dla wystąpienia przepływu pracy. Ta procedura jest taka sama jak dołączanie do procesu hosta w kodzie zarządzanym.  
  
-   Naciśnij klawisz **F5** uruchomione wystąpienie przepływu pracy lub będą nadal działać po został trafiony punkt przerwania.  
  
-   Użyj zdalnego debugowania. Aby uzyskać informacje na temat korzystania z debugowania zdalnego, zobacz [porady: Włączanie debugowania zdalnego](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
    > [!NOTE]
    >  Jeśli aplikacja przepływu pracy jest przeznaczony dla x86 architektury, która jest hostowana na komputerze z systemem 64-bitowym systemie operacyjnym, a następnie zdalne debugowanie nie będzie działać, o ile nie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] jest zainstalowany na komputerze zdalnym lub element docelowy dla aplikacji przepływu pracy zostanie zmieniona na **Dowolny procesor CPU**.  
  
### <a name="stepping-through-code"></a>Krokowe wykonywanie kodu  
  
-   **Wkrocz**: możesz wejść do czynności za pomocą **F11**. Debuger nie wchodzi do dowolnej procedury obsługi, który jest zdefiniowany. Jeśli żadna procedura obsługi nie jest zdefiniowany, Przekrocz działania lub za pomocą złożonych działań, które zawierają inne działania, wkroczenia do pierwszego działania wykonywania.  
  
-   **Limit krok:** możesz wejść korzyści z używania działania **Shift F11**. Przechodzenie krok po kroku, poza działanie uruchamia bieżące działanie i jego element równorzędny działania ukończone. Debuger jest następnie przerywa w nadrzędnego bieżącego działania. Przy przechodzeniu od obsługi kodu, debuger przerywa na działaniu, z którą jest skojarzony program obsługi.  
  
-   **Step Over**: użytkownik może przechodzić przez działanie przy użyciu **F10**. Przy przechodzeniu przez działanie złożone, debuger przerywa na pierwszy element podrzędny wykonywalnego działanie złożone. Przy przechodzeniu przez inne niż złożone, takich jak <xref:System.Activities.Statements.Assign> działania, debuger wykonuje działanie i jego związanymi obsługami i przerw na następne działanie. Jeśli działania, który jest wykonywany jest ostatniego działania podrzędne działania złożonego, następnie, po wykonaniu debuger przerywa na działanie nadrzędne.  
  
### <a name="debugging-with-f5"></a>Debugowanie za pomocą F5  
  
-   Jeśli tworzysz projekt aplikacji konsoli przepływu pracy, po prostu nacisnąć skrót **F5** aby rozpocząć debugowanie w aplikacji sieci Web i przepływ pracy. Jeśli tworzysz biblioteki działań na swój własny, musi mieć aplikację hosta wykonywalny jako projekt startowy. Aby ustawić projekt startowy w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, hosta i wybierz **Ustaw jako projekt startowy**.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Ustawianie punktów przerwania w przepływach pracy](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [Debugowanie przepływów pracy za pomocą Projektanta przepływu pracy](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)