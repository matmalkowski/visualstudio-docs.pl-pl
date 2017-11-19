---
title: IDebugStackFrame::GetThread | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugStackFrame.GetThread
apilocation: jscript.dll
helpviewer_keywords: IDebugStackFrame::GetThread
ms.assetid: ece24728-a6b2-4b01-a6f0-0a82b15be39b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 888e15bdd154fbac444eb91fc31ad7f17c2981ca
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframegetthread"></a>IDebugStackFrame::GetThread
Zwraca wątek skojarzony z tą ramką stosu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetThread(  
   IDebugApplicationThread**  ppat  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppat`  
 [out] Wątek skojarzony z tą ramką stosu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wątek skojarzony z tą ramką stosu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)