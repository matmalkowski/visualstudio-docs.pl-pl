---
title: Port dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1f1ba09c1802bdeb1c6a402e95a6de408b277532
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099073"
---
# <a name="port-suppliers"></a>Port dostawcy
Pod względem architektury debugera **portu dostawcy**:  
  
-   Znajduje się na serwerze i udostępnia porty na żądanie do tego serwera.  
  
-   Można dodawać i usuwać porty z zawierającego serwera.  
  
-   Można wyliczyć wszystkie porty, które dostarczył się do serwera.  
  
-   Jest reprezentowana przez [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfejsu, który jest zarejestrowany w programie Visual Studio za pomocą rejestru. Ten interfejs można uzyskać przez wywołanie metody [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] udostępnia domyślny port dostawcy i domyślny port. Jeśli port niestandardowy musi zostać wdrożone, dostawcy niestandardowego numeru portu również musi zostać wdrożone w celu dostarczania te porty niestandardowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Serwery](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Porty](../../extensibility/debugger/ports.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)