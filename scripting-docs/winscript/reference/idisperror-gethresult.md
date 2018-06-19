---
title: IDispError::GetHresult | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHresult
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHresult
ms.assetid: a14d566e-473f-497b-a2f9-85331433e6c9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 859708b8aec4f89dd1ea49bf6e248d7bcade7624
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794209"
---
# <a name="idisperrorgethresult"></a>IDispError::GetHresult
Pobiera kod błędu z `IDispError` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetHresult(  
   HRESULT*  phr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phr`  
 [out] Określa kod błędu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda pobiera kod błędu z `IDispError` obiektu.  
  
> [!NOTE]
>  Ta metoda nie jest zaimplementowana.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDispError](../../winscript/reference/idisperror-interface.md)