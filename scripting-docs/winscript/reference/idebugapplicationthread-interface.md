---
title: Interfejs IDebugApplicationThread | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread interface
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e731ba866504c9a3c3c9ad081a90a12b161355d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthread-interface"></a>Interfejs IDebugApplicationThread
Umożliwia aparaty języka i hosty synchronizacja wątku i przechowuje informacji o stanie debugowania właściwe dla wątków. Ten interfejs stanowi rozszerzenie `IRemoteDebugApplicationThread` interfejsu w celu zapewnienia dostępu zdalnego z systemem innym niż do wątku.  
  
 Oprócz dziedziczone z metody `IRemoteDebugApplicationThread`, `IDebugApplicationThread` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|Udostępnia mechanizm dla obiekt wywołujący, aby uruchomić kod w wątku aplikacji.|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|Określa, czy ten wątek jest aktualnie uruchomiony.|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|Określa, czy ten wątek jest wątek debugera.|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|Ustawia opis tego wątku.|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|Ustawia opis stan wątku.|