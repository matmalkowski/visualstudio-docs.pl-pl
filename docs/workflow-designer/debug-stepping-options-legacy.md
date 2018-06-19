---
title: Projektant przepływu pracy — opcje debugowania wykonywanie krok po kroku (starsze)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f46c0ab382a0e189c595e6e0f8aeb69c71814faf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31969073"
---
# <a name="debug-stepping-options-legacy"></a>Debugowanie wykonywania krokowego opcje (starsze)

W tym temacie opisano, jak można debugować aplikacji Windows Workflow Foundation (WF), które mają równoczesnych działań w starszej wersji projektanta przepływów pracy systemu Windows. Starsze projektanta przepływów pracy należy używać wtedy, gdy konieczne objęcie .NET Framework w wersji 3.5 lub WinFX.

Podczas debugowania starsze działania mające równoczesnych wykonywania, takie jak **ParallelActivity** lub **grupy ConditionedActivityGroup**, można użyć jednej z poniższych dwóch opcji do wykonania kroków opisanych w kodzie .

-   **Rozgałęzienie wykonywanie krok po kroku.** Ten tryb krokowe wykonywanie umożliwia kroków i debugowania gałąź złożonego działania, takie jak **ParallelActivity** lub **ConditionalActivityGroup** działania. Tej opcji debugowania można nie zauważyć, że zmiany w formancie występuje z powodu równoczesnych wykonywanie innych działań w przepływie pracy. Debuger kroki tylko do działania w aktualnie zaznaczonej gałęzi, podczas gdy inne działania w przepływie pracy mogą być wykonywane jednocześnie. Na przykład domyślnie lewej strony gałęzi w **ParallelActivity** działania i pierwsze działanie podrzędne względem **grupy ConditionedActivityGroup** działania są używane do przeglądania. Jeśli użytkownik jest zainteresowana debugowania innych działań gałęzi lub podrzędny, jawne punktu przerwania muszą znajdować się na tej gałęzi lub podrzędnym działania. Wykonywanie krok po kroku nadal w oddziale, po wyzwoleniu punktu przerwania.

-   **Wystąpienia wykonywanie krok po kroku.** Ten tryb krokowe wykonywanie umożliwia utworzenie kroków i debugowania równocześnie wykonywanych działań w przepływie pracy. Po wybraniu tej opcji można zauważyć, że zmiany w formancie występuje, gdy równocześnie wykonywanych działań uruchamianych w przepływie pracy.

Domyślnie wybrano opcję wykonywania krokowego gałęzi, a użytkownicy mogą przełączać dwóch opcji podczas debugowania przepływem pracy starszego.

Należy wybrać wystąpienie krokowe wykonywanie opcja podczas debugowania przepływów pracy maszyny stanu starszej wersji.

## <a name="see-also"></a>Zobacz także

- [Debugowanie starszych wersji przepływów pracy](../workflow-designer/debugging-legacy-workflows.md)
- [Instrukcje: Opcja zmiany debugowania krokowego (starsza wersja)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)