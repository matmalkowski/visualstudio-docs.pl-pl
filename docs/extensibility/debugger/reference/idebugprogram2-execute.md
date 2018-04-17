---
title: IDebugProgram2::Execute | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f7f4e26a5c892e1c796a2b6e2f9371898db21f68
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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