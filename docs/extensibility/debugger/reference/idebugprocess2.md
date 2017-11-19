---
title: IDebugProcess2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2
helpviewer_keywords: IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d8b349bee09f068a5777ecc212223c36951236ee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess2"></a>IDebugProcess2
Ten interfejs reprezentuje procesu uruchomionego na porcie. Jeśli port jest port lokalny, następnie `IDebugProcess2` zazwyczaj reprezentuje fizyczny procesu na komputerze lokalnym.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez dostawcę niestandardowego numeru portu do zarządzania programami jako grupa. Ten interfejs musi być implementowana przez dostawcę portu.  
  
 Jeśli obsługuje uruchamianie programu przy użyciu aparatu debugowania również implementuje ten interfejs [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest wywoływana przede wszystkim przez Menedżera debugowania sesji (SDM) w celu interakcji z grupy programów, które zostały zidentyfikowane w tym procesie.  
  
 Wywołanie [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) lub [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) uzyskać tego interfejsu. Ten interfejs jest także zwracany przez wywołanie metody `IDebugEngineLaunch2::LaunchSuspended`.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugProcess2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Pobiera opis procesu.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Wylicza programy, które są zawarte w tym procesie.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Pobiera tytuł, przyjazną nazwę lub nazwę pliku procesu.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Pobiera wystąpienie przez ten proces jest uruchomiony na serwerze maszyny.|  
|[Zakończenie](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Kończy proces.|  
|[Dołącz](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Dołącza do procesu.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Określa, czy model SDM można odłączyć procesu.|  
|[Odłączanie](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Odłącza debugera w procesie.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Pobiera identyfikator procesu systemu.|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Pobiera unikatowy identyfikator globalny tego procesu.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [PRZESTARZAŁY]|Pobiera nazwę sesji, która jest debugowania procesu.<br /><br /> [PRZESTARZAŁY. NALEŻY ZAWSZE POWROTU `E_NOTIMPL`.]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Wylicza wątki uruchomione w procesie.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Żądania wysyłane przez następnego programu Uruchamianie kodu w Zatrzymaj ten proces.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Pobiera portu, którego ten proces.|  
  
## <a name="remarks"></a>Uwagi  
 `IDebugProcess2` Zawiera jeden lub więcej [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejsów.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [Dalej](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)