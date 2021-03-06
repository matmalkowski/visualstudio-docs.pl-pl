---
title: IDebugPortEx2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a6742b18c426c193716151e43cdd5b277c387e4c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31117855"
---
# <a name="idebugportex2"></a>IDebugPortEx2
Ten interfejs umożliwia sesji debugowania kontroli Menedżer (SDM), programów i procesów uruchomionych na porcie.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawcy niestandardowego numeru portu implementuje ten interfejs dla tego samego obiektu, który implementuje [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołania SDM [QueryInterface](/cpp/atl/queryinterface) na `IDebugPort2` interfejs do uzyskania tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugPortEx2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Uruchamia plik wykonywalny.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Wznawia wykonania procesu.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Określa, czy Proces może zostać zakończone.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Kończy proces.|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Pobiera identyfikator procesu samego portu.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Pobiera program skojarzony z węzłem programu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest zwykle prywatnych między SDM i dostawcy niestandardowego numeru portu.  
  
 W razie potrzeby, aparat debugowania (DE) można wyszukać ten interfejs [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfejsu przekazany do [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) i użyj [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) do uruchomienia programu. Nie wymagany, jednak i URZ mogą wykonywać, niezależnie od należy wykonać, aby uruchomić program żądania.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)