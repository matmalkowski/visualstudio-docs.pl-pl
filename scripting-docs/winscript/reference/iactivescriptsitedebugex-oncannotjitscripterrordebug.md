---
title: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e428f12b3d199603ac341a5e069fcc5ce5d36f93
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Informuje, że host o błędów czasu wykonywania skryptu, gdy proces debugowania Manager nie znalazł debugera skryptów tylko w czasie.  
  
 Aby zaimplementować debugera na hoście, powinna obsługiwać [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). Oparte na akcję użytkownika, host albo można dołączyć debugera i zwraca lub zwraca uruchamiania w debugerze programu OnScriptErrorDebug `pfEnterDebugger` parametru. Powinny również implementować ten interfejs, aby otrzymywać powiadomienia o błędów czasu wykonywania, nawet jeśli nie ma żadnych debugery zewnętrznych, które mogą być interpretowane przez Menedżera debugowania procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pErrorDebug`  
 [in] Wystąpił błąd czasu wykonywania.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 [out] Czy wywołać [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) Jeśli użytkownik zdecyduje kontynuować bez debugowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Powinny również implementować ten interfejs, aby otrzymywać powiadomienia.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptSiteDebugEx](../../winscript/reference/iactivescriptsitedebugex-interface.md)