---
title: IEnumDebugFrameInfo2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 858250c3c951880cf905ea6ee150f1ff61008204
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Ten interfejs wylicza [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs w celu zapewnienia listy struktur, który opisuje bieżącego stosu wywołań.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Visual Studio wywołania [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) uzyskać ten interfejs zawsze, gdy punkt przerwania, wyjątek lub zatrzymania występuje w programie debugowany.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IEnumDebugFrameInfo2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Pobiera określoną liczbę [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury w kolejności wyliczenia.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Pomija określoną liczbę [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury w kolejności wyliczenia.|  
|[Resetowanie](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Resetuje sekwencję wyliczenia na początku.|  
|[klonowania](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Tworzy moduł wyliczający, który zawiera takim samym stanie wyliczenie jako bieżący modułu wyliczającego.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Pobiera liczbę [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury w moduł wyliczający.|  
  
## <a name="remarks"></a>Uwagi  
 Visual Studio pobiera ten interfejs jako pierwszy krok w celu obsługi punktu przerwania, wyjątek lub Wstrzymaj wygenerowaną przez użytkowników na debugowany program. Lista [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury reprezentuje bieżącego stosu wywołań, z bieżącego wywołania funkcji na początku listy i funkcja najstarsze Zadzwoń na końcu listy. Każdy `FRAMEINFO` reprezentuje ramka stosu kontekstu, w którym można oszacować wyrażenia i przeglądał zmiennych lokalnych.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)