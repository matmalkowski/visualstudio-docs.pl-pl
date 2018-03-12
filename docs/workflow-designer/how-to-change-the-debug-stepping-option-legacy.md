---
title: "Porady: Zmień opcję krokowe wykonywanie debugowania (starsze) | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ea687b0a08aa4697ac9f7c7b0aca875af131a561
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Porady: Zmień opcję krokowe wykonywanie debugowania (starsze)
W tym temacie opisano, jak zmienić opcję wykonywania krokowego debugowania dla [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplikacji w Projektancie przepływów pracy starszej wersji systemu Windows, które mają równoczesnych akcje. Użyj starszego [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] konieczność docelowy: [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] lub [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Podczas debugowania starsze działania mające równoczesnych wykonywania, takie jak **ParallelActivity** lub **grupy ConditionedActivityGroup**, można użyć jednej z dwóch opcji do wykonania kroków opisanych w kodzie.

 Wykonaj następujące kroki, aby zmienić debugowania krokowe wykonywanie opcja w projekcie przepływem pracy starszego.

## <a name="procedures"></a>Procedury

#### <a name="to-change-the-debug-stepping-option"></a>Aby zmienić opcję debugowania wykonywania krokowego

1.  Uruchom program Visual Studio.

2.  Otwórz istniejący projekt przepływem pracy starszego lub Utwórz nowy projekt, który wykorzystuje równoczesnych działań i który jest przeznaczony dla jednego [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] lub [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

3.  Na **przepływu pracy** menu w starszych [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], wskaż pozycję **debugowania**, a następnie wskaż **opcje krokowe wykonywanie**.

4.  Wybierz opcję **wystąpienia** lub **gałęzi**.

## <a name="see-also"></a>Zobacz także

- [Debugowanie starszych wersji przepływów pracy](../workflow-designer/debugging-legacy-workflows.md)
- [Opcje debugowania wykonywania krokowego (starsza wersja)](../workflow-designer/debug-stepping-options-legacy.md)