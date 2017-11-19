---
title: "Ijsdebugstackwalker — interfejs | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbea11bf1188d148818ea8a082bceec76c704c2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugstackwalker-interface"></a>IJsDebugStackWalker — Interfejs
Reprezentuje walkera stosu dla określonego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IJsDebugStackWalker::GetNext — metoda](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Pobiera następnej ramki.|  
  
## <a name="remarks"></a>Uwagi  
 Walkers stosu można tworzyć tylko w przypadku, gdy element docelowy zostanie zatrzymana i są nieprawidłowe, gdy proces docelowy jest kontynuowane ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)