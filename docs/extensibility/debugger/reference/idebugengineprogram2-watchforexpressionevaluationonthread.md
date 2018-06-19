---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a3f89502beeb1e8165450c7c07f3f55f83dd39e1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112336"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Umożliwia lub nie zezwala na Obliczanie wyrażenia występuje w danym wątku, nawet jeśli zostało zatrzymane.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT WatchForExpressionEvaluationOnThread(   
   IDebugProgram2*       pOriginatingProgram,  
   DWORD                 dwTid,  
   DWORD                 dwEvalFlags,  
   IDebugEventCallback2* pExprCallback,  
   BOOL                  fWatch  
);  
```  
  
```csharp  
int WatchForExpressionEvaluationOnThread(   
   IDebugProgram2       pOriginatingProgram,  
   uint                  dwTid,  
   uint                  dwEvalFlags,  
   IDebugEventCallback2 pExprCallback,  
   int                   fWatch  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pOriginatingProgram`  
 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekt reprezentujący program, który jest obliczenie wyrażenia.  
  
 `dwTid`  
 [in] Określa identyfikator wątku.  
  
 `dwEvalFlags`  
 [in] Kombinacja flag z [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) wyliczenie określające sposób oceny ma zostać wykonane.  
  
 `pExprCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) obiektu ma być używany do wysyłania zdarzeń debugowania podczas obliczania wyrażenia.  
  
 `fWatch`  
 [in] Jeśli różna od zera (`TRUE`), umożliwia obliczanie wyrażenia w wątku identyfikowane przez `dwTid`; w przeciwnym razie wartość zero (`FALSE`) nie zezwala na Obliczanie wyrażenia w tym wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Gdy Menedżer debugowania sesji (SDM) żąda programu identyfikowane przez `pOriginatingProgram` parametru można obliczyć wyrażenia, powiadomi wszystkie inne programy dołączone przez wywołanie tej metody.  
  
 Szacowanie wyrażeń w jednym programie może uruchomić kod w innym, ze względu na obliczanie funkcji lub oceny dowolnego `IDispatch` właściwości. W związku z tym ta metoda umożliwia obliczanie wyrażenia zostać uruchomione i ukończone, nawet jeśli wątek może być zatrzymana w tym programie.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)