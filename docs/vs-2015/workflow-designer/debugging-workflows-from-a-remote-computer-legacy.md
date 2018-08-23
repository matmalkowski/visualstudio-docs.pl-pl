---
title: Debugowanie przepływów pracy na komputerze zdalnym (starsza wersja) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 458f5d2a8d2be83f465f9b96ac9ff9dd1eca2d37
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681437"
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Debugowanie przepływów pracy ze zdalnego komputera (starsza wersja)
W tym temacie opisano sposób debugowania zdalnego starsza wersja [!INCLUDE[wf](../includes/wf-md.md)] aplikacje, które są tworzone za pomocą starszego [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Użyj starszego [!INCLUDE[wfd2](../includes/wfd2-md.md)] gdy Twoja aplikacja potrzebuje docelowy: [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Po zainstalowaniu [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)], jedną z opcji instalacji składników polega na zainstalowaniu [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] debugera dla [!INCLUDE[wf](../includes/wf-md.md)]. Spowoduje to zainstalowanie składników zdalnego debugowania. Te składniki debugowania zdalnego należy zainstalować na komputerze, który przeznaczonych do debugowania zdalnego przepływu pracy.  
  
 Ponadto zestaw, który zawiera definicję przepływu pracy w starszej wersji przepływu pracy, który debugujesz na komputerze zdalnym musi być zainstalowany w globalnej pamięci podręcznej zestawów (GAC) z komputera lokalnego, który jest debugowany z. Na przykład jeśli starszej wersji przepływu pracy jest uruchomiony na komputerze zdalnym, A i debugowany z komputera lokalnego B, definicja przepływu pracy musi być obecny w GAC komputera B. Dzięki temu projektanta do deserializacji i wyświetlanie na komputerze B znaczników przepływu pracy, przepływu pracy, który jest zdalnie uruchomiony na komputerze A. Aby uzyskać więcej informacji na temat globalnej pamięci podręcznej Zobacz Biblioteka MSDN.  
  
 [!INCLUDE[wf2](../includes/wf2-md.md)] zdalne debugowanie działa tak samo, jak zdalne debugowanie dla innych [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] składników. Aby uzyskać więcej informacji, zobacz [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] zdalnego debugowania w bibliotece MSDN.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie starszych wersji przepływów pracy](../workflow-designer/debugging-legacy-workflows.md)