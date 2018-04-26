---
title: 'Projektant przepływu pracy — porady: Zmień opcję krokowe wykonywanie debugowania (starsze)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31047cedd4e8772b9ebab4ef238a8fe32bc07663
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Porady: Zmień opcję krokowe wykonywanie debugowania (starsze)

W tym temacie opisano, jak zmienić debugowania krokowe wykonywanie opcję dla aplikacji Windows Workflow Foundation (WF) w Projektancie przepływów pracy starszej wersji systemu Windows, które mają równoczesnych akcje. Starsze projektanta przepływów pracy należy używać wtedy, gdy konieczne objęcie .NET Framework w wersji 3.5 lub WinFX.

Podczas debugowania starsze działania mające równoczesnych wykonywania, takie jak **ParallelActivity** lub **grupy ConditionedActivityGroup**, można użyć jednej z dwóch opcji do wykonania kroków opisanych w kodzie.

Wykonaj następujące kroki, aby zmienić debugowania krokowe wykonywanie opcja w projekcie przepływem pracy starszego.

## <a name="procedures"></a>Procedury

### <a name="to-change-the-debug-stepping-option"></a>Aby zmienić opcję debugowania wykonywania krokowego

1.  Uruchom program Visual Studio.

2.  Otwórz istniejący projekt starszych przepływu pracy lub Utwórz nowy projekt używającego równoczesnych działań i którego element docelowy .NET Framework w wersji 3.5 lub WinFX.

3.  Na **przepływu pracy** menu w starszej wersji projektanta przepływów pracy, wskaż pozycję **debugowania**, a następnie wskaż **krokowe wykonywanie opcje**.

4.  Wybierz opcję **wystąpienia** lub **gałęzi**.

## <a name="see-also"></a>Zobacz także

- [Debugowanie starszych wersji przepływów pracy](../workflow-designer/debugging-legacy-workflows.md)
- [Opcje debugowania wykonywania krokowego (starsza wersja)](../workflow-designer/debug-stepping-options-legacy.md)