---
title: IDebugPendingBreakpoint2::SetCondition | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPendingBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugPendingBreakpoint2::SetCondition method
ms.assetid: 0534224f-654f-4862-bc4d-a9a81a5f8899
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 34c47fd8bd4843b74eb78d96723e3aae051616d3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpendingbreakpoint2setcondition"></a>IDebugPendingBreakpoint2::SetCondition
Ustawia lub zmienia warunek skojarzony z oczekującym punktem przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```csharp  
int SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bpCondition`  
 [in] A [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) struktury, która określa warunek, którego chcesz ustawić.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wszelkie warunek, który został wcześniej skojarzony z oczekującym punktem przerwania zostaną utracone. Wszystkie punkty przerwania powiązany z tego czasu punktu przerwania są wywoływane w celu ich warunek do wartości określonej w `bpCondition` parametru.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)