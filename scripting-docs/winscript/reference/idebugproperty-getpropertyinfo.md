---
title: IDebugProperty::GetPropertyInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugProperty.GetPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetPropertyInfo
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: edd878419c6f2b4fd0f882a070d80c98a96eba56
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertygetpropertyinfo"></a>IDebugProperty::GetPropertyInfo
Pobiera wartość `IDebugProperty` , który opisuje metody lub właściwości indeksowanej.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGSdwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFields`  
 [in] Określa `DBGPROP_INFO_FLAGS` stałe, które określają pola, które mają zostać wypełnione `DebugPropertyInfo` struktury.  
  
 `nRadix`  
 [in] Podstawa ma być używany podczas formatowania wszelkie informacje numeryczne.  
  
 `pPropertyInfo`  
 [out] Zwraca `DebugPropertyInfo` struktury, która opisuje właściwość.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca prawidłową `HRESULT`, zwykle `S_OK`.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [Struktura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)