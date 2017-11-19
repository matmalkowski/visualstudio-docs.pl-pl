---
title: IEnumDebugExtendedPropertyInfo::Clone | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumDebugExtendedPropertyInfo.Clone
apilocation: scrobj.dll
helpviewer_keywords: IEnumDebugExtendedPropertyInfo::Clone
ms.assetid: dd645cf6-bfb3-486c-829e-bb91a6639665
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d873ba29ea2dc327cd6499613abb66d2a728008c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugextendedpropertyinfoclone"></a>IEnumDebugExtendedPropertyInfo::Clone
Tworzy moduł wyliczający, który zawiera takim samym stanie wyliczenie jako bieżący modułu wyliczającego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Clone (  
   IEnumDebugExtendedPropertyInfo** ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Zwraca sklonowany `IEnumDebugExtendedPropertyInfo` interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca prawidłową `HRESULT`, zwykle `S_OK`.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IEnumDebugExtendedPropertyInfo](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)