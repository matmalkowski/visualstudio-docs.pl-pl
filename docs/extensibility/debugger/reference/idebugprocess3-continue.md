---
title: IDebugProcess3::Continue | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess3::Continue
helpviewer_keywords: IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f666f35a71f65b839073e7d360bc357627fb7c5f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Nadal uruchomienie tego procesu w stanie zatrzymania. Wszelkie poprzedniego stanu wykonywania (na przykład krok) jest zachowywana, i uruchamiania procesu wykonywania ponownie.  
  
> [!NOTE]
>  Ta metoda powinna być używana zamiast [Kontynuuj](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
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
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt reprezentujący wątku będzie kontynuowane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana w tym procesie, niezależnie od tego, jak wiele procesów są debugowane lub proces, który wygenerował zdarzenie zatrzymania. Wdrożenie musi zachować poprzedni stan wykonywania (na przykład krok) i kontynuować działanie, tak jakby nie było nigdy nie zatrzymane przed ukończeniem jego wcześniejszego wykonania. Oznacza to, jeśli wątek ten proces wykonywanych operacji przejścia i została zatrzymana, ponieważ niektóre inne proces został zatrzymany, a następnie `Continue` została wywołana, określony wątek należy wykonać operację przejścia.  
  
 **Ostrzeżenie** nie wysyłaj zdarzeniem zatrzymującym lub natychmiastowego zdarzenia (synchroniczne) w celu [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może się zawiesić.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)