---
title: Interfejs IDebugApplicationThread110 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110 Interface
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aee30ae68319810f58bf31f8d0eb32cf8f30d34c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794059"
---
# <a name="idebugapplicationthread110-interface"></a>Interfejs IDebugApplicationThread110
Udostępnia więcej funkcji dla [interfejs IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md) interfejsu.  
  
> [!IMPORTANT]
>  Interfejs jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
## <a name="methods"></a>Metody  
 `IDebugApplicationThread110` Interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|Powoduje, że wywołanie asynchroniczne w głównym wątku.|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|Liczba aktualnie przetwarzanego liczbę żądań wątku z wątku PDM przełączanie mechanizmów. Zazwyczaj 0 lub 1, ale jego może to być większe, jeśli jedno wywołanie wątku rozpoczyna przetwarzanie, ale wyzwala synchroniczne wywołanie z wątku lub w przeciwnym razie wstrzymuje wątku (na przykład, wyzwalając zdarzenie IDebugApplicationEvents, który wydano dla debugera Wątek)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) została wywołana dla tego wątku i nie zostało jeszcze zakończone.|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|Ten wątek jest w stanie, który może przetwarzać wywołań za pomocą wątku PDM przełączanie mechanizmów (na przykład SynchronousCallInThread).|