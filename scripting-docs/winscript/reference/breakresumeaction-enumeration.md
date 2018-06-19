---
title: Wyliczenie BREAKRESUMEACTION | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1b830d314b1db40d7b83557d894ad6f8751bdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791878"
---
# <a name="breakresumeaction-enumeration"></a>Wyliczenie BREAKRESUMEACTION
Zawiera opis sposobów, aby kontynuować od punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum tagBREAKRESUME_ACTION {  
   BREAKRESUMEACTION_ABORT,  
   BREAKRESUMEACTION_CONTINUE,  
   BREAKRESUMEACTION_STEP_INTO,  
   BREAKRESUMEACTION_STEP_OVER,  
   BREAKRESUMEACTION_STEP_OUT,  
   BREAKRESUMEACTION_IGNORE,  
   BREAKRESUMEACTION_STEP_DOCUMENT,  
} BREAKRESUMEACTION;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|BREAKRESUMEACTION_ABORT|Przerywa aplikacji.|  
|BREAKRESUMEACTION_CONTINUE|Będzie kontynuował działanie.|  
|BREAKRESUMEACTION_STEP_INTO|Kroki opisane w procedurze.|  
|BREAKRESUMEACTION_STEP_OVER|Kroki opisane w procedurze.|  
|BREAKRESUMEACTION_STEP_OUT|Kroki poza bieżącą procedurę.|  
|BREAKRESUMEACTION_IGNORE|Będzie kontynuował działanie ze stanem.|  
|BREAKRESUMEACTION_STEP_DOCUMENT|Kroki, aby następny dokument.|  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe debugera aktywnego skryptu, wyliczenia i struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)