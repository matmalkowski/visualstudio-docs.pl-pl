---
title: ISetNextStatement::CanSetNextStatement | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ISetNextStatement.CanSetNextStatement
apilocation: scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bd32ddf73076f9e29ca3377186ff64be256b8fc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="isetnextstatementcansetnextstatement"></a>ISetNextStatement::CanSetNextStatement
Ta metoda określa, czy punkcie wykonanie, które określa następnej instrukcji na wykonanie kodu, można ustawić w określonej lokalizacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CanSetNextStatement(  
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
|`S_OK`|Następna instrukcja może zostać zaktualizowana w kontekście określony kod.|  
|`S_FALSE`|Nie można zaktualizować następnej instrukcji dla kontekstu określonego kodu.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs ISetNextStatement](../../winscript/reference/isetnextstatement-interface.md)