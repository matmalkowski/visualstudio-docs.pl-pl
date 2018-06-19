---
title: IDebugThread2::Resume | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7f51fdb05fb44a23227a1a35fd6504f2d18aa804
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121420"
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