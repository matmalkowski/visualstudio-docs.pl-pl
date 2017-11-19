---
title: IDebugThread2::SetNextStatement | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2::SetNextStatement
helpviewer_keywords: IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6dd345fe298af42a69ac076bf92de7df9db82ec2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Ustawia bieżący wskaźnik instrukcji w kontekście podanego kodu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```csharp  
int SetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStackFrame`  
 Zarezerwowane do użytku w przyszłości; Ustaw wartość null.  
  
 `pCodeContext`  
 [in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiektu, który opisuje lokalizacji kodu o do wykonania i jego kontekstu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono innych możliwych wartości.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|Następna instrukcja nie może być w ramce stosu głębiej ramki stosu.|  
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|Następna instrukcja nie jest skojarzony z dowolnym ramki stosu.|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Niektóre aparaty debugowania nie można ustawić następnej instrukcji po wystąpieniu wyjątku.|  
  
## <a name="remarks"></a>Uwagi  
 Wskaźnik instrukcji wskazuje następnej instrukcji lub instrukcji do wykonania. Ta metoda jest używana, aby ponowić próbę wykonania wiersza kodu źródłowego lub aby wymusić wykonanie, aby kontynuować w innej funkcji, na przykład.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)