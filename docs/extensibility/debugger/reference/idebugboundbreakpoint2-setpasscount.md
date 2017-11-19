---
title: IDebugBoundBreakpoint2::SetPassCount | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBoundBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugBoundBreakpoint2::SetPassCount method
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4bc3ca953a6a0eacb20862627d2cbc39f11d404b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
Ustawia lub zmienia liczba hasło skojarzone z tym powiązania punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```csharp  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bpPassCount`  
 [in] [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) strukturę, która określa liczbę przebiegu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `E_BP_DELETED` Jeśli stan obiektu powiązanego punktu przerwania jest równa `BPS_DELETED` (część [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) wyliczenie).  
  
## <a name="remarks"></a>Uwagi  
 Liczba przebiegu Określa, kiedy punkt przerwania jest uruchamiany. Bieżący przebieg lub liczba trafień można uzyskać przez wywołanie metody [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) metody.  
  
 Dowolnej liczbie przebiegu, który został wcześniej skojarzony z tego punktu przerwania zostaną utracone.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)