---
title: Debugowanie wykonywania krokowego opcje (starsze) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: b93226b7223272c04b7d2e6b36b82cf737cd1b86
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="debug-stepping-options-legacy"></a>Debugowanie wykonywania krokowego opcje (starsze)
W tym temacie opisano sposób debugowania [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplikacji, które mają równoczesnych działań w starszych [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]. Użyj starszego [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] konieczność docelowy: [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] lub [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Podczas debugowania starsze działania mające równoczesnych wykonywania, takie jak **ParallelActivity** lub **grupy ConditionedActivityGroup**, można użyć jednej z poniższych dwóch opcji do wykonania kroków opisanych w kodzie .  
  
-   **Rozgałęzienie wykonywanie krok po kroku.** Ten tryb krokowe wykonywanie umożliwia kroków i debugowania gałąź złożonego działania, takie jak **ParallelActivity** lub **ConditionalActivityGroup** działania. Tej opcji debugowania można nie zauważyć, że zmiany w formancie występuje z powodu równoczesnych wykonywanie innych działań w przepływie pracy. Debuger kroki tylko do działania w aktualnie zaznaczonej gałęzi, podczas gdy inne działania w przepływie pracy mogą być wykonywane jednocześnie. Na przykład domyślnie lewej strony gałęzi w **ParallelActivity** działania i pierwsze działanie podrzędne względem **grupy ConditionedActivityGroup** działania są używane do przeglądania. Jeśli użytkownik jest zainteresowana debugowania innych działań gałęzi lub podrzędny, jawne punktu przerwania muszą znajdować się na tej gałęzi lub podrzędnym działania. Wykonywanie krok po kroku nadal w oddziale, po wyzwoleniu punktu przerwania.  
  
-   **Wystąpienia wykonywanie krok po kroku.** Ten tryb krokowe wykonywanie umożliwia utworzenie kroków i debugowania równocześnie wykonywanych działań w przepływie pracy. Po wybraniu tej opcji można zauważyć, że zmiany w formancie występuje, gdy równocześnie wykonywanych działań uruchamianych w przepływie pracy.  
  
 Domyślnie wybrano opcję wykonywania krokowego gałęzi, a użytkownicy mogą przełączać dwóch opcji podczas debugowania przepływem pracy starszego.  
  
 Należy wybrać wystąpienie krokowe wykonywanie opcja podczas debugowania przepływów pracy maszyny stanu starszej wersji.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie przepływów pracy starsza wersja](../workflow-designer/debugging-legacy-workflows.md)   
 [Instrukcje: Opcja zmiany debugowania krokowego (starsza wersja)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)