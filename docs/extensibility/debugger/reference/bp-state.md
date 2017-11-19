---
title: BP_STATE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_STATE
helpviewer_keywords: BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 51574fd91a338f7d05d38755884412202d33637b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="bpstate"></a>BP_STATE
Określa, czy istnieje powiązane punkt przerwania oraz określa, czy jest włączone.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
typedef DWORD BP_STATE;  
```  
  
```csharp  
public enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 BPS_NONE  
 Określa, czy przerwania nie istnieje.  
  
 BPS_DELETED  
 Określa, że punkt przerwania został usunięty.  
  
 BPS_DISABLED  
 Określa, że punkt przerwania jest wyłączone.  
  
 BPS_ENABLED  
 Określa, czy punkt przerwania jest włączona.  
  
## <a name="remarks"></a>Uwagi  
 Zwrócony z [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)