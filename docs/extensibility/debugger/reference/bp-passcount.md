---
title: BP_PASSCOUNT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_PASSCOUNT
helpviewer_keywords: BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 45fdea434b419f0e681e8946c4c8dee3db945d8c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="bppasscount"></a>BP_PASSCOUNT
Opisuje liczbę i warunki, na których jest uruchamiany warunkowych punktów przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _BP_PASSCOUNT {   
   DWORD              dwPassCount;  
   BP_PASSCOUNT_STYLE stylePassCount;  
} BP_PASSCOUNT;  
```  
  
```csharp  
public struct BP_PASSCOUNT {   
   public uint dwPassCount;  
   public uint stylePassCount;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `dwPassCount`  
 Liczba razy, aby przekazać za pośrednictwem punktu przerwania, zanim zostanie zainicjowane go.  
  
 `stylePassCount`  
 Wartość z zakresu od [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) Liczba przebiegów wyliczenia, która określa rodzaj punktu przerwania.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest elementem członkowskim [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struktury.  
  
 Ta struktura jest również przekazany jako parametr[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) i[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)   
 [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)   
 [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)