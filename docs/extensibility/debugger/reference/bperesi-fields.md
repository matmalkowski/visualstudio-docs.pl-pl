---
title: BPERESI_FIELDS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2280740766e20a048f57e58590cc529d98b85264
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="bperesifields"></a>BPERESI_FIELDS
Określa informacje, które mają zostać pobrane rozstrzygnięcia punkt przerwania nie powiodło się.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 PERESI_BPRESLOCATION  
 Inicjowanie użycia `bpResLocation` pola (lokalizacji punktu przerwania rozpoznawania) [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struktury.  
  
 BPERESI_PROGRAM  
 Inicjowanie użycia `pProgram` pole `BP_ERROR_RESOLUTION_INFO` struktury.  
  
 BPERESI_THREAD  
 Inicjowanie użycia `pThread` pole `BP_ERROR_RESOLUTION_INFO` struktury.  
  
 BPERESI_MESSAGE  
 Inicjowanie użycia `bstrMessage` pole `BP_ERROR_RESOLUTION_INFO` struktury.  
  
 BPERESI_TYPE  
 Inicjowanie użycia `dwType` pola (typ punktu przerwania) `BP_ERROR_RESOLUTION_INFO` struktury.  
  
 BPERESI_ALLFIELDS  
 Inicjowanie użycia wszystkie pola `BP_ERROR_RESOLUTION_INFO` struktury.  
  
## <a name="remarks"></a>Uwagi  
 Przekazany jako parametr [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) metody, aby wskazać, które pola [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struktury mają być zainicjowany.  
  
 Te wartości są również używane w celu wskazania, które pola w `BP_ERROR_RESOLUTION_INFO` struktury są używane i prawidłowe, gdy jest zwracany tej struktury.  
  
 Te wartości mogą być łączone z bitowego `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)