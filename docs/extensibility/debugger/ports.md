---
title: Porty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a350e0579f7e60d8a7ffc3e879d79364cfdf0317
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ports"></a>Porty
Pod względem architektury debugera **portu**:  
  
-   Kontener dla zestawu procesów jest uruchomiona na serwerze. Na przykład port może reprezentować połączenie z urządzenia z systemem Windows CE przez kabel szeregowy lub maszynie sieciowych z systemem innym niż DCOM. Jeden port specjalny o nazwie portów lokalnych zawiera wszystkich procesów uruchomionych na komputerze lokalnym.  
  
-   Można zidentyfikować sama nazwa lub identyfikator.  
  
-   Można wyliczyć wszystkich procesów działających na porcie uruchomienie i zakończenie tych procesów.  
  
-   Jest reprezentowana przez [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfejsu, który jest tworzony przez przekazanie [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) argument [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] udostępnia domyślny port obsługująca wszystkich komputerów z systemem Windows procesów, natywnych i zarządzanych. Użyć niestandardowego numeru portu musi być implementowana dla połączeń z urządzeń zewnętrznych, które nie są oparte na systemie Windows. Aby przekazać takie porty niestandardowe, dostawcy niestandardowego numeru portu musi również do zaimplementowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Serwery](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Procesy](../../extensibility/debugger/processes.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)