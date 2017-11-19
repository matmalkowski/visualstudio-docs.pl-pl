---
title: "Ijsdebugprocess — interfejs | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2a81104f51ca1a66c493779146b7eaa102ea300
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugprocess-interface"></a>IJsDebugProcess — Interfejs
Zawiera procedury sprawdzania i kontrolowania procesu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IJsDebugProcess::CreateBreakPoint — metoda](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Ustawia punkt przerwania w pozycji określonego dokumentu.|  
|[IJsDebugProcess::CreateStackWalker — metoda](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Metoda fabryki walkera stosu.|  
|[IJsDebugProcess::PerformAsyncBreak — metoda](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Umieszcza aparat skryptu w trybie przerwania powodowania podział na następną instrukcję skryptu.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)