---
title: BP_LOCATION_CODE_CONTEXT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_LOCATION_CODE_CONTEXT
helpviewer_keywords:
- BP_LOCATION_CODE_CONTEXT structure
ms.assetid: 37412896-021a-4f73-9bb7-4125502c2e18
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: afe1d63a5496f44e9d55112f0fedf5f4c1822aa0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="bplocationcodecontext"></a>BP_LOCATION_CODE_CONTEXT
Określa lokalizację punktu przerwania powiązanej bezpośrednio z adresu w programie debugowany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _BP_LOCATION_CODE_CONTEXT {   
   IDebugCodeContext2* pCodeContext;  
} BP_LOCATION_CODE_CONTEXT;  
```  
  
## <a name="members"></a>Elementy członkowskie  
 pCodeContext  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiektu, który określa położenie punktu przerwania w kodzie.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest elementem członkowskim [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struktury jako część Unii.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)