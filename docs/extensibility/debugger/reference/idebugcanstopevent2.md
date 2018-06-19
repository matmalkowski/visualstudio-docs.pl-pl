---
title: IDebugCanStopEvent2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 48f049648fcbd93d7ad7411a4dfeba8bbdb4431d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105609"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Ten interfejs jest używany do żądania Menedżer debugowania sesji (SDM), czy można zatrzymać w bieżącej lokalizacji kodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs obsługuje krokowe wykonywanie kodu źródłowego. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu (używa SDM [QueryInterface](/cpp/atl/queryinterface) dostępu `IDebugEvent2` interfejs).  
  
 Implementację tego interfejsu muszą komunikować się wywołanie SDM [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) do aparatu debugowania. Na przykład można to zrobić z następującym komunikatem publikowanego obsługa wątku komunikatów aparat debugowania lub obiekt zawierający implementację tego interfejsu może utrzymywanie odwołania do aparatu debugowania i wywołania zwrotnego do aparatu debugowania przy użyciu flagi przekazywane do `IDebugCanStopEvent2::CanStop`.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Niemcy może wysyłać ta metoda zawsze, gdy DE monitu o kontynuowanie wykonywania i DE jest krokowe wykonywanie kodu. To zdarzenie jest wysyłany przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) dostarczonych przez SDM, gdy jest on dołączony do debugowanego programu funkcja wywołania zwrotnego.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugCanStopEvent2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Pobiera przyczynę tego zdarzenia.|  
|[Wartości właściwości CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Określa, czy debugowanego programu należy zatrzymać w lokalizacji tego zdarzenia (oraz wysyłania zdarzenia opisujące przyczynę zatrzymywania) lub tylko kontynuować działanie.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Pobiera kontekst dokumentu, który opisuje lokalizacja tego zdarzenia.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Pobiera kontekst kodu, który opisuje lokalizacja tego zdarzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Niemcy wysyła ten interfejs, jeśli czynności użytkownika do funkcji i DE znajdzie żadnych informacji debugowania lub informacje o debugowaniu istnieje, ale DE nie wie, jeśli dla tej lokalizacji można wyświetlić kodu źródłowego.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)