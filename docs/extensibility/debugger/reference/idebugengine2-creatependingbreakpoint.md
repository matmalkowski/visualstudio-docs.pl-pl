---
title: IDebugEngine2::CreatePendingBreakpoint | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords: IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fdc73a2245390ec04cc3adc2b3a4ac4f5ced3f51
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Tworzy oczekującym punktem przerwania aparat debugowania (DE).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```csharp  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBPRequest`  
 [in] [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) obiektu, który opisuje oczekującym punktem przerwania, aby utworzyć.  
  
 `ppPendingBP`  
 [out] Zwraca [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) obiekt, który reprezentuje oczekującym punktem przerwania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwykle zwraca `E_FAIL` Jeśli `pBPRequest` parametru jest niezgodny z dowolnego języka, obsługiwane przez DE, jeśli `pBPRequest` parametru jest nieprawidłowa lub niekompletna.  
  
## <a name="remarks"></a>Uwagi  
 Oczekującym punktem przerwania jest zasadniczo zbiór wszystkie informacje wymagane do powiązania punktu przerwania do kodu. Oczekującym punktem przerwania, zwracane z tej metody nie jest powiązany z kodu do [powiązać](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) metoda jest wywoływana.  
  
 Dla każdego oczekujących punktu przerwania zestawów użytkownika Menedżera debugowania sesji (SDM) wywołuje tę metodę w każdym DE dołączone. Jest DE, aby sprawdzić, czy punkt przerwania jest prawidłowa dla programów, w tym DE.  
  
 Gdy użytkownik punkt przerwania w wierszu kodu, DE jest bezpłatna powiązać punktu przerwania do najbliższego wiersza w dokumencie, który odpowiada tego kodu. Dzięki temu użytkownik może ustawić punkt przerwania w pierwszym wierszu instrukcji wiele wierszy, ale powiązać go z ostatniego wiersza (w którym przypisać cały kod w informacje o debugowaniu).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób zaimplementować tę metodę dla prostego `CProgram` obiektu. Implementacja DE `IDebugEngine2::CreatePendingBreakpoint` następnie przesłać dalej wszystkie wywołania tej implementacji metody w każdy program.  
  
```  
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)     
{    
  
   // Create and initialize the CPendingBreakpoint object.  
   CComObject<CPendingBreakpoint> *pPending;    
   CComObject<CPendingBreakpoint>::CreateInstance(&pPending);    
   pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);    
   return pPending->QueryInterface(ppPendingBP);    
}    
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [BIND](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)