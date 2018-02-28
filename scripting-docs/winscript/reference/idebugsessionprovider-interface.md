---
title: Interfejs IDebugSessionProvider | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugSessionProvider interface
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e61b1e5e794c68e34250f958cdda0f50b68334c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsessionprovider-interface"></a>Interfejs IDebugSessionProvider
Podstawowy interfejs dostarczony przez debuger IDE umożliwiające hosta i język zainicjować debugowania. Ustanawia ona sesję debugowania dla działającej aplikacji. Ten interfejs jest implementowany przez Menedżera maszyny debugowania.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IDebugSessionProvider` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Inicjuje sesję debugowania z określonej aplikacji.|