---
title: BPREQI_FIELDS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BPREQI_FIELDS
helpviewer_keywords: BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 212949df682a71dd3debc28001bcdf07dbe8c061
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="bpreqifields"></a>BPREQI_FIELDS
Określa informacje, które mają zostać pobrane o żądaniu punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
typedef DWORD BPREQI_FIELDS;  
```  
  
```csharp  
public enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 BPREQI_BPLOCATION  
 Inicjowanie użycia `bpLocation` pola (lokalizacji punktu przerwania) [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) lub [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktury.  
  
 BPREQI_LANGUAGE  
 Inicjowanie użycia `guidLanguage` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.  
  
 BPREQI_PROGRAM  
 Inicjowanie użycia `pProgram` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.  
  
 BPREQI_PROGRAMNAME  
 Inicjowanie użycia `bstrProgramName` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.  
  
 BPREQI_THREAD  
 Inicjowanie użycia `pThread` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.  
  
 BPREQI_THREADNAME  
 Inicjowanie użycia `bstrThreadName` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.  
  
 BPREQI_PASSCOUNT  
 Inicjowanie użycia `bpPassCount` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.  
  
 BPREQI_CONDITION  
 Inicjowanie użycia `bpCondition` pola (warunku punktu przerwania) `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.  
  
 BPREQI_FLAGS  
 Inicjowanie użycia `dwFlags` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.  
  
 BPREQI_ALLOLDFIELDS  
 Inicjowanie użycia wszystkie pola z `BP_REQUEST_INFO` struktury.  
  
 BPREQI_VENDOR  
 Inicjowanie użycia `guidVendor` pole `BP_REQUEST_INFO2` struktury.  
  
 BPREQI_CONSTRAINT  
 Inicjowanie użycia `bstrConstraint` pole `BP_REQUEST_INFO2` struktury.  
  
 BPREQI_TRACEPOINT  
 Inicjowanie użycia `bstrTracepoint` pole `BP_REQUEST_INFO2` struktury.  
  
 BPREQI_ALLFIELDS  
 Określa wszystkie pola `BP_REQUEST_INFO2` struktury.  
  
## <a name="remarks"></a>Uwagi  
 Przekazany jako argument [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) i [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) metod, aby określić, które pola [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) i [BP_REQUEST_INFO2 ](../../../extensibility/debugger/reference/bp-request-info2.md) struktury są do zainicjowania.  
  
 Te flagi są również używane w celu wskazania, które pola `BP_REQUEST_INFO` i `BP_REQUEST_INFO2` struktury są używane i ważne, gdy każda struktura jest zwracany.  
  
 Te wartości mogą być łączone z bitowego `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)