---
title: PENDING_BP_STATE_INFO | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a4bf5f77ae24d83a0c0874d2cd03d1f5abbc0e2f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="pendingbpstateinfo"></a>PENDING_BP_STATE_INFO
Zawiera informacje o stanie punktu przerwania, który jest gotowy do powiązania do lokalizacji kodu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _tagPENDING_BP_STATE_INFO {   
   PENDING_BP_STATE       state;  
   PENDING_BP_STATE_FLAGS flags;  
} PENDING_BP_STATE_INFO;  
```  
  
```csharp  
public struct PENDING_BP_STATE_INFO {   
   public uint state;  
   public uint flags;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 state  
 Wartość z zakresu od [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) wyliczenia, który określa stan oczekujący punkt przerwania.  
  
 flagi  
 Kombinacja flag z [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) wyliczenia, która określa, czy punkt przerwania zostaje zwirtualizowany.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest przekazywana do [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) metody, gdzie jest wypełnione.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)   
 [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)   
 [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)