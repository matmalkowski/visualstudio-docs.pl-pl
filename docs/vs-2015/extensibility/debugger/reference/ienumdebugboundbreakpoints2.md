---
title: IEnumDebugBoundBreakpoints2 | Dokumentacja firmy Microsoft
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
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 525b16a39836a3e22ce624d2bcd8893d9bf3bf55
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42683438"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IEnumDebugBoundBreakpoints2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugboundbreakpoints2).  
  
Ten interfejs wylicza powiązane punkty przerwania, skojarzone z Oczekujący punkt przerwania lub punkt przerwania powiązane zdarzenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugBoundBreakpoints2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs jako część jego obsługę punktów przerwania. Należy można zaimplementować ten interfejs, jeśli punkty przerwania są obsługiwane.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołuje program Visual Studio:  
  
-   [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) uzyskać ten interfejs reprezentujący listę wszystkich punktów przerwania, które zostały wyzwolone.  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) uzyskać ten interfejs reprezentujący listę wszystkich punktów przerwania, które były powiązane.  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) uzyskać ten interfejs reprezentujący listę wszystkich punktów przerwania, powiązany z tym oczekujący punkt przerwania.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IEnumDebugBoundBreakpoints2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Pobiera określoną liczbę powiązanych punktów przerwania w kolejności wyliczenia.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Pomija określoną liczbę powiązanych punktów przerwania w kolejności wyliczenia.|  
|[Resetuj](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
|[Klon](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Pobiera liczbę powiązanych punktów przerwania w moduł wyliczający.|  
  
## <a name="remarks"></a>Uwagi  
 Aby zaktualizować wyświetlane punkty przerwania w środowisku IDE programu Visual Studio korzysta z powiązane punkty przerwania reprezentowany przez ten interfejs.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)

