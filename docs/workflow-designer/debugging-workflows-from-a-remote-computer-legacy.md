---
title: Debugowanie przepływów pracy na komputerze zdalnym (starsze) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: e6a3058d61d2aff0369fd52e1f03726a91a2267c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Debugowanie przepływów pracy na komputerze zdalnym (starsze)
W tym temacie opisano sposób debugowania zdalnego starszych [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplikacji utworzonych przy użyciu starszej wersji projektanta przepływu pracy systemu Windows. Użyj starszego [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] gdy aplikacja potrzebuje docelowy: [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] lub [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Po zainstalowaniu [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)], jedną z opcji instalacji składnika jest zainstalowanie [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] debugera dla [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]. Spowoduje to zainstalowanie składników debugowania zdalnego. Te zdalnego debugowania składniki muszą być zainstalowane na komputerze, który ma być przeznaczona dla debugowania zdalnego przepływu pracy.

 Ponadto zestaw, który zawiera definicję przepływu pracy starszego przepływu pracy, który debugowania na zdalnym komputerze musi być zainstalowany w globalnej pamięci podręcznej zestawów (GAC) z komputera lokalnego, który jest debugowany z. Na przykład jeśli starszych przepływu pracy jest uruchomiony na komputerze zdalnym A, a debugowany z komputera lokalnego B, definicji przepływu pracy musi znajdować się w pamięci podręcznej GAC komputera B. Dzięki temu projektanta do deserializacji i wyświetlać na komputerze B znacznik przepływu pracy przepływu pracy, który jest uruchamiany zdalnie na komputerze A. Aby uzyskać więcej informacji o pamięci podręcznej GAC Zobacz bibliotece MSDN.

 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] debugowanie zdalne działa tak samo, jak zdalnego debugowania dla innych [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] składników. Aby uzyskać więcej informacji, zobacz [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] zdalnego debugowania w bibliotece MSDN.

## <a name="see-also"></a>Zobacz także

- [Debugowanie starszych wersji przepływów pracy](../workflow-designer/debugging-legacy-workflows.md)