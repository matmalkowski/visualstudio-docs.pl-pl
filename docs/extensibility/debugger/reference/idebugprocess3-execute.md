---
title: IDebugProcess3::Execute | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess3::Execute
helpviewer_keywords: IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 96b18bdb8aa0097071369a01013772dc3bd0d5bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Nadal uruchomienie tego procesu w stanie zatrzymania. Wszelkie poprzedniego stanu wykonywania (na przykład krok) jest wyczyszczone i uruchamiania procesu wykonywania ponownie.  
  
> [!NOTE]
>  Ta metoda powinna być używana zamiast [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt reprezentujący na wykonanie wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Gdy użytkownik uruchomi wykonywania z zatrzymana w wątku w innym procesie, ta metoda jest wywoływana w tym procesie. Ta metoda również jest wywoływana, gdy użytkownik wybierze **Start** polecenie **debugowania** menu w środowisku IDE. Implementacja tej metody może być równie proste co wywołanie [Wznów](../../../extensibility/debugger/reference/idebugthread2-resume.md) metody w bieżącym wątku w procesie.  
  
> [!WARNING]
>  Nie wysyłaj zdarzeniem zatrzymującym lub natychmiastowego zdarzenia (synchroniczne) w celu [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może się zawiesić.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Wznów](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)