---
title: IPerPropertyBrowsing2::MapPropertyToPage | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.MapPropertyToPage
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::MapPropertyToPage
ms.assetid: e6418a8e-500b-42e1-9b5a-52e6f7567f99
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 79b8d7cb9e1c8a9f79cdddc4f8d3404ff7a2036c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iperpropertybrowsing2mappropertytopage"></a>IPerPropertyBrowsing2::MapPropertyToPage
Zwraca identyfikator CLSID strony właściwości, która może służyć do edycji tej właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT MapPropertyToPage(  
   DISPID  dispid,  
   CLSID*  pClsidPropPage  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dispid`  
 [in] Wyślij identyfikator właściwości zainteresowań.  
  
 `pClsidPropPage`  
 [out] Wskaźnik do identyfikatora CLSID identyfikujący stronę właściwości skojarzone z właściwością. Jeśli ta metoda zawiedzie, *`pClsidPropPage` ma ustawioną wartość CLSID_NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca prawidłową `HRESULT`, zwykle `S_OK`.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IPerPropertyBrowsing2 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)