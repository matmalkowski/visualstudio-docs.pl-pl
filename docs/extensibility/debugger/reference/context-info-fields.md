---
title: CONTEXT_INFO_FIELDS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CONTEXT_INFO_FIELDS
helpviewer_keywords: CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8f0316e8822706b26103f02eda1849568cf79994
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
Określa, jakie informacje pobrać o kontekście pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 CIF_MODULEURL  
 Inicjowanie użycia `bstrModuleUrl` pole [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) struktury.  
  
 CIF_FUNCTION  
 Inicjowanie użycia `bstrFunction` pole `CONTEXT_INFO` struktury.  
  
 CIF_FUNCTIONOFFSET  
 Inicjowanie użycia `posFunctionOffset` pole `CONTEXT_INFO` struktury.  
  
 CIF_ADDRESS  
 Inicjowanie użycia `bstrAddress` pole `CONTEXT_INFO` struktury.  
  
 CIF_ADDRESSOFFSET  
 Inicjowanie użycia `bstrAddressOffset` pole `CONTEXT_INFO` struktury.  
  
 CIF_ALLFIELDS  
 Inicjowanie użycia wszystkie pola `CONTEXT_INFO` struktury.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są przekazywane parametr [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) metody, aby wskazać, które pola [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) struktury mają być zainicjowany.  
  
 Te flagi są również używane w celu wskazania, które pola `CONTEXT_INFO` struktury są używane i ważne, gdy struktura jest zwracany.  
  
 Te wartości mogą być łączone z bitowego OR.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)