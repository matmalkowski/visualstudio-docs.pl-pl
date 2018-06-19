---
title: IEnumDebugExtendedPropertyInfo::Skip | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Skip
ms.assetid: a0b4a9fc-e122-482b-9384-b83c460b61fe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd7f686ccaa5a3195b82458cf3ee11f02be104f3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794509"
---
# <a name="ienumdebugextendedpropertyinfoskip"></a>IEnumDebugExtendedPropertyInfo::Skip
Pomija określoną liczbę `ExtendedDebugPropertyInfo` struktury w kolejności wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba `ExtendedDebugPropertyInfo` struktury w kolejności wyliczenie do pominięcia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca prawidłową `HRESULT`, zwykle `S_OK`. Zwraca `S_FALSE` i ustawia bieżący wskaźnik elementu koniec wyliczenia, jeśli `celt` jest większa niż liczba elementów w lewo w moduł wyliczający.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IEnumDebugExtendedPropertyInfo](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [Struktura ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)