---
title: IDebugStopCompleteEvent2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e92138f969189a33e1a5aad5a083c8ac57852dc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
Aparat debugowania (DE) umożliwia wysyłanie to opcjonalne zdarzenie do menedżera sesji debugowania (SDM), jeśli zostało zatrzymane.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Jest to nowy interfejs dla [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]. Wcześniejsze wersje nie obsługują zatrzymywania asynchronicznego.  
  
 [Zatrzymaj](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) jest wywoływana przez SDM w scenariuszach wieloprocesowa lub wielu programów. Gdy program wysyła zdarzeniem zatrzymującym SDM, SDM żądań inne programy, aby zatrzymać zbyt.  
  
 Służy do informowania asynchronicznie SDM, która została zatrzymana, program. Jest to przydatne dla aparatu debugowania interpreter, gdzie czasami żaden kod nie jest uruchomiony debugowany program, więc [zatrzymać](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) nie można synchronicznie wykonać. Jeśli aparat debugowania chce zastosować asynchroniczne odbieranie tego powiadomienia, musi zwracać `S_ASYNC_STOP` z [zatrzymać](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll