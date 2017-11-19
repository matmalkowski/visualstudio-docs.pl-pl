---
title: Wyliczenie SCRIPT_DEBUGGER_OPTIONS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: SCRIPT_DEBUGGER_OPTIONS Enumeration
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54b910562670104f0fb5679f2b09780afcd17751
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="scriptdebuggeroptions-enumeration"></a>Wyliczenie SCRIPT_DEBUGGER_OPTIONS
Wskazuje zestaw opcji i/lub możliwości, które dotyczą dołączony debuger. Używane w [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) i [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  Te stałe są implementowane przez PDM 10.0 i większa. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Wartość|Opis|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|Opcje nie są ustawione.|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|Wskazuje, że wykonywania skryptów należy podnieść BREAKREASON_ERROR zdarzenia, gdy jest zgłaszany wyjątek. Ta opcja może ustawić przez debuger, lub ustaw przez kod użytkownika za pośrednictwem `Debug.enableFirstChanceExceptions(<true&#124;false>)`.|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|Wskazuje, że dołączony debuger obsługuje pracowników w sieci web.|  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe debugera aktywnego skryptu, wyliczenia i struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)