---
title: Interfejs IRemoteDebugApplication | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication interface
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea91afdc44b70a91846d7b1a3dc4c017c0c4c80e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795034"
---
# <a name="iremotedebugapplication-interface"></a>Interfejs IRemoteDebugApplication
Reprezentuje działającej aplikacji. Nie musi odpowiadać do procesu systemu operacyjnego. Zazwyczaj debugera dotyczy aplikacji do debugowania. Menedżer debugowania procesu zwykle implementuje obiektu aplikacji.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IRemoteDebugApplication` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|Nadal aplikacji, która jest aktualnie punktu przerwania.|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|Powoduje przerwanie w debugerze przy najbliższej okazji aplikacji.|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|Nawiązuje połączenie debugera do tej aplikacji.|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|Odłącza bieżący debuger z aplikacji.|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|Zwraca bieżący debuger jest podłączony do aplikacji.|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|Udostępnia mechanizm dla debugera IDE, uruchamianie poza procesem do aplikacji, do tworzenia obiektów w procesie aplikacji.|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|Wskazuje, czy aplikacja jest elastyczny.|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|Wylicza wszystkie wątki wiadomo, że są skojarzone z aplikacją.|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|Zwraca nazwę tego węzła aplikacji.|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|Zwraca węzła aplikacji, do którego są dodawane wszystkie węzły skojarzone z aplikacją.|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|Wylicza kontekstów wyrażenia globalnego dla wszystkich języków, działające w tej aplikacji.|