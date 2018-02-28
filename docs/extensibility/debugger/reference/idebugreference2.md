---
title: IDebugReference2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 30f3b8351789adbb52651909cf9ff3b669934d66
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugreference2"></a>IDebugReference2
Ten interfejs reprezentuje odwołanie do właściwości ramki stosu lub pewne inne właściwości.  
  
> [!NOTE]
>  `IDebugReference2`jest zarezerwowany do użytku w przyszłości i wszystkie jego metody powinna zwracać `E_NOTIMPL`.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Niemcy implementuje ten interfejs do reprezentowania odwołanie do określonego typu wartości. Na przykład wartość może być wartość liczbową wyniku Obliczanie wyrażenia w kontekście pamięci służący do wyświetlania w pamięci lub lista rejestrów i ich wartości.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) uzyskanie tego interfejsu. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) i [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) również zwrócić tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugReference2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Pobiera [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktury, która opisuje to odwołanie.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Ustawia wartość to odwołanie z ciągu.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Ustawia wartość to odwołanie z innego odwołania.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Wylicza elementy podrzędne tego odwołania.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Pobiera element nadrzędny tego odwołania.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Pobiera odwołanie pochodzi większość tego odwołania.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Pobiera bajtów pamięci, do których odwołuje się tego odwołania.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Pobiera kontekst pamięci dla tego odwołania.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Pobiera rozmiar w bajtach tego odwołania.|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Ustawia tego typu odwołania.|  
|[Porównaj](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Porównuje to odwołanie z inną.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Nie należy mylić to użycie "właściwości" z oznacza zmiennej członkowskiej klasy, mimo że `IDebugReference2` może reprezentować taka jednostka.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) reprezentuje właściwość, podczas gdy `IDebugReference2` reprezentuje odwołanie do właściwości, zwykle odwołanie do obiektu w debugowanym program.  
  
 Podstawowa różnica między właściwość i odwołanie jest, że właściwość odwołuje się do nazwanego wystąpienia obiektu, gdy odwołanie odnosi się do nazwy wystąpienia. Na przykład właściwość może odwoływać się do obiektu w stosie programu przez `"a.b"`. Inna właściwość może odwoływać się do tego samego obiektu jako `"c.d"`. Sposób odwoływania się do tej właściwości wymaga, aby `"a.b"` lub `"c.d"` się w zakresie. Odwołanie do tego samego obiektu nie została określona; Obiekt można odwoływać się tak długo, jak pamięci dla tego obiektu jest nieprawidłowy.  
  
 `IDebugProperty2` Interfejsu można traktować jako wartość z nazwą, typ i adresu. `IDebugReference2`, W drugim ręcznie, można traktować jako typ i adresu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)