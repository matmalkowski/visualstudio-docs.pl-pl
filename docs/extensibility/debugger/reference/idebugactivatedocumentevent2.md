---
title: IDebugActivateDocumentEvent2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce8307776a3dda9f086cdb77d2880228f14a62b2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102551"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
Aparat debugowania (DE) używa tego interfejsu do żądań dokumentu do załadowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugActivateDocumentEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Niemcy implementuje ten interfejs w razie potrzeby można otworzyć pliku źródłowego. Ten interfejs jest implementowany tylko przez aparaty debugowania, które współpracować lub są częścią tłumaczy skryptu. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu (używa SDM [QueryInterface](/cpp/atl/queryinterface) dostępu `IDebugEvent2` interfejs).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Niemcy tworzy i wysyła ten obiekt zdarzenia, kiedy zachodzi potrzeba otwarty plik źródłowy. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) dostarczonych przez SDM, gdy jest on dołączony do debugowanego programu funkcja wywołania zwrotnego.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugActivateDocumentEvent2`.  
  
|Metody|Opis|  
|-------------|-----------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|Pobiera dokument, aby aktywować.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Pobiera kontekst dokumentu, który opisuje sytuację, w tym dokumencie.|  
  
## <a name="remarks"></a>Uwagi  
 Typowy scenariusz, w którym ten interfejs jest używany jest, jeśli wystąpi błąd podczas analizy w kodzie skryptu na stronie HTML, skrypt DE wysyła ten interfejs SDM wyświetlenia dokumentu z powodu błędu analizy.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)