---
title: IDebugExpression::Start | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.Start
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::Start
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14d293649e3a6a87c7f594e244378dc2a7e15ac6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794434"
---
# <a name="idebugexpressionstart"></a>IDebugExpression::Start
Rozpoczyna się obliczania wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdecb`  
 [in] Wywołanie zwrotne wskazujące, po zakończeniu Obliczanie wyrażenia. Jeśli ten parametr ma `NULL`, zdarzenia nie są uruchamiane, a klient musi wykonać sondowanie stanu wyrażenie przy użyciu `QueryIsComplete`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda rozpoczyna obliczania wyrażenia.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)   
 [Interfejs IDebugExpression](../../winscript/reference/idebugexpression-interface.md)