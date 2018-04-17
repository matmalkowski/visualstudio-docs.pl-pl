---
title: IDebugProperty2::EnumChildren | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9631ee89dc9d241932b745db4ce094799a899bad
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Pobiera listę elementów podrzędnych właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumChildren (   
   DEBUGPROP_INFO_FLAGS      dwFields,  
   DWORD                     dwRadix,  
   REFGUID                   guidFilter,  
   DBG_ATTRIB_FLAGS          dwAttribFilter,  
   LPCOLESTR                 pszNameFilter,  
   DWORD                     dwTimeout,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumChildren (   
   enum_DEBUGPROP_INFO_FLAGS   dwFields,  
   uint                        dwRadix,  
   ref Guid                    guidFilter,  
   uint                        dwAttribFilter,  
   string                      pszNameFilter,  
   uint                        dwTimeout,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFields`  
 [in] Kombinacja flag z [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) wyliczenie określający pola, które w wyliczany [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury mają zostać wypełnione.  
  
 `dwRadix`  
 [in] Określa podstawa ma być używany podczas formatowania wszelkie informacje numeryczne.  
  
 `guidFilter`  
 [in] Identyfikator GUID używany z filtru `dwAttribFilter` i `pszNameFilter` parametry wybranie `DEBUG_PROPERTY_INFO` elementy podrzędne mają zostać wyliczone. Na przykład `guidFilterLocals` filtry dla zmiennych lokalnych.  
  
 `dwAttribFilter`  
 [in] Kombinacja flag z [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) wyliczenia, która określa, jakiego typu obiektów do wyliczenia, na przykład `DBG_ATTRIB_METHOD` dla wszystkich metod, które mogą być elementami podrzędnymi tej właściwości. W połączeniu z `guidFilter` i `pszNameFilter` parametrów.  
  
 `pszNameFilter`  
 [in] Nazwa filtru używane z `guidFilter` i `dwAttribFilter` parametry wybranie `DEBUG_PROPERTY_INFO` elementy podrzędne mają zostać wyliczone. Na przykład ustawienie tego parametru do filtrów "MyX" dla wszystkich elementów podrzędnych o nazwie "MyX."  
  
 `dwTimeout`  
 [in] Określa maksymalny czas (w milisekundach) oczekiwania przed powrotem z tej metody. Użyj `INFINITE` będzie czekać w nieskończoność.  
  
 `ppEnum`  
 [out] Zwraca [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) obiektu zawierającego listę właściwości podrzędnej.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)