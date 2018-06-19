---
title: BP_UNBOUND_REASON | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 65398ac0c4bde18dc772d75ceea203bdbfe3b189
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109006"
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
Zapewnia punkt przerwania został niezwiązanego przyczyny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```csharp  
public enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 BPUR_UNKNOWN  
 Przyczyną jest nieznany.  
  
 BPUR_CODE_UNLOADED  
 Kod, który zawiera punkt przerwania został zwolniony.  
  
 BPUR_BREAKPOINT_REBIND  
 Punkt przerwania zostało odbitych do innej lokalizacji. To po edycji i kontynuowania operacji po przemieszczeniu punkt przerwania lub gdy punkt przerwania jest powiązana z pliku ze ścieżką, która nie jest już prawidłowy.  
  
 BPUR_ BREAKPOINT_ERROR  
 Punkt przerwania jest określony jako błąd po jest powiązany. Dzieje się to do zarządzanego punktów przerwania, którego warunki nie są już prawidłowe.  
  
## <a name="remarks"></a>Uwagi  
 Zwrócony przez [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)