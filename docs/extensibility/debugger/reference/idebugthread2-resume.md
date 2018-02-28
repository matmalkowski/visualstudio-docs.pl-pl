---
title: IDebugThread2::Resume | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5de844c3b07a509f266e2f9d278d1f78bea2b089
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Wznawia wykonywanie wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwSuspendCount`  
 [out] Zwraca liczbę wstrzymania po wykonaniu operacji wznowienia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Każdy wywołanie zmniejsza to metoda liczba zawieszenia aż osiągnie 0 po tym czasie, wykonanie faktycznie zostanie wznowione. Ten licznik wstrzymania jest wyświetlany w **wątków** okna debugowania.  
  
 Dla każdego wywołania tej metody, musi być poprzednie wywołanie [zawieszenia](../../../extensibility/debugger/reference/idebugthread2-suspend.md) metody. Liczba Wstrzymaj Określa, ile razy `IDebugThread2::Suspend` wykonanej do tej pory zostanie wywołana metoda.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Wstrzymaj](../../../extensibility/debugger/reference/idebugthread2-suspend.md)