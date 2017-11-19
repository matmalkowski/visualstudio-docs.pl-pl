---
title: Serwery (Visual Studio SDK) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 496e9b361dbb7f5c3eb5cf5197a1351a1182af3e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="servers-visual-studio-sdk"></a>Serwery (Visual Studio SDK)
Pod względem architektury debugera **serwera**:  
  
-   Jest kontenerem portów i dostawców portu i jest używany do komunikacji portów i portu dostawcy do menedżera sesji debugowania (SDM) i aparaty debugowania.  
  
-   Można identyfikacji według nazwy i wyliczyć jego portów i portu dostawcy.  
  
-   Jest reprezentowana przez [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) interfejs, który jest implementowane tylko przez program Visual Studio (jedno wystąpienie serwera dla każdego wystąpienia uruchamiania programu Visual Studio).  
  
## <a name="see-also"></a>Zobacz też  
 [Porty](../../extensibility/debugger/ports.md)   
 [Port dostawcy](../../extensibility/debugger/port-suppliers.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)