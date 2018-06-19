---
title: Interfejs IDebugThreadCall | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugThreadCall interface
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b2b1b500aec08520166d9092edfa6a58c1df0fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794236"
---
# <a name="idebugthreadcall-interface"></a>Interfejs IDebugThreadCall
`IDebugThreadCall` Interfejsu jest zwykle implementowany przez składnik wywołań między wątkami z `IDebugThread` kierowanie implementacji zapewnione przez Menedżera debugowania procesu (PDM).  
  
 Wywołania PDM `IDebugThreadCall` interfejsu w wątku żądaną i `IDebugThreadCall` interfejsu wywołuje wywołanie żądanej implementacji. `IDebugThreadCall` Interfejsu rzutuje informacje na temat parametrów przekazanych do góry odpowiednie parametry.  
  
 `IDebugThreadCall` Interfejsu jest obiektem bezwątkowy.  
  
## <a name="methods"></a>Metody  
 Oprócz dziedziczone z metody `IUnknown`, `IDebugThreadCall` interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Obsługuje wywołania do uruchomienia kodu w innym wątku.|