---
title: IDebugProcessEx2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcessEx2
helpviewer_keywords: IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3d23b1b97145b5e0b24ebfe814aeca5168ef6a06
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Ten interfejs umożliwia sesji debugowania Menedżera (SDM) powiadomić procesu, który jest dołączenie do lub odłączanie od procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawcy niestandardowego numeru portu implementuje ten interfejs dla tego samego obiektu jako [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interfejsu w celu:  
  
-   Obsługa śledzenia sesji połączenia z procesem  
  
-   Obsługa automatyczne dołączanie w wielu aparatami debugowania  
  
 Jeśli wybiera dostawcy niestandardowego numeru portu może zawierać implementację tego interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
  
-   Wywołania SDM [QueryInterface](/cpp/atl/queryinterface) na `IDebugProcess2` interfejs do uzyskania tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugProcessEx2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informuje o tym procesie czy sesji jest teraz debugowania procesu.|  
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informuje o tym procesie czy sesja jest już debugowania procesu.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Dodaje węzłów programu listę aparaty debugowania.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest prywatny między SDM i procesu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)