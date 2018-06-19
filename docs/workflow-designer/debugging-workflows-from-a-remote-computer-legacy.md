---
title: Projektant przepływu pracy — debugowania przepływów pracy na komputerze zdalnym (starsze)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 391180cd76fe5e0cccca802ba1cbfb78277dabc1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31967911"
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Debugowanie przepływów pracy na komputerze zdalnym (starsze)

W tym temacie opisano, jak do debugowania zdalnego starsze aplikacje systemu Windows Workflow Foundation (WF), utworzonych przy użyciu starszej wersji projektanta przepływów pracy systemu Windows. Jeśli aplikacja wymaga objęcie .NET Framework w wersji 3.5 lub WinFX, należy użyć starszego projektanta przepływów pracy.

 Po zainstalowaniu programu Visual Studio jest jedną z opcji instalacji składników do zainstalowania programu Visual Studio Debugger dla Windows Workflow Foundation (WF). Spowoduje to zainstalowanie składników debugowania zdalnego. Te zdalnego debugowania składniki muszą być zainstalowane na komputerze, który ma być przeznaczona dla debugowania zdalnego przepływu pracy.

 Ponadto zestaw, który zawiera definicję przepływu pracy starszego przepływu pracy, który debugowania na zdalnym komputerze musi być zainstalowany w globalnej pamięci podręcznej zestawów (GAC) z komputera lokalnego, który jest debugowany z. Na przykład jeśli starszych przepływu pracy jest uruchomiony na komputerze zdalnym A, a debugowany z komputera lokalnego B, definicji przepływu pracy musi znajdować się w pamięci podręcznej GAC komputera B. Dzięki temu projektanta do deserializacji i wyświetlać na komputerze B znacznik przepływu pracy przepływu pracy, który jest uruchamiany zdalnie na komputerze A. Aby uzyskać więcej informacji o pamięci podręcznej GAC Zobacz bibliotece MSDN.

 Debugowanie zdalne programu Windows Workflow Foundation działa tak samo, jako zdalne debugowanie dla innych składników programu Visual Studio. Aby uzyskać więcej informacji zobacz Visual Studio debugowanie zdalne w bibliotece MSDN.

## <a name="see-also"></a>Zobacz także

- [Debugowanie starszych wersji przepływów pracy](../workflow-designer/debugging-legacy-workflows.md)