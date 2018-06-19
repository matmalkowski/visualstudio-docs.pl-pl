---
title: Serwery (Visual Studio SDK) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2904641e8188abc6ef2382b2da272a9f96fd0f81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31125497"
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