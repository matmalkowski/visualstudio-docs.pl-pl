---
title: IEnumDebugStackFrames::Clone | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Clone
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Clone
ms.assetid: 9d9e01a3-0be3-4336-832a-f065af388571
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 910b05024efcde8614882e0c95cdfab2ffe9be3e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugstackframesclone"></a>IEnumDebugStackFrames::Clone
Tworzy moduł wyliczający, który zawiera stan tego samego jako bieżący modułu wyliczającego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Clone(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppedsf`  
 [out] Zwraca `IEnumDebugStackFrames` interfejsu klonu modułu wyliczającego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda tworzy moduł wyliczający, który zawiera stan tego samego jako bieżący modułu wyliczającego.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IEnumDebugStackFrames](../../winscript/reference/ienumdebugstackframes-interface.md)