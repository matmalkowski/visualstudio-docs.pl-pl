---
title: IDebugCanStopEvent2::CanStop | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a3e2507ba86e00434c12a67ba70cad51fa5850ce
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Czy chcesz zatrzymać w bieżącej lokalizacji kodu lub po prostu kontynuowania wykonywania powiadamia aparat debugowania (DE).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```csharp  
int CanStop (   
   int fCanStop  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fCanStop`  
 [in] Niezerowa (`TRUE`) Jeśli DE powinna zostać przerwana w bieżącej lokalizacji kodu; w przeciwnym razie wartość zero (`FALSE`).  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Odbiorcy zdarzeń to zwykle wymaga [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) metodę, aby określić przyczynę DE chce, aby zatrzymać, a następnie wywołania `IDebugCanStopEvent2::CanStop` metody z właściwą odpowiedź.  
  
 Jeśli zostanie zatrzymana DE, wysyła odpowiednie zdarzenie, opisujący przyczynę zatrzymania. Zazwyczaj są dwa zdarzenia, które są wysyłane, użytkownika lub sygnał przerwania, reprezentowany przez [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) interfejsu i zdarzenie punktu przerwania reprezentowany przez [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)