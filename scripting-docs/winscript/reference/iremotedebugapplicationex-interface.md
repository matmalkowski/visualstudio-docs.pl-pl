---
title: Interfejs IRemoteDebugApplicationEx | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IRemoteDebugApplicationEx Interface
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3360cea0d1649348a795356ad827b32b6f8ebc19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationex-interface"></a>Interfejs IRemoteDebugApplicationEx
Reprezentuje działającej aplikacji. Nie musi odpowiadać procesu systemu operacyjnego. Zazwyczaj debugera dotyczy aplikacji do debugowania. Menedżer debugowania procesu zwykle implementuje obiektu aplikacji.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IRemoteDebugApplicationEx` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|Zwraca identyfikator procesu hosta aplikacji.|  
|GetHostMachineName|Zwraca nazwę komputera, na którym działa aplikacja hosta na.|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|Określa język dla lokalizacji debugera.|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|Wymusza debugera w tryb jednego kroku.|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|Odwołuje się polecenie break.|  
|SetProxyBlanketAndAddRef|Aktualizuje informacje o zabezpieczeniach COM na serwer proxy dla obiekt debugera w celu zapewnienia zgodności z debugowanie zdalne z systemów operacyjnych opartych na systemie Windows 95.|  
|ReleaseFromSetProxyBlanket|AddRef wersjach z SetProxyBlanketAndAddRef.|