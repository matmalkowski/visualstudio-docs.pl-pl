---
title: IEnumDebugExtendedPropertyInfo::Next | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumDebugExtendedPropertyInfo.Next
apilocation: scrobj.dll
helpviewer_keywords: IEnumDebugExtendedPropertyInfo::Next
ms.assetid: ac41c9a3-19d1-4596-8a87-01c10b131be3
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 343620e4539e9d095f2708ab46077ee0dafd1932
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugextendedpropertyinfonext"></a>IEnumDebugExtendedPropertyInfo::Next
Pobiera określoną liczbę`ExtendedDebugPropertyInfo` struktury w kolejności wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Next (  
   ULONGcelt,  
   ExtendedDebugPropertyInfo *rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba `ExtendedDebugPropertyInfo`struktur, które mają zostać pobrane.  
  
 `rgelt`  
 [out] Tablica `ExtendedDebugPropertyInfo` pobrać struktury.  
  
 `pceltFetched`  
 [out] Liczba `ExtendedDebugPropertyInfo` struktury faktycznie pobrany.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca prawidłową `HRESULT`, zwykle `S_OK`.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IEnumDebugExtendedPropertyInfo](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [Struktura ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)