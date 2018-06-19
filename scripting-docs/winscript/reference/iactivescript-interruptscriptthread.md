---
title: IActiveScript::InterruptScriptThread | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.InterruptScriptThread
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_InterruptScriptThread
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad717ee950dda4f0f0d7a14292f0f5f150ab4973
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792082"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Przerwanie wykonywania uruchomiony wątek skryptu (obiekt sink zdarzenia, natychmiastowego wykonania lub wywołanie makra). Ta metoda umożliwia zakończenie skryptu, zatrzymane (na przykład w pętli nieskończonej). Może być wywołana z wątków innych niż podstawowe powodowała objaśnienia innych niż podstawowe do obiektów hosta lub do [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stidThread`  
 [in] Identyfikator wątku w celu przerwania lub jeden z następujących wartości identyfikatora wątku specjalne:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Wszystkie wątki. Przerwanie jest stosowany do wszystkich metod skryptu w toku. Należy pamiętać, że chyba, że obiekt wywołujący zażądał rozłączona skryptu, następne zdarzenie inicjowanych przez skrypty powoduje, że kod skryptu uruchomić ponownie, wywołując [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) metody z SCRIPTSTATE_DISCONNECTED lub Ustaw flagę SCRIPTSTATE_INITIALIZED.|  
|SCRIPTTHREADID_BASE|Podstawowy wątku; oznacza to, że utworzono wystąpienie wątku, w którym skryptów aparatu.|  
|SCRIPTTHREADID_CURRENT|Wątek aktualnie wykonywane.|  
  
 `pexcepinfo`  
 [in] Adres `EXCEPINFO` struktury zawierającej informacje o błędzie, który powinien być zgłaszane do skryptu zostało przerwane.  
  
 `dwFlags`  
 [in] Flagi opcji skojarzone z czas przestoju. Może być jedną z następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Jeśli jest to obsługiwane, wprowadź debugera aparat skryptów do bieżącego punkt wykonanie skryptu.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Jeśli jest to obsługiwane przez aparat skryptów języka, umożliwiają skryptu obsłużyć wyjątek. W przeciwnym razie metoda skryptu zostało przerwane i do wywołującego jest zwrócony kod błędu oznacza to, że element zdarzeń źródła lub makro wywołujący.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_INVALIDARG`|Argument był nieprawidłowy.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparatu skryptów jeszcze nie został załadowany lub zainicjować).|  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)