---
title: IActiveScript::GetScriptState | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetScriptState
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetScriptState
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 285a09308c7477dbeed68f9f93417b503ca4fe49
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
Pobiera bieżący stan aparatu skryptów. Ta metoda może być wywołana z wątków innych niż podstawowe powodowała objaśnienia innych niż podstawowe do obiektów hosta lub do [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pss`  
 [out] Adres zmiennej, która odbiera wartość zdefiniowana w [wyliczenie SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md) wyliczenia. Wartość wskazuje bieżący stan skojarzony z wątkiem wywołującym aparatu skryptów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia lub `E_POINTER` Jeśli określono nieprawidłowy wskaźnik.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)