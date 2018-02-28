---
title: SEEK_START | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1719230909da6f3b5d08c912039bbd23882828fa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="seekstart"></a>SEEK_START
Określa położenie, w którym należy rozpocząć wyszukiwanie w strumieniu dezasemblacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
typedef DWORD SEEK_START;  
```  
  
```csharp  
public enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 SEEK_START_BEGIN  
 Uruchamia wyszukiwanie na początku bieżącego dokumentu.  
  
 SEEK_START_END  
 Uruchamia wyszukiwanie na koniec bieżącego dokumentu.  
  
 SEEK_START_CURRENT  
 Uruchamia wyszukiwania w bieżącym położeniu bieżącego dokumentu.  
  
 SEEK_START_CODECONTEXT  
 Uruchamia wyszukiwanie w kontekście podanego kodu bieżącego dokumentu.  
  
 SEEK_START_CODELOCID  
 Uruchamia wyszukiwanie na identyfikator lokalizacji podanego kodu. Identyfikatory lokalizacji kodu są uzyskiwane przez wywołanie metody [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md).  
  
## <a name="remarks"></a>Uwagi  
 Przekazany jako argument [wyszukiwania](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Wyszukiwanie](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)   
 [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)