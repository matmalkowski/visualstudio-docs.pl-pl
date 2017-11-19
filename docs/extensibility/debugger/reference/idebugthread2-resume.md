---
title: IDebugThread2::Resume | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2::Resume
helpviewer_keywords: IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 25b0f663b6f512cbe8ea6eaafa2167a6828280c9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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