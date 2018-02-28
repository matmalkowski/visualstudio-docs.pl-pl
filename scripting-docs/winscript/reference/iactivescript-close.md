---
title: IActiveScript::Close | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.Close
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c90b5d089ea6665060944e0a6f720a43aa1295a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Powoduje, że aparat skryptów abandon dowolnego skryptu aktualnie załadowanych utratę stanu i zwolnić wszystkie wskaźniki interfejsu, wymagana jest wartość inne obiekty, w związku z tym wprowadzanie stanie zamkniętym. Wychwytywanie zdarzeń, natychmiast wykonać skryptu tekst i wywołań makra, które są już w toku zostały zakończone przed zmianą stanu (Użyj [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) anulować uruchomiony wątek skryptu). Tej metody należy wywołać można przez hosta tworzenia interfejsu zwolnieniu aby zapobiec problemom odwołanie cykliczne.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparatu skryptów jest już w stanie zamkniętym).|  
|`OLESCRIPT_S_PENDING`|Metoda została pomyślnie w kolejce, ale nie zmienił się stan jeszcze. Podczas zmiany stanu lokacji ma być wywołanie zwrotne [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) metody.|  
|`S_FALSE`|Metoda zakończyło się pomyślnie, ale skrypt został już zamknięty.|  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)