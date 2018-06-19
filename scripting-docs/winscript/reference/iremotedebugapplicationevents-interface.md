---
title: Interfejs IRemoteDebugApplicationEvents | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplicationEvents interface
ms.assetid: 9626519e-910c-48e0-ae99-c711ce6628fd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04d40d3e03cfb9582075ec1be7abace963d1377f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795046"
---
# <a name="iremotedebugapplicationevents-interface"></a>Interfejs IRemoteDebugApplicationEvents
`IRemoteDebugApplicationEvents` Interfejs jest interfejsu zdarzenia dostarczone przez aplikację do debugowania. Ten interfejs jest zawsze wywołane wewnątrz wątek debugera.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IRemoteDebugApplicationEvents` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IRemoteDebugApplicationEvents::OnConnectDebugger](../../winscript/reference/iremotedebugapplicationevents-onconnectdebugger.md)|Zdarzenie połączenia dojść do a debugera.|  
|[IRemoteDebugApplicationEvents::OnDisconnectDebugger](../../winscript/reference/iremotedebugapplicationevents-ondisconnectdebugger.md)|Uchwyty a debugera zdarzenia rozłączenia.|  
|[IRemoteDebugApplicationEvents::OnSetName](../../winscript/reference/iremotedebugapplicationevents-onsetname.md)|Obsługuje zdarzenie nazwę zestawu.|  
|[IRemoteDebugApplicationEvents::OnDebugOutput](../../winscript/reference/iremotedebugapplicationevents-ondebugoutput.md)|Obsługuje zdarzenie danych wyjściowych debugera.|  
|[IRemoteDebugApplicationEvents::OnClose](../../winscript/reference/iremotedebugapplicationevents-onclose.md)|Obsługuje zdarzenie zamknięcia aplikacji.|  
|[IRemoteDebugApplicationEvents::OnEnterBreakPoint](../../winscript/reference/iremotedebugapplicationevents-onenterbreakpoint.md)|Obsługuje zdarzenie wprowadzania punktu przerwania.|  
|[IRemoteDebugApplicationEvents::OnLeaveBreakPoint](../../winscript/reference/iremotedebugapplicationevents-onleavebreakpoint.md)|Obsługuje zdarzenie opuszczenia punktu przerwania.|  
|[IRemoteDebugApplicationEvents::OnCreateThread](../../winscript/reference/iremotedebugapplicationevents-oncreatethread.md)|Obsługuje tworzenie zdarzenia wątku.|  
|[IRemoteDebugApplicationEvents::OnDestroyThread](../../winscript/reference/iremotedebugapplicationevents-ondestroythread.md)|Obsługuje zdarzenie zniszczone wątku.|  
|[IRemoteDebugApplicationEvents::OnBreakFlagChange](../../winscript/reference/iremotedebugapplicationevents-onbreakflagchange.md)|Obsługuje zdarzenie zmiany flagi podziału.|