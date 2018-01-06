---
title: IDebugBoundBreakpoint2::SetCondition | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBoundBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugBoundBreakpoint2::SetCondition method
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 88cfedfd31532750d9db4fd00f43e507e6812e2b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugboundbreakpoint2setcondition"></a>IDebugBoundBreakpoint2::SetCondition
Ustawia lub zmienia warunek skojarzony z tym powiązania punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```csharp  
int SetCondition(   
   enum_BP_CONDITION bpCondition  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bpCondition`  
 [in] Wartość z zakresu od [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) wyliczenie opisujące stan.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `E_BP_DELETED` Jeśli stan obiektu powiązanego punktu przerwania jest równa `BPS_DELETED` (część [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) wyliczenie).  
  
## <a name="remarks"></a>Uwagi  
 Wszelkie warunek, który został wcześniej skojarzony z tego punktu przerwania zostaną utracone.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)