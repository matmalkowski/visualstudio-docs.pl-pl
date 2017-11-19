---
title: "Debugowanie przepływów pracy na komputerze zdalnym (starsze) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: f6b1f88fcc796cbee0a48fd39da2ad9c4fe1489a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Debugowanie przepływów pracy na komputerze zdalnym (starsze)
W tym temacie opisano sposób debugowania zdalnego starszych [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplikacje utworzone przy użyciu starszego [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]. Użyj starszego [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] gdy aplikacja potrzebuje docelowy: [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] lub [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Po zainstalowaniu [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)], jedną z opcji instalacji składnika jest zainstalowanie [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] debugera dla [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]. Spowoduje to zainstalowanie składników debugowania zdalnego. Te zdalnego debugowania składniki muszą być zainstalowane na komputerze, który ma być przeznaczona dla debugowania zdalnego przepływu pracy.  
  
 Ponadto zestaw, który zawiera definicję przepływu pracy starszego przepływu pracy, który debugowania na zdalnym komputerze musi być zainstalowany w globalnej pamięci podręcznej zestawów (GAC) z komputera lokalnego, który jest debugowany z. Na przykład jeśli starszych przepływu pracy jest uruchomiony na komputerze zdalnym A, a debugowany z komputera lokalnego B, definicji przepływu pracy musi znajdować się w pamięci podręcznej GAC komputera B. Dzięki temu projektanta do deserializacji i wyświetlać na komputerze B znacznik przepływu pracy przepływu pracy, który jest uruchamiany zdalnie na komputerze A. Aby uzyskać więcej informacji o pamięci podręcznej GAC Zobacz bibliotece MSDN.  
  
 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)]debugowanie zdalne działa tak samo, jak zdalnego debugowania dla innych [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] składników. Aby uzyskać więcej informacji, zobacz [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] zdalnego debugowania w bibliotece MSDN.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie przepływów pracy starsza wersja](../workflow-designer/debugging-legacy-workflows.md)