---
title: ISetNextStatement::SetNextStatement | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ISetNextStatement.SetNextStatement
apilocation: scrobj.dll
ms.assetid: c5534f3b-39a5-4466-b8fc-69b717c6eee9
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d21dafcd8cdb762e39f0cfcbde1162dd66c275ec
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="isetnextstatementsetnextstatement"></a>ISetNextStatement::SetNextStatement
Ta metoda aktualizacji dalej kontekst kodu, który może zostać uruchomiony interpreter skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStackFrame`  
 [in] Wskaźnik do obiektu ramki stosu.  
  
 `pCodeContext`  
 [in] Wskaźnik do obiektu kontekstu kodu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs ISetNextStatement](../../winscript/reference/isetnextstatement-interface.md)