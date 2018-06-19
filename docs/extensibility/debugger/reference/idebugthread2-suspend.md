---
title: IDebugThread2::Suspend | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f865194e023ed0311f06988dd026fb2b123aaf4a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121664"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Wstrzymuje wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Suspend (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
HRESULT Suspend (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwSuspendCount`  
 [out] Zwraca liczbę wstrzymania po wykonaniu operacji wstrzymania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Każde wywołanie tej metody zwiększa liczbę Wstrzymaj powyżej 0. Ten licznik wstrzymania jest wyświetlany w **wątków** okna debugowania.  
  
 Dla każdego wywołania tej metody, musi być wywołanie nowsze [Wznów](../../../extensibility/debugger/reference/idebugthread2-resume.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Wznów](../../../extensibility/debugger/reference/idebugthread2-resume.md)