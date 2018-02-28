---
title: IDebugThread2::GetProgram | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThread2::GetProgram
helpviewer_keywords:
- IDebugThread2::GetProgram
ms.assetid: 8c9c5ea1-2031-472e-bc8f-30e22e754566
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1fff62ec1f84b6574d9c4b2d1f1e648644173360
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugthread2getprogram"></a>IDebugThread2::GetProgram
Pobiera program, w którym jest uruchomiony wątek.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetProgram (   
   IDebugProgram2** ppProgram  
);  
```  
  
```csharp  
int GetProgram (   
   out IDebugProgram2 ppProgram  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppProgram`  
 [out] Zwraca [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekt, który reprezentuje program ten wątek jest uruchomiony w.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)