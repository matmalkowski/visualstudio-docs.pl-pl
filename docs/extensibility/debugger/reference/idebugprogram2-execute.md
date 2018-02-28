---
title: IDebugProgram2::Execute | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2e53f13aea93de8f39c5802dd2a12598ad938f64
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Jest nadal uruchomiony ten program w stanie zatrzymania. Wszelkie poprzednie stan wykonywania (na przykład krok) jest usuwany, i uruchomi ponownie wykonywania.  
  
> [!NOTE]
>  Ta metoda jest przestarzała. Użyj [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) metody zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Execute(  
   void  
);  
```  
  
```csharp  
int Execute();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Gdy użytkownik uruchomi wykonywania w stanie zatrzymania wątku przez inny program, ta metoda jest wywoływana dla tego programu. Ta metoda również jest wywoływana, gdy użytkownik wybierze **Start** polecenie **debugowania** menu w środowisku IDE. Implementacja tej metody może być równie proste co wywołanie [Wznów](../../../extensibility/debugger/reference/idebugthread2-resume.md) metody w bieżącym wątku w programie.  
  
> [!WARNING]
>  Nie wysyłaj zdarzeniem zatrzymującym lub natychmiastowego zdarzenia (synchroniczne) w celu [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może się zawiesić.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Wznów](../../../extensibility/debugger/reference/idebugthread2-resume.md)