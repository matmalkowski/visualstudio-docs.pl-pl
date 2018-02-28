---
title: Wyliczenie SCRIPTSTATE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- SCRIPTSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTSTATE enum
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35e062a9c2f3076144063ffb77895c8a03ecc4ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="scriptstate-enumeration"></a>Wyliczenie SCRIPTSTATE
Określa stan aparatu skryptów. To wyliczenie jest używany przez [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) , i [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## <a name="enumeration-values"></a>Wartości wyliczenia  
  
|||  
|-|-|  
|SCRIPTSTATE_UNINITIALIZED|Skrypt został utworzony, ale nie została zainicjowana przy użyciu `IPersist*` interfejsu i [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|Skryptu został zainicjowany, ale nie systemem (Nawiązywanie połączenia z innymi obiektami lub wychwytywanie zdarzeń) lub jest wykonaniem jakiegokolwiek kodu. Kod może być badana wykonywania przez wywołanie metody [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md) metody.|  
|SCRIPTSTATE_STARTED|Skrypt można uruchomić kod, ale nie jest jeszcze wychwytywanie zdarzeń obiektów dodanych przez [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) — metoda.|  
|SCRIPTSTATE_CONNECTED|Skrypt jest załadowany i połączony wychwytywanie zdarzeń.|  
|SCRIPTSTATE_DISCONNECTED|Skrypt jest załadowany i ma stan wykonywania czasu wykonywania, ale jest tymczasowo odłączone od wychwytywanie zdarzeń.|  
|SCRIPTSTATE_CLOSED|Skrypt został zamknięty. Aparat skryptów już nie działa i zwraca informacje o błędach dla większości metod.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kody błędów, wyliczenia i stałe aktywnego skryptu](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)