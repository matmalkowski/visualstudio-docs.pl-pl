---
title: IActiveScriptSite::GetLCID | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetLCID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6e128f5ac5de11b45af59c83750411c35e6efa7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793543"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Pobiera identyfikator ustawień regionalnych skojarzoną z interfejsem użytkownika hosta. Aparat skryptów używa identyfikatora zapewnienie, że błąd ciągów i inne elementy interfejsu użytkownika, generowane przez aparat są wyświetlane w odpowiednim języku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `plcid`  
 [out] Adres zmiennej, która odbiera identyfikator ustawień regionalnych dla elementów interfejsu użytkownika, wyświetlane przez aparat skryptów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_NOTIMPL`|Ta metoda nie jest zaimplementowana. Użyj ustawień regionalnych zdefiniowane przez system.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ta metoda zwraca `E_NOTIMPL`, powinien być używany identyfikator ustawień regionalnych z zdefiniowane przez system.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)