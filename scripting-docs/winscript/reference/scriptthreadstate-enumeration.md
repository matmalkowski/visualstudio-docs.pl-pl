---
title: Wyliczenie SCRIPTTHREADSTATE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- SCRIPTTHREADSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADSTATE enum
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e18cc6f5f2afb1dcea6835983f69f6a6f7b9280
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="scriptthreadstate-enumeration"></a>Wyliczenie SCRIPTTHREADSTATE
Określa stan wątku aparatu skryptów. To wyliczenie jest używany przez [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>Wartości wyliczenia  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|Określony wątek nie jest obecnie obsługi zdarzenia przy użyciu skryptu, przetwarzania natychmiast wykonać skryptu tekstu, lub uruchomienie skryptu makra.|  
|SCRIPTTHREADSTATE_RUNNING|Określony wątek jest aktywnie obsługi zdarzenia przy użyciu skryptu, przetwarzania natychmiast wykonać skryptu tekstu, lub uruchomienie makra skryptu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kody błędów, wyliczenia i stałe aktywnego skryptu](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)