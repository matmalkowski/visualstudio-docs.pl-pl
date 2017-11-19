---
title: IDebugFormatter::GetVariantForString | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugFormatter.GetVariantForString
apilocation: jscript.dll
helpviewer_keywords: IDebugFormatter::GetVariantForString
ms.assetid: 2993431d-0ee2-4d8d-b62c-0a810a8bc391
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f9f783c8fe1864999e017ff348853df5464c93f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugformattergetvariantforstring"></a>IDebugFormatter::GetVariantForString
Zwraca typ VARIANT zawierający dany ciąg znaków.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetVariantForString(  
   LPCOLESTR  pwstrValue,  
   VARIANT*   pvar  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwstrValue`  
 [in] Ciąg do przechowywania w VARIANT.  
  
 `pvar`  
 [out] VARIANT zawierający `pwstrValue`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca typ VARIANT zawierający dany ciąg znaków.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)