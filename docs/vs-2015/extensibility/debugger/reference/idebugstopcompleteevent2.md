---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f880888ab675fc7923b50e3b1fbce144f8108abd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42688677"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugStopCompleteEvent2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugstopcompleteevent2).  
  
Aparat debugowania (DE) można wysłać zdarzenie to opcjonalne Menedżer debugowania sesji (SDM), po zatrzymaniu program.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Jest to nowy interfejs dla [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]. Wcześniejsze wersje nie obsługują zatrzymywanie asynchronicznego.  
  
 [Zatrzymaj](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) jest wywoływana przez SDM w scenariuszach wieloprocesowe lub wielu programów. Gdy jeden program wysyła zdarzenia zatrzymywanie SDM, SDM żądań inne programy, aby zatrzymać zbyt.  
  
 Służy do asynchronicznie powiadamia SDM, który programu została zatrzymana. Jest to przydatne dla aparat debugowania interpreter, których czasami żaden kod działa wewnątrz debugowanego programu, dzięki czemu [zatrzymać](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) nie może zostać ukończona synchronicznie. Jeśli aparat debugowania chce używać tego asynchronicznego powiadomienia, aplikacja musi zwracać `S_ASYNC_STOP` z [zatrzymać](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

