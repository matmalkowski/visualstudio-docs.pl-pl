---
title: IActiveScript::SetScriptState | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptState
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 146cd5e4f2b6137fc6fe6e32e8ca153c3aab8fd5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793294"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
Umieszcza aparat skryptów w danym stanie. Ta metoda może być wywołana z wątków innych niż podstawowe powodowała objaśnienia innych niż podstawowe do obiektów hosta lub do [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ss`  
 [in] Ustawia aparat skryptów w danym stanie. Może być jedna z wartości zdefiniowanych w [wyliczenie SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md) wyliczenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_FAIL`|Aparat skryptów nie obsługuje przejście do stanu zainicjowane. Hosta należy odrzucić to aparat skryptów i utworzyć, zainicjować i załadować nowy aparat obsługi skryptów, aby osiągnąć ten sam efekt.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparatu skryptów jeszcze nie został załadowany lub zainicjować) i dlatego nie powiodła się.|  
|`OLESCRIPT_S_PENDING`|Metoda została pomyślnie w kolejce, ale nie zmienił się stan jeszcze. Podczas zmiany stanu lokacji zostanie wywołany przez [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) metody.|  
|`S_FALSE`|Metoda zakończyło się pomyślnie, ale skrypt został już w danym stanie.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat skryptów aparatu stanów, zobacz sekcję stanów aparatu skryptu [aparaty skryptów systemu Windows](../../winscript/windows-script-engines.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)