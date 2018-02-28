---
title: Wyliczenie BREAKREASON | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- BREAKREASON
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKREASON enumeration
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf1baa8b627df50db33cbd86302ce06e80c1cf34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="breakreason-enumeration"></a>Wyliczenie BREAKREASON
Wskazuje powód przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|BREAKREASON_STEP|Aparat języka jest w trybie wykonywania krokowego.|  
|BREAKREASON_BREAKPOINT|Aparat języka napotkał jawne punktu przerwania.|  
|BREAKREASON_DEBUGGER_BLOCK|Aparat języka napotkał bloku debugera w innym wątku.|  
|BREAKREASON_HOST_INITIATED|Host żądana przerwy.|  
|BREAKREASON_LANGUAGE_INITIATED|Aparat języka żądana przerwy.|  
|BREAKREASON_DEBUGGER_HALT|Debuger IDE żądana przerwy.|  
|BREAKREASON_ERROR|Błąd wykonywania spowodował przerwy.|  
|BREAKREASON_JIT|Przyczyną uruchomienia debugowanie JIT.|  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe debugera aktywnego skryptu, wyliczenia i struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)