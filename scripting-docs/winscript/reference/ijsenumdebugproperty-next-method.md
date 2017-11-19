---
title: "IJsEnumDebugProperty::Next — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsEnumDebugProperty.Next
apilocation: jscript9diag.dll
ms.assetid: 9fad1893-483a-440c-88c1-469494212300
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b8c85601709bb727549152ffdb01e15dbd84e510
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ijsenumdebugpropertynext-method"></a>IJsEnumDebugProperty::Next — Metoda
Odczytuje właściwości dla tego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Next(  
   ULONG count,  
   IJsDebugProperty **ppDebugProperty,  
   ULONG *pActualCount  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `count`  
 [in] Liczba właściwości do odczytu.  
  
 `ppDebugProperty`  
 [out] Obiekt reprezentujący przeglądarce właściwości.  
  
 `pActualCount`  
 [out] Rzeczywista liczba właściwości obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Ijsenumdebugproperty — interfejs](../../winscript/reference/ijsenumdebugproperty-interface.md)