---
title: IDebugThread2::Suspend | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2::Suspend
helpviewer_keywords: IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4c689cf4b8295fb17a11bef23c8dca70144421d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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