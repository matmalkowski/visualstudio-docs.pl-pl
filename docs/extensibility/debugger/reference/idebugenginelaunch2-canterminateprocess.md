---
title: IDebugEngineLaunch2::CanTerminateProcess | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords: IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f4c4157d0c3fcdd3e0de4be4fa2fcf39c16ba67a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugenginelaunch2canterminateprocess"></a>IDebugEngineLaunch2::CanTerminateProcess
Określa, czy Proces może zostać zakończone.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CanTerminateProcess (   
   IDebugProcess2* pProcess  
);  
```  
  
```csharp  
int CanTerminateProcess (   
   IDebugProcess2 pProcess  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProcess`  
 [in] [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) obiekt, który reprezentuje ma zostać zakończony.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `S_FALSE` Jeśli aparat nie można przerwać ten proces, na przykład, ponieważ nastąpiła odmowa dostępu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ta metoda zwraca `S_OK`, następnie go [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) można wywołać metody faktycznie zakończenie procesu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)