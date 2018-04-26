---
title: 'Projektant przepływu pracy — porady: Ustawianie punktów przerwania w przepływach pracy'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2ef863bfb899c218a65673236c284bed63aed11
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Porady: Ustawianie punktów przerwania w przepływach pracy

Korzystając z projektanta przepływów pracy systemu Windows, można ustawić punktów przerwania na graficznego przepływy pracy w sposób jak w kodzie języka Visual Basic lub C#. Zgodnie z oczekiwaniami, w każdym punkcie przerwania ustawionych powoduje zatrzymanie wykonywania przepływu pracy.

 Punkt przerwania ma trzy stany: *oczekujące*, *powiązany*, i *błąd*. Po ustawieniu punkt przerwania jest oczekujące i jest reprezentowany przez stałe czerwona ikona. Gdy środowiska wykonawczego został załadowany typu przepływu pracy, staje się powiązana. Jeśli określono nieprawidłowy format dla punktu przerwania, takich jak nazwy działania, która nie jest prawidłowy, pojawi się okno błędu. Punkt przerwania nadal został dodany do okna punkt przerwania, ale jest on oznaczony małą "x".

> [!NOTE]
> Ustawianie punktów przerwania w przepływach pracy wywoływanego nie jest obsługiwane.

> [!WARNING]
> Upewnij się, że wybrano opcję **Włącz opcję tylko mój kod (tylko zarządzane)** z **narzędzia**, **opcje**, **debugowanie** menu przed debugowania. Jeśli masz dwie sekwencje zagnieżdżone w obrębie innej sekwencji i ustawić punkt przerwania w pierwszym wewnętrzny sekwencji, naciskając klawisz **F11** nie będzie debugowania do drugiego wewnętrzny sekwencji, jeśli **Włącz opcję tylko mój kod (zarządzane tylko)** nie wybrano opcji.

> [!WARNING]
> Punkty przerwania w przepływie pracy nie zostanie pobrać odwołań, jeśli Pełna ścieżka do właściwości pliku XAML nie jest dokładne. Pełna ścieżka do pliku XAML nie jest dokładne po przeniesieniu projektu/rozwiązania do innego folderu lub na innym komputerze. Wybierz kombinację klawiszy Ctrl + S, aby zapisać i zaktualizować właściwość pełną ścieżkę.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Aby ustawić punkt przerwania w działaniu w widoku Projekt

1.  Wybierz działanie debugera do dzielenia na.

2.  Na **debugowania** menu, wybierz opcję **Przełącz punkt przerwania**. Czerwona ikona pojawią się po lewej górnej krawędzi działania.

     Alternatywnie można również nacisnąć skrót **F9** klucza po wybraniu działania lub można kliknij prawym przyciskiem myszy działanie i wybierz **punktu przerwania** następnie **wstawić punktu przerwania**z menu kontekstowego.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Wywoływanie debugera przepływu pracy](../workflow-designer/how-to-invoke-the-workflow-debugger.md)
- [Debugowanie przepływów pracy za pomocą Projektanta przepływu pracy](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Instrukcje: Debugowanie kodu XAML za pomocą Projektanta przepływu pracy](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)