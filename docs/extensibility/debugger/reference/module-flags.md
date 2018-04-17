---
title: MODULE_FLAGS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 945a4a0fd5a7de1e9d04d409390caddfc718d92d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="moduleflags"></a>MODULE_FLAGS
Używany w przypadku modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
typedef DWORD MODULE_FLAGS;  
```  
  
```csharp  
public enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 MODULE_FLAG_NONE  
 Określa nie modułu.  
  
 MODULE_FLAG_SYSTEM  
 Określa moduł systemowy.  
  
 MODULE_FLAG_SYMBOLS  
 Określa moduł symbolu.  
  
 MODULE_FLAG_64BIT  
 Określa moduł 64-bitowych.  
  
 MODULE_FLAG_OPTIMIZED  
 Określa, że moduł został zoptymalizowany. Ten stan jest widoczny w **modułów** okna.  
  
 MODULE_FLAG_UNOPTIMIZED  
 Określa, że moduł nie został zoptymalizowany. Ten stan jest widoczny w **modułów** okna. Jest to domyślny stan.  
  
## <a name="remarks"></a>Uwagi  
 Używany do `m_dwModuleFlags` członkiem [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struktury.  
  
 Te flagi mogą być łączone z bitowego `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)