---
title: IDebugEngineLaunch2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1abff9f393b34bbf5950c9e56b6f489f332840db
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Używane przez aparat debugowania (DE) do uruchomienia i zakończenia programów.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez niestandardowe DE, jeśli ma specjalne wymagania dotyczące uruchamiania procesu, które nie mogą być obsługiwane wyłącznie przez port niestandardowy. Jest to zazwyczaj wielkość liter, jeśli DE jest częścią interpreter i debugowany proces jest skryptem: interpretera musi być uruchamiany najpierw, a następnie ładowany i uruchomić skrypt. Port można uruchomić interpretera, ale skrypt może wymagają specjalnej obsługi, (czyli gdzie DE ma rolę). Ten interfejs jest implementowany tylko wtedy, gdy istnieją unikatowe wymagania dotyczące uruchamiania programu, który nie może obsługiwać użyć niestandardowego numeru portu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest wywoływana przez menedżera sesji debugowania (SDM) Jeśli SDM można uzyskać interfejsu z [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfejs (przy użyciu metody QueryInterface). Jeśli ten interfejs można uzyskać, SDM wie, że DE ma specjalne wymagania i wywołuje ten interfejs, aby uruchomić program zamiast portu, uruchom ją.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugEngineLaunch2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Uruchamia proces, za pomocą DE.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Wznawia przetworzyć wykonywania.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Określa, czy Proces może zostać zakończone.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Kończy proces.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)