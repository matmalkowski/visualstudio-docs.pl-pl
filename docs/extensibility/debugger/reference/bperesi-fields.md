---
title: BPERESI_FIELDS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BPERESI_FIELDS
helpviewer_keywords: BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e758309c10f9d5dace6a95337130599f34fdb76d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)