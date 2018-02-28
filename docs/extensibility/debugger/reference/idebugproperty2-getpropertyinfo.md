---
title: IDebugProperty2::GetPropertyInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty2::GetPropertyInfo
helpviewer_keywords:
- IDebugProperty2::GetPropertyInfo
ms.assetid: 39d6e942-df72-4c84-a5d9-a386d112714c
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 094ad1d47aa3c1af3ad24020a1caac6ddc6a665d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty2getpropertyinfo"></a>IDebugProperty2::GetPropertyInfo
Pobiera [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) strukturę, która opisuje właściwość.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetPropertyInfo (   
   DEBUGPROP_INFO_FLAGS dwFields,  
   DWORD                nRadix,  
   DWORD                dwTimeout,  
   IDebugReference2**   rgpArgs,  
   DWORD                dwArgCount,  
   DEBUG_PROPERTY_INFO* pPropertyInfo  
);  
```  
  
```cpp  
int GetPropertyInfo (   
   enum_DEBUGPROP_INFO_FLAGS dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_PROPERTY_INFO[]     pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFields`  
 [in] Kombinacja wartości z [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) wyliczenia, która określa pola, które mają zostać wypełnione `pPropertyInfo` struktury.  
  
 `nRadix`  
 [in] Podstawa ma być używany podczas formatowania wszelkie informacje numeryczne.  
  
 `dwTimeout`  
 [in] Określa maksymalny czas (w milisekundach) oczekiwania przed powrotem z tej metody. Użyj `INFINITE` będzie czekać w nieskończoność.  
  
 `rgpArgs`  
 [w, out] Zarezerwowane do użytku w przyszłości; Ustaw wartość null.  
  
 `dwArgCount`  
 [in] Zarezerwowane do użytku w przyszłości; ustawić na zero.  
  
 `pPropertyInfo`  
 [out] A [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury, która jest wypełniane opis właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)