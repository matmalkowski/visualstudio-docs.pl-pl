---
title: IScriptScriptlet::SetSimpleEventName | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptScriptlet.SetSimpleEventName
apilocation: scrobj.dll
helpviewer_keywords: IScriptScriptlet::SetSimpleEventName
ms.assetid: 7de9132e-635f-45df-9c92-83a24242b477
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 958478d8c8ead6500711a7866a784235adb869b8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptscriptletsetsimpleeventname"></a>IScriptScriptlet::SetSimpleEventName
Ustawia nazwę zdarzenia prostego skojarzony z skryptlet. Jest to nazwa jednowyrazowej, która nie zawiera żadnego odstępu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetSimpleEventName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `psz`  
 [in] Buforu, który zawiera nazwę zdarzenia prostego, z którym skojarzony jest `IScriptScriptlet` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IScriptScriptlet](../../winscript/reference/iscriptscriptlet-interface.md)