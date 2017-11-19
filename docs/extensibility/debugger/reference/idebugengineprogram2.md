---
title: IDebugEngineProgram2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineProgram2
helpviewer_keywords: IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9e4b7d83f40607dbb94371e4ca3244a9bb5b9a5b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Ten interfejs obsługuje wielowątkowych debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania implementuje ten interfejs obsługuje wiele wątków jednoczesnych debugowania. Ten interfejs jest wdrażany na ten sam obiekt, który implementuje [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Użyj [QueryInterface](/cpp/atl/queryinterface) uzyskać ten interfejs z `IDebugProgram2` interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugEngineProgram2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Zatrzymaj](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Zatrzymuje wszystkie wątki uruchomione w tym programie.|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Oczekuje na wykonanie (lub zatrzymania oczekiwania na wykonanie) występuje dla danego wątku.|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Umożliwia lub nie zezwala na Obliczanie wyrażenia występuje w danym wątku, nawet jeśli program zostanie zatrzymana.|  
  
## <a name="remarks"></a>Uwagi  
 Visual Studio wymaga tego interfejsu w odpowiedzi na [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zdarzenia i ustawić Stany "Obejrzyj dla kroku wątku" i "Obejrzyj dla wyrażenia oceny na wątku" programu. [Zatrzymaj](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) jest wywoływany za każdym razem program jest zatrzymanie; ta metoda zapewnia program szansy zakończyć wszystkie wątki.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)