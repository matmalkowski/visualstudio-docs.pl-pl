---
title: MODULE_INFO_FIELDS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fcc6bd76a4a9aecade72347613ed4f36968c65eb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31125932"
---
# <a name="moduleinfofields"></a>MODULE_INFO_FIELDS
Określa flagi dla informacji debugowania modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
typedef DWORD MODULE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 MIF_NONE  
 Inicjowanie/użycie żadne z pól w strukturze.  
  
 MIF_NAME  
 Inicjowanie użycia `m_bstrName` w [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struktury.  
  
 MIF_URL  
 Inicjowanie użycia `m_bstrUrl` w `MODULE_INFO` struktury.  
  
 MIF_VERSION  
 Inicjowanie użycia `m_bstrVersion` w `MODULE_INFO` struktury.  
  
 MIF_DEBUGMESSAGE  
 Inicjowanie użycia `m_bstrDebugMessage` w `MODULE_INFO` struktury.  
  
 MIF_LOADADDRESS  
 Inicjowanie użycia `m_addrLoadAddress` w `MODULE_INFO` struktury.  
  
 MIF_PREFFEREDADDRESS  
 Inicjowanie użycia `m_addrPreferredLoadAddress` w `MODULE_INFO` struktury.  
  
 MIF_SIZE  
 Inicjowanie użycia `m_dwSize` w `MODULE_INFO` struktury.  
  
 MIF_LOADORDER  
 Inicjowanie użycia `m_dwLoadOrder` w `MODULE_INFO` struktury.  
  
 MIF_TIMESTAMP  
 Inicjowanie użycia `m_TimeStamp` w `MODULE_INFO` struktury.  
  
 MIF_URLSYMBOLLOCATION  
 Inicjowanie użycia `m_bstrUrlSymbolLocation` w `MODULE_INFO` struktury.  
  
 MIF_FLAGS  
 Inicjowanie użycia `m_dwModuleFlags` w `MODULE_INFO` struktury.  
  
 MIF_ALLFIELDS  
 Inicjowanie/Użyj wszystkich pól w `MODULE_INFO` struktury.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są przekazywane jako argument [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) metody, aby wskazać, które pola [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struktury mają być zainicjowany.  
  
 Te wartości są również używane w `MODULE_INFO` struktury, aby wskazać pola, które są używane i prawidłowe.  
  
 Te flagi mogą być łączone z bitowego `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)