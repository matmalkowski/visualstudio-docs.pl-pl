---
title: Interfejs IDebugApplication110 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110 Interface
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd7c283e925db5b42b4d04bfc42ea087ecc22b6f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplication110-interface"></a>Interfejs IDebugApplication110
`IDebugApplication110` Interfejsu rozszerza funkcjonalność [interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md). Wystąpienie tego interfejsu można uzyskać przez wywołanie metody QueryInterface wykonania [interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md).  
  
> [!IMPORTANT]
>  Interfejs jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
## <a name="methods"></a>Metody  
 `IDebugApplication110` Interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|Wykonuje synchroniczne wywołania w głównym wątku.|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|Powoduje, że wywołanie asynchroniczne w głównym wątku.|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|Czeka na dowolny określony uchwyt do zasygnalizować zezwalając międzywątkowe do zaksięgowania tego wątku. Ta metoda musi zostać wywołana z wątku debugera.|