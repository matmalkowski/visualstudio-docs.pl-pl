---
title: Stałe SCRIPTTHREADID | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADID
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADID
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc692716115ea0c205b1cfd982b189fffd54a9ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796411"
---
# <a name="scriptthreadid-constants"></a>Stałe SCRIPTTHREADID
Można określić typ wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Stałe  
  
|Stała|Wartość|Znaczenie|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|Wątek aktualnie wykonywane.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|Podstawowy wątku; oznacza to, że utworzono wystąpienie wątku, w którym skryptów aparatu.|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|Wszystkie wątki.|  
  
## <a name="remarks"></a>Uwagi  
 `SCRIPTTHREADID` Typ jest używany przez `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState`, i `IActiveScript::InterruptScriptThread`, ale stałe może być używany tylko przez `IActiveScript::GetScriptThreadState` i `IActiveScript::InterruptScriptThread`.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)