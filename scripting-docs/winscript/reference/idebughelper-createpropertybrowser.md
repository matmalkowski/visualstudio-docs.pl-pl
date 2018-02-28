---
title: IDebugHelper::CreatePropertyBrowser | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowser
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowser
ms.assetid: 2fa819cf-c7f7-4bd7-b018-ea33b804ba8f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f728068b6d1db6fe70a084ae680f32a78a0a2760
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebughelpercreatepropertybrowser"></a>IDebugHelper::CreatePropertyBrowser
Zwraca właściwości przeglądarki, która opakowuje VARIANT.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pvar`  
 [in] Wariant głównego do przeglądania.  
  
 `bstrName`  
 [in] Nazwa katalogu głównego.  
  
 `pdat`  
 [in] Wątek, na których chcesz żądać właściwości. Jeśli ten parametr ma wartość NULL, kierowanie nie jest wykonywana.  
  
 `ppdob`  
 [out] Przeglądarka właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wartość właściwości przeglądarki, która opakowuje VARIANT.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)   
 [Interfejs IDebugHelper](../../winscript/reference/idebughelper-interface.md)   
 [Interfejs IDebugProperty](../../winscript/reference/idebugproperty-interface.md)