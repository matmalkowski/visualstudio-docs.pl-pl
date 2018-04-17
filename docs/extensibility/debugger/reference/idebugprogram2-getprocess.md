---
title: IDebugProgram2::GetProcess | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4a0e51725cf809e5c224fd438e507bcfde6ca2c5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Pobierz proces tego programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```csharp  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppProcess`  
 [out] Zwraca [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interfejs, który reprezentuje procesu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie implementuje aparat debugowania (DE) [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) interfejsu, DE implementacja tej metody należy zawsze zwracają `E_NOTIMPL` URZ nie może ustalić, który proces jest uruchomiony w i dlatego nie można spełnia implementacja tej metody.  
  
 Implementowanie `IDebugEngineLaunch2` interfejs oznacza, że DE musi wiedzieć, jak utworzyć procesu; w związku z tym DE implementacja [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejsu jest w stanie wiedzieć, jakie procesy jest uruchomiony w.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)