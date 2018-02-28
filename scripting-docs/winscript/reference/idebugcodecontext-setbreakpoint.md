---
title: IDebugCodeContext::SetBreakPoint | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugCodeContext.SetBreakPoint
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugCodeContext::SetBreakPoint
ms.assetid: ecd42eae-66fa-40d3-9e47-08b826784108
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a0111deba23f29aa6b7d31a1aed8d729ff4e7fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugcodecontextsetbreakpoint"></a>IDebugCodeContext::SetBreakPoint
Ustawia lub czyści punkt przerwania w tym kontekście kodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetBreakPoint(  
   BREAKPOINT_STATE  bps  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bps`  
 [in] Określa stan punktu przerwania dla tego kontekstu kodu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda ustawia lub czyści punkt przerwania w tym kontekście kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugCodeContext](../../winscript/reference/idebugcodecontext-interface.md)   
 [Wyliczenie BREAKPOINT_STATE](../../winscript/reference/breakpoint-state-enumeration.md)