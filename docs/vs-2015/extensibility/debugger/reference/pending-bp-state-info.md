---
title: PENDING_BP_STATE_INFO | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 77151825f1e241110a0af1fece80f34ea39fd331
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681594"
---
# <a name="pendingbpstateinfo"></a>PENDING_BP_STATE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [PENDING_BP_STATE_INFO](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/pending-bp-state-info).  
  
Zawiera informacje o stanie punktu przerwania, który jest gotowy do powiązania do lokalizacji kodu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 Wartość z zakresu od [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) wyliczenie, który określa stan oczekujący punkt przerwania.  
  
 flagi  
 Kombinacja flag z [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) wyliczenia, która określa, czy punkt przerwania zostaje zwirtualizowany.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest przekazywany do [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) metody, gdzie jest wypełnione.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktur i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)   
 [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)   
 [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)

