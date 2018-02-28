---
title: IDebugExpression::GetResultAsDebugProperty | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsDebugProperty
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsDebugProperty
ms.assetid: 9075bf2f-d5bb-464e-b6c2-3fa3215e9ae0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6ce67df5dd55bd8c1ae55bb19fe2a19aed9e40f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressiongetresultasdebugproperty"></a>IDebugExpression::GetResultAsDebugProperty
Zwraca wynik wyrażenia jako właściwość debugowania i wartość zwracana operacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phrResult`  
 [out] Wartość zwracana operacji.  
  
 `ppdp`  
 [out] Właściwość debugowania dla wyrażenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_PENDING`|Operacja jest nadal oczekujące.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wynik wyrażenia jako `IDebugProperty` i operacji `HRESULT`.  
  
 Ta metoda zwraca `S_OK` i `phrResult` zwraca `E_ABORT` Jeśli `Abort` przerwanie operacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugExpression](../../winscript/reference/idebugexpression-interface.md)   
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)