---
title: "IJsDebugBreakPoint::IsEnabled — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJSDebugBreakPoint.IsEnabled
apilocation: jscript9diag.dll
ms.assetid: 39b63f49-2a0d-41b7-a2ba-75dcb06251a9
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb7ab887b8e3442a0c38ea403ad43bdea10cdd66
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugbreakpointisenabled-method"></a>IJsDebugBreakPoint::IsEnabled — Metoda
Określa, czy punkt przerwania jest włączone.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT IsEnabled(  
   BOOL *pIsEnabled  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pIsEnabled`  
 [out] Zwraca wartość PRAWDA, jeśli punkt przerwania jest włączone; w przeciwnym razie zwraca wartość false.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Zwraca E_UNEXPECTED, jeśli wywołano usunięto punktu przerwania.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Ijsdebugbreakpoint — interfejs](../../winscript/reference/ijsdebugbreakpoint-interface.md)