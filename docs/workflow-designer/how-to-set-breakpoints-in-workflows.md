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
ms.openlocfilehash: a1d7dcb437a77bd91c8dbb3360a33c7260fabb91
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755242"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Porady: Ustawianie punktów przerwania w przepływach pracy

Korzystając z projektanta przepływów pracy, można ustawić punktów przerwania na graficznego przepływy pracy w sposób jak w kodzie języka Visual Basic lub C#. Zgodnie z oczekiwaniami, w każdym punkcie przerwania ustawionych powoduje zatrzymanie wykonywania przepływu pracy.

Punkt przerwania ma trzy stany: *oczekujące*, *powiązany*, i *błąd*. Po ustawieniu punkt przerwania jest oczekujące i jest reprezentowany przez stałe czerwona ikona. Gdy środowiska wykonawczego został załadowany typu przepływu pracy, staje się powiązana. Jeśli określono nieprawidłowy format dla punktu przerwania, takich jak nazwy działania, która nie jest prawidłowy, pojawi się okno błędu. Punkt przerwania nadal został dodany do okna punkt przerwania, ale jest on oznaczony małą "x".

> [!NOTE]
> Ustawianie punktów przerwania w przepływach pracy wywoływanego nie jest obsługiwane.

> [!NOTE]
> Upewnij się, że wybrano opcję **Włącz opcję tylko mój kod (tylko zarządzane)** z **narzędzia** > **opcje** > **debugowania**  menu przed debugowania. Jeśli nie została wybrana opcja masz dwie sekwencje zagnieżdżone w obrębie innej sekwencji i ustawić punkt przerwania w pierwszym wewnętrzny sekwencji, naciskając klawisz **F11** nie debugowania w drugim wewnętrzny sekwencji.

> [!NOTE]
> Punkty przerwania w przepływie pracy nie są osiągane, jeśli Pełna ścieżka do właściwości pliku XAML nie jest dokładne. Pełna ścieżka do pliku XAML nie jest dokładne po przeniesieniu projektu lub rozwiązania do innego folderu lub na innym komputerze. Wybierz **Ctrl**+**S** Aby zapisać i zaktualizować właściwość pełną ścieżkę.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Aby ustawić punkt przerwania w działaniu w widoku Projekt

1. Wybierz działanie debugera do dzielenia na.

2. Na **debugowania** menu, wybierz opcję **Przełącz punkt przerwania**. Czerwona ikona pojawią się po lewej górnej krawędzi działania.

   Alternatywnie możesz nacisnąć przycisk **F9** po wybraniu działania, lub można kliknij prawym przyciskiem myszy działanie i wybierz **punktu przerwania** > **wstawić punktu przerwania** z menu kontekstowego.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Wywoływanie debugera przepływu pracy](../workflow-designer/how-to-invoke-the-workflow-debugger.md)
- [Debugowanie przepływów pracy za pomocą Projektanta przepływu pracy](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Instrukcje: Debugowanie kodu XAML za pomocą Projektanta przepływu pracy](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)