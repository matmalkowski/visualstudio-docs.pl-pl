---
title: IEnumDebugPropertyInfo2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugPropertyInfo2
helpviewer_keywords: IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9e7f261a449e20873183ff59487c1a6b2df6b678
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Ten interfejs wylicza [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania informacje dla określonej właściwości.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) uzyskać ten interfejs reprezentujący element podrzędny elementu określonej właściwości. Wywołanie [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) uzyskać ten interfejs reprezentujący właściwości ramki stosu w szczególności.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IEnumDebugPropertyInfo2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dalej](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Pobiera określoną liczbę [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury w kolejności wyliczenia.|  
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Pomija określoną liczbę [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury w kolejności wyliczenia.|  
|[Resetowanie](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Resetuje sekwencję wyliczenia na początku.|  
|[Klonowania](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Tworzy moduł wyliczający, który zawiera takim samym stanie wyliczenie jako bieżący modułu wyliczającego.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Pobiera liczbę [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury w moduł wyliczający.|  
  
## <a name="remarks"></a>Uwagi  
 Ogólnie rzecz biorąc właściwość jest hierarchii informacje, które mogą obejmować nazwę, wartość, adres lub typu, jak również inne informacje odpowiednie do skojarzonej właściwości ramki stosu lub obiektu. Zobacz [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) więcej szczegółów.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)