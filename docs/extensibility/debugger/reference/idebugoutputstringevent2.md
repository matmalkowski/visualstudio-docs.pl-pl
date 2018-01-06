---
title: IDebugOutputStringEvent2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugOutputStringEvent2
helpviewer_keywords: IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f222df8aa2a6fc35db08ceae3e8f49dfe7537960
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
Ten interfejs jest wysyłane przez aparat debugowania (DE) z menedżerem sesji debugowania (SDM) do ciągu wyjściowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugOutputStringEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Niemcy implementuje ten interfejs do wysyłania ciąg **dane wyjściowe** okno środowiska IDE. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu. Używa SDM [QueryInterface](/cpp/atl/queryinterface) dostępu `IDebugEvent2` interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Niemcy tworzy i wysyła ten obiekt zdarzenia do wysłania ciąg **dane wyjściowe** okna. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcja wywołania zwrotnego, która jest dostarczana przez SDM, gdy jest on dołączony do debugowanego programu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugOutputStringEvent2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Pobiera komunikat zawiera.|  
  
## <a name="remarks"></a>Uwagi  
 Na przykład za pomocą kodu niezarządzanego, ciąg jako dane wyjściowe może prowadzić gdy debugowany program wysyła ciąg do środowiska Win32 `OutputDebugString` funkcji. Ten ciąg jest przechwycony przez Niemcy i wysłane na SDM jako `IDebugOutputStringEvent2` zdarzeń.  
  
 Użyj [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) można wysłać komunikatu, która wymaga reakcji użytkownika.  
  
 Użyj [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) wysłać komunikat o błędzie, który nie wymaga odpowiedzi.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)