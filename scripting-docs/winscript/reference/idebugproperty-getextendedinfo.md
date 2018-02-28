---
title: IDebugProperty::GetExtendedInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugProperty.GetExtendedInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc549ecc4cfa3b3cbbb754585c751b16df2fd8a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
Pobiera rozszerzone informacje dla właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cInfos`  
 [in] Liczba obiektów rozszerzonych informacji.  
  
 `rgguidExtendedInfo`  
 [in] Tablica `GUID`s jest przekazywana, dzięki czemu wiele elementów rozszerzone informacje mogą być pobierane w tym samym czasie.  
  
 `pExtendedInfo`  
 [out] Zwraca tablicę `VARIANT`s, którego można pobrać informacji o rozszerzonych właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca prawidłową `HRESULT`, zwykle `S_OK`.  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs pobiera rozszerzone informacje dla tego obiektu. Interfejs API istnieje tylko na potrzeby pobierania informacji, które nie nadają się do pobierania za pomocą `IDebugProperty::GetPropertyInfo`).  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugProperty](../../winscript/reference/idebugproperty-interface.md)