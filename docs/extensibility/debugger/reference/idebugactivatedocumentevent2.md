---
title: IDebugActivateDocumentEvent2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugActivateDocumentEvent2
helpviewer_keywords: IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c6ace15a6e2a88aa214261d3d8ec137ebb6d7ebe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)