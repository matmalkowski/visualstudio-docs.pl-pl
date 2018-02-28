---
title: Wyliczenie APPBREAKFLAGS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- APPBREAKFLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- APPBREAKFLAGS constants
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 126dcd704a60b591b71913f2e8e739de35c14636
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="appbreakflags-enumeration"></a>Wyliczenie APPBREAKFLAGS
Wskazuje bieżący stan debugowania aplikacji i wątków.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_APPBREAKFLAGS{APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,APPBREAKFLAG_STEP= 0x00010000,APPBREAKFLAG_NESTED= 0x00020000,APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,APPBREAKFLAG_IN_BREAKPOINT= 0x80000000};  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Wartość|Opis|  
|------------|-----------|-----------------|  
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|Aparat powinien natychmiast przerywanie na wszystkie wątki przy użyciu BREAKREASON_DEBUGGER_BLOCK.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|Aparat powinien natychmiast przerywanie przy użyciu BREAKREASON_DEBUGGER_HALT.|  
|APPBREAKFLAG_STEP|0x00010000|Aparat powinien natychmiast włamanie się wykonywania krokowego wątku z BREAKREASON_STEP.|  
|APPBREAKFLAG_NESTED|0x00020000|Aplikacja jest zagnieżdżony wykonywania na punkt przerwania.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|Debuger jest wykonywanie krok po kroku na poziomie źródła.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|Debuger jest wykonywanie krok po kroku na poziomie kodu bajtów.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|Debuger jest wykonywanie krok po kroku na poziomie komputera.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|Maska factoring limit typy kroku.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|Punkt przerwania jest w toku.|  
  
## <a name="remarks"></a>Uwagi  
 Niektóre flagi określają, że aparaty języka powinna zostać podzielona przy następnej okazji, podczas gdy inne flagi Określanie trybu wykonywania krokowego debugera.  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe debugera aktywnego skryptu, wyliczenia i struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [Wyliczenie BREAKREASON](../../winscript/reference/breakreason-enumeration.md)