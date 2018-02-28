---
title: IActiveScriptSite::OnScriptTerminate | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptTerminate
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptTerminate
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eef8bd2a3f2e2a4eb4fd4b5f0e35fcd9acfe5bc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Informuje hosta, że skrypt zakończy działanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pvarResult`  
 [in] Adres zmiennej, która zawiera wynik skryptu lub `NULL` skrypt utworzony żadnego wyniku.  
  
 `pexcepinfo`  
 [in] Adres `EXCEPINFO` strukturę, która zawiera informacje o wyjątku generowane, gdy skrypt zakończone, lub `NULL` Jeśli żaden wyjątek nie wygenerowano.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia.  
  
## <a name="remarks"></a>Uwagi  
 Aparat skryptów wywołuje tę metodę przed wywołaniem do [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) metody z ustawioną flagą SCRIPTSTATE_INITIALIZED, zostało zakończone. Ta metoda może służyć do zwrócenia stanu ukończenia i wyniki do hosta. Należy zauważyć, że wiele języków skryptu, które są oparte na wychwytywanie zdarzeń z hosta, życia zakresy, które są zdefiniowane przez hosta. W takim przypadku ta metoda nie może zostać wywołana.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)