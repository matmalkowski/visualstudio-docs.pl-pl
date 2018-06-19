---
title: Interfejs IActiveScriptStats | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptStats interface
ms.assetid: dbe84d6f-1b77-4877-aced-cd4e01ead5b5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d459b89bde609dfdf5963d4b6b10b24db4706a7e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793633"
---
# <a name="iactivescriptstats-interface"></a>Interfejs IActiveScriptStats
Pozwala hostom zapytania statystyki uruchamianie skryptu. Hosta można użyć tych informacji do ustalenia, czy skrypt trwało zbyt długo.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IActiveScriptStats` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)|Zwraca jedną z statystyki skrypty standardowe.|  
|[IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)|Zwraca statystyki skryptu niestandardowego.|  
|[IActiveScriptStats::ResetStats](../../winscript/reference/iactivescriptstats-resetstats.md)|Resetuje statystyki dla tego skryptu.|