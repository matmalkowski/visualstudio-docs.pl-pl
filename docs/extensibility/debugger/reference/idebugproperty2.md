---
title: IDebugProperty2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8dc1305fb8534dc8e14192268913290aef25f2cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty2"></a>IDebugProperty2
Ten interfejs reprezentuje właściwości ramki stosu, właściwości dokumentu programu lub pewne inne właściwości. Właściwość jest zazwyczaj wynikiem obliczania wyrażenia.  
  
> [!NOTE]
>  Nie należy mylić to użycie "właściwości" z oznacza zmiennej członkowskiej klasy, mimo że `IDebugProperty2` może reprezentować taka jednostka.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Niemcy implementuje ten interfejs do reprezentowania określonego typu wartości. Na przykład wartość może być wartość liczbową wyniku Obliczanie wyrażenia w kontekście pamięci służący do wyświetlania w pamięci lub lista rejestrów i ich wartości.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) uzyskać ten interfejs, który reprezentuje wyniki oceny. `IDebugExpression2::EvaluateAsync`zwraca ten interfejs, wysyłając [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interfejsu SDM, która z kolei wywołuje [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) można pobrać właściwości.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) zwraca Podaj dokument skryptu skojarzonych w tym interfejsie.  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) zwraca ten interfejs reprezentujący wartość zwracaną przez funkcję.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) zwraca reprezentuje różne właściwości programu, np. nazwę lub kontekstu pamięci w tym interfejsie.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) zwraca reprezentuje różne właściwości ramki stosu, takich jak zmiennych lokalnych w tym interfejsie.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugProperty2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Wypełnia [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) strukturę, która opisuje właściwość.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Ustawia wartości właściwości z ciągu.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Ustawia wartości właściwości z wartością danego odwołania.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Wylicza elementy podrzędne właściwości.|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Zwraca element nadrzędny właściwości.|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Zwraca właściwości, opisujący właściwość pochodnych większość właściwości.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Zwraca liczbę bajtów pamięci, które tworzą wartość właściwości.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Zwraca kontekst pamięci dla wartości właściwości.|  
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Zwraca rozmiar w bajtach wartości właściwości.|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Zwraca odwołanie do tej właściwości wartości.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Zwraca informacje rozszerzone właściwości.|  
  
## <a name="remarks"></a>Uwagi  
 Właściwość reprezentowany przez `IDebugProperty2` interfejsu, można traktować jako wartość z nazwą, typ i adresu. Bardziej ogólnie rzecz biorąc `IDebugProperty2` może reprezentować wszystko, co ma strukturę hierarchiczną z obiektów nadrzędnych i podrzędnych węzłów.  
  
 Właściwość jest zwykle przejściowe, trwające tylko tak długo, jak bieżącej ramki stosu, np. Z drugiej strony, odwołanie, reprezentowany przez [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) interfejsu okresu tak długo, jak wartość pozostaje w pamięci.  
  
 Można użyć IDE `IDebugProperty2` interfejsu, aby umożliwić użytkownikom Przeglądaj i Modyfikuj właściwości w czasie wykonywania.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)