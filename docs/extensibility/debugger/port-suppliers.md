---
title: Port dostawców | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5385e006bcd2f79ab7b1c2e723e696b833991f36
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252352"
---
# <a name="port-suppliers"></a>Dostawcy portów
W architekturze debugera *dostawcy portu*:  
  
-   Znajduje się na serwerze i udostępnia porty na żądanie do tego serwera.  
  
-   Dodawać i usuwać portów z zawierającego serwera.  
  
-   Można wyliczyć wszystkie porty, które udostępnił się do serwera.  
  
-   Jest reprezentowany przez [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfejsu, który jest zarejestrowany w programie Visual Studio za pomocą rejestru. Ten interfejs można uzyskać przez wywołanie metody [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zapewnia dostawcy portu domyślnego i domyślny port. Jeśli port niestandardowy, musi zostać wdrożone, dostawca niestandardowy port również musi zaimplementować tak, aby podać te porty niestandardowe.  
  
## <a name="see-also"></a>Zobacz także  
 [Serwery](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Porty](../../extensibility/debugger/ports.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)