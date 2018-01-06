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
ms.workload: vssdk
ms.openlocfilehash: 5d59de29078db46f716fe9d01a3f3fa076139ddf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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