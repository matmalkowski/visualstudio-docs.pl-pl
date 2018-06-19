---
title: IDebugExpression::GetResultAsString | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsString
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 557fe65859d1e3046d64884982070ad233e12559
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794629"
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
Zwraca wynik wyrażenia jako ciąg i wartość zwracana operacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phrResult`  
 [out] Wartość zwracana operacji.  
  
 `pbstrResult`  
 [out] Wynik obliczania wyrażenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_PENDING`|Operacja jest nadal oczekujące.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wynik wyrażenia jako ciąg i operacji `HRESULT`.  
  
 Ta metoda zwraca `S_OK` i `phrResult` zwraca `E_ABORT` Jeśli `Abort` przerwanie operacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugExpression](../../winscript/reference/idebugexpression-interface.md)