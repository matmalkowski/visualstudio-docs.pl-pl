---
title: IDebugProgram2::Step | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::Step
helpviewer_keywords: IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0e4b8533c1b6a14c61fc556f06594945037bbbd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Wykonuje kroku.  
  
> [!NOTE]
>  Ta metoda jest przestarzała. Użyj [krok](../../../extensibility/debugger/reference/idebugprocess3-step.md) metody zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```csharp  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje wątku jest przeprowadził.  
  
 `sk`  
 [in] Wartość z zakresu od [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) wyliczenia, które określa rodzaj kroku.  
  
 `step`  
 [in] Wartość z zakresu od [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) wyliczenia, który określa jednostki kroku (na przykład przy użyciu instrukcji lub instrukcji).  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku braku dowolnego synchronizacja wątku lub komunikacji między wątkami, inne wątki w programie należy uruchamiać przy przechodzeniu jest danego wątku.  
  
> [!WARNING]
>  Nie wysyłaj zdarzeniem zatrzymującym lub natychmiastowego zdarzenia (synchroniczne) w celu [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może się zawiesić.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)