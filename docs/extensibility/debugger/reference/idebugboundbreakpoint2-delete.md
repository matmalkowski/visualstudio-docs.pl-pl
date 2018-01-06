---
title: IDebugBoundBreakpoint2::Delete | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBoundBreakpoint2::Delete
helpviewer_keywords:
- Delete method
- IDebugBoundBreakpoint2::Delete method
ms.assetid: 7088dc66-f24a-446f-a52a-397d02457a41
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c526b821af16c8d9f0f7931be7f7aa60397ce400
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugboundbreakpoint2delete"></a>IDebugBoundBreakpoint2::Delete
Usuwa punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Delete(   
   void   
);  
```  
  
```csharp  
int Delete();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `E_BP_DELETED` Jeśli stan obiektu powiązanego punktu przerwania jest równa `BPS_DELETED` (część [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) wyliczenie).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób zaimplementować tę metodę dla prostego `CBoundBreakpoint` obiekt ujawniający [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfejsu.  
  
```  
HRESULT CBoundBreakpoint::Delete(void)    
{    
   HRESULT hr;    
  
   // Verify that the bound breakpoint has not been   
   // deleted. If deleted, then return hr = E_BP_DELETED.    
   if (m_state != BPS_DELETED)    
   {    
      m_pInterp->RemoveBreakpoint(m_sbstrDoc, this);    
  
      // Change the state of the breakpoint to BPS_DELETED.    
      m_state = BPS_DELETED;    
      hr = S_OK;    
   }    
   else    
   {    
      hr = E_BP_DELETED;    
   }    
  
   return hr;    
}     
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)