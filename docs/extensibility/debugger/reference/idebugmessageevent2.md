---
title: IDebugMessageEvent2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMessageEvent2
helpviewer_keywords: IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5e14e8ea2df83520724b9f6663c9624d54cf772c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Ten interfejs jest używany przez aparat debugowania (DE), aby wysłać wiadomość do programu Visual Studio, który wymaga od użytkownika odpowiedzi.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Niemcy implementuje ten interfejs do wysyłania komunikatu do programu Visual Studio wymaga odpowiedzi użytkownika. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu. Używa SDM [QueryInterface](/cpp/atl/queryinterface) dostępu `IDebugEvent2` interfejsu.  
  
 Implementację tego interfejsu muszą komunikować się wywołanie Visual Studio [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) do DE. Na przykład można to zrobić z następującym komunikatem publikowanego obsługa wątku komunikatów DE lub obiekt zawierający implementację tego interfejsu może przechowuje odwołania do DE i wywołanie zwrotne DE z odpowiedzią przekazany `IDebugMessageEvent2::SetResponse`.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Niemcy tworzy i wysyła ten obiekt zdarzeń, aby wyświetlić komunikat dla użytkownika, który wymaga odpowiedzi. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcja wywołania zwrotnego, która jest dostarczana przez SDM, gdy jest on dołączony do debugowanego programu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugMessageEvent2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Pobiera komunikat do wyświetlenia.|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Ustawia odpowiedzi z pola wiadomości.|  
  
## <a name="remarks"></a>Uwagi  
 Niemcy będą używać tego interfejsu, jeśli wymaga ona określoną odpowiedź od użytkownika dla danego komunikatu. Na przykład, jeśli DE pobiera komunikat "Odmowa dostępu" po próbie zdalnie dołączyć do programu, DE wysyła tego konkretnego komunikatu dla programu Visual Studio w `IDebugMessageEvent2` zdarzenie z styl okna komunikatu `MB_RETRYCANCEL`. Dzięki temu użytkownikowi ponów próbę lub anulować operacji dołączania.  
  
 Niemcy Określa, jak ten komunikat ma zostać obsłużone przez zgodne z konwencjami funkcji Win32 `MessageBox` (zobacz [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8) szczegółowe informacje).  
  
 Użyj [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) interfejs do wysyłania komunikatów do programu Visual Studio, które nie wymagają odpowiedzi od użytkownika.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)