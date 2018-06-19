---
title: IActiveScriptSiteInterruptPoll::QueryContinue | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteInterruptPoll.QueryContinue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteInterruptPoll::QueryContinue
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93323d500ae7e99957c365d60741fa612ba0fc34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793678"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Umożliwia hosta określić, że skrypt należy zakończyć.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wywołanie zakończyło się pomyślnie i skryptu, aby kontynuować działanie zezwala na hoście.|  
|`S_FALSE`|Wywołanie zakończyło się pomyślnie i żądań hosta, które przerwanie skryptu.|  
  
## <a name="remarks"></a>Uwagi  
 Hostowanej skryptu należy zakończyć, chyba że wartość zwracana `QueryContinue` jest metoda `S_OK`. Zwracana wartość `S_FALSE` wskazuje, że host wyraźnie zażąda, że skrypt zakończyć.  
  
 Wielowątkowe hosta może używać `IActiveScript::InterruptScriptThread` metody zakończenie skryptu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptSiteInterruptPoll](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)