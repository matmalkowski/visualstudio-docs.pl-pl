---
title: ISimpleConnectionPoint::Unadvise | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Unadvise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Unadvise
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f926f206bb8a27e6265fd147909a5adb13c3543
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpointunadvise"></a>ISimpleConnectionPoint::Unadvise
Przerywa połączenie doradczych wcześniej ustanowione za pośrednictwem `ISimpleConnectionPoint::Advise`.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwCookie`  
 [in] Token połączenia, aby zakończyć, ponieważ zwrócony z `ISimpleConnectionPoint::Advise`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Zespół Doradczy połączenie zostało zakończone, połączenie punkcie wywołania `Release` metodę na wskaźniku, który został zapisany dla połączenia podczas `ISimpleConnectionPoint::Advise` metody. Które wywołują odwrócona `AddRef` który została wykonana podczas `ISimpleConnectionPoint::Advise` gdy punkt połączenia wywołuje zbiornika advisory `QueryInterface`.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)