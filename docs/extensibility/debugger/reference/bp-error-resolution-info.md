---
title: BP_ERROR_RESOLUTION_INFO | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 58358efb6822fab2141f3d9957829470a9fd0398
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="bperrorresolutioninfo"></a>BP_ERROR_RESOLUTION_INFO
Opisuje rozwiązanie przerwania błędu, takie jak lokalizacja, program i wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _BP_ERROR_RESOLUTION_INFO {   
   BPERESI_FIELDS         dwFields;  
   BP_RESOLUTION_LOCATION bpResLocation;  
   IDebugProgram2*        pProgram;  
   IDebugThread2*         pThread;  
   BSTR                   bstrMessage;  
   BP_ERROR_TYPE          dwType;  
} BP_ERROR_RESOLUTION_INFO;  
```  
  
```csharp  
public struct BP_ERROR_RESOLUTION_INFO {   
   public uint                   dwFields;  
   public BP_RESOLUTION_LOCATION bpResLocation;  
   public IDebugProgram2         pProgram;  
   public IDebugThread2          pThread;  
   public string                 bstrMessage;  
   public uint                   dwType;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `dwFields`  
 Kombinacja wartości z [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) wyliczenie opisujące są wypełnione pola, które tej struktury.  
  
 `bpResLocation`  
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Unii, który określa rozwiązania lokalizacji punktu przerwania.  
  
 `pProgram`  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekt, który reprezentuje aplikacji, w którym wystąpił błąd punktu przerwania.  
  
 `pThread`  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje wątku, w którym jest uruchomiona aplikacja, który wygenerował błąd punktu przerwania.  
  
 `bstrMessage`  
 Ciąg zawierający dowolny komunikat ostrzeżenia lub błędu, wynikające z tego rozwiązania błędów.  
  
 `dwType`  
 Wartość z zakresu od [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) wyliczenie określający typ błędu punktu przerwania.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest zwracana z [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)   
 [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)