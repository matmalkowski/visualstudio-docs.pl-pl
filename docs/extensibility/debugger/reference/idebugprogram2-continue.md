---
title: IDebugProgram2::Continue | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::Continue
helpviewer_keywords: IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 81a8bf23ee0272f448c49b6d58d194d3ba261509
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Jest nadal uruchomiony ten program w stanie zatrzymania. Wszelkie poprzedniego stanu wykonywania (na przykład krok) jest zachowywana, i uruchomi ponownie wykonywania.  
  
> [!NOTE]
>  Ta metoda jest przestarzała. Użyj [Kontynuuj](../../../extensibility/debugger/reference/idebugprocess3-continue.md) metody zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Continue(   
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(   
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana dla tego programu, niezależnie od tego, ile programy są debugowane lub program, który wygenerował zdarzenie zatrzymania. Wdrożenie musi zachować poprzedni stan wykonywania (na przykład krok) i kontynuować działanie, tak jakby nie było nigdy nie zatrzymane przed ukończeniem jego wcześniejszego wykonania. Oznacza to jeśli wątek w tym programie wykonywanych operacji przejścia i została zatrzymana, ponieważ inny program zatrzymane, a następnie ta metoda została wywołana, program wykonać operację przejścia.  
  
> [!WARNING]
>  Nie wysyłaj zdarzeniem zatrzymującym lub natychmiastowego zdarzenia (synchroniczne) w celu [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może się zawiesić.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)