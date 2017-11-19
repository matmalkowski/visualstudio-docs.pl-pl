---
title: IObjectIdentity::IsEqualObject | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IObjectIdentity.IsEqualObject
apilocation: scrobj.dll
helpviewer_keywords: IsEqualObject method
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52e386055e458568f8d4076a37489b7b2397f399
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
Określa, czy obiekt jest taki sam jak bieżący obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `punk`  
 [in] Adres obiekt do porównania z bieżącym obiektem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Obiekty są równe.|  
|`S_FALSE`|Obiekty nie są takie same.|  
  
## <a name="remarks"></a>Uwagi  
 Implementacja interfejsu `IsEqualObject` metoda powinna zwrócić `S_OK` tylko wtedy, gdy obiekty są identyczne.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IObjectIdentity](../../winscript/reference/iobjectidentity-interface.md)