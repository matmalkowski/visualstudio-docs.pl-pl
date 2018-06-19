---
title: IDebugApplication::HandleRuntimeError | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleRuntimeError
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleRuntimeError
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eead4780ff061ff9c7280aeee0936c8f64741981
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793891"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Powoduje, że bieżący wątek zablokować, a następnie wysyła powiadomienie z informacją o błędzie do debugera w IDE.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pErrorDebug`  
 [in] Wystąpił błąd.  
  
 `pScriptSite`  
 [in] Witryna skryptu wątku.  
  
 `pbra`  
 [out] Akcja do wykonania po debuger wznowieniu działania aplikacji.  
  
 `perra`  
 [out] Działania w sytuacji, gdy debuger wznawia aplikacji, jeśli występuje błąd.  
  
 `pfCallOnScriptError`  
 [out] Flaga, która jest `TRUE` Jeśli aparat powinny wywoływać `IActiveScriptSite::OnScriptError` metody.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Aparat języka wywołuje tę metodę w kontekście wątku, który powoduje błąd czasu wykonywania. Ta metoda powoduje, że bieżący wątek zablokować i wysyła powiadomienia o błędach do wysłania do debugera w IDE. Gdy debuger IDE wznawia aplikacji, ta metoda zwraca o podjęcie działań.  
  
> [!NOTE]
>  W błędów czasu wykonywania aparatu język może zostać wywołana przez wątek do wykonywania takich zadań jak wyliczyć ramek stosu lub obliczać wyrażeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Interfejs IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [Wyliczenie BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)   
 [Wyliczenie ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)