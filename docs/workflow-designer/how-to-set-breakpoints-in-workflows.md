---
title: "Porady: Ustawianie punktów przerwania w przepływach pracy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
caps.latest.revision: "10"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 4c9a3124ddefc892207ccc821b80056baab14166
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Porady: Ustawianie punktów przerwania w przepływach pracy
Jeśli używasz [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)], ustaw punkty przerwania w graficznym przepływy pracy w sposób jak w kodzie języka Visual Basic lub C#. Zgodnie z oczekiwaniami, w każdym punkcie przerwania ustawionych powoduje zatrzymanie wykonywania przepływu pracy.  
  
 Punkt przerwania ma trzy stany: *oczekujące*, *powiązany*, i *błąd*. Po ustawieniu punkt przerwania jest oczekujące i jest reprezentowany przez stałe czerwona ikona. Gdy środowiska wykonawczego został załadowany typu przepływu pracy, staje się powiązana. Jeśli określono nieprawidłowy format dla punktu przerwania, takich jak nazwy działania, która nie jest prawidłowy, pojawi się okno błędu. Punkt przerwania nadal został dodany do okna punkt przerwania, ale jest on oznaczony małą "x".  
  
> [!NOTE]
>  Ustawianie punktów przerwania w przepływach pracy wywoływanego nie jest obsługiwane.  
  
> [!WARNING]
>  Upewnij się, że wybrano opcję **Włącz opcję tylko mój kod (tylko zarządzane)** z **narzędzia**, **opcje**, **debugowanie** menu przed debugowania. Jeśli masz dwie sekwencje zagnieżdżone w obrębie innej sekwencji i ustawić punkt przerwania w pierwszym wewnętrzny sekwencji, naciskając klawisz **F11** nie będzie debugowania do drugiego wewnętrzny sekwencji, jeśli **Włącz opcję tylko mój kod (zarządzane tylko)**nie wybrano opcji.  
  
> [!WARNING]
>  Punkty przerwania w przepływie pracy nie zostanie pobrać odwołań, jeśli Pełna ścieżka do właściwości pliku XAML nie jest dokładne. Pełna ścieżka do pliku XAML nie jest dokładne po przeniesieniu projektu/rozwiązania do innego folderu lub na innym komputerze. Wybierz kombinację klawiszy Ctrl + S, aby zapisać i zaktualizować właściwość pełną ścieżkę.  
  
### <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Aby ustawić punkt przerwania w działaniu w widoku Projekt  
  
1.  Wybierz działanie debugera do dzielenia na.  
  
2.  Na **debugowania** menu, wybierz opcję **Przełącz punkt przerwania**. Czerwona ikona pojawią się po lewej górnej krawędzi działania.  
  
     Alternatywnie można również nacisnąć skrót **F9** klucza po wybraniu działania lub można kliknij prawym przyciskiem myszy działanie i wybierz **punktu przerwania** następnie **wstawić punktu przerwania**z menu kontekstowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: wywoływanie Debugger przepływu pracy](../workflow-designer/how-to-invoke-the-workflow-debugger.md)   
 [Debugowanie przepływów pracy za pomocą projektanta przepływów pracy](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)   
 [Instrukcje: Debugowanie kodu XAML za pomocą Projektanta przepływu pracy](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)