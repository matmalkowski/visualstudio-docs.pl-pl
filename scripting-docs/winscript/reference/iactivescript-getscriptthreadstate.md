---
title: IActiveScript::GetScriptThreadState | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b11b8566857bc70aaeac5bdf8e8e357fa5d9c2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791890"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
Pobiera bieżący stan wątku skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stidThread`  
 [in] Identyfikator wątku, dla którego stan jest pożądane, lub jeden z następujących identyfikatorów specjalne wątku:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|Podstawowy wątku; oznacza to, że utworzono wystąpienie wątku, w którym skryptów aparatu.|  
|SCRIPTTHREADID_CURRENT|Wątek aktualnie wykonywane.|  
  
 `pstsState`  
 [out] Adres zmiennej, która otrzymuje stan wskazanych wątku. Stan jest wskazywany przez jedną o nazwie stałej wartości zdefiniowanych przez [wyliczenie SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md) wyliczenia. Jeśli ten parametr wskazuje bieżący wątek, stan może zmienić w dowolnym momencie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparatu skryptów jeszcze nie został załadowany lub zainicjować).|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda może być wywołana z wątków innych niż podstawowe powodowała objaśnienia innych niż podstawowe do obiektów hosta lub do [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)